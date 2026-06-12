---
title: "Install Webmin and phpadmin"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by Diana Rogger on 2007-07-01
Hi,

Can someone help me how to get and to install phpadmin and Webmin on ubuntu?

Thank you in advanced,

Diana

---

### Post by trak87 on 2007-07-01
You can install phpmyadmin via Synaptic, but it's only meaningful if you also have apache2, php and mysql installed as well, also installable via Synaptic. Not sure about webmin.

---

### Post by virushioyo on 2007-07-01
1. download from webmin.com
2. save it to /usr/local/src
3. untar it if u dl d tar file
4. before install, apt-get install perl5 libnet-ssleay-perl
5. then apt-get install openssl
6 cd /usr/local/src/webmin-1.350
7. sh setup.sh
8. then just follow the wizard will do. thanks

---

### Post by Diana Rogger on 2007-07-03
Hi everone,

Thanks for the replies.

Regards,

Diana

---

