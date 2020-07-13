# Policy component is disabled.

# Telemetry component is disabled.

# images

```
grafana/grafana:6.7.4
quay.io/kiali/kiali:v1.18
docker.io/prom/prometheus:v2.15.1
docker.io/istio/proxyv2:1.6.4
docker.io/jaegertracing/all-in-one:1.16
docker.io/istio/proxyv2:1.6.4
docker.io/istio/pilot:1.6.4
```

# install

## NS

```
k apply -f namespace
```

## CRD

```
k apply -f crd/istio-mixer
k apply -f crd/istio-pilot
k apply -f crd/istio-operator
```

## istio-system

```
k apply -f istio-system
k apply -f istio-sidecars
```

## istiod

```
k apply -f istiod
```

等待部署完畢，再繼續下一步

## ingressgateway

```
k apply -f istio-ingressgateway
```

## tracing

```
k apply -f tracing
k apply -f prometheus
k apply -f grafana
k apply -f kiali
```

## 測試，部署bookinfo

```
k apply -f sample/bookinfo
```

http://{clusterIP}:{nodePort}/productpage

