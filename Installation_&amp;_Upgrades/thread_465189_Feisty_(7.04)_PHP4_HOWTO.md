---
title: "Feisty (7.04) PHP4 HOWTO"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by pestilence on 2007-06-05
This is a short tutorial on how to enable PHP4 support in feisty **without needing to compile any sources or use a fastcgi solution.**
[B]1) [COLOR="Red"]Download[/COLOR] the following packages from a Debian repository:
libapache2-mod-php4_4.4.4-9+lenny1_i386.deb
php4_4.4.4-9+lenny1_all.deb
php4-cli_4.4.4-9+lenny1_i386.deb
php4-common_4.4.4-9+lenny1_i386.deb
php4-curl_4.4.4-9+lenny1_i386.deb
php4-gd_4.4.4-9+lenny1_i386.deb
php4-mysql_4.4.4-9+lenny1_i386.deb[/B]

The above files can be found in the Debian repository inside under the following directory:
**```
ftp://ftp.somedebianrepository.com/pub/linux/debian/pool/main/p/php4/
```**

[B]2) Install the following packages from adept:
libzzip-0-12
apache2
apache2.2-common
apache2-mpm-prefork[/B]

After installing the packages from step2, proceed installing the packages you downloaded in step1.
Restart you webserver, you should be running apache2 with php4 enabled.
**In case you need any additional packages of php installed: (e.g php4-dommxlm) Just download the required package from the repository and install it.**

Enjoy!

---

