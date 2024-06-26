# container-info ![](https://img.shields.io/github/actions/workflow/status/tetra-fox/container-info/docker.yml?branch=main&style=flat-square)

A tiny Golang API that returns metadata of all Docker containers.

I created this because I wanted a simple way to get the status of the various services that run my home network without returning sensitive information (such as my network configuration, volume bindings or entrypoint arguments).

You can see a live instance of this [here](https://home.tetra.cool/api), and in use [here](https://home.tetra.cool)!

### docker-compose example

```yaml
services:
  container-info:
    image: "ghcr.io/tetra-fox/container-info:latest"
    ports:
      - "3621:8080"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro # So we can get information from Docker!
```

### Endpoints

| Method | Endpoint       | Description                                                           |
| ------ | -------------- | --------------------------------------------------------------------- |
| GET    | /              | Returns the metadata of all containers.                               |
| GET    | /{name(s)} | Returns the metadata of the specified container(s). (comma-separated) |
