---
title: "dpkg: error processing libssl0.9.8_0.9.8o-7ubuntu3.1_amd64.deb (--install):"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by salwaya on 2013-02-19
hi 
am a newbie to ubuntu so i trumbeled to so many problems while installing NDprotector-folloing instructions:
# apt-get source libssl0.9.8
# cd openssl-0.9.8g
# vim debian/rules #to add "enable-rfc3779" 
# dpkg-buildpackage -rfakeroot
# sudo dpkg -i _[COLOR="Red"]libssl0.9.8_0.9.8g-16ubuntu3.1_i386.deb[/COLOR]_
the last line i didn't  understand am working with ubuntu version12.10 and i noticd during dpkg building that libssl0.9.8_0.9.8o-7ubuntu3.1_amd64.deb should be insted of ]libssl0.9.8_0.9.8g-16ubuntu3.1_i386.deb
this what it gives :
dpkg: error processing libssl0.9.8_0.9.8o-7ubuntu3.1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libssl0.9.8_0.9.8o-7ubuntu3.1_amd64.deb
can you pleaze help me ](*,)
and my english isn't so good  and am sorry about any inconvnient

---

### Post by dino99 on 2013-02-19
you can get a deb package from there:
[http://amnesiak.org/NDprotector/](http://amnesiak.org/NDprotector/)

but you might hit some issues: ipv6 with python for example.

what are your needs about that app ?

---

