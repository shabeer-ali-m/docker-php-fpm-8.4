# PHP 8.4 FPM Alpine Docker Image

This repository provides a lightweight **PHP 8.4 FPM Docker image based on Alpine Linux** with commonly used extensions and tools for modern PHP applications (Laravel, Symfony, WordPress, custom apps, etc.).

The image is optimized for development and production environments and includes database drivers, Redis support, and Composer.

---

# Base Image

* `php:8.4-fpm-alpine`

Alpine Linux keeps the image small while still providing the required build tools and libraries.

---

# Included System Packages

The following Alpine packages are installed:

* git
* curl
* wget
* gzip
* zip / unzip
* poppler-utils
* libpng-dev
* oniguruma-dev
* libxml2-dev
* libzip-dev
* icu-dev
* linux-headers
* postgresql-dev
* PHP build dependencies (`$PHPIZE_DEPS`)

These packages support common PHP features and extensions such as image processing, internationalization, and database connectivity.

---

# Installed PHP Extensions

The following PHP extensions are compiled and enabled:

Core extensions:

* intl
* zip
* mbstring
* exif
* pcntl
* bcmath
* gd
* opcache

Database extensions:

* pdo_mysql
* pdo_pgsql
* pgsql

Additional extensions:

* redis (installed via PECL)

---

# OPcache Configuration

OPcache is enabled by default with the following settings:

```
opcache.enable=1
opcache.memory_consumption=256
opcache.interned_strings_buffer=16
opcache.max_accelerated_files=10000
opcache.revalidate_freq=2
opcache.validate_timestamps=1
```

These values provide a good balance between development and production performance.

---

# Composer

The latest version of **Composer** is included in the image.

Location:

```
/usr/bin/composer
```

Usage example:

```
composer install
```

---

# Working Directory

The container working directory is set to:

```
/var/www
```

This is where your application code should be mounted or copied.

---

# Example docker-compose

```
services:
  php:
    image: shabeeralim/php8-fpm:0.1.1
    volumes:
      - ./:/var/www
    working_dir: /var/www
```

---

# Use Cases

This image is suitable for:

* Laravel applications
* Symfony applications
* WordPress
* API backends
* Queue workers
* CLI scripts

---

# Notes

* Build dependencies are removed after installation to keep the image small.
* Alpine Linux keeps the overall image size minimal.
* Redis support is provided through the PECL extension.

---

# License

MIT License
