# Helm Charts

A collection of Helm charts for Kubernetes and OpenShift deployments.

## Usage

```bash
helm repo add yakovbeder https://yakovbeder.github.io/helm-charts
helm repo update
```

## Available Charts

| Chart | Version | App Version | Description |
|-------|---------|-------------|-------------|
| [wiki](#wiki) | 3.1.0 | 2 | Wiki.js - open source wiki software (OpenShift ready) |
| [redhat-rhaap-portal](#redhat-rhaap-portal) | 2.1.0 | 2.1.1 | Ansible self-service automation portal |

---

### wiki

The most powerful and extensible open source Wiki software ([Wiki.js](https://js.wiki)), modified for OpenShift compatibility.

**OpenShift modifications (v3.1.0):**
- OpenShift Route with TLS edge termination (enabled by default instead of Ingress)
- Security contexts compatible with the `restricted` SCC (`runAsNonRoot`, `drop ALL`, `seccompProfile`)
- PostgreSQL 18 deployed as a StatefulSet with matching security contexts

**Install:**

```bash
helm install wikijs yakovbeder/wiki -n wikijs --create-namespace
```

**Install with custom values:**

```bash
helm install wikijs yakovbeder/wiki -n wikijs --create-namespace \
  --set route.host=wiki.apps.example.com \
  --set postgresql.postgresqlPassword=changeme
```

**Images used:**
- `requarks/wiki:2`
- `postgres:18`

---

### redhat-rhaap-portal

A Helm chart to deploy the Red Hat Ansible Automation Platform self-service automation portal.

**Install:**

```bash
helm install rhaap yakovbeder/redhat-rhaap-portal -n rhaap --create-namespace
```
