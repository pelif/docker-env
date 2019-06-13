FROM ubuntu:latest

MAINTAINER Felipe Daniel <felipe.dandev@gmail.com>

RUN apt-get update && apt-get clean
RUN export TZ=America/Sao_Paulo

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get install -y nginx
RUN apt-get install -y php7.2
RUN apt-get install -y php-dev
RUN apt-get install -y libmcrypt-dev
RUN apt-get install -y php-pear
RUN apt-get install -y php-pear php7.2-curl php7.2-gd php7.2-mbstring  php7.2-zip php7.2-mysql php7.2-xml php-token-stream php7.2-json


RUN pecl install mcrypt-1.0.1

RUN apt-get install -y build-essential checkinstall zlib1g-dev
RUN apt-get install -y vim
RUN apt-get install -y curl
RUN apt-get clean

ADD ./configs/nginx.conf /etc/nginx/sites-enabled/defaul

#RUN docker-php-ext-install curl
#RUN docker-php-ext-install ctype
#RUN docker-php-ext-install json
#RUN docker-php-ext-install mbstring
#RUN docker-php-ext-install openssl
#RUN docker-php-ext-install pdo
#RUN docker-php-ext-install tokenizer
#RUN docker-php-ext-install xml
#RUN docker-php-ext-install mysqli
#RUN docker-php-ext-install pdo_mysql
#RUN docker-php-ext-install intl

RUN ln -sf /dev/stdout /var/log/nginx/access.log
RUN ln -sf /dev/sterr /var/log/nginx/error.log
RUN echo "daemon off;" >> /etc/nginx/nginx.conf

RUN apt-get install -y composer

CMD service nginx start -g

RUN cd /var/www/html
RUN composer create-project --prefer-dist laravel/laravel LocalApp
