# Commands for Relevant Tech Stacks

These are lists of commands that I commonly use for my personal projects as well as for work.

## Docker

List the file parameters with their values on your docker-compose.yml file
```bash
docker-compose config
```

Delete all images:
```bash
docker rm -vf $(docker ps -a -q)
docker rmi $(docker images -a -q)
```

Delete containers:
```bash
docker rm -f $(docker ps -a -q)
```

Delete all volumes:
```bash
docker volume rm $(docker volume ls -q)
docker volume prune
```

Remove all unused containers, networks, images (both dangling and unreferenced), and optionally, volumes.
```bash
Docker system prune -a
```

All Docker commands in one. This is meant to be used to wipe all docker images, containers, and volumes across board. `yes | *` is used to force user acceptance. Use this only at a last resort as this is a very destructive command. Will delete everything even outside the scope of this directory.
```bash
docker rm -vf $(docker ps -a -q)
docker rm -f $(docker ps -a -q)
docker rmi $(docker images -a -q)
docker volume rm $(docker volume ls -q)
yes | docker volume prune
yes | docker system prune -a
```

## Kubernetes

List all services
```bash
kubectl get svc
```

Retrieve all deployments
```bash
kubectl get deployments
```

Exposes the service externally so they can hit that point. `-type` from TYPE when listing all kubetcl services.
```bash
kubectl expose deployment httpbin —type=LoadBalancer —name=myhttpbin
```


Give information about which cluster you’re connecting to.
```bash
kubectl  cluster info
```


## MongoDB

List all available databases
```bash
show dbs || show databases
```

Connect to the database
```bash
mongo "mongodb://Admin:${DBPASSWORD}@<host>:<port>/admin?authSource=admin"
```

Example of the above connection
```bash
mongo mongodb://root:rootpassword@localhost:27017/admin?authSource=admin
```

List the entries of a database
```bash
show <db_entry_name>
```

Start using into the database
```bash
use <database_name>
```

Create a user (on admin db)
```bash
db.createUser(
  {
    user: "kifarunixdemoAdmin",
    pwd: passwordPrompt(),
    roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
  }
)
```

Create Collection
```bash
db.createCollection(“<collection_name>”)
```

Index your collection for performance reasons
```bash
db.invoices.createIndex({<>:1})
```

Insert Documents
```bash
db.<collection_name>.insertMany([<json_parameter_value_pairs])
```

Search for documents
```baSH
db.<collection_name>.find().pretty()
```
