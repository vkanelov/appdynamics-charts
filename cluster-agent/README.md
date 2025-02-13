# Appdynamics Helm Chart

## ⚠️ Deprecation Notice
This is a notice for sunsetting this public facing repository containing AppDynamics Cluster Agent helm charts in Github.

This repository will be maintained till October 31st 2023, post which it will not be updated. After this date, the latest helm charts will be made available via the [Appdynamics production artifactory](https://appdynamics.jfrog.io/ui/repos/tree/General/appdynamics-cloud-helmcharts/)

### Add AppDynamics helm repo
```bash
helm repo add appdynamics-charts https://ciscodevnet.github.io/appdynamics-charts
```
### Create values yaml to override default ones
```yaml
installClusterAgent: true
installInfraViz: false

imageInfo:
  agentImage: docker.io/appdynamics/cluster-agent
  agentTag: 22.1.0
  operatorImage: docker.io/appdynamics/cluster-agent-operator
  operatorTag: 22.1.0
  imagePullPolicy: Always           # Will be used for operator pod
  machineAgentImage: docker.io/appdynamics/machine-agent
  machineAgentTag: latest
  machineAgentWinImage: docker.io/appdynamics/machine-agent-analytics
  machineAgentWinTag: win-latest
  netVizImage: docker.io/appdynamics/machine-agent-netviz
  netvizTag: latest                            

controllerInfo:
  url: <controller-url>
  account: <controller-account>
  username: <controller-username>
  password: <controller-password>
  accessKey: <controller-accesskey>
  globalAccount: <controller-global-account>   # To be provided when using machineAgent Window Image

agentServiceAccount: appdynamics-cluster-agent
operatorServiceAccount: appdynamics-operator
infravizServiceAccount: appdynamics-infraviz
```
### Install cluster agent or machine agent using helm chart
```bash
helm install cluster-agent appdynamics-charts/cluster-agent -f <values-file>.yaml --namespace appdynamics
```
### Note:
For more details and config options please visit official documentation
[https://docs.appdynamics.com/display/PRO45/Deploy+the+Cluster+Agent+with+Helm+Charts](https://docs.appdynamics.com/display/PRO45/Deploy+the+Cluster+Agent+with+Helm+Charts)
