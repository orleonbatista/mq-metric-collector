# mq_prometheus local configuration

This directory provides an example configuration file for the `mq_prometheus` collector that connects to an IBM MQ queue manager using a local (bindings) connection.

## Configuration

`mq_prometheus.yaml` combines the common settings from [`config.common.yaml`](../config.common.yaml) with the Prometheus options defined in [`cmd/mq_prometheus/config.collector.yaml`](../cmd/mq_prometheus/config.collector.yaml). It assumes the collector runs on the same host as the queue manager. Update `connection.queueManager` if your queue manager name differs.

The `prometheus` section also supports optional attributes such as `host`, `httpsCertFile`/`httpsKeyFile` for TLS, and `overrideCType` for controlling metric types; see [`cmd/mq_prometheus/config.go`](../cmd/mq_prometheus/config.go) for the full list of properties.

## Running the collector

Execute the collector and point it at the configuration file:

```sh
mq_prometheus -f mq_prometheus.yaml
```

The Prometheus endpoint will be available on port `9157` and exposes metrics at `/metrics`.
