# helm-charts-oci-proxy-in-k8s

## Введение
В этой статье будет описано

## Kubernetes кластер
Для начала создадим Kubernetes кластер (например, в Яндекс облаке с помощью Terragrunt).

Создание kubernetes кластера кратко описана в файле [create-k8s-by-terraform-in-yc.md]
(terragrunt-k8s/create-k8s-by-terraform-in-yc.md)

# Установка Cert-manager для TLS Ingress controller c Let’s Encrypt
```shell
helm repo add jetstack https://charts.jetstack.io
helm install cert-manager --namespace cert-manager --version v1.12.2 jetstack/cert-manager
```

# Установка Harbor
```shell
helm repo add harbor https://helm.goharbor.io
```

## Ingress для Harbor
Ingress: Ingress controller должен быть установлен в кластере Kubernetes. Примечания: если TLS отключен, 
порт должен быть включен в команду при pulling/pushing образов. Подробности смотрите в issue [5291]
(https://github.com/goharbor/harbor/issues/5291).

```shell
helm install harbor harbor/harbor --version 0.2.1 -n harbor --create-namespace
```