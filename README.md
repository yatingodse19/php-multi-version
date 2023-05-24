# Multi-Version PHP Docker Setup

This repository contains a Docker Compose setup for running multiple versions of PHP (5.6 and 7.4) using Nginx as the web server. MySQL is also included for database functionality.

## Prerequisites

Ensure you have Docker and Docker Compose installed on your system. 

## Structure

The project contains the following directories:

- `php56` - contains the PHP 5.6 application files.
- `php74` - contains the PHP 7.4 application files.
- `mysql` - contains MySQL data files.
- `nginx` - contains Nginx configuration files and SSL certificates.

## Setup

1. Clone this repository:

2. Navigate to the project directory:

3. Build and start the containers:

Your services should now be running at `https://php56.local` and `https://php74.local`.

## MySQL

MySQL service is also provided with this Docker setup. The default root password is defined in the docker-compose file.

The MySQL data directory is mounted to the `mysql` directory in the project root. This ensures that the data persists even when the MySQL container is stopped or removed.

The MySQL server can be accessed at `localhost:3306` or from other services like `php56` or `php74` using the service name `mysql` as the hostname.

## Configuration

You can customize the PHP, Nginx, and MySQL configurations by editing the respective files in the project. 

Remember to restart your containers for the changes to take effect:

docker-compose down
docker-compose up -d


## Security

This project is configured to use SSL for secure connections. Create cert directory put your SSL certificates init.
To create Local SSL use following command

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout php-local.key -out php-local.crt

Fill in the required information when prompted. The generated php-local.key and php-local.crt files will be used for both PHP 5.6 and PHP 7.4 domains.


