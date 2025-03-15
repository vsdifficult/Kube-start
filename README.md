# pgAdmin Kubernetes Cluster

This repository contains Kubernetes configuration files for deploying a cluster of pgAdmin servers.

## Components

- **Namespace**: Isolates pgAdmin resources
- **Secret**: Stores pgAdmin credentials
- **Deployment**: Deploys multiple pgAdmin instances
- **PersistentVolumeClaim**: Provides storage for pgAdmin data
- **Service**: Provides access to pgAdmin for external users
- **Ingress**: (Optional) Provides routing with a custom domain

## Prerequisites

- Kubernetes cluster
- kubectl configured to interact with your cluster
- (Optional) Ingress controller installed in your cluster

## Deployment

To deploy the pgAdmin cluster:

```bash
kubectl apply -f namespace.yaml
kubectl apply -f secret.yaml
kubectl apply -f pvc.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml  # Optional
```

## Accessing pgAdmin

If you deployed with a LoadBalancer service type, you can access pgAdmin at the external IP provided by your cloud provider:

```bash
kubectl get svc -n pgadmin
```

If you used Ingress, configure DNS to point to your Ingress controller's IP address and access pgAdmin at the configured host (pgadmin.example.com in the example).

## Credentials

Default login credentials:
- Email: admin
- Password: qwerty

**Note**: It is recommended to change these default credentials for production use.

## Customization

You can customize the deployment by modifying the following:

- `secret.yaml`: Change pgAdmin credentials
- `deployment.yaml`: Adjust number of replicas
- `pvc.yaml`: Change storage requirements
- `ingress.yaml`: Modify host and path settings
