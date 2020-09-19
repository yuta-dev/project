FROM php:7.4-apache
COPY ./php.ini /usr/local/etc/php/

RUN apt-get update \
  && apt-get install -y libzip-dev libpq-dev unzip\
  && docker-php-ext-install zip pdo_mysql mysqli bcmath\
  && docker-php-ext-enable mysqli

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

WORKDIR /var/www/html