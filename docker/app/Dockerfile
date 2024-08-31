FROM php:8.2-fpm

ENV TZ Asia/Tokyo

RUN apt-get update && \
	apt-get install -y \
	vim \
	git \
	unzip \
	nodejs \
	npm \
	libzip-dev libicu-dev libonig-dev && \
	docker-php-ext-install intl pdo_mysql zip bcmath


RUN npm install n -g
#好みのiniファイル
COPY ./docker/app/php.ini /usr/local/etc/php/php.ini
#bashrc追加
COPY ./docker/app/.bashrc /root/.bashrc
# composer 2.21を使用
COPY --from=composer:2.2 /usr/bin/composer /usr/bin/composer

WORKDIR /app