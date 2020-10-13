FROM jenkinsci/blueocean

# 使用 root
USER root

# 安裝 git 等基本指令
RUN apk add bash
RUN apk add --no-cache git
RUN apk add vim

# 安裝跟 php 相關的指令, 否則無法使用 composer
RUN apk add curl php7 php7-json php7-openssl php7-iconv php7-phar php7-mbstring php7-xml php-dom

# 安裝 composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# 安裝 phpunit
RUN wget -O phpunit https://phar.phpunit.de/phpunit-7.phar
RUN chmod +x phpunit
RUN cp ./phpunit /usr/bin

# 安裝 xdebug
RUN apk add gcc g++ make libffi-dev openssl-dev
RUN apk add php7-dev
RUN apk add php7-pear php7-dev
 #php-pecl php-pear
RUN apk add build-base php7-tokenizer
RUN apk add clang

RUN pecl install xdebug
RUN echo "zend_extension=/usr/lib/php7/modules/xdebug.so" >> /etc/php7/php.ini

# php code sniffer
RUN apk add --update composer php-simplexml php-xmlwriter
RUN pear install PHP_CodeSniffer

# phpcs --report=checkstyle --report-file=checkstyle.xml --standard=Zend *.php

# 安裝 phploc 統計專案規模大小
# https://github.com/sebastianbergmann/phploc
RUN wget https://phar.phpunit.de/phploc.phar
RUN cp ./phploc.phar /usr/bin
RUN chmod +x /usr/bin/phploc

# 安裝 phpcpd Copy/Paste Detector (CPD) for php code
RUN wget https://phar.phpunit.de/phpcpd.phar
RUN cp ./phpcpd.phar /usr/bin
RUN chmod +x /usr/bin/phpcpd


