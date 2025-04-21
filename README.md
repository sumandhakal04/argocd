# Argo CD Example: GitOps Deployment

This repository demonstrates a basic GitOps workflow using [Argo CD](https://argo-cd.readthedocs.io/en/stable/), a declarative continuous delivery tool for Kubernetes.

## 📁 Repository Structure

```
argocd/
└── apps/
    └── example-app/
        ├── deployment.yaml
        ├── service.yaml
        └── ...
```

- `apps/example-app/`: Contains Kubernetes manifests for deploying the `example-app`.

## 🚀 Getting Started

### Prerequisites

- A Kubernetes cluster
- Argo CD installed in the cluster

### Deploying the Application

1. **Register the Git repository with Argo CD**:

   ```bash
   argocd repo add https://github.com/sumandhakal04/argocd
   ```

2. **Create the Argo CD application**:

   ```bash
   argocd app create example-app \
     --repo https://github.com/sumandhakal04/argocd \
     --path apps/example-app \
     --dest-server https://kubernetes.default.svc \
     --dest-namespace default
   ```

3. **Sync the application**:

   ```bash
   argocd app sync example-app
   ```
