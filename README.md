# react-ci3-apache-api-cr-list 🚀

![badge4](https://img.shields.io/badge/docker-3.3.1-blue)
[![Report an issue](https://img.shields.io/badge/Support-Issues-green)](https://github.com/tquangdo/react-ci3-apache-api-cr-list/issues/new)

## deploy local
1. ### FE
    - `cd php/react_app`
    - `react_app% npm i`
    > (when reflect to BE by webpack after change in FE: delete folder `php/react_app/dist`)
    - `npm run prod`
    - => will auto create folder `php/react_app/dist` 
1. ### BE
    - `cd ../..`
    - `docker-compose up -d`
    - access browser: `localhost:8000`
![demo](demo.png)

## note
1. ### check Docker's MEM limit
    - $ docker exec -it php74-dotq bash
    - php -r 'phpinfo();' | grep memory_limit
    - php -r "echo ini_get('memory_limit').PHP_EOL;"
    - cd /usr/local/etc/php/conf.d/
    - see 2 files "memory_limit.ini" & "docker-php-memlimit.ini"
1. ### config OpenSSL
    - $ docker exec -it php74-dotq bash
    - vim /etc/ssl/openssl.cnf
    > if not install vim yet: `apt-get install -y vim`
    - edit "CipherString = DEFAULT@SECLEVEL=2" -> "CipherString = DEFAULT@SECLEVEL=1"
    - exit
    - $ docker-compose restart
