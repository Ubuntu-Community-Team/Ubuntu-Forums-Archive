---
title: "exit status 139"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by mlucool on 2007-09-08
I try:  sudo apt-get -f dist-upgrade 

and get:
[B]Preconfiguring packages ...
(Reading database ... 24079 files and directories currently installed.)
Removing cvs ...
Removing ubuntu-minimal ...
Removing base-config ...
(Reading database ... 23842 files and directories currently installed.)
Preparing to replace klibc-utils 1.0.14-1ubuntu4 (using .../klibc-utils_1.4.10-0ubuntu3_i386.deb) ...
Unpacking replacement klibc-utils ...
Preparing to replace libklibc 1.0.14-1ubuntu4 (using .../libklibc_1.4.10-0ubuntu3_i386.deb) ...
Unpacking replacement libklibc ...
Preparing to replace initramfs-tools 0.32 (using .../initramfs-tools_0.69ubuntu20_all.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 5: 10141 Segmentation fault      mv /etc/mkinitramfs /etc/initramfs-tools
dpkg: error processing /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 139
Errors were encountered while processing:
 /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

---

### Post by mlucool on 2007-09-08
anyone have any ideas on where to start?

---

