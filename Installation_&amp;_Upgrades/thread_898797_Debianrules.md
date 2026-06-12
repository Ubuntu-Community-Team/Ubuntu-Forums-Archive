---
title: "Debian/rules?"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by witchbutter on 2008-08-23
I'm trying to compile a custom revision of the 2.6.24-19 kernel provided by ubuntu using the "ubuntu method" as described on [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) and I'm to the point where I've edited the debian style config file in /boot and now must use the ensuing commands to compile and install it.  I've compiled custom kernels using make commands before and have not used debian or a debian based distro since 2.4.9 was exciting and new so can anyone explain to me what "debian/rules" is?  And why does it not work for me when I follow this how-to?

a copy of the error:

root@noisyfecker:/boot# debian/rules updateconfigs
bash: debian/rules: No such file or directory
root@noisyfecker:/boot#

---

### Post by kerry_s on 2008-08-23
[http://www.debian.org/doc/debian-policy/ch-source.html](http://www.debian.org/doc/debian-policy/ch-source.html)

---

