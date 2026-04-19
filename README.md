# 🚀 Cloud-Native GitOps Platform (EKS + Terraform + CI/CD + ArgoCD)

## 📌 Overview

This project demonstrates a **production-style end-to-end DevOps/SRE platform** built using modern cloud-native tools and practices. It showcases Infrastructure as Code, CI/CD automation, GitOps-based deployments, Kubernetes orchestration, and observability.

The platform is designed to simulate a real-world environment focusing on **scalability, reliability, automation, and cost efficiency**.

---

## 🏗️ Architecture

```
Developer → GitHub → GitHub Actions (CI) → Docker Hub
                                          ↓
                                  GitOps Repository
                                          ↓
                                      ArgoCD
                                          ↓
                                 Kubernetes (EKS)
                                          ↓
                          Prometheus + Grafana Monitoring
```

---

## ⚙️ Tech Stack

### ☁️ Cloud & Infrastructure

* AWS (EKS, EC2, VPC)
* Terraform (Infrastructure as Code)

### 🐳 Containerization & Orchestration

* Docker
* Kubernetes (EKS)

### 🔄 CI/CD & GitOps

* GitHub Actions (CI Pipeline)
* ArgoCD (GitOps Continuous Delivery)

### 📊 Observability

* Prometheus (Metrics collection)
* Grafana (Visualization & dashboards)

---

## 🚀 Key Features

* Infrastructure provisioning using **Terraform**
* Containerized application using **Docker**
* Automated CI pipeline using **GitHub Actions**
* GitOps-based deployment using **ArgoCD**
* Kubernetes-based deployment with:

  * High availability (replicas)
  * Auto-scaling (HPA)
  * Health checks (readiness probe)
* Observability with Prometheus and Grafana
* Scalable and production-ready architecture

---

## 📂 Repository Structure

```
.
├── app/                    # Application source code
├── Dockerfile             # Container image definition
├── .github/workflows/     # CI pipeline
├── infra/terraform/       # Infrastructure as Code (EKS)
├── k8s/                   # Kubernetes manifests
├── argocd/                # ArgoCD application config
└── README.md
```

---

## 🛠️ Setup & Deployment

### 1️⃣ Provision Infrastructure (EKS)

```bash
cd infra/terraform
terraform init
terraform apply
```

---

### 2️⃣ Build & Push Docker Image

```bash
docker build -t <docker-username>/sre-app:latest .
docker push <docker-username>/sre-app:latest
```

---

### 3️⃣ Configure CI Pipeline

* Add GitHub Secrets:

  * `DOCKER_USER`
  * `DOCKER_PASS`

Push code to trigger pipeline.

---

### 4️⃣ Deploy ArgoCD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Access UI:

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

---

### 5️⃣ Deploy Application via GitOps

Apply ArgoCD application:

```bash
kubectl apply -f argocd/app.yaml
```

---

### 6️⃣ Install Monitoring Stack

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install monitoring prometheus-community/kube-prometheus-stack
```

Access Grafana:

```bash
kubectl port-forward svc/monitoring-grafana 3000:80
```

---

## 📊 Observability

* Application metrics collected via Prometheus
* Dashboards created in Grafana
* Enables monitoring of:

  * Pod health
  * CPU/Memory usage
  * Application availability

---

## 🔐 Security Considerations

* Secure credential handling using GitHub Secrets
* Kubernetes readiness probes for health validation
* Network isolation via VPC and Kubernetes policies

---

## 📸 Screenshots (Add After Deployment)

* ArgoCD Dashboard
* Grafana Dashboard
* Kubernetes Pods (`kubectl get pods`)
* CI/CD Pipeline Execution

---

## 📈 Future Enhancements

* Implement Helm charts for modular deployments
* Add Ingress controller with domain routing
* Enable Blue-Green / Canary deployments
* Integrate security scanning in CI/CD pipeline
* Implement cost monitoring (FinOps dashboard)

---

## 💼 Resume Highlight

Designed and implemented an end-to-end cloud-native platform using Terraform, AWS EKS, GitHub Actions, and ArgoCD, enabling automated CI/CD, GitOps deployments, auto-scaling, and observability with Prometheus and Grafana.

---

## 👤 Author

**Pankaj Kumar Agrahari**
Principal Site Reliability Engineer | DevOps Architect   | Platform Engineer  | Kubernetes | AWS | OCI

---

## ⭐ If you find this useful

Give this repo a star ⭐ and feel free to fork or contribute!

