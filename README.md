Deploy the Seleniumb Hub:

```
kubectl create -f selenium-hub-rc.yaml
kubectl create -f selenium-hub-svc.yaml
```

Deploy some Firefox and Chrome pods:
```
kubectl create -f selenium-node-chrome-rc.yaml
kubectl create -f selenium-node-firefox-rc.yaml
```

Grab the Service ip or nodeport:
```
kubectl describe service selenium-hub
```
Then it should be on serviceip:4444 or kube-host:nodeport/

To check on one of the browser nodes via VNC, you may have to proxy depending on your kube setup:
```
kubectl port-forward -p <POD_NAME> 9000:5900
```
Then connect to localhost:9000 with your VNC client.

TODO: Figure out healthcheck for the nodes.

Adapted from: https://github.com/SeleniumHQ/docker-selenium