# Azure Pet Store Cloud-Native Application

### Note: This assignment demonstrates the use of Azure Service Bus (both sending and receiving), CI-CD pipeline implementation, and AI service integration.

## Overview

This project showcases a full-stack cloud-native application for an online pet store. The application uses a microservices architecture deployed on a Kubernetes cluster and integrates Azure Service Bus for the Order Queue, AI-powered pet descriptions and image generation using GPT-4 and DALL-E, and MongoDB for data persistence.

---

## Application Architecture

### Updated Architecture Diagram
![image](https://github.com/user-attachments/assets/c21a9933-b7c9-41e5-b436-8a3d5e9282c0)

The architecture includes the following components:
1. **Store-Front**: A customer-facing application for browsing and placing pet-related orders.
2. **Store-Admin**: An employee-facing application for managing pet products and orders.
3. **Order-Service**: Manages order creation and interacts with the managed order queue (Azure Service Bus).
4. **Product-Service**: Handles CRUD operations for pet product data.
5. **Makeline-Service**: Processes and completes orders by reading from the Azure Service Bus.
6. **AI-Service**: Generates AI-powered pet descriptions and images using GPT-4 and DALL-E.
7. **Database**: MongoDB for storing order and product data.

---

## Features

- **AI Integration**:
  - GPT-4 for generating pet product descriptions.
  - DALL-E for generating pet-related product images.
- **Order Queue**:
  - Managed order queue using Azure Service Bus.
- **Kubernetes**:
  - Deployment using ConfigMaps and Secrets.
  - StatefulSets for MongoDB persistence.

---

## Deployment Instructions

### Prerequisites

- Kubernetes Cluster (e.g., AKS).
- kubectl CLI.
- Docker CLI.
- Azure Subscription (for Service Bus and OpenAI API).

### Steps

1. **Clone Repositories**
2. **Build Docker Images**:
   ```
   docker build -t scottx18/store-front .
   docker build -t scottx18/store-admin .
   docker build -t scottx18/order-service .
   docker build -t scottx18/product-service .
   docker build -t scottx18/makeline-service .
   docker build -t scottx18/ai-service .
   ```
   Push the images to Docker Hub.
3. **Configure Secrets**:
   Apply the provided secrets:
   ```
   kubectl apply -f secrets.yaml
   kubectl apply -f azurebus-secrets.yaml
   ```
4. **Deploy Services**:
   Apply the deployment files:
   ```
   kubectl apply -f deployment-files/petstore.yaml
   kubectl apply -f deployment-files/admin-tasks.yaml
   ```

---

## Microservice Repositories

| Service          | Repository Link                  |
|-------------------|----------------------------------|
| Store-Front       | [GitHub Link](https://github.com/scot8/store-front-L8)                |
| Store-Admin       | [GitHub Link](https://github.com/scot8/store-admin-L8)                |
| Order-Service     | [GitHub Link](https://github.com/scot8/order-service-L8)                |
| Product-Service   | [GitHub Link](https://github.com/scot8/product-service-L8)                |
| Makeline-Service  | [GitHub Link](https://github.com/scot8/makeline-service-L8)                |
| AI-Service        | [GitHub Link](https://github.com/scot8/ai-service-L8)   |
| Virtual-Customer        | [GitHub Link](https://github.com/scot8/virtual-customer-L8)  |
| Virtual-Worker        | [GitHub Link](https://github.com/scot8/virtual-worker-L8)  |

---

## Docker Images

| Service               | Docker Image Link                                      |
|-----------------------|-------------------------------------------------------|
| Store-Front           | [scottx18/store-front-l8](https://hub.docker.com/r/scottx18/store-front-l8) |
| AI-Service            | [scottx18/ai-service-l8](https://hub.docker.com/r/scottx18/ai-service-l8)   |
| Product-Service       | [scottx18/product-service-l8](https://hub.docker.com/r/scottx18/product-service-l8) |
| Virtual-Worker        | [scottx18/virtual-worker-l8](https://hub.docker.com/r/scottx18/virtual-worker-l8) |
| Virtual-Customer      | [scottx18/virtual-customer-l8](https://hub.docker.com/r/scottx18/virtual-customer-l8) |
| Store-Admin           | [scottx18/store-admin-l8](https://hub.docker.com/r/scottx18/store-admin-l8) |
| Makeline-Service      | [scottx18/makeline-service-l8](https://hub.docker.com/r/scottx18/makeline-service-l8) |
| Order-Service         | [scottx18/order-service-l8](https://hub.docker.com/r/scottx18/order-service-l8) |





