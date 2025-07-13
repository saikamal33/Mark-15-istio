# This repo is used for istio setup

## Istio

it help us to control and secure how micro services talk to each other without chnaging the services themselves.

it controlles - traffic management, security, observability, resiliency, Policy Enforcement.

# Working

its typically uses a sidecar proxy pattern, where a lighweight proxy is deployed alongside each microservice. these proxies intercepts and manages all networks traffic between services.

## Admission Controllers

Admission controllers in kubernetes enforce policies on objects during their creation or modification. They intercept requests to the kubernetes API server before objects are persisted and can modify or deny requests based on predefined rules.

we can find the predefined admission controllers in the kubernets api server config file.

~~~
sudo cat /etc/kubernetes/manifests/kube-apiserver.yaml
# we can find them at  "--enable-admission-plugins"
~~~

we can test the admission controllers by using default controlled which is storage limit and trying to create a pod later above the limit.
~~~
kubectl apply -f resourcequota.yaml
kubectl apply -f pod.yaml

# we will face an error like below because of resouce quota controller, which is a default admission controller.
Error from server (Forbidden): error when creating "pod.yaml": pods "demo-pod" is forbidden: exceeded quota: quota-demo, requested: memory=10Gi, used: memory=0, limited: memory=2Gi
~~~

# Installation of Istio 

Please follow the below link for the installation of Istio.
~~~
https://istio.io/latest/docs/setup/getting-started/
~~~


