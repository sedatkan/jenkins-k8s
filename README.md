# Jenkins in Kubernetes
This repository has a `Dockerfile` and a `helm` chart for setting up a simple Jenkins master for running in Kubernetes.

This Jenkins has the required tools to work in and with Kubernetes
- Jenkins application with pre-loaded plugins (see [plugins.txt](plugins.txt))
- Skipped setup wizard
  - You can control admin user and password with `--set adminUser=${USER},adminPassword=${PASSWORD}`
  - You can add and remove plugins by editing the [plugins.txt](plugins.txt) file


### Build the Jenkins Docker image
You can build the image yourself
```bash

# Build the image
$ docker build -t sedatkan/jenkins:v0.0.1 .

# Push the image
$ docker push sedatkan/jenkins:v0.0.1
```

### Deploy Jenkins helm chart to Kubernetes
```bash

$ helm init


# Deploy the Jenkins helm chart
# (same command for install and upgrade)
$ helm upgrade --install jenkins ./helm/jenkins-k8s
```

### Data persistence
By default, in Kubernetes, the Jenkins deployment uses a persistent volume claim that is mounted to `/var/jenkins_home`.
This assures your data is saved across crashes, restarts and upgrades.   

