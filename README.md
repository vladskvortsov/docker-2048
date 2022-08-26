# Light Docker version of 2048

Based on alpine
Based on NGINX

# Dockerfile


```sh
FROM alpine:latest

MAINTAINER vladskvortsov

RUN apk --update add nginx

COPY 2048 /usr/share/nginx/html

RUN echo $'server { \n\
	listen 80; \n\
	listen [::]:80; \n\
	root /usr/share/nginx/html; \n\
	index index.html index.htm index.nginx-debian.html index.php; \n\
	server_name examp.com; \n\
}' > /etc/nginx/http.d/default.conf

CMD ["nginx", "-g", "daemon off;"]
```


## Run the docker container with your own build


```sh
    git clone https://github.com/vladskvortsov/docker-2048.git
    docker build . -t docker-2048
    docker run -d -p 8080:80 --name 2048 docker-2048
```

> Note: `--name 2048` to name the container.

## Run the docker container by pulling the image directly


```sh
    docker run -d -p 8080:80 vladskvortsov/docker-2048
```
## Access the game


```sh
    http://localhost:8080
```

If you run docker with boot2docker on Mac or Windows, the URL should be:

```sh
    http://192.168.59.103:8080
```
