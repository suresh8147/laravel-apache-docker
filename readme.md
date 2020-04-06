# Laravel + Apache + Docker

## Description
Start developing a fresh Laravel application with `docker` using `docker-compose`.

The images used in this repo is `php:7.2-apache` and `mysql:5.7`. The goal is to make setting up the development as simple as possible.

## Up and running
Clone the repo:
```
$ git clone https://github.com/chbharathkumar/laravel-apache-docker.git
$ cd laravel-apache-docker
```
Next, use Docker’s composer image to mount the directories that you will need for your Laravel project and avoid the overhead of installing Composer globally:
$ docker run --rm -v $(pwd):/app composer install
```
As a final step, set permissions on the project directory
$ sudo chown -R ~/laravel-apache-docker
```
Copy `.env.example` to `.env`
```
$ cp .env.example .env 
```

Build the images and start the services:
```
$ docker-compose build
$ docker-compose up -d
```
## After Build
Once the process is complete, use the following command to list all of the running containers:

$ docker ps

We’ll now use docker-compose exec to set the application key for the Laravel application. The  docker-compose exec command allows you to run specific commands in containers.

The following command will generate a key and copy it to your .env file, ensuring that your user sessions and encrypted data remain secure:


$ docker-compose exec laravel-app php artisan key:generate

You now have the environment settings required to run your application. To cache these settings into a file, which will boost your application’s load speed, run:

$ docker-compose exec laravel-app php artisan config:cache


Your configuration settings will be loaded into /var/www/bootstrap/cache/config.php on the container.

As a final step, visit http://your_server_ip in the browser.


