# STEPS:

## Configure nginx-ingress controller

Ref:  https://learn.microsoft.com/en-us/azure/aks/app-routing

Managed NGINX ingress with the application routing add-on

# Enable approuting in your aks cluster.

Enable on an existing cluster

`$ az aks approuting enable --resource-group $RESOURCE_GROUP --name $CLUSTER_NAME`

`$ kubectl get pods -n app-routing-system`

# Create new ns and deploy blue/green apps

`$ kubectl create namespace app-store`

`$ kubectl apply -f bule-app.yaml -n app-store`

`$ kubectl apply -f green-app.yaml -n app-store`

`$ kubectl get all -n app-store`

# Create path-based ingress to run apps

`$ kubectl apply -f ingress.yaml -n app-store`

`$ kubectl get ingress -n app-store`

# Run Apps

`http://<Address_of_path-based_ingress>/blue`

`http://<Address_of_path-based_ingress>/green`
