# Cloud--Computing-Assignment2
## To-Do Web Application Deployment (Flask + MongoDB + Kubernetes)

---

## 📌 Overview

This project implements a cloud-native To-Do web application using Flask and MongoDB. The application is containerized with Docker and deployed using Kubernetes both locally (Minikube) and in the cloud (AWS EKS).

The goal of this project is to demonstrate key cloud computing concepts such as containerization, orchestration, scalability, rolling updates, and health monitoring in a real-world deployment scenario.

---

## 🏗️ Architecture

The system follows a typical cloud-native architecture:

User → Browser  
     → Kubernetes Service  
     → Flask Web Application (Pods)  
     → MongoDB Database  

---

## ⚙️ Tech Stack

- Backend Framework: Flask (Python)
- Database: MongoDB
- Containerization: Docker
- Orchestration: Kubernetes (Minikube & AWS EKS)
- Cloud Platform: AWS


---

## 🐳 Docker Setup

Build and run the application locally using Docker Compose:

docker compose up --build

Access the application:

http://localhost:5000

---

## ☸️ Kubernetes Deployment (Minikube)

minikube start

kubectl apply -f mongo-deployment.yaml  
kubectl apply -f mongo-service.yaml  
kubectl apply -f web-deployment.yaml  
kubectl apply -f web-service.yaml  

minikube service todo-web-service --url

---

## ☁️ AWS EKS Deployment

### Create EKS Cluster

eksctl create cluster --name todo-cluster --region us-east-2 --nodegroup-name standard-workers --node-type t3.medium --nodes 2

### Configure kubectl

aws eks update-kubeconfig --region us-east-2 --name todo-cluster

### Deploy Application

kubectl apply -f mongo-deployment.yaml  
kubectl apply -f mongo-service.yaml  
kubectl apply -f web-deployment.yaml  
kubectl apply -f web-service.yaml  

### Access Application

kubectl get svc

Open in browser:

http://<EXTERNAL-IP>

---

## 🔄 Scaling

kubectl scale deployment todo-web --replicas=4

---

## 🔁 Rolling Update

kubectl rollout status deployment/todo-web

---

## ❤️ Health Monitoring

kubectl describe pod <pod-name>

---

## 📂 Project Structure

Cloud-Assignment-3-Files/  
├── app.py  
├── Dockerfile  
├── docker-compose.yml  
├── requirements.txt  
├── mongo-deployment.yaml  
├── mongo-service.yaml  
├── web-deployment.yaml  
├── web-service.yaml  
├── templates/  
├── static/  
└── README.md  

