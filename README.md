# Docker Notes

## **Terminologies**

* Docker Images: run Dockerfiles, are immutable, a new image is created after editing a Dockerfile, and can run multiple instances of containers
* Dockerfile: build instructions in your directory e.g.

```
FROM xxx:tag
COPY package.json /app/
COPY src /app/
WORKDIR /app # equivalent to cd
RUN npm install
CMD ["node", "server.js"]
```

* Docker Registries: storage and distribution system(s) for Docker images
* Docker Containers: standalone, lightweight, executable package of software

*Registries/Dockerfile/Loadable Artifact (e.g. tar.gz) -> Image -> Container(s)*

## **Docker Commands**

### **Building Images**

Build an image. `.` refers to the Dockerfile being in your current dir

`docker built -t "name" .`

Pulls image 'xxx' from Docker registry with tag 0.00. By default, pulls from Docker Hub (docker.io).

`docker pull xxx:0.00`

Pulls image with tag "latest"

`docker pull xxx`

### **Building Containers from Image**

Runs a container from the image

`docker run name:latest`

Runs a container from the image, set a specified tag

`docker build it "name:X.X"`

Runs a container, generates a random name for container if not specified

`docker run xxx:tag` 

-d or --detach runs container in the background and prints container id

`docker run -d xxx:tag` 

Run container in local host

`docker run -d -p 9000:80 xxx:tag`

Starts a container, even ones that were previously stopped

`docker start containerid`

Names your container with --name

`docker run --name hello-world -d -p 9000:80 xxx:tag`

Stops a container

`docker stop containerid`

Exits and kills container

`ctrl + c`

### **Checks**

List running images

`docker images`

List running containers

`docker ps`

List running and stopped containers

`docker ps -a`

See logs for debugging

`docker logs containerid`
