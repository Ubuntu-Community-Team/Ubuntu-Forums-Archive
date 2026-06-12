---
title: "Can somone show me how to create a symlink for php please"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by Hawkowl on 2006-08-08
I posted this in newbs, but thought it might be more appropriate here.
The problem is i don't have any links for php in my mods-enabled, mods available folders in apache.

Could someone walk me through creating the necessary link please?

---

### Post by ngdias on 2006-08-10
I don't think it's necessary to create any simlink. You can look for hints on these locations

[http://strdoc.net/ubuntu-apache-php-mysql-server/](http://strdoc.net/ubuntu-apache-php-mysql-server/)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[http://ubuntuguide.org/wiki/Dapper#How_to_install_PHP_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Dapper#How_to_install_PHP_for_Apache_HTTP_Server)

but i think you probably jus need to install *libapache2-mod-php5* and it should work right away. Don't forget to check if you have the necessary filesystem permissions to execute the .php files.

---

