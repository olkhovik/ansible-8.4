# ansible-8.4

## Что делает playbook

Плейбук развернёт три приложения:

- Clickhouse
- Lighthouse
- Vector

Дистрибутивы Clickhouse, Vector в пакетах `rpm`, статика Lighthouse c GitHub и Nginx из epel-репозитория скачиваются при запуске плейбука.

## Какие у него есть теги

- clickhouse
- lighthouse
- vector

## Какие у него есть параметры

`Clickhouse` и `vector` будут установлены как службы, `lighthouse` будет установлен в `/home/dmitry/lighthouse` с правами `root`

### Clickhouse

* Параметр, который определяет какой версии clickhouse будет установлен
    ```yml
    clickhouse_version: 'latest' 	
    ```

### Lighthouse

* Чтобы открыть `lighthouse` на хосте вместе с ним будет запущен веб-сервер `nginx`


### Vector

* Версия Vector.
  ```yml
  vector_version: "0.21.2"
  ```
* После установки и запуска `vector` он будет провалидирован


## Как запустить

1. Задайте IP хостов в [hosts.yml](inventory/hosts.yml)
1. Запустите плейбук
    ```bash
    ansible-inventory -i inventory/hosts.yml site.yml
    ```