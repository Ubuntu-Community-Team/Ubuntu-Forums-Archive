---
title: "I cant install any apache packages"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by kustomjs on 2007-11-08
Hi Guys
I can not install this at all "apt-get install apache2 apache2-common apache2-doc apache2-mpm-prefork apache2-utils libapr0 libexpat1 ssl-cert" and when I enter it in terminal I get this:"root@Server1:~/tmp# apt-get install apache2 apache2-common apache2-doc apache2-mpm-prefork apache2-utils libapr0 libexpat1 ssl-cert
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
Package apache2-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  apache2.2-common apache2-utils
E: Package apache2-common has no installation candidate
root@Server1:~/tmp# "

how do I fix this?

---

### Post by taurus on 2007-11-08
I just checked and there is no apache2-common.  Instead, install the **apache2.2-common** as suggested.

---

