# Spring Microservices Bookstore – Kubernetes Manifests

This repository contains the Kubernetes manifests to deploy the **Spring Microservices Bookstore** application with databases, messaging, monitoring, and ingress.

## Folder Structure

```
k8s/
├── base/                # Namespace, ConfigMap, Secrets
├── core-services/       # Eureka, Config Server, API Gateway
├── databases/           # Databases (Postgres + MongoDB)
├── frontend/
├── messaging/           # Kafka + Zookeeper
├── microservices/       # Business services
├── networking/
└── README.md
```

## Deployment Order

```sh
kubectl apply -f k8s/base/
kubectl apply -f k8s/databases/
kubectl apply -f k8s/messaging/
kubectl apply -f k8s/monitoring/
kubectl apply -f k8s/core-services/
kubectl apply -f k8s/microservices/
kubectl apply -f k8s/frontend/
kubectl apply -f k8s/networking/
```

## Exposed Endpoints

| Service                | URL                                     |
|-------------------------|-----------------------------------------|
| Frontend (Next.js)     | https://tienphatng237.it.com            |
| API Gateway            | https://api.tienphatng237.it.com        |
| Eureka (Discovery)     | https://eureka.tienphatng237.it.com     |
| Config Server          | https://config.tienphatng237.it.com     |

## Notes

- Databases (Postgres + MongoDB) use **PVCs** for persistent storage.
- Secrets and ConfigMaps are defined in `base/01-config-and-secrets.yaml`.
- Update DNS records of your domain to point to the Kubernetes Ingress Controller.
- Docker images must be pushed to Docker Hub under `tienphatng237/*:v1`.
