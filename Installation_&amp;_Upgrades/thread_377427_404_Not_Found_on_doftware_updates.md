---
title: "404 Not Found on doftware updates"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by niC666 on 2007-03-06
Hi

There are reportedly 16 packages waiting to be upgraded but when i try to do this (software updates or apt-get upgrade) i get a 404 Not Found error.

All the packages relate to php5 (except libmagik9 and slocate), and all come from security.ubuntu.com

My system is edgy.

On looking at the package file (in package.tgz) i see the reference to the file i'm trying to get:
 [http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2.2_i386.deb)

when browsing the repository, i see the file is actually called:
[http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2_i386.deb)

(*ubuntu2* not *ubuntu2.2*)

Anyone got any advice on fixing htis, or have i done something stupid?

niC

---

### Post by Kateikyoushi on 2007-03-06
I do not think you did anything stupid, just wait a bit and try to update then upgrade again.

---

