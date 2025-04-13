# docker

### redis
```
docker run -d -p 6379:6379 --name redis-server redis
```

### redis-insight
```
docker run -v redisinsight:/db -p 8001:8001 --name redis-insight redislabs/redisinsight:latest
```

### redis and redisinsight network 
```
docker network create redisnetwork
docker network connect redisnetwork redis-server
docker network connect redisnetwork redis-insight
```

### elasticsearch + kibana
```
docker run -d -p 9200:9200 -p 5601:5601 --name elastic-kibana-server nshou/elasticsearch-kibana
```

### mongo
```
docker run -d -p 27017:27017 --name mongo-server mongo:latest
```

### postgres
```
docker run -d -p 5432:5432 --name postgres-server -e POSTGRES_PASSWORD=1 postgres
```

### rabbitmq
```
docker run -d -p 15672:15672 -p 5672:5672 --name rabbitmq-server rabbitmq:3-management

// username: guest
// password: guest
```

### consul
```
docker run -d -p 8500:8500 -p 8600:8600/udp --name=consul-server consul agent -server -ui -node=server-1 -bootstrap-expect=1 -client=0.0.0.0
```

### strapi
```
docker run -d --name strapi-server -e DATABASE_CLIENT=mongo -e DATABASE_NAME=strapi -e DATABASE_HOST=localhost -e DATABASE_PORT=27017 -e DATABASE_USERNAME=strapi -e DATABASE_PASSWORD=strapi -p 1337:1337 -v `pwd`/strapi-server:/srv/app strapi/strapi
```

### mysql
```
docker run -d --name mysql-server --network=mysqlnetwork -e MYSQL_ROOT_PASSWORD=1 -p 3306:3306 mysql:latest
```

### phpmyadmin
```
docker run -d --name phpmyadmin-ui --network=mysqlnetwork -e PMA_HOST=mysql-server -e PMA_PORT=3306 -p 8080:80 phpmyadmin/phpmyadmin:latest

// username: root
// password: 1
```

### mysql and phpmyadmin network 
```
docker network create mysqlnetwork
```

### ubuntu
```
docker run -it ubuntu
```