# openapi-implementation-tracker
A repo to track openapi implementations

## Project Goals
There are many many openapi implementations, but it is unclear exactly which features they support, and which version of openapi document they support.
One can curate a list but it will become out of date as time goes on. We can do better than manual curation of a list.
Instead, a listing of a projects supported features should be maintained by individual projects with a standard file format.
This project defines that standard file format, and will inlcude all of those files in one place and collate the data into a listing of implementations with suppoted features.
When new features are added, the workflow is:
- source project udates their supprted feature file; file PR
- this project updates the git submodule to pull in the latest version of that file; file PR
- updates published to github pages

## What would this Standard File Look Like?
- Json schema definitions of openapi documents exist here and are versioned: https://github.com/OAI/OpenAPI-Specification/blob/main/schemas/v3.0/schema.yaml
- I propose writing files based on that yaml where the json paths are preserved, and the values are an object:
```
FeatureSupportInfo:
  type: object
  properties:
    supported:
      type: boolean
    docUrl:
      type: string
    verificationTestUrl:
      type: string
  required:
  - supported
```
So for example if root document servers are supported, the value for `#/servers` would be an instance of FeatureSupportInfo

Questions:
- Can this be one already using additionalProperties?
- Can one json schema file extend another?

## Todo
- demonstrate git submodule connection to one file
- see https://stackoverflow.com/questions/6238590/set-git-submodule-to-shallow-clone-sparse-checkout
- see https://web.archive.org/web/20150819045120/http://blog.quilitz.de/2010/03/checkout-sub-directories-in-git-sparse-checkouts

## Similar-To Projects
- https://github.com/OAI/Tooling
- https://github.com/apisyouwonthate/openapi.tools
