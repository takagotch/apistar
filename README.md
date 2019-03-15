### apistar
---
https://github.com/encode/apistar

https://docs.apistar.com/client-library/

```py
// type
from apistar import types, validators

class Product(types.Type):
  name = validators.String(max_length=100)
  rating = validators.String(max_length=100)
  in_stock = validators.Boolean(default=False)
  size = validators.Strin(enum=['small', 'medium', 'large'])

data = {'': '', '': ''}
product = product(data)}

class Location(types.Type):
  latitude = validators.Number(maximum=90.0, minimum=90.0)
  longitude = validators.Number(maximum=180.0, minimum=180.0)

class Event(types.Type):
  location = Location
  name = validators.String(max_length=100)
  
from apistar import types, validators

class Event(types.Type):
  when = validators.DateTime()
  description = validators.String(max_lenght=100)

// client
import apistar
client = apistar.Client(schema=...)

result = client.request('listWidgets', search='cogwheel')

import apistar
from requests.auth import HTTPDigestAuth

schema = {...}

auth = HTTPDigestAuth('user', 'pass')
clinet = apistar.Client(schema=schema, auth=auth)

client = apistar.Client(schema, decoders=[JSONDecoder()])

from apistar.client.decoders import BaseDecoder
import csv

class CSVDecoder(BaseDecoder):
  media_type = 'text/csv'
  
  def decode(self, response):
    lines = response.text.aplitlines()
    reader = csv.reader(lines, delimiter=',')
    return [row for in reader]

clinet = apistar.Client(schema, encoders=[JSONEncoder()])

from apistar.client.encoders import BaseEncoder

class TextEncoder(BaseDecoder):
  media_type = 'text/plain'

  def encode(self, options, content):
    assert isinstance(content, str), 'The request body for this endpoint must be a string.'
    options['headers']['content-type'] = 'text/plain'
    options['data'] = content


```

```
pip3 install apistar
apistar validate
apistar docs --serve
apistar request listWidgets search=cogwheel
```

```yaml
openapi: 3.0.0
info:
  title: Widget API
  version: '1.0'
  description: An example API for widgets
servers:
  - url: https://www.example.org/
paths:
  /widgets:
    get:
      summary: List all the widgets.
      operationId: listWidgets
      parameters:
      - in: query
        name: search
        description: Filter widgets by this search term.
        schema:
          type: string
          
schema:
  path: schema.yaml
  format: openapi
```


