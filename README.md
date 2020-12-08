# flink-standalone-docker-cluster

A simple standalone flink docker cluster for development and testing, which is modified from [big-data-europe/docker-flink](https://github.com/big-data-europe/docker-flink).

Flink version: 1.10.2

## Build Docker Images

Before setting up the flink docker cluster, we first need to build the docker images for jobmanager (master) and taskmanager (worker):

```shell
$ chmod +x build.sh
$ ./build.sh
```

This script will create three docker images:

1.  **bde2020/flink-base**: A base image originated from `openjdk:8` with flink 1.10.2 binary
2.  **bde2020/flink-master**: An image based on `bde2020/flink-base` for creating flink master containers
3.  **bde2020/flink-worker**: An image based on `bde2020/flink-base` for creating flink worker containers

## Start Flink Standalone Cluster

After building the required docker images, now we can start our Flink standalone cluster by executing the following command:

```shell
$ docker-compose up -d
```

You can check the status of the docker containers by the following command:

```shell
$ docker-compose ps
```

To shut down the flink cluster, enter the command:

```shell
$ docker-compose down
```

## Check the Flink UI

You should be able to check the Flink UI under [http://localhost:8081/#/overview](http://localhost:8081/#/overview).

By default, you will create 1 jobmanager and 2 taskmanagers with 6 task slots for each taskmanager. To add more workers, you can directly modify `docker-compose.yml`.

For more detailed flink settings, please check the [official doc](https://ci.apache.org/projects/flink/flink-docs-release-1.10) and the [original docker repository](https://github.com/big-data-europe/docker-flink).

