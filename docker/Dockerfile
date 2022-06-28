FROM yiisoftware/yii2-php:8.1-apache

RUN apt update && apt install -y git zip

COPY ./config/xdebug.development.ini /usr/local/etc/php/conf.d/xdebug.ini

RUN mkdir -p /vault/secrets/mw-ops/

COPY ./vault/secrets/mw-ops/composer-auth.json /root/.composer/auth.json

RUN mkdir -p /app
COPY ./app /app

WORKDIR /app

RUN composer install

COPY ./config/local/params.php config/params.php

ENV PHP_ENABLE_XDEBUG=1