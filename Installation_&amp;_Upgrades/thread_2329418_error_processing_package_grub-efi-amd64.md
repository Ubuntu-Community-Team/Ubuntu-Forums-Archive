---
title: "error processing package grub-efi-amd64"
date: 2016-07-01
forum: Installation &amp; Upgrades
---

### Post by bulgin on 2016-07-01
me@linux:~$ cat /etc/*-releaseDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.4 LTS"
NAME="Ubuntu"
VERSION="14.04.4 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.4 LTS"
VERSION_ID="14.04"
uname -r
3.13.0-91-generic

Errors after sudo apt-get update and sudo apt-get upgrade:

dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 128
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-efi-amd64 (= 2.02~beta2-9ubuntu1.8); however:
  Package grub-efi-amd64 is not configured yet.


HELP?

---

### Post by kansasnoob on 2016-07-01
Try:

```
sudo dpkg --configure -a
```

Then try to update again.

---

### Post by bulgin on 2016-07-01
Thank you.

Same response as before:

me@linux:~$ sudo dpkg --configure -a
[sudo] password for me: 
Setting up grub-efi-amd64 (2.02~beta2-9ubuntu1.8) ...
dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 128
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-efi-amd64 (= 2.02~beta2-9ubuntu1.8); however:
  Package grub-efi-amd64 is not configured yet.


dpkg: error processing package grub-efi (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-efi-amd64
 grub-efi

---

