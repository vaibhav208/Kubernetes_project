
# Kubernetes Multi-Container Application: Node.js & MongoDB

This project demonstrates the deployment of a multi-container application using Kubernetes.  
It includes a Node.js-based web UI and a MongoDB database, showcasing best practices in container orchestration, service management, and persistent storage.

---

## 📁 Project Structure

```
Kubernetes_project/
├── db-demo-app/             # MongoDB deployment and service configurations
├── express-demo/            # Node.js application source code
├── k8 config/               # Kubernetes YAML configurations
├── node-file-demo/         # Additional Node.js application files
├── testapp/                 # Test application files
├── Kubernete.pdf            # Project documentation
└── README.md                # Project overview and instructions
```

---

## 🚀 Getting Started

### Prerequisites

Ensure you have the following installed:

- [Docker](https://www.docker.com/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)

### Setup Steps

1. **Start Minikube:**

   ```bash
   minikube start
   ```

2. **Enable the Kubernetes Dashboard (Optional):**

   ```bash
   minikube dashboard
   ```

3. **Build and Push Docker Images:**

   Navigate to the `express-demo/` directory and build the Docker image:

   ```bash
   docker build -t your-dockerhub-username/node-mongo-app:latest .
   docker push your-dockerhub-username/node-mongo-app:latest
   ```

4. **Apply Kubernetes Configurations:**

   Navigate to the `k8 config/` directory and apply the YAML files:

   ```bash
   kubectl apply -f mongo-deployment.yaml
   kubectl apply -f mongo-service.yaml
   kubectl apply -f node-deployment.yaml
   kubectl apply -f node-service.yaml
   ```

5. **Access the Application:**

   ```bash
   minikube service node-service
   ```

---

## 🧱 Application Architecture

- **Frontend:** Node.js-based web UI  
- **Backend:** MongoDB database  
- **Deployment Strategy:** Each component is deployed in separate pods with individual services facilitating communication.  
- **Networking:** Services are exposed using `NodePort` for external access.  
- **Persistence:** MongoDB utilizes Persistent Volumes to ensure data durability.  

---

## 📄 Kubernetes Components

### MongoDB

- **Deployment:** `mongo-deployment.yaml`
- **Service:** `mongo-service.yaml`
- **Persistent Volume:** Ensures data persists beyond pod lifecycles.

### Node.js Application

- **Deployment:** `node-deployment.yaml`
- **Service:** `node-service.yaml`
- **Environment Variables:** Configured to connect to the MongoDB service.

---

## 🔧 Useful Commands

```bash
# Check Deployments
kubectl get deployments

# Check Pods
kubectl get pods

# Describe a Pod
kubectl describe pod <pod-name>

# Delete a Deployment
kubectl delete deployment <deployment-name>

# Access Services
kubectl get services
```

---

## 📘 Documentation

For a detailed explanation of the project, refer to the [Kubernete.pdf](./Kubernete.pdf) file included in the repository.

---

## 🤝 Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any enhancements or bug fixes.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
