# Webinar_hpa_k8s_demo

### We will test horizontal pod autoscaler and cluster autoscaler in MCS kubernetes as a service

## Prerequisites


### Create K8s cluster in mcs and download kubeconfig
Instruction: https://mcs.mail.ru/help/ru_RU/k8s-start/create-k8s

Kubernetes as a Service: https://mcs.mail.ru/app/services/containers/add/

### Install kubectl
https://mcs.mail.ru/help/ru_RU/k8s-start/connect-k8s

### Set path to kubeсonfig for kubectl
```console
export KUBECONFIG=/replace_with_path/to_your_kubeconfig.yaml
```

### also it will be easier to work with kubectl while enabling autocomplete and using alias
```console
alias k=kubectl
source <(kubectl completion bash)
complete -F __start_kubectl k
```

## Start demo app and service for it
```console
kubectl apply -f app.yaml
```

## Start workload generator
```console
kubectl apply -f load-generator.yaml
```

## Enable horizontal pod autoscaler (HPA)
```console
kubectl apply -f hpa.yaml
```

## Check HPA status 
```console
kubectl get hpa
```

## Get number and status of pods, so you can check work of HPA in action
```console
kubectl get pod -o wide -w

press CTRL+C to stop
```

## Check number and status of nodes, so you can see cluster autoscaler in action
```console
kubectl get nodes -w

press CTRL+C to stop
```

## Stop workload generator, so you can check how number of pods and nodes will return to normal
```console
kubectl delete -f load-generator.yaml
```

## Other useful commands
```console
kubectl top node
kubectl get deployments 
```


