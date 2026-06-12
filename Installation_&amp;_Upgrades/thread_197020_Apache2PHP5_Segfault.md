---
title: "Apache2/PHP5 Segfault"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by bstevant on 2006-06-15
Hi all,

I am running into problems with Apache2/PHP on Ubuntu Server 6.06 on i386. I am trying to install apps such as cacti and phpmyadmin.
Also notice the message when Apache is terminating :

[Thu Jun 15 10:46:04 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 PHP/5.1.2 configured -- resuming normal operations
[Thu Jun 15 10:46:09 2006] [notice] child pid 8912 exit signal Segmentation fault (11)
[Thu Jun 15 11:29:44 2006] [notice] child pid 8913 exit signal Segmentation fault (11)
[Thu Jun 15 11:32:32 2006] [notice] caught SIGTERM, shutting down
*** glibc detected *** double free or corruption (fasttop): 0x081f4450 ***

Segmentation fault appears each time I access a php page (which then is blank).
Any idea ?

---

### Post by bstevant on 2006-06-15
**Fixed:** I removed php4 from /etc/apache2/mods-available/
Why was I running both ? I don't know ...

---

