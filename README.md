# Apps Config

Example Kustomize config for the Argo CD demo

### To access dev
```shell
export ENV=dev
export APP=apples-service
export HOST_PORT=8080
export POD_NAME=$(kubectl get pods --namespace $ENV -l "app=$APP" -o jsonpath="{.items[0].metadata.name}")
export CONTAINER_PORT=$(kubectl get pod --namespace $ENV $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
echo "Visit http://127.0.0.1:$HOST_PORT to use your application"
kubectl --namespace $ENV port-forward $POD_NAME $HOST_PORT:$CONTAINER_PORT
```

### To access prod
```shell
export ENV=prod
export APP=apples-service
export HOST_PORT=8081
export POD_NAME=$(kubectl get pods --namespace $ENV -l "app=$APP" -o jsonpath="{.items[0].metadata.name}")
export CONTAINER_PORT=$(kubectl get pod --namespace $ENV $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
echo "Visit http://127.0.0.1:$HOST_PORT to use your application"
kubectl --namespace $ENV port-forward $POD_NAME $HOST_PORT:$CONTAINER_PORT
```
