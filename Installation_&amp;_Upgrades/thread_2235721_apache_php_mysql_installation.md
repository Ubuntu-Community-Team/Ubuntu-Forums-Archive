---
title: "apache php mysql installation"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by mure-suresh-redd on 2014-07-22
i have installed ubuntu 14.04 server on this i have installed apache, mysql, php5.
the problem is when i try to open .php files. the file simply goes to save mode and does not open in brouser
some explain and guide me to solve it

---

### Post by yancek on 2014-07-22
See the link below which is a tutorial for installing LAMP on Ubuntu 14.04 and has some specifics on what you need in the apache configuration file for php.

[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04)

---

### Post by SeijiSensei on 2014-07-22
Make sure libapache2-mod-php5 is installed from the repositories.

The best way to install LAMP on Ubuntu is described [here](https://help.ubuntu.com/community/ApacheMySQLPHP).

---

### Post by mure-suresh-redd on 2014-07-25
i have tried as adviced. now i am getting a new blank browser page for "   phpinfo   ", it is not showing any information on php. is this correct or should i get some text information in browser

---

### Post by SeijiSensei on 2014-07-25
Where is the page located?  in 14.04 the default website directory is /var/www/html.  Is there a file in that directory that includes the code
```
<?php phpinfo() ?>
```

---

