# PHP 5.3 Apache

PHP 5.3 [reached EOL](http://php.net/eol.php) on 14 Aug 2014 and thus, official docker support was [dropped](https://github.com/docker-library/php/pull/20). I still needed to run 5.3 so I built this image based on the latest official builds of PHP.

# What is PHP?

PHP is a server-side scripting language designed for web development, but which can also be used as a general-purpose programming language. PHP can be added to straight HTML or it can be used with a variety of templating engines and web frameworks. PHP code is usually processed by an interpreter, which is either implemented as a native module on the web-server or as a common gateway interface (CGI).

> [wikipedia.org/wiki/PHP](http://en.wikipedia.org/wiki/PHP)

![logo](https://raw.githubusercontent.com/docker-library/docs/master/php/logo.png)

# How to use this image.

## With Command Line

For PHP projects run through the command line interface (CLI), you can do the following.

### Create a `Dockerfile` in your PHP project

    FROM reallyenglish/php:5.3
    COPY . /var/www/html

Then, run the commands to build and run the Docker image:

    docker build -t my-php-app .
    docker run -it --rm --name my-running-app my-php-app

### Installing modules

To install additional modules use a `Dockerfile` like this:

``` Dockerfile
FROM reallyenglish/php:5.3

# Installs curl
RUN docker-php-ext-install curl
```

Then build the image:

``` bash
$ docker build -t my-php-app .
```

### Without a `Dockerfile`

If you don't want to include a `Dockerfile` in your project, it is sufficient to do the following:

    docker run -it --rm --name my-php-app -v "$PWD":/var/www/html reallyenglish/php:5.3

## Credits

- [helderco](https://github.com/helderco/docker-php-5.3) for the `fpm` version
- [eugeneware](https://github.com/eugeneware/docker-php-5.3-apache) for the `apache` version

# License

View [license information](http://php.net/license/) for the software contained in this image.
