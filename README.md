![ci [CMS]](https://github.com/fastmachinelearning/SuperSONIC/actions/workflows/ci-github-cms.yaml/badge.svg)
![docs](https://github.com/fastmachinelearning/SuperSONIC/actions/workflows/sphinx-docs.yaml/badge.svg)

# SuperSONIC

This Helm chart will install components depicted at the diagram below, excluding Prometheus and model repository, which must be connected by specifying relevant parameters in configuration file (see configuration reference below).

In its current form, the chart allows to deploy multiple server instances with different settings at once. This can be useful if you need to host servers with different GPU models, different Triton server versions, or different model repository mounts. 

For correct behavior, the server saturation metric (`servers[].prometheus.serverAvailabilityMetric`) used by Envoy proxy and autoscaler must be carefully defined.
It is recommended to start with examining the metric in Prometheus interface, in order to
define an appropriate threshold and avoid typos in the metric definition.

The KEDA autoscaler can be enabled / disabled via the `servers[].autoscaler.enabled` parameter.

![diagram](docs/img/diagram.svg "SONIC Server Infrastructure")