[![](https://img.shields.io/nuget/v/soenneker.cursor.cloudagents.openapiclient.svg?style=for-the-badge)](https://www.nuget.org/packages/soenneker.cursor.cloudagents.openapiclient/)
[![](https://img.shields.io/github/actions/workflow/status/soenneker/soenneker.cursor.cloudagents.openapiclient/publish-package.yml?style=for-the-badge)](https://github.com/soenneker/soenneker.cursor.cloudagents.openapiclient/actions/workflows/publish-package.yml)
[![](https://img.shields.io/nuget/dt/soenneker.cursor.cloudagents.openapiclient.svg?style=for-the-badge)](https://www.nuget.org/packages/soenneker.cursor.cloudagents.openapiclient/)
[![](https://img.shields.io/github/actions/workflow/status/soenneker/soenneker.cursor.cloudagents.openapiclient/codeql.yml?label=CodeQL&style=for-the-badge)](https://github.com/soenneker/soenneker.cursor.cloudagents.openapiclient/actions/workflows/codeql.yml)

# Soenneker.Cursor.CloudAgents.OpenApiClient

A generated .NET client for creating and managing Cursor Cloud Agents, runs, repositories, models, artifacts, usage, and run streams.

## Installation

```bash
dotnet add package Soenneker.Cursor.CloudAgents.OpenApiClient
```

## Create the client directly

```csharp
using System.Net.Http.Headers;
using Microsoft.Kiota.Abstractions.Authentication;
using Microsoft.Kiota.Http.HttpClientLibrary;
using Soenneker.Cursor.CloudAgents.OpenApiClient;

using var httpClient = new HttpClient();
httpClient.DefaultRequestHeaders.Authorization =
    new AuthenticationHeaderValue("Bearer", apiKey);

var authentication = new AnonymousAuthenticationProvider();
using var adapter = new HttpClientRequestAdapter(authentication, httpClient: httpClient);
var client = new CursorCloudAgentsOpenApiClient(adapter);

var keyInfo = await client.V1.Me.GetAsync(cancellationToken: cancellationToken);
```

The client defaults to `https://api.cursor.com`. Cursor also accepts Basic authentication with the API key as the username and an empty password; the example uses the equivalent bearer scheme.

Endpoints follow Kiota's request-builder hierarchy beneath `client.V1`. Generated methods accept request-configuration callbacks and cancellation tokens, while request and response types live in `Soenneker.Cursor.CloudAgents.OpenApiClient.Models`.

For managed transport reuse and configuration, use `Soenneker.Cursor.CloudAgents.OpenApiClientUtil` with `Soenneker.Cursor.CloudAgents.HttpClients`.

This repository contains generated source. Keep application-specific behavior in wrapper services or separate partial-class files because regeneration can replace generated files.
