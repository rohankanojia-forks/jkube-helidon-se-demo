# Deploying Helidon Quickstart SE to Kubernetes using Kubernetes Maven Plugin

This project is generated using Helidon Starter. It showcases how seamlessly you can package and deploy your Helidon application to Kubernetes using Kubernetes Maven Plugin

## Build and run

With JDK11+
```bash
mvn package
java -jar target/helidon-quickstart-se.jar
```

## Exercise the application

```shell
$ curl -X GET http://localhost:8080/greet
{"message":"Hello World!"}

$ curl -X GET http://localhost:8080/greet/Joe
{"message":"Hello Joe!"}
```

## Build the Docker Image

```shell
$ mvn k8s:build
```

## Start the application with Docker

```shell
$ docker run --rm -p 8080:8080 helidon-quickstart-se:latest
```

Exercise the application as described above

## Deploy the application to Kubernetes

Make sure you've logged into some remote Kubernetes cluster from your local machine. You can also use local Kubernetes distributions like minikube and kind for testing purposes.

```shell
$ mvn k8s:resource                # Generate kubernetes manifests
$ mvn k8s:apply                   # Apply generated Kubernetes manifests to Kubernetes Cluster
$ kubectl get service helidon-quickstart-se  # Get service info
```

## Deploy the application to Red Hat OpenShift

In order to deploy to Red Hat OpenShift you'd require access to an OpenShift cluster. You can create an account at [Red Hat Developer Sandbox](https://developers.redhat.com/developer-sandbox) which allows trying OpenShift for a limited period.

Once installed, you can deploy your application like this:
```shell
$ mvn oc:build oc:resource oc:apply -Popenshift
```
