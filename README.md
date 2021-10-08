# 1. Docker util Commands

## 1.1. Copy Files from Host to Container
```
docker cp <sourceFile->foo.txt> <mycontainer>:</pathDestinyFile->foo.txt>
```

## 1.2. Copy Files from Container to Host 
```
docker cp <mycontainer>:</pathSourceFile->foo.txt> <DestinyFile->foo.txt> 
```

## 1.3. Run File Scripts on container
```
docker exec -u postgresuser containername psql dbname postgresuser -f /container/path/file.sql
```

## 1.4. Backup and Restore databases (Postgres) [Ref.](https://davejansen.com/how-to-dump-and-restore-a-postgresql-database-from-a-docker-container/)

### 1.4.1. Dump using pg_dump
```
docker exec -i pg_container_name /bin/bash -c "PGPASSWORD=pg_password pg_dump --username pg_username database_name" > /desired/path/on/your/machine/dump.sql
```

### 1.4.2. Restore using psql
```
docker exec -i pg_container_name /bin/bash -c "PGPASSWORD=pg_password psql --username pg_username database_name" < /path/on/your/machine/dump.sql
```

# 2. Configurations to Run Docker commands without sudo

### 2.1. Add the `docker` group if it doesn't already exist

```console
$ sudo groupadd docker
```

### 2.2. Add the connected user `$USER` to the docker group

Optionally change the username to match your preferred user.

```console
$ sudo gpasswd -a $USER docker
```

### 2.3. Restart the `docker` daemon

```console
$ sudo service docker restart
```

If you are on Ubuntu 14.04-15.10, use `docker.io` instead:

```console
$ sudo service docker.io restart
```
