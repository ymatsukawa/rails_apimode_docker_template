# rails template

## system requirements

* docker
* docker-compose

## ruby / rails version

* ruby 3.1.1
* rails 7.0.2.3

## installation

```
$ docker-compose build
```

## db migration

this template uses [ridgepole](https://github.com/ridgepole/ridgepole)

when edit schema, see [db/Schemafile](./db/Schemafile)

```
$ docker-compose run app rake ridge:reset

# if you want to seed
$ docker-compose run app rake ridge:seed
```

## start server

```
$ docker-compose up

# in other terminal
$  curl -X POST -H "Content-Type: application/json" -d '{"title":"my title", "text":"lorem ipsum"}' localhost:5000/v1/articles

{"status":201,"message":"resource created","body":{"article":{"title":"my title"}}}
```

## testing

before running

```
$ docker-compose run app rake ridge:reset RAILS_ENV=test
```

### unit test

```
$ docker-compose run app rspec

# specific spec
$ docker-compose run app rspec/request
```