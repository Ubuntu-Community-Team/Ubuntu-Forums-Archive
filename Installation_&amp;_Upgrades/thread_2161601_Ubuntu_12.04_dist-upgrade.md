---
title: "Ubuntu 12.04 dist-upgrade"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by isac630728 on 2013-07-11
Hi, 
I ran apt-get dist-upgrade, and this is what I see. Did it get upgraded? 


xvz@cache001:~$ sudo  apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.2.0-49 linux-headers-3.2.0-49-generic linux-image-3.2.0-49-generic
The following packages will be upgraded:
  linux-headers-server linux-image-server linux-server
3 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/51.2 MB of archives.
After this operation, 217 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Reading changelogs... Done
Get:1 Changelog for linux-image-server ([http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.2.0.49.59/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.2.0.49.59/changelog)) [32.3 kB]
linux-meta (3.2.0.49.59) precise; urgency=low
  [ Steve Conklin ]
  * Bump ABI
 -- Steve Conklin <sconklin@canonical.com>  Tue, 18 Jun 2013 12:37:21 -0500
/tmp/tmpoDsH7r (END)


I think it did not get upgraded.. why?

xvz@cache001:~$ dpkg --list | grep linux
ii  linux-firmware                   1.79.4                       Firmware for Linux kernel drivers
ii  linux-headers-3.2.0-23           3.2.0-23.36                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-23-generic   3.2.0-23.36                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-41           3.2.0-41.66                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic   3.2.0-41.66                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-43           3.2.0-43.68                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic   3.2.0-43.68                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-44           3.2.0-44.69                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic   3.2.0-44.69                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-45           3.2.0-45.70                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-generic   3.2.0-45.70                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48           3.2.0-48.74                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic   3.2.0-48.74                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-server             3.2.0.48.58                  Linux kernel headers on Server Equipment.
ii  linux-image-3.2.0-23-generic     3.2.0-23.36                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-41-generic     3.2.0-41.66                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-43-generic     3.2.0-43.68                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-44-generic     3.2.0-44.69                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-45-generic     3.2.0-45.70                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-48-generic     3.2.0-48.74                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-server               3.2.0.48.58                  Linux kernel image on Server Equipment.
ii  linux-libc-dev                   3.2.0-49.75                  Linux Kernel Headers for development
ii  linux-server                     3.2.0.48.58                  Complete Linux kernel on Server Equipment.




Thanks!

---

### Post by Toz on 2013-07-11
You must have apt-listchanges installed if you're seeing the changelog file. At the (END) statement, press your 'q' key to continue with the upgrade.

---

### Post by isac630728 on 2013-07-11
> **Toz said:**
> You must have apt-listchanges installed if you're seeing the changelog file. At the (END) statement, press your 'q' key to continue with the upgrade.

Thank you! It's now upgraded.

---

