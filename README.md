# Customizing and Running Nginx in Docker

This guide demonstrates how to create, customize, and run an Nginx server using Docker.

## Table of Contents
1. [Starting with the Default Nginx Configuration](#starting-with-the-default-nginx-configuration)
2. [Customizing the Nginx Homepage](#customizing-the-nginx-homepage)
3. [Managing Docker Containers](#managing-docker-containers)
4. [Summary](#summary)

## Starting with the Default Nginx Configuration

### 1. Creating a Basic Dockerfile for Nginx

Create a file named `Dockerfile` with the following content:

```dockerfile
FROM nginx:alpine
```

This Dockerfile uses the official Nginx image based on Alpine Linux, which is lightweight and efficient.

### 2. Building the Docker Image

Build the Docker image using the following command:

```bash
docker build -t nginx_test:v0 -f Dockerfile .
```

This command builds a new Docker image tagged as `nginx_test:v0` using the instructions from the `Dockerfile`.

### 3. Running the Nginx Container with Default Configuration

Run the Nginx container using the following command:

```bash
docker run -d -p 9090:80 nginx_test:v0
```

This command runs the `nginx_test:v0` image in a Docker container, mapping port 9090 on the host to port 80 in the container.

### 4. Accessing the Default Nginx Page

Navigate to `http://localhost:9090` in your web browser. You should see the default Nginx welcome page.

## Customizing the Nginx Homepage

### 1. Modifying the Dockerfile to Overwrite the Homepage

Update the `Dockerfile` with the following content:

```dockerfile
FROM nginx:alpine
RUN echo "Overwrite Testing" > /usr/share/nginx/html/index.html
```

This modification overwrites the default Nginx homepage with custom content.

### 2. Rebuilding the Docker Image

Rebuild the Docker image with the new instructions:

```bash
docker build -t nginx_test:v1 -f Dockerfile .
```

This command rebuilds the Docker image and tags it as `nginx_test:v1`.

### 3. Running the Customized Nginx Container

Run the new customized Nginx container:

```bash
docker run -d -p 9090:80 nginx_test:v1
```

### 4. Accessing the Customized Nginx Page

Navigate to `http://localhost:9090` in your web browser. You should now see the custom content: "Overwrite Testing".

## Managing Docker Containers

### 1. Stopping a Running Container

To stop a running container:

```bash
docker stop <container_name>
```

Replace `<container_name>` with the actual name of your container.

### 2. Viewing All Containers

To view all containers, including stopped ones:

```bash
docker ps -a
```

### 3. Starting a Specific Container

To start a specific container:

```bash
docker run -d -p 9090:80 nginx_test:v1
```

This command starts a new container using the `nginx_test:v1` image.

## Summary

This guide demonstrates the process of:
1. Creating a basic Nginx Docker image
2. Customizing the Nginx homepage
3. Building and rebuilding Docker images
4. Running Docker containers with port mapping
5. Managing Docker containers (stopping, viewing, and starting)

These steps showcase the flexibility Docker provides in developing and deploying customized application environments.
