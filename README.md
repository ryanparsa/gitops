
#### Apply Backend Prod Application
```bash
kubectl apply -f gitops-repo/backend/overlays/prod/application.yaml
```

#### Apply Backend Beta Application
```bash
kubectl apply -f gitops-repo/backend/overlays/beta/application.yaml
```

#### Apply Frontend Prod Application
```bash
kubectl apply -f gitops-repo/frontend/overlays/prod/application.yaml
```

#### Apply Frontend Beta Application
```bash
kubectl apply -f gitops-repo/frontend/overlays/beta/application.yaml
```

### Verify ArgoCD Sync

Once you’ve applied the `application.yaml` files, ArgoCD will start monitoring the GitOps repository for changes in those specific paths and sync the resources to your Kubernetes cluster. To verify that everything is synced correctly, you can:

1. **Access the ArgoCD UI**:
   - You can access the ArgoCD UI by port-forwarding the ArgoCD server to your local machine:
     ```bash
     kubectl port-forward svc/argocd-server -n argocd 8080:443
     ```
   - Then, visit `https://localhost:8080` in your browser and log in.

2. **Check Application Status**:
   - In the ArgoCD UI, you should see your applications (`backend-prod`, `backend-beta`, `frontend-prod`, `frontend-beta`) listed.
   - ArgoCD will automatically sync these applications by pulling the configuration from your GitOps repo and applying it to the cluster.
