# Weblio Kubernetes applications

A comprehensive Kubernetes cluster running on Talos OS in Proxmox, featuring a complete homelab setup with media services, authentication, monitoring, and productivity applications.

## 🚀 Deployment Patterns

### Standard Application Deployment
Each application follows a consistent deployment pattern:

```
<application-name>/
├── <application-name>-namespace.yaml        # Kubernetes namespace
├── <application-name>-statefulset.yaml      # Main application deployment
├── <application-name>-service.yaml          # Service definition
├── <application-name>-ingress.yaml          # Traefik ingress rules
├── <application-name>-sealed-secrets.yaml   # Encrypted sensitive configuration (if needed)
```

### Security Considerations
- **Sealed Secrets**: Sensitive configuration is encrypted using [Sealed Secrets](sealed-secrets/README.md) and safely stored in Git
- Regular secrets containing plain text are never committed to the repository
- Ingress routes are configured with appropriate middleware

## 🛠️ Management Commands

### Application Deployment
```bash
# Deploy a specific application
kubectl apply -f application-name/

# Check application status
kubectl get all -n application-namespace

# View logs
kubectl logs -f -n application-namespace deployment/application-name
```
