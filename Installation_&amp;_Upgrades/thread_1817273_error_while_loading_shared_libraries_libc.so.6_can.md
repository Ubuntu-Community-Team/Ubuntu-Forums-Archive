---
title: "error while loading shared libraries: libc.so.6: cannot open shared object file: No s"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by dannneman on 2011-08-03
Hello.

Im running  a 8.04 LTS ( Linux web-t 2.6.24-23-server #1 SMP Mon Jan 26 00:55:21 UTC 2009 i686 GNU/Linux)

I runned apt-get update and then apt-get upgrade.

When the process came to libc6 it stopped.. (libc6_2.7-10ubuntu8_i386.deb)
Then everyting just said.. 
error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

(couldnt even do ps or ls).


Luckily i runned under vmware and had a snapshot to revert to.

But how do I update my system?

Thanx
Daniel

---

### Post by eugenevdm on 2011-12-22
How did you solve this problem? I have a VM that is down with this error:


root@radman:/var/lib/dpkg/triggers# /etc/init.d/radiusd start
Starting FreeRADIUS:/usr/local/sbin/radiusd: error while loading shared libraries: libfreeradius-radius-2.1.8.so: cannot open shared object file: No such file or directory
radiusd


This happened after trying to upgrade the VM.

---

