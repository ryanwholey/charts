# monica

![Version: 5.1.1](https://img.shields.io/badge/Version-5.1.1-informational?style=flat-square) ![AppVersion: 3.1.1-apache](https://img.shields.io/badge/AppVersion-3.1.1--apache-informational?style=flat-square)

A Personal Relationship Management tool to help you organize your social life

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/monicahq/monica>
* <https://hub.docker.com/_/monica>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | mariadb | 9.3.19 |
| https://library-charts.k8s-at-home.com | common | 3.3.0 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install monica k8s-at-home/monica
```

## Installing the Chart

To install the chart with the release name `monica`

```console
helm install monica k8s-at-home/monica
```

## Uninstalling the Chart

To uninstall the `monica` deployment

```console
helm uninstall monica
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install monica \
  --set env.TZ="America/New York" \
    k8s-at-home/monica
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install monica k8s-at-home/monica -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env | object | See below | environment variables. See [monica documentation](https://raw.githubusercontent.com/monicahq/monica/master/.env.example) for more details. |
| env.APP_ENV | string | `"production"` | Use `local` if you want to install Monica as a development version. Use `production` otherwise. |
| env.APP_KEY | string | `nil` | The encryption key. This is the most important part of the application. Keep this secure otherwise, everyone will be able to access your application. Must be 32 characters long exactly. Use `php artisan key:generate` or `echo -n 'base64:'; openssl rand -base64 32` to generate a random key. |
| env.APP_URL | string | `"https://crm.k8s-at-home.com"` | The URL of your application. |
| env.DB_DATABASE | string | `nil` | Database to connect to |
| env.DB_HOST | string | `nil` | Database hostname |
| env.DB_PASSWORD | string | `nil` | Database password |
| env.DB_USERNAME | string | `nil` | Database username |
| env.TZ | string | `"UTC"` | Set the container timezone |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"monica"` | image repository |
| image.tag | string | `"3.1.1-apache"` | image tag |
| ingress.main | object | See values.yaml | Enable and configure ingress settings for the chart under this key. |
| mariadb | object | See values.yaml | Enable and configure mariadb database subchart under this key.    For more options see [mariadb chart documentation](https://github.com/bitnami/charts/tree/master/bitnami/mariadb) |
| persistence | object | See values.yaml | Configure persistence settings for the chart under this key. |
| service | object | See values.yaml | Configures service settings for the chart. |

## Changelog

All notable changes to this application Helm chart will be documented in this file but does not include changes from our common library. To read those click [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common#changelog).

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

### [5.0.0]

#### Changed

- **BREAKING**: Upgraded the common library dependency to version 3.2.0. This introduces several breaking changes (`service`, `ingress` and `persistence` keys have been refactored).
  Be sure to check out the [library chart](https://github.com/k8s-at-home/library-charts/blob/common-3.2.0/charts/stable/common/) for the up-to-date values.
- Changed image tag to `3.1.1-apache`.

### [1.0.0]

#### Added

- N/A

#### Changed

- N/A

#### Removed

- N/A

[5.0.0]: #500
[1.0.0]: #100

## Support

- See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
