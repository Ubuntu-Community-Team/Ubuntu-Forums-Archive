---
title: "php 8.1 modules installed but missing"
date: 2024-02-11
forum: Installation &amp; Upgrades
---

### Post by freedom7070 on 2024-02-11
Hello,

I did an upgrade from Ubuntu Server 20.04 to **22.04 **which include an  upgrade from php7.4 to **8.1.** Now my problem is that my web-pages have  problems (Internal Server Error). After some evaluation I found out that  sever modules that are installed are not found.

 ```

#dpkg -l | grep php8


ii  libapache2-mod-php8.1                 8.1.2-1ubuntu2.14                             amd64        server-side, HTML-embedded scripting language  (Apache 2 module)
ii  php8.1                                8.1.2-1ubuntu2.14                             all          server-side, HTML-embedded scripting language  (metapackage)
ii  php8.1-apcu                           5.1.21+4.0.11-7ubuntu1                       amd64        APC User Cache for PHP
ii  php8.1-bcmath                         8.1.2-1ubuntu2.14                            amd64        Bcmath module for PHP
ii  php8.1-bz2                            8.1.2-1ubuntu2.14                            amd64        bzip2 module for PHP
ii  php8.1-cli                            8.1.2-1ubuntu2.14                             amd64        command-line interpreter for the PHP  scripting language
ii  php8.1-common                         8.1.2-1ubuntu2.14                             amd64        documentation, examples and common module for  PHP
ii  php8.1-curl                           8.1.2-1ubuntu2.14                            amd64        CURL module for PHP
rc  php8.1-fpm                            8.1.2-1ubuntu2.14                             amd64        server-side, HTML-embedded scripting language  (FPM-CGI binary)
ii  php8.1-gd                             8.1.2-1ubuntu2.14                            amd64        GD module for PHP
ii  php8.1-gmp                            8.1.2-1ubuntu2.14                            amd64        GMP module for PHP
ii  php8.1-igbinary                       3.2.6+2.0.8-7ubuntu1                         amd64        igbinary PHP serializer
ii  php8.1-imagick                        3.6.0-4ubuntu1                                amd64        Provides a wrapper to the ImageMagick  library
ii  php8.1-imap                           8.1.2-1ubuntu2.14                            amd64        IMAP module for PHP
ii  php8.1-intl                           8.1.2-1ubuntu2.14                             amd64        Internationalisation module for PHP
ii  php8.1-mbstring                       8.1.2-1ubuntu2.14                            amd64        MBSTRING module for PHP
ii  php8.1-memcache                        8.0+4.0.5.2+3.0.9~20170802.e702b5f9+-7       amd64        memcache  extension module for PHP
ii  php8.1-memcached                      3.1.5+2.2.0-14.1                              amd64        memcached extension module for PHP, uses  libmemcached
ii  php8.1-msgpack                        2.2.0~rc1+2.1.2+0.5.7-6                       amd64        PHP extension for interfacing with  MessagePack
ii  php8.1-mysql                          8.1.2-1ubuntu2.14                            amd64        MySQL module for PHP
ii  php8.1-opcache                        8.1.2-1ubuntu2.14                            amd64        Zend OpCache module for PHP
ii  php8.1-phpdbg                         8.1.2-1ubuntu2.14                             amd64        server-side, HTML-embedded scripting language  (PHPDBG binary)
ii  php8.1-raphf                          2.0.1+1.1.2-13                               amd64        raphf module for PHP
ii  php8.1-readline                       8.1.2-1ubuntu2.14                            amd64        readline module for PHP
ii  php8.1-redis                          5.3.5+4.3.0-5.1                               amd64        PHP extension for interfacing with Redis
ii  php8.1-xml                            8.1.2-1ubuntu2.14                             amd64        DOM, SimpleXML, XML, and XSL module for PHP
ii  php8.1-xmlrpc                         3:1.0.0~rc3-2                                 amd64        XML-RPC servers and clients functions for PHP
ii  php8.1-xsl                            8.1.2-1ubuntu2.14                            all          XSL module for PHP (dummy)
ii  php8.1-zip                            8.1.2-1ubuntu2.14                            amd64        Zip module for PHP

```

shows several modules, e.g. mysql and zip

which are not shown here:
```

#php -m

[PHP Modules]
apcu
calendar
Core
ctype
date
exif
FFI
fileinfo
filter
ftp
gettext
hash
iconv
igbinary
imagick
json
libxml
memcached
msgpack
openssl
pcntl
pcre
PDO
Phar
posix
raphf
readline
redis
Reflection
session
shmop
sockets
sodium
SPL
standard
sysvmsg
sysvsem
sysvshm
tokenizer
Zend OPcache
zlib

[Zend Modules]
Zend OPcache


```

On the web side I see that at least the mysql and zip module are missing as well.
What am I missing out? I cannot remember that I ever needed to do anything after I installed an php-package apth apt.

---

### Post by SeijiSensei on 2024-02-11
I'm sure this isn't the problem, but you did restart the web server after installing the modules, right?

---

### Post by freedom7070 on 2024-02-12
Of cause I did restart the web-server (apache2) and reboot the computer. I think it cannot be a problem of the web-server, since console and web show the same behaviour.

---

### Post by freedom7070 on 2024-02-13
Actually I was able to solve the problem myself running phpenmod manually:

```
# cd /etc/php/8.1/mods-available
# for i in `ls |sed 's/.ini//'`;do phpenmod $i; done
```

---

