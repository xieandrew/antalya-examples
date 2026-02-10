# Antalya Setup Guide

This guide explains how to set up Project Antalya on different environments. Find the instructions for 
each environment below:
* Docker Compose - Try out Antalya quickly on a local machine
* Kubernetes - Deploy on EKS or locally with Minikube

## Docker Compose

The [Docker Compose file](../docker/docker-compose.yml) bundles the following containers together for a complete Antalya setup:
- ClickHouse vector server for issuing queries
- 2x ClickHouse swarm servers
- ClickHouse keeper server
- ice-rest-catalog, the catalog for Iceberg
- MinIO for local S3-compatible object storage
- spark-iceberg

For detailed instructions, follow the docker [README](../docker/README.md).

## Kubernetes

The Kubernetes setup example works on both EKS and Minikube.

### EKS

For a complete Amazon EKS setup, follow the steps in the Kubernetes [README](../kubernetes/README.md).

You can also find instructions for each part of the setup:
1. [Applying the Terraform configuration](../kubernetes/terraform/README.md)
2. [Installing the Altinity Kubernetes Operator for ClickHouse](../kubernetes/README.md#install-the-altinity-operator-for-kubernetes)
3. [Setting up ice-rest-catalog and S3](../kubernetes/ice/README.md)
4. [Applying Kubernetes manifests](../kubernetes/manifests/README.md)

### MiniKube

[MiniKube](https://minikube.sigs.k8s.io/docs/) lets you run Antalya on local Kubernetes.
The helm chart provides a setup that includes the ClickHouse vector, swarm, and keeper nodes plus
ice-rest-catalog and MinIO for local S3 storage.

First, you must have a MiniKube cluster running with the [Altinity Kubernetes Operator](../kubernetes/README.md#install-the-altinity-operator-for-kubernetes)
already installed. Make sure the cluster has at least 50GB of storage available. Then,
just [install the helm chart](../kubernetes/README.md#minikube).
