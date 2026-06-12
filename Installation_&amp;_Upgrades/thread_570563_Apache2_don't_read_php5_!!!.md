---
title: "Apache2 don't read php5 !!!"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by dannowel on 2007-10-08
Hi,

I recently installed ubuntu server 7.04 with lamp... the problem is that apache don't read my php file, instead he pop me to open the file with a program or save it to hd... i searched many hour on forum, but now i'm out of idea :(

 i got the 2 files specified many times on forum 

/etc/apache2/mods-available/php5.load
/etc/apache2/mods-available/php5.conf

and there is php5.conf content:

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

Any idea will be very appreciated!

Thank you !

---

### Post by dannowel on 2007-10-09
Up ! ;)

---

