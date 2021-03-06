## IsReady

Type
: Function

Sender
: SDL

Purpose
: Request ready state of <abbr title="Text To Speech">TTS</abbr> Module

### Request

!!! note

1. SDL sends `TTS.IsReady` request after HMI confirms its readiness via `BC.OnReady` notification.
2. If HMI responds with `"available":false`, SDL will not further communicate over <abbr title="Text To Speech">TTS</abbr> interface with HMI.
3. If HMI does not respond during SDL's default timeout, SDL will continue to send RPCs over <abbr title="Text To Speech">TTS</abbr> interface to HMI.

!!!

#### Parameters

This RPC has no additional parameter requirements

### Response

!!! must

1. Check whether <abbr title="Text To Speech">TTS</abbr> component is available and ready.
2. Respond correspondingly to results of this check.

!!!

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|available|Boolean|true||

### Sequence Diagrams

|||
IsReady
![IsReady](./assets/IsReady.png)
|||

### JSON Message Examples

#### Example Request

```json
{
  "id" : 45,
  "jsonrpc" : "2.0",
  "method" : "TTS.IsReady"
}
```

#### Example Response

```json
{
  "id" : 45,
  "jsonrpc" : "2.0",
  "result" :
  {
    "available" : true,
    "code" : 0,
    "method" : "TTS.IsReady"
  }
}
```

#### Example Error

```json
{
  "id" : 45,
  "jsonrpc" : "2.0",
  "error" :
  {
    "code" : 11,
    "message" : "Invalid data",
    "data" :
    {
      "method" : "TTS.IsReady"
    }
  }
}
```
