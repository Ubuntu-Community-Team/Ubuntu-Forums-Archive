---
title: "torrentflux is not working"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Martje_001 on 2007-10-27
Hi,
I've installed torrentflux on Ubuntu. It installed fine, my mysql passwords were correct. But when I go to 'myserver.lan/torrentflux', it try's to download a file (PHTML) :(.

---

### Post by changlinn on 2008-02-05
My solution was long arduous and involved a lot of googling, but started with apt-get remove php4 php5 --purge
and then reinstalling torrentflux and  apt-get install php5-mysql
This seemed to fix that error...

---

