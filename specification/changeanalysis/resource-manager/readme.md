# changeanalysis

> see https://aka.ms/autorest

This is the AutoRest configuration file for changeanalysis.

## Getting Started

To build the SDKs for My API, simply install AutoRest via `npm` (`npm install -g autorest`) and then run:

> `autorest readme.md`

To see additional help and options, run:

> `autorest --help`

For other options on installation see [Installing AutoRest](https://aka.ms/autorest/install) on the AutoRest github page.

---

## Configuration

### Basic Information

These are the global settings for the changeanalysis.

``` yaml
openapi-type: arm
tag: package-2021-04-01
```

### Tag: package-2020-04-01-preview

These settings apply only when `--tag=package-2020-04-01-preview` is specified on the command line.

``` yaml $(tag) == 'package-2020-04-01-preview'
input-file:
- Microsoft.ChangeAnalysis/preview/2020-04-01-preview/changeanalysis.json
```

### Tag: package-2021-04-01

These settings apply only when `--tag=package-2021-04-01` is specified on the command line.

``` yaml $(tag) == 'package-2021-04-01'
input-file:
- Microsoft.ChangeAnalysis/stable/2021-04-01/changeanalysis.json
```

---

# Code Generation

## Swagger to SDK

This section describes what SDK should be generated by the automatic system.
This is not used by Autorest itself.

``` yaml $(swagger-to-sdk)
swagger-to-sdk:
  - repo: azure-sdk-for-python-track2
  - repo: azure-sdk-for-java
  - repo: azure-sdk-for-go
  - repo: azure-sdk-for-js
  - repo: azure-sdk-for-ruby
    after_scripts:
      - bundle install && rake arm:regen_all_profiles['azure_mgmt_changeanalysis']
  - repo: azure-resource-manager-schemas
```

## Go

See configuration in [readme.go.md](./readme.go.md)

## Python

See configuration in [readme.python.md](./readme.python.md)

## Ruby

See configuration in [readme.ruby.md](./readme.ruby.md)

## TypeScript

See configuration in [readme.typescript.md](./readme.typescript.md)

## CSharp

See configuration in [readme.csharp.md](./readme.csharp.md)

## Suppression

``` yaml
directive:
  - suppress: BodyTopLevelProperties
    where: $.definitions.ConfigurationProfileResource.properties
    from: changeanalysis.json
    reason: |-
      https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/common-api-contracts.md#system-metadata-for-all-azure-resources

      The systemData should be top level element based on the new requirement: 
      {
        "id": "/subscriptions/{id}/resourceGroups/{group}/providers/{rpns}/{type}/{name}",
        "name": "{name}",
        "type": "{resourceProviderNamespace}/{resourceType}",
        "location": "North US",
        "systemData":{
            "createdBy": "<string>",
            "createdByType": "<User|Application|ManagedIdentity|Key>",
            "createdAt": "<date-time>",
            "lastModifiedBy": "<string>",
            "lastModifiedByType": "<User|Application|ManagedIdentity|Key>",
            "lastModifiedAt": "<date-time>"
        },
        "tags": {
          "key1": "value 1",
          "key2": "value 2"
        },
        "kind": "resource kind",
        "properties": {
          "comment": "Resource defined structure"
        }
      }
```


