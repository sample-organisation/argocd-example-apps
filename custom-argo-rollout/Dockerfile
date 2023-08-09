FROM ubuntu as downloader

WORKDIR /downloads

RUN apt-get update && apt-get install -y wget

RUN <<SCRIPT
wget https://github.com/argoproj-labs/rollouts-plugin-trafficrouter-gatewayapi/releases/download/v0.0.0-rc1/gateway-api-plugin-linux-amd64
mv gateway-api-plugin-linux-amd64 argo-rollout-gateway-api-plugin
chmod +x argo-rollout-gateway-api-plugin
SCRIPT

FROM quay.io/argoproj/argo-rollouts:v1.5.1

COPY --from=downloader --chown=999 /downloads/argo-rollout-gateway-api-plugin /bin/argo-rollout-gateway-api-plugin
