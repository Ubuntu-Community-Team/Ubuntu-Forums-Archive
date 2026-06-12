---
title: "[SOLVED] Update Error - How do I proceed"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by Bill Roberts on 2008-08-08
I applied updates after installing Hardy and something failed.  Every update since finishes with the following messages:

E: linux-image-2.6.24-19-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-19-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-19-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

I have tried re-applying these items using the Synaptic Package Manager, but the result is always the same as above.

What's the next step?

---

### Post by Diabolis on 2008-08-08
Your drive might not have enough free space.
```
sudo apt-get autoclean
sudo apt-get autoremove
```

Run:
```
df -H
```

To see the usage of your drives.

---

### Post by Bill Roberts on 2008-08-09
Here's the output from apt-get autoremove:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-19-generic (2.6.24-19.36) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.24-19-generic)
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-19-generic; however:
  Package linux-restricted-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.19.21); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

and df -H

Filesystem             Size   Used  Avail Use% Mounted on
/dev/md2               7.5G   531M   6.6G   8% /
varrun                 1.1G   111k   1.1G   1% /var/run
udev                   1.1G   205k   1.1G   1% /dev
devshm                 1.1G    13k   1.1G   1% /dev/shm
/dev/md0               128M    26M    95M  22% /boot
/dev/md3                15G   2.3G    12G  16% /usr
/dev/md4                15G   1.2G    14G   8% /var
/dev/md5               7.5G   151M   7.0G   3% /tmp
/dev/md6               2.2T   364M   2.1T   1% /home
gvfs-fuse-daemon       7.5G   531M   6.6G   8% /home/xxxxx/.gvfs

---

### Post by Bill Roberts on 2008-08-09
A little more research and I tried apt-get -f upgrade

Problem solved

---

### Post by Diabolis on 2008-08-09
Fix broken packages and try it again.
```
sudo apt-get install -f install
```

---

### Post by Diabolis on 2008-08-09
Oh, a bit late.

Don't forget to mark the thread as solved.
*thread tools / mark as solved*

---

