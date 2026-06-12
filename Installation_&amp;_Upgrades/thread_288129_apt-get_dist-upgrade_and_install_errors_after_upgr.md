---
title: "apt-get dist-upgrade and install errors after upgrading to Edgy"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by rcnap on 2006-10-29
Started getting this after upgrading to Edgy.

sudo apt-get dist-upgrade
Reading package lists... Done
Segmentation fault (core dumped)

Anyone got any ideas?

I get this along with the segmentation fault (core dumped) when I try and run aptitude:

Ouch!  Got SIGSEGV, dying..

---

### Post by nardis_Miles1 on 2006-10-29
A seg fault can happen if there isn't enough room for caching during the update (I have a fairly superficial grasp of this.) Append the following line to apt.conf in /etc/apt and see what happens.

Apt::Cache-Limit 12582912;

Good luck!

---

### Post by nardis_Miles1 on 2006-10-29
A seg fault can happen if there isn't enough room for caching during the update (I have a fairly superficial grasp of this.) Append the following line to apt.conf in /etc/apt and see what happens.

Apt::Cache-Limit 12582912;

Good luck!

---

### Post by rcnap on 2006-10-29
It is still doing the same thing, but thanks for the idea.

---

### Post by Jandark on 2008-05-12
check this topic [http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

---

