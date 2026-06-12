---
title: "Apache2 +PHP5"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by Wimmeke on 2006-07-04
Hi all,

My first post and my first steps with Ubuntu. I have installed apache2 by doing apt-get install apache2. This is working fine and serving html files happily. I also installed PHP5 by doing apt-get install php5. After this I enabled php in Apache by doing a2enmod php5

I created a php info file called test.php and put it in the root. When I surf to this  page it downloads it instead of executing it. If I download it and open the file; I can see the php code inside.

What am I missing here?? Probably it is something obvious, but I can't figure it out. Oh, and I found the following in my apache2.conf file:

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

Hope someone can help me with this

Thanks in advance!

Wim Toremans

---

### Post by Wimmeke on 2006-07-05
Ok, I solved this one myself. I reloaded apache yet another time (I already did before), but this time with a force-reload param.

/etc/init.d/apache2 force-reload

Problem solved.

Thanks!

---

