---
title: "I skipped LAMP on the install and now want it, easy solution?"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by 0xCAFEFACE on 2010-10-27
On ubuntu server 9.10, the installation offers pre-set setups for different services such as LAMP, samba, etc... I skipped LAMP on the server but now I want it.

When I went to install with apt-get, I noticed all ownership for the web was under root and I'm not experienced enough to know all the things this option did to ensure security (such as create a user and give ownership to "WWW-DATA" instead).

Is there a simple option for me to go back and get this process to install a second time, or if not, is there a great tutorial that provides a step-by-step example of the best way to secure LAMP on a fresh install?

(side-note, when I installed, I typed in _sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server_ )

Thanks!

---

### Post by sisco311 on 2010-10-27
Check out the Ubuntu Server Guide: [uhelp]9.10/serverguide/C/index.html[/uhelp]

---

### Post by efflandt on 2010-10-28
Here is one link of an explanation how to install LAMP [http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/](http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/)

But I was interrupted by a phone call while installing phpmyadmin, so not sure if I did something wrong, but that part did not work in Maverick until I symlinked it to apache2 sites-enabled:

[B]sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/sites-enabled/.

sudo /etc/init.d/apache2 restart[/B]

I also played around with how to add and configure name based virtual hosts in apache2 by creating another file in sites-enabled with <VirtualHost *:80> </VirtualHost> wrappers

---

### Post by 0xCAFEFACE on 2010-10-28
Thanks for the responses everyone.

The solution was to use 'tasksel' as per the Ubuntu Server Guide: 9.10.

---

