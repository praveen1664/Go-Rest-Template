# go-rest-template

Go (Golang) API REST Template/Boilerplate with Gin Framework

The project is formed following the good practices for structuring projects in Golang specified in https://github.com/golang-standards/project-layout
* /cmd: In this folder are the input files to the project (main.go) as well as other files depending on the type of execution (eg database.db, config.yml, etc)
* /docs: In this folder the swagger configuration files are saved to automatically generate the API documentation (available at http://localhost:3000/docs/index.html)
* /internal: The application code is divided into two folders: api and pkg:
* /internal/api: Main application, controllers, middlewares and router
* /internal/pkg: Models, persistence and database.
* /pkg: Modules reusable in other applications (For example: crypto, handlers, etc)
* /test: Project unit tests
* Makefile: It facilitates the use of the application, it has the following format


## 1. Run with Docker

1. **Build**

```shell script
make build
docker build . -t go-rest-api-template
```

2. **Run**

```shell script
docker run -p 3000:3000 go-rest-api-template
```

3. **Test**

```shell script
go test -v ./test/...
```

_______

## 2. Generate Docs

```shell script
# Get swag
go get -u github.com/swaggo/swag/cmd/swag

# Generate docs
swag init --dir cmd/api --parseDependency --output docs
```

Run and go to **http://localhost:3000/docs/index.html**
