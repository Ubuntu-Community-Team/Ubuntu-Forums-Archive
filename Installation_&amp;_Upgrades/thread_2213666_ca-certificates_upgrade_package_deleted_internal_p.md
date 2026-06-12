---
title: "ca-certificates upgrade package deleted internal private CA root certificate"
date: 2014-03-27
forum: Installation &amp; Upgrades
---

### Post by Paul_Suh on 2014-03-27
Folks,

First time posting to these forums; I'm a long-time Mac OS X and OpenBSD admin and developer, dabbling with Ubuntu server. 

I just did an "sudo apt-get upgrade" on my 13.10 server and one of the packages (ca-certificates, almost certainly) deleted the private CA root certificate that I had installed in /usr/share/ca-certificates (at the top level, NOT inside the mozilla/ or spi-inc.org/ subdirectories). 

First, is this a bug that I should report? If so, where is the right place to report it? 

Second, is there a better place for me to install the private CA root certificate, where it will be found by the "dpkg-reconfigure ca-certificates" and "update-ca-certificates" commands, but not overwritten by future updates? 


--Paul

---

