# rso-k8s

## Configuration
- `kubectl apply -f nginx-ingress-deployment.yml`
- `kubectl apply -f kubectl apply -f nginx-ingress-svc.yml`

Update routes to microservices:
- `kubectl apply -f ingress.yaml`

## ETCD
- `kubectl apply -f etcd.yaml`

## Filebeat
Open the manifest and around line 76 you should see the environment variables controlling the logging destination. You need to update them to point to your stack.

```yaml
env:
- name: LOGSTASH_HOST
  value: "your-logstash-host"
- name: BEATS_PORT
  value: "your-port"
```

Now your deployment manifest is updated, you can deploy it using.
- `kubectl apply -f filebeat-kubernetes.yaml`

Confirm Completed Deployme
- `kubectl --namespace=kube-system get ds/filebeat`
- `kubectl --namespace=kube-system get pods`

