# API client integration

The supported integration surface today is the REST API and its generated
OpenAPI description. The repository publishes the specification at
`backend/docs/openapi.json` and `backend/docs/openapi.yaml`; use those files
with an OpenAPI generator for the language of your choice.

## REST API

Set the API base URL to your deployment and send the bearer token returned by
the wallet authentication flow:

```bash
curl -H "Authorization: Bearer $TOKEN" \
  "$MARKETPAY_API/api/jobs?status=open&limit=20"
```

The endpoint paths, request shapes, response types, and error schema are
defined in the OpenAPI files. The backend is the source of truth; regenerate
the specification when routes change.

## Repository client package

`packages/client/` currently contains the `MessageThread` UI component and a
small generated TypeScript schema/client package. It is not published to npm
and does not yet provide the fluent `client.jobs` API described by the old
version of this document. Treat it as repository source, not an installable
SDK.

## Planned SDKs

Dedicated TypeScript, Python, and Go packages remain planned. Until the SDK
bootstrap work is complete, generate a client from the OpenAPI document or
call the REST API directly. This keeps the documentation aligned with what
can be installed and run today.
