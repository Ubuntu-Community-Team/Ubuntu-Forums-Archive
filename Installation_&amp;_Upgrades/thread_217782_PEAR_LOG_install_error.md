---
title: "PEAR LOG install error"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by hermy on 2006-07-17
Hi, 

I got the following error when trying to install pear log module.

sudo pear install log
Did not download optional dependencies: pear/DB, pear/MDB2, use --alldeps to download automatically
pear/Log can optionally use package "pear/DB" (version >= 1.3)
pear/Log can optionally use package "pear/MDB2" (version >= 2.0.0RC1)
downloading Log-1.9.7.tgz ...
Starting to download Log-1.9.7.tgz (38,592 bytes)
..........done: 38,592 bytes

Fatal error: Allowed memory size of 8388608 bytes exhausted (tried to allocate 92160 bytes) in /usr/share/php/PEAR/PackageFile/v2/Validator.php on line 871



I use Apache2 and php5 from Ubuntu 6.06 on my 64bit AMD.


 dpkg -l | grep php
ii  libapache-mod-php5                               5.1.4-1.dotdeb.2                      PHP 5 scripting language - apache 1.3 module
ii  libapache2-mod-php5                              5.1.4-1.dotdeb.2                      PHP 5 scripting language - apache 2.0 module
ii  php-fpdf                                         1.53.dfsg-2                           PHP class to generate PDF files
ii  php-pear                                         5.1.2-1ubuntu3                        PEAR - PHP Extension and Application Reposit
ii  php5                                             5.1.4-1.dotdeb.2                      server-side, HTML-embedded scripting languag
ii  php5-cgi                                         5.1.4-1.dotdeb.2                      PHP 5 scripting language
ii  php5-cli                                         5.1.4-1.dotdeb.2                      PHP 5 scripting language
ii  php5-common                                      5.1.4-1.dotdeb.2                      Common files for packages built from the php
ii  php5-mysql                                       5.1.4-1.dotdeb.2                      MySQL module for php5
ii  php5-mysqli                                      5.1.4-1.dotdeb.2                      MySQLi module for php5
ii  php5-pgsql                                       5.1.4-1.dotdeb.2                      PostgreSQL module for php5

Has anyone some help?


Thanks

Hermy

---

### Post by gevans on 2006-07-20
Try this:

sudo nano /etc/php5/apache2/php.ini

Look for: 
```
memory_limit = 8M      ; Maximum amount of memory a script may consume (8MB)

```

change it to:
```
memory_limit = 32M      ; Maximum amount of memory a script may consume (32MB)
```

That should fix you up I think

---

