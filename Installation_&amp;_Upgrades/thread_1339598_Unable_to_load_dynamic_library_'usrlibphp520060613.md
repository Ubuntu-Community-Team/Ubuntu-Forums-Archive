---
title: "Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so'"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by breauxlg on 2009-11-27
Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' I have this error in my apache log.Here's the complete error log. I'm trying to trouble shoot why images won't show up in my Drupal website. The Drupal people say it's a problem with my server.  Any help is greatly appreciated.
Lynn

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' - /usr/lib/php5/20060613+lfs/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Sun Nov 22 07:57:40 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.11-0.dotdeb.1 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Sun Nov 22 07:57:40 2009] [warn] long lost child came home! (pid 23214)
[Sun Nov 22 11:39:47 2009] [error] [client 61.160.216.63] File does not exist: /var/www/sharedip/prx2.php
[Sun Nov 22 21:51:32 2009] [error] [client 72.30.78.251] File does not exist: /var/www/sharedip/robots.txt
[Mon Nov 23 13:01:37 2009] [error] [client 61.160.216.63] File does not exist: /var/www/sharedip/prx2.php
[Mon Nov 23 15:47:00 2009] [error] [client 194.72.238.62] Invalid method in request \x16\x03
[Tue Nov 24 15:11:46 2009] [error] [client 61.160.216.63] File does not exist: /var/www/sharedip/prx2.php
[Tue Nov 24 16:43:42 2009] [error] [client 194.72.238.62] Invalid method in request \x16\x03\x01
[Wed Nov 25 12:14:59 2009] [error] [client 65.55.230.164] File does not exist: /var/www/sharedip/robots.txt
[Wed Nov 25 13:34:21 2009] [notice] caught SIGWINCH, shutting down gracefully
[Wed Nov 25 13:46:11 2009] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' - /usr/lib/php5/20060613+lfs/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Wed Nov 25 13:46:14 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.11-0.dotdeb.1 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Wed Nov 25 13:46:17 2009] [notice] caught SIGWINCH, shutting down gracefully
[Wed Nov 25 13:46:28 2009] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' - /usr/lib/php5/20060613+lfs/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Wed Nov 25 13:46:28 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.11-0.dotdeb.1 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Wed Nov 25 21:54:47 2009] [error] [client 72.30.78.251] File does not exist: /var/www/sharedip/robots.txt
[Thu Nov 26 08:16:52 2009] [notice] caught SIGWINCH, shutting down gracefully
[Thu Nov 26 08:17:28 2009] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' - /usr/lib/php5/20060613+lfs/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Thu Nov 26 08:17:29 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.11-0.dotdeb.1 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Thu Nov 26 11:06:30 2009] [error] [client 61.160.216.63] File does not exist: /var/www/sharedip/prx2.php
[Thu Nov 26 14:19:02 2009] [error] [client 212.119.226.86] File does not exist: /var/www/sharedip/user
[Fri Nov 27 10:03:17 2009] [error] [client 61.160.216.63] File does not exist: /var/www/sharedip/prx2.php
[Fri Nov 27 13:39:47 2009] [error] [client 142.240.200.10] File does not exist: /var/www/sharedip/favicon.ico
[Fri Nov 27 15:11:46 2009] [error] [client 65.55.207.119] File does not exist: /var/www/sharedip/robots.txt

---

### Post by CyberJack on 2009-11-30
Do the files '/usr/lib/php5/20060613+lfs/sqlite.so' and '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' exist?

It seems they do not, but are loaded in the php.ini file.
Both the .so files are provided by the php5-sqlite package.

---

### Post by codeFX on 2011-12-12
Just had the same problem with a newer version after upgrade:
```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/sqlite.so' - /usr/lib/php5/20090626/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
```It's not too hard to fix that ...just open that file:
```
nano /etc/php5/conf.d/sqlite.ini
```... and comment out the load instruction:
```
; configuration for php SQLite module
; extension=sqlite.so
```[http://www.codefx.biz]("http://www.codefx.biz/")

---

