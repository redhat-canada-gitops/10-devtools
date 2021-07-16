# OpenShift ServiceMesh - Control Plane

Installs the Control Plane component of OpenShift ServiceMesh.

## Prerequisites

First, install the following operators in your cluster:

- [Openshift Elasticsearch Operator](../elasticsearch-operator)
- [Red Hat Openshift Jaeger Operator](../jaeger-operator)
- [Kiali Operator](../kaili-operator)
- [OpenShift ServiceMesh Operator](../openshift-servicemesh-operator)

Review the [Service Mesh Install](https://docs.openshift.com/container-platform/4.7/service_mesh/v1x/installing-ossm.html#jaeger-operator-install-elasticsearch_installing-ossm-v1x) documentation for information on specific versions of the operators to install for your cluster version.

Do not use the `base` directory directly, as you will need to patch the `channel` and `version` based on the version of OpenShift you are using, or the version of the operator you want to use.

The current *overlays* available are:
* [v2.0](overlays/v2.0)

## Usage

If you have cloned the `catalog` repository, you can install Noobaa by running from the root `catalog` directory

```
oc apply -k openshift-servicemesh-controlplane/overlays/v2.0
```

Or, without cloning:

```
oc apply -k https://github.com/redhat-canada-gitops/catalog/openshift-servicemesh-controlplane/overlays/v2.0
```

As part of a different overlay in your own GitOps repo:

```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization

bases:
  - github.com/redhat-canada-gitops/catalog/openshift-servicemesh-controlplane/overlays/v2.0?ref=master
```