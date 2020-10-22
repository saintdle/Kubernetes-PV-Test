Re-create Steps.

Deploy and config VMware K8S Storage as per guidance.
( URL )

Create test namespace -
kubectl create ns test

Create StorageClass and deploy stateful-set-primary.yaml.
kubectl apply -f ./storageclass.yaml -n test
kubectl apply -f ./stateful-set-primary.yaml -n test


This will create a busybox container that is 'sleeping', connect to the test container.
Confirm both are available

kubectl get pvc -n test
kubectl get StatefulSet -n test
kubectl get pods -n test

Connect into the Pod
kubectl exec -it test-pod-1-0 -n test sh

try and write a file here
touch /usr/sw/var/test

What should happen
The file 'test' should be created at the path /usr/sw/var/test

What Actually happens
Permission denied.
