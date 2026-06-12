---
title: "Imagick got lost after upgrade"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by baju on 2008-04-26
Hi
I upgraded to Hardy yesterday. Most things work fine, but one problem remains. I have php5 and Imagick installed. However, since I upgraded ubutu php doesn't load the Imagick class anymore. phpinfo() reports that php is parsing the correspondig .ini-file and every file is in the right place.
I even tried to reinstall Imagick, which didn't help.
Any suggestions?

---

### Post by stevenwagner on 2008-04-26
Im having the same issue. On a clean install though.

---

### Post by stevenwagner on 2008-04-27
bug report here:
[https://bugs.launchpad.net/ubuntu/+source/php-imagick/+bug/203023](https://bugs.launchpad.net/ubuntu/+source/php-imagick/+bug/203023)

work around here:
[http://kevin.vanzonneveld.net/techblog/article/class_imagick_not_found/](http://kevin.vanzonneveld.net/techblog/article/class_imagick_not_found/)

---

### Post by baju on 2008-04-27
thanks, the fix works fine

---

