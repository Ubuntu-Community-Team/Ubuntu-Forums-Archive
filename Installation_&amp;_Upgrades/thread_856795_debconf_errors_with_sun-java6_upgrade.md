---
title: "debconf errors with sun-java6 upgrade"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by daryl314 on 2008-07-11
hello,

i canceled my sun-java6 upgrade a few days ago because i couldn't read the user agreement.  now when i try to install it with apt-get, i am getting the following errors.  any ideas?

thanks,
daryl

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 136575 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-06-0ubuntu1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Unpacking sun-java6-jre (from .../sun-java6-jre_6-06-0ubuntu1_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-06-0ubuntu1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb
 /var/cache/apt/archives/sun-java6-jre_6-06-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2008-07-11
Close Synaptic if you have it open.
sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by daryl314 on 2008-07-11
i still get the same errors when i do a sudo apt-get install sun-java6-jre after running the commands you suggested

> **Pumalite said:**
> Close Synaptic if you have it open.
sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

