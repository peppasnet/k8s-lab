# K8s Lab — Everything as Code

Every resource in this cluster is defined in YAML. Nothing is created manually.

## Structure

```
k8s-lab/
├── namespaces/       # Namespace definitions
├── rbac/             # Users, roles, permissions
├── apps/
│   ├── nginx/        # Test app
│   └── postgres/     # Database
└── README.md
```

## Apply everything

```bash
# Apply in order: namespaces first, then RBAC, then apps
kubectl apply -f namespaces/
kubectl apply -f rbac/
kubectl apply -f apps/nginx/
kubectl apply -f apps/postgres/
```

## Destroy everything

```bash
kubectl delete -f apps/postgres/
kubectl delete -f apps/nginx/
kubectl delete -f rbac/
kubectl delete -f namespaces/
```

## See what's running

```bash
kubectl get all -A          # Everything across all namespaces
kubectl get all -n dev      # Everything in dev namespace
kubectl get pods -o wide    # Which pod is on which node
kubectl top nodes           # Node CPU/memory
kubectl top pods -A         # Pod CPU/memory
```
