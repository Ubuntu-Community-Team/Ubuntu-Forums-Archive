---
title: "phpmyadmin doesn't work on 16.04, showing source instead of executing it"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by spectatorx on 2016-06-20
Today on fresh xubuntu 16.04 amd64 i've installed lamp by executing following command:
> 

sudo apt-get install apache2 mysql-server mysql-client php7.0-mysql php7.0-curl php7.0-json php7.0-cgi php7.0 phpmyadmin



Restarted apache2, checked if apache works and it works. Next i checked if phmyadmin works and it didn't work, initially i added [COLOR=#333333][FONT=UbuntuMono]Include /etc/phpmyadmin/apache.conf to [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] /etc/apache2/apache2.conf and aftter it code of phpmyadmin is not executed but it is just displayed in browser when i go to address [/FONT][/COLOR]http://localhost/phpmyadmin . How to fix this issue?


P.S.
Anyone can suggest more modules, libraries to install for lamp or these listed above are enough and ok for local coding with oop php?

---

### Post by spectatorx on 2016-06-21
Ok, i sort of solved problem by myself. Here is instruction how:

> 

sudo apt-get install -f apache2 mysql-server mysql-client php7.0-mysql php7.0-curl php7.0-json php7.0-cgi php7.0 phpmyadmin libapache2-mod-php7.0 php7.0-mbstring php7.0-fpm php7.0-cli php7.0-common php7.0-gd php7.0-bz2 php7.0-xml php7.0-intl php-pear php-imagick php7.0-imap php7.0-mcrypt php-memcache php7.0-pspell php7.0-recode php7.0-sqlite3 php7.0-tidy php7.0-xmlrpc php7.0-xsl php-gettext php-apcu


To set up under Apache all you need to do is include the following line in /etc/apache2/apache2.conf.


Include /etc/phpmyadmin/apache.conf



---

