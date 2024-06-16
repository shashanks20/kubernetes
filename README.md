# Kubernetes Project Repository

This repository contains the setup and deployment files for a Kubernetes project, organized into two main directories: `k8s-connection` and `k8s-data`. Below are the details and instructions for connecting, operating, and deploying the Kubernetes cluster.

## Repository Structure

```
Kubernetes/
│
├── k8s-connection/
│   └── README.md
│
├── k8s-data/
│   ├── Dockerfile
│   ├── k8s-files/
│   │   ├── loginsvc.yaml
│   │   ├── pod.yaml
│   │   └── secret.yaml
│   ├── README.md
│   ├── src/
│   │   ├── images/
│   │   │   └── img.jpg
│   │   ├── index.html
│   │   └── style.css
│
└── README.md
```

## k8s-connection

The `k8s-connection` directory contains information and instructions on how to connect and operate the Kubernetes cluster.

### Steps to Connect to the Kubernetes Cluster

1. **Install Kubernetes CLI (kubectl)**:
   - Follow the instructions to install `kubectl` on your local machine from the [Kubernetes documentation](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

2. **Set Up Kubernetes Configuration**:
   - Ensure you have the correct kubeconfig file to authenticate and interact with your Kubernetes cluster. This file is typically provided by your cluster administrator.

3. **Connect to the Cluster**:
   - Use the kubeconfig file to set up the context for `kubectl`:
     ```sh
     export KUBECONFIG=/path/to/your/kubeconfig
     kubectl config use-context your-cluster-context
     ```

4. **Verify the Connection**:
   - Run the following command to verify your connection:
     ```sh
     kubectl cluster-info
     ```

## k8s-data

The `k8s-data` directory contains the files necessary for deploying applications and services to the Kubernetes cluster.

### Deployment Files

- **Dockerfile**: Defines the container image for the application.
- **k8s-files**:
  - `loginsvc.yaml`: Kubernetes manifest file for the login service.
  - `pod.yaml`: Kubernetes manifest file for a generic pod.
  - `secret.yaml`: Kubernetes manifest file for managing secrets.

### Application Source Code

- **src**:
  - `images/img.jpg`: Example image used in the application.
  - `index.html`: Main HTML file for the application.
  - `style.css`: CSS file for styling the application.

### Steps to Deploy to Container Registry

1. **Build the Docker Image**:
   - Navigate to the `k8s-data` directory and build the Docker image:
     ```sh
     cd k8s-data
     docker build -t your-container-registry/your-image-name:tag .
     ```

2. **Push the Docker Image to the Container Registry**:
   - Tag your Docker image and push it to the container registry (e.g., Docker Hub, Google Container Registry):
     ```sh
     docker push your-container-registry/your-image-name:tag
     ```

3. **Update Kubernetes Manifests**:
   - Ensure your Kubernetes manifest files (e.g., `loginsvc.yaml`, `pod.yaml`) reference the correct container image.

4. **Deploy to Kubernetes**:
   - Apply the Kubernetes manifests to your cluster:
     ```sh
     kubectl apply -f k8s-files/loginsvc.yaml
     kubectl apply -f k8s-files/pod.yaml
     kubectl apply -f k8s-files/secret.yaml
     ```

## Additional Resources

For further information and advanced configurations, please refer to the [Kubernetes documentation](https://kubernetes.io/docs/home/).

## GitLab Repository

This project is also available on GitLab at [https://gitlab.com/devops9104120](https://gitlab.com/devops9104120). Ensure to synchronize changes between GitHub and GitLab repositories as necessary.
