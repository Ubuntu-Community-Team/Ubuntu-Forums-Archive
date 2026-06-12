---
title: "Postgresql works from cli but not from cgi"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by forceoflight on 2011-08-04
Hello,

I have weird problem with postgresql + nginx + php5 0 ubuntu 11.04. Postgresql works just fine, when I run "php test.php" from shell. I assume php runs from shell are called cgi runs?

When I open page from browser http://<some url>/test.php I get following error. I assume php runs from browser are called cgi runs?

Fatal error: Call to undefined function pg_connect() in /var/www/mydomain/htdocs/test.php on line 7


When you print php info, only reference to postgresql is pgsql.ini and pdo_pgsql.ini files that are parsed.

Additional .ini files parsed	/etc/php5/fpm/conf.d/curl.ini, /etc/php5/fpm/conf.d/gd.ini, /etc/php5/fpm/conf.d/mongodb.ini, /etc/php5/fpm/conf.d/mysql.ini, /etc/php5/fpm/conf.d/mysqli.ini, /etc/php5/fpm/conf.d/pdo.ini, /etc/php5/fpm/conf.d/pdo_mysql.ini, /etc/php5/fpm/conf.d/pdo_pgsql.ini, /etc/php5/fpm/conf.d/pgsql.ini, /etc/php5/fpm/conf.d/xmlrpc.ini

I do not have single php.ini file. I have cgi and cli. I don't know why it did two :)

/etc/php5/cgi/php.ini
/etc/php5/cli/php.ini

ubuntu@ip-10-114-81-139:~$ diff /etc/php5/cgi/php.ini /etc/php5/cli/php.ini
458c458
< memory_limit = 128M
---
> memory_limit = -1

As you can see files are fairly similar.



ubuntu@ip-10-114-81-139:~$ locate pgsql.ini
/etc/php5/conf.d/pdo_pgsql.ini
/etc/php5/conf.d/pgsql.ini


ubuntu@ip-10-114-81-139:~$ cat /etc/php5/conf.d/pgsql.ini
; configuration for php PostgreSQL module
extension=pgsql.so


ubuntu@ip-10-114-81-139:~$ locate pgsql.so
/usr/lib/php5/20090626/pdo_pgsql.so
/usr/lib/php5/20090626/pgsql.so
/usr/lib/postgresql/8.4/lib/plpgsql.so


ubuntu@ip-10-114-81-139:~$ ls -la /usr/lib/php5/20090626/*pgsql.so
-rw-r--r-- 1 root root  39344 2011-05-02 23:09 /usr/lib/php5/20090626/pdo_pgsql.so
-rw-r--r-- 1 root root 120896 2011-05-02 23:09 /usr/lib/php5/20090626/pgsql.so


I did install postgresql by running following commands:

sudo -s
aptitude install postgresql
aptitude install php5-pgsql

Regards,
FoL

---

### Post by skall on 2011-08-09
Did you restart the php-cgi server after install php postgre extension ?

---

### Post by forceoflight on 2011-08-09
Ye, it helped. Thanks!

/etc/init.d/php5-fpm restart

---

