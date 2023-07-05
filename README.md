## MySQL Operator Workshop

### Start minikube
The following command aims to start minikube using 4 vCPU and 11 GB RAM
```
minikube start --driver=podman cpus 4 --memory 11962 --extra-config=kubeadm.pod-network-cidr=10.0.0.0/16
```
See what are images available on minikube's docker local registry
```
minikube ssh 'docker images'
```
### Import MySQL Enterprise Edition and MySQL Enterprise Operator Container Images
Copy container images from local machine into minikube
```
scp -i ~/.minikube/machines/minikube/id_rsa /home/opc/images/*.tar docker@$(minikube ip):/home/docker/
scp -i ~/.minikube/machines/minikube/id_rsa /home/opc/images/*.tar.gz docker@$(minikube ip):/home/docker/
```
The following steps aim to load MySQL Enterprise container images into minikube's docker local registry
```
ssh -i ~/.minikube/machines/minikube/id_rsa docker@$(minikube ip) -- docker load -i /home/docker/mysql-enterprise-operator-8.0.32-2.0.8-docker.tar.gz
ssh -i ~/.minikube/machines/minikube/id_rsa docker@$(minikube ip) -- docker load -i /home/docker/mysql-enterprise-server-8.0.33.tar
ssh -i ~/.minikube/machines/minikube/id_rsa docker@$(minikube ip) -- docker load -i /home/docker/mysql-enterprise-router-8.0.33.tar
```
See what are images available on minikube's docker local registry
```
minikube ssh 'docker images'
```
