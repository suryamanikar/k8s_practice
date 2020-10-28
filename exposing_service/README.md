Exposing Service
----------------
It contains both Deployment and Service specification in the same file.
The nginx server serves HTTP traffic on port 80.

Execute following commands to verify
% kubectl create -f service_deplopyment_with_no_external_ip.yml 
% kubectl get deployments,pods
% kubectl get svc my-nginx

% kubectl describe svc my-nginx
Name:                     my-nginx
Namespace:                default
Labels:                   run=my-nginx
Annotations:              <none>
Selector:                 run=my-nginx
Type:                     NodePort
IP:                       10.100.108.67
LoadBalancer Ingress:     localhost
Port:                     http  80/TCP
TargetPort:               80/TCP
NodePort:                 http  30175/TCP
Endpoints:                10.1.0.30:80,10.1.0.31:80
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>

% kubectl get svc my-nginx
NAME       TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
my-nginx   NodePort   10.100.108.67   <none>        80:30175/TCP   30m

# Use the localport 30175 to access the nginx server
$ curl localhost:30175
or use browser "http://localhost:30175


