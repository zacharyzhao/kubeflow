# memcached

> Memcached is an in-memory key-value store for small chunks of arbitrary data (strings, objects) from results of database calls, API calls, or page rendering.

* [Quickstart](#quickstart)
* [Using Prototypes](#using-prototypes)
  * [io.ksonnet.pkg.memcached-simple](#io.ksonnet.pkg.memcached-simple)

## Quickstart

*The following commands use the `io.ksonnet.pkg.memcached-simple` prototype to generate Kubernetes YAML for memcached, and then deploys it to your Kubernetes cluster.*

First, create a cluster and install the ksonnet CLI (see root-level [README.md](rootReadme)).

If you haven't yet created a [ksonnet application](linkToSomewhere), do so using `ks init <app-name>`.

Finally, in the ksonnet application directory, run the following:

```shell
# Expand prototype as a Jsonnet file, place in a file in the
# `components/` directory. (YAML and JSON are also available.)
$ ks prototype use io.ksonnet.pkg.memcached-simple memcached \
  --name memcached \
  --namespace default

# Apply to server.
$ ks apply -f memcached.jsonnet
```

## Using the library

The library files for memcached define a set of relevant *parts* (_e.g._, deployments, services, secrets, and so on) that can be combined to configure memcached for a wide variety of scenarios. For example, a database like Redis may need a secret to hold the user password, or it may have no password if it's acting as a cache.

This library provides a set of pre-fabricated "flavors" (or "distributions") of memcached, each of which is configured for a different use case. These are captured as ksonnet *prototypes*, which allow users to interactively customize these distributions for their specific needs.

These prototypes, as well as how to use them, are enumerated below.

### io.ksonnet.pkg.memcached-simple

Deploys Memcached on a your Kubernetes cluster through a stateful set with 3replicas, pod distribution budget (pdb), and service. Memcached
can be accessed via port 11211 within the cluster.

#### Example

```shell
# Expand prototype as a Jsonnet file, place in a file in the
# `components/` directory. (YAML and JSON are also available.)
$ ks prototype use io.ksonnet.pkg.memcached-simple memcached \
  --namespace YOUR_NAMESPACE_HERE \
  --name YOUR_NAME_HERE
```

Below is the Jsonnet file generated by this command.

```
// memcached.jsonnet
<JSONNET HERE>
```

#### Parameters

The available options to pass prototype are:

* `--namespace=<namespace>`: Namespace in which to put the application [string]
* `--name=<name>`: Name to give to each of the components [string]


[rootReadme]: https://github.com/ksonnet/mixins