# Cyphernode

## API v1 (RESTful)

### Collections

#### watchedAddresses

| Request | Descripton |
|---------|------------|
| `POST /v1/watchedAddresses` | Create new address watch |
| `GET /v1/watchedAddresses` | Get list of watched addresses |
| `GET /v1/watchedAddresses/<address>` | Get details of watched address |
| `DELETE /v1/watchedAddresses/<address>` | Remove watched address |

##### POST /v1/watchedAddresses

Request body
```
{
  "address": <string: address>,
  "callback": <string: url>
}
```

Response body - 200 - OK
```
{
  "id": <int>,
  "address": <string: address>,
  "callback": <string: url>",
  "estimatesmartfee2blocks": <float: bitcoin>,
  "estimatesmartfee6blocks": <float: bitcoin>,
  "estimatesmartfee36blocks": <float: bitcoin>,
  "estimatesmartfee144blocks": <float: bitcoin>
}
```

Response body - 503 - Resource temporarily unavailable
```
{
  "reason": <string: reason>
}
```

Response body - 403 - Forbidden
```
{
}
```

##### GET /v1/watchedAddresses

Response body - 200 - OK
```
[
  {
    "id": <int>,
    "address": <string: address>,
    "imported": <bool>,
    "callback": <string: url>,
    "watching_since": <datetime: ISO8601-UTC>
  },
  ...
]
```

Response body - 503 - Resource temporarily unavailable
```
{
  "reason": <string: reason>
}
```

Response body - 403 - Forbidden
```
{
}
```

##### GET /v1/watchedAddresses/\<address\>

Response body - 200 - OK
```
{
  "id": <int>,
  "address": <string: address>,
  "imported": <bool>,
  "callback": <string: url>,
  "watching_since": <datetime: ISO8601-UTC>
}
```

Response body - 503 - Resource temporarily unavailable
```
{
  "reason": <string: reason>
}
```

Response body - 403 - Forbidden
```
{
}
```

Response body - 404 - Not found
```
{
}
```


##### DELETE /v1/watchedAddresses/\<address\>

Response body - 200 - OK
```
{
  "address": "<address>",
  "imported": <bool>,
  "callback": <string: url>,
  "watching_since":  <datetime: ISO8601-UTC>
}
```

Response body - 503 - Resource temporarily unavailable
```
{
  "reason": <string: reason>
}
```

Response body - 403 - Forbidden
```
{
}
```

Response body - 404 - Not found
```
{
}
```

##### Asynchronous callbacks

Request body
```
{
  "id": <int> ,
  "address": <string: address>,
  "hash": <string: hash>,
  "vout_n": <int>,
  "sent_amount": <float: bitcoin>,
  "confirmations": <int>,
  "received":  <datetime: ISO8601-UTC>,
  "size": <int: bytes>,
  "vsize": <int: bytes>,
  "fees": <float: bitcoin>,
  "is_replaceable": <bool>,
  "blockhash": <string: hash>,
  "blocktime": <int>,
  "blockheight": <int>
}
```

Response body - 200 - OK
```
{
}
```

Response body - 503 - Resource temporarily unavailable
```
{
  "reason": <string: reason>
}
```

