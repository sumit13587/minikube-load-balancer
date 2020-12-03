# Minikube Load Balancer
Example deployment of a load balanced nginx webapp in Minikube

## Pre-requisites
* hyperkit on MacOS (or virtualbox if windows)
* minikube
* kubectl

## Steps to install above on MacOS with homebrew
```
brew update
brew install hyperkit
brew install minikube # Also installs kubectl as it is a dependency for minikube
```

## For more details on Minikube installation: 
https://minikube.sigs.k8s.io/docs/start/

## Nginx app deployment

```
minikube start # Start the cluster, by default configures kubectl to use minikube
cd minikube-load-balancer # Be in the git repo directory
kubectl apply -f my-nginx-deploy.yaml # Create deployment
kubectl apply -f my-nginx-service.yaml # Create load balancer service
```

## Verifying app deployment on browser
1. http://localhost or http://127.0.0.1 - nginx web app behind the load balancer
2. `minikube dashboard` to launch the minikube dashboard [More details](https://minikube.sigs.k8s.io/docs/handbook/dashboard/)


## Ascertain load balancing
1. Navigate to the pods section of the minikube dashboard.
2. Go to the pods corresponding to the my-nginx-deployment.
3, Use the view logs option to check logs for incoming requests.
4. With multiple requests it can be observed from logs that requests are being served by both pods.


