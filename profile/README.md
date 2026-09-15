# TatNet

**[tatnet.ru](https://tatnet.ru)** — российская платформа для разработчиков:
деплой приложений из Git, serverless-функции, ИИ-конструктор сайтов — и
полноценная инфраструктура под капотом: виртуальные машины KVM, приватные
сети, управляемые Postgres, Valkey и Kubernetes, объектное хранилище S3,
DNS и бесплатные SSL. Оплата в рублях, дата-центры в России.

[Панель](https://min.tatnet.ru) · [Документация](https://docs.tatnet.ru) ·
[Справочник API](https://api.tatnet.ru/v1/docs) ·
[Контракт OpenAPI](https://api.tatnet.ru/v1/openapi.json)

## Здесь — то, что работает у вас

В этой организации лежит код, который вы запускаете сами: клиенты
публичного API и компоненты, работающие внутри ваших кластеров Kubernetes.
Всё под Apache-2.0.

| | |
|---|---|
| **[tatnet-cli](https://github.com/tatnet-ru/tatnet-cli)** | Консольный клиент. `npx tatnet` — и всё облако из терминала |
| **[tatnet-go](https://github.com/tatnet-ru/tatnet-go)** | Go-клиент API, генерируемый из контракта `/v1` |
| **[tatnet-cloud-controller-manager](https://github.com/tatnet-ru/tatnet-cloud-controller-manager)** | `Service` типа `LoadBalancer` и жизненный цикл узлов в managed Kubernetes |
| **[tatnet-csi-driver](https://github.com/tatnet-ru/tatnet-csi-driver)** | Блочные тома: PVC поверх дисков платформы |
| **[libovsdb](https://github.com/tatnet-ru/libovsdb)** | Форк клиента OVSDB с исправлениями гонок при переподключении |

## Начать

```bash
npx tatnet auth login     # ключ создаётся в панели: min.tatnet.ru/api-keys
npx tatnet project list
```

CCM и CSI ставить руками не нужно — их доставляет платформа в managed-кластер.
Они открыты потому, что работают на ваших узлах с привилегиями, и код,
который там исполняется, должен быть доступен для проверки.

## API

Всё публичное API описано контрактом OpenAPI, из которого генерируется
[Go-клиент](https://github.com/tatnet-ru/tatnet-go), а на нём построены CLI и
оба компонента Kubernetes. Расхождение контракта и клиентов ловится тестами,
а не договорённостью.
