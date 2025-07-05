# Generic Node.js Helm Chart

This repository contains a **generic Helm chart template** for deploying Node.js applications to Kubernetes. It supports production-ready configurations, scaling, environment variables, secrets, and integration with GitOps workflows like **Argo CD**.

---

## Usage

### 1. Clone the Chart

This chart is meant to be **stored in a Helm module repository** (e.g., `dev.boni.co.in/helm-modules.git`) under a folder like `node-js`.

### 2. Define Application-Specific Values

Create a `values.yaml` file **outside this repo**, typically inside your **GitOps repository** (e.g., `helmcharts/nodejs1/values.yaml`).

Use the `values.example.yaml` provided here as a reference.

> **Do not commit environment-specific `values.yaml` files into this module repo.**

---

## values.yaml Location

- **Chart repo:** `https://dev.boni.co.in/helm-modules.git/node-js/`
- **Your values.yaml:** `https://dev.boni.co.in/gitea/DevOps/helmcharts.git → {app_name}/values.yaml`

This `values.yaml` should be referenced either:
- Inline in your Argo CD `Application` manifest (`helm.values`)
- Or with `helm.valueFiles` (if both chart and values are in the same repo)

## Usage guide

replicaCount: Number of pod replicas to run.
image: Container image details (repository, tag, port).
service: Kubernetes service type and port exposed.
resources: CPU and memory limits/requests.
ingress: Enable and configure Ingress rules and TLS.
env: Environment variables passed to the application.
secret: Sensitive environment variables (stored as Kubernetes secrets).
strategy: Deployment strategy (e.g., RollingUpdate).
hpa: Horizontal Pod Autoscaler settings.
vpa: Vertical Pod Autoscaler resource boundaries.
affinity, tolerations, nodeSelector: Advanced pod scheduling options.

---
