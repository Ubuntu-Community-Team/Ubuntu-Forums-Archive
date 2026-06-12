---
title: "Update Ubuntu 7.10 to 8.04 &amp; get error: signal Segmentation fault (11)"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by gregory24 on 2008-08-28
Hi, I update from Ubuntu 7.10 to 8.04 and have problem only in php website. All pages is blank :(
In logs /var/log/apache2/error.log show this error all time after update:
[PHP][Thu Aug 28 00:50:42 2008] [notice] child pid 21380 exit signal Segmentation fault (11)[/PHP]
How I can repair this? All answers well be welcome. Thanks.

---

### Post by gregory24 on 2008-08-28
I find solution :D
I do this :rolleyes::
```
cp /usr/share/doc/php5-common/examples/php.ini-recommended  /etc/php5/apache2/php.ini
```
Now not have error in logs and pages in php work fine :D

---

