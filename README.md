# Building Quarkus using Tekton, Maven, Jib and GraalVM

Quarkus guide: https://quarkus.io/guides/rest-json

This repository is a fork of one of the Quarkus example repositories **rest-json-quickstart**, and is largely unchanged.

The interesting parts in the `pipelines` directory.

- `Pipeline` to fetch and build
- `Task` to define a Quarkus/Maven/Jib/GraalVM build
- `PersistentVolumeClaim` to stop the business from being miserably slow
- `PipelineRun` sample file to get things started

### Performance

The _standard_ build takes 8 seconds, but with Tekton overhead takes about 30 seconds in total to push the image.

The _native image_ build takes around 3:30 minutes, or a bit over 4 minutes in total. 
The size of the final images is about 50MB.


### Credentials

Tekton credentials are tricky, but we haven't covered them here. However, this process does work fine with:
 
- private Git repositories
- private image registries
