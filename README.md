# TMC Flux SSH Fix


This is a quick fix for the issue reported [here](https://github.com/fluxcd/flux2/issues/4726). This is needed until the TMC provided flux adds this argument to the sourcecontroller.


## How it works

This implements a gatekeeper mutation policy that will add the correct arguments to source-controller pod. after adding the mutation, a restart of the pod will inject the fix.


## Usage


apply the mutate policy

```bash

k apply -f add-arg.yml

k delete pod -n tanzu-source-controller -l app=source-controller
```


## Removal

to remove this after the fix is ready from TMC

```bash

k delete -f add-arg.yml

k delete pod -n tanzu-source-controller -l app=source-controller
```