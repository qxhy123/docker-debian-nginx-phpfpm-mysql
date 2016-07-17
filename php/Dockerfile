FROM daocloud.io/php:5.6-fpm
# Install modules
RUN apt-get update && apt-get install -y \
        Imagemagick \
        libevent-dev \
        libmagickwand-dev --fix-missing \
        vim \
        htop \
        tmux \
    && docker-php-ext-install pdo_mysql mysqli pcntl \
    && pecl install imagick-3.4.0 \
    && docker-php-ext-enable imagick \
    && pecl install redis-2.2.8 \
    && docker-php-ext-enable redis \
    && pecl install Xdebug-2.4.0 \
    && docker-php-ext-enable xdebug \
    && pecl install libevent-0.1.0 \
    && docker-php-ext-enable libevent \
    && export TERM=xterm \
    && apt-get clean \
    && apt-get autoclean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && curl -sS https://getcomposer.org/installer \
    | php -- --install-dir=/usr/bin --filename=composer
EXPOSE 9000 9001
CMD ["php-fpm"]