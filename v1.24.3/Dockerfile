FROM debian:buster-slim

ENV HOME="/" \
    OS_ARCH="amd64" \
    OS_NAME="linux" \
    KUBECTL_VERSION="v1.24.3"

RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y ca-certificates curl git gzip jq procps tar wget gettext-base && \
    rm -r /var/lib/apt/lists /var/cache/apt/archives

RUN curl -LO https://dl.k8s.io/release/${KUBECTL_VERSION}/bin/${OS_NAME}/${OS_ARCH}/kubectl && \
    chmod +x ./kubectl && \
    mv ./kubectl /usr/local/bin/kubectl

RUN mkdir /.kube && chmod g+rwX /.kube

USER 1001
ENTRYPOINT [ "kubectl" ]
CMD [ "--help" ]