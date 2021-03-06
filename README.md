# Observability Demo
This demo can be deployed in Google Cloud. The scripts can be run in a sequence starting from `1-start.sh`

Youtube link is: https://www.youtube.com/watch?v=GyqMx-XrKWc

- `1-start.sh`- Sets up the envirobment with Google Cloud login. Change the project id and cluster name to your project and your Kubernetes cluster.
- `2-apply-config.sh`- Deploys the `distributed-trace.yml` in the cluster
- `3-linkerd-setup.sh`- Sets up Linkerd in the cluster
- `4-linkerd-inject.sh`- Inject linkerd sidecars in the deployment.
- `curl.sh` - Does a recursive call to the application to create artificial traffic to the application.
- `distributed-trace.yml`- Deployment config in Kubernetes for having `spring-cloud-sleuth-server` and `spring-cloud-sleuth-client` deployed as 2 containers in a single pod. They have distributed tracing enabled using Spring Cloud Sleuth which helps in Distributed tracing.
- `spring-cloud-sleuth-example` - code based for the client and server microservice which has already been dockerized and uploaded to Google Container Registry(gcr.io). It's public, so you can use it as well.

## Demo Architecture
This demo covers the 3 pillars of observability - Metrics, Logging and Tracing.
### Microservices 
- `client` - Exposed from external service
- `server` - Accessible from the `client`
<img src="demo-architecture.png" alt="architecture" />

### Metrics and Logging Monitoring
- `linkerd` service mesh collects metrics about the pods and containers.
- Spring Cloud Sleuth is used for Distributed tracing across microservices.
- Google Stack Driver also collects the logs, metrics in the Google Cloud platform from the Google Kubernetes Engine.
<img src="demo-architecture-linkerd.png" alt="linkerd architecture" />

