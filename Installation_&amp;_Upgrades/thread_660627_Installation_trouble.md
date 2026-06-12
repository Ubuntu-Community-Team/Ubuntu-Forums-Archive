---
title: "Installation trouble"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by nzgabriel on 2008-01-07
Whenever I try to install an application in Ubuntu 7.10 64bit, it returns an error. The following is the entire steps trying to install a program with the terminal:

```
gabriel@X2-Global-V:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by adprice on 2008-01-07
I'm pretty new at this so I don't know if it will help, but it looks like some part of the installer is trying to use getopt, which it claims it can't find.  Maybe type "whereis getopt" to see if you have it installed.

---

### Post by Pumalite on 2008-01-07
Try this first:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
Post results.

---

### Post by nzgabriel on 2008-01-07
> **Pumalite said:**
> Try this first:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
Post results.

Results below, and to summarise: it failed.

```
gabriel@X2-Global-V:~$ sudo dpkg --configure -a
[sudo] password for gabriel:
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up clamav-base (0.91.2-3ubuntu2.1) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-base (>= 0.91.2-3ubuntu2.1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.91.2-3ubuntu2.1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 clamav-base
 clamav-daemon
 clamav-freshclam
 clamav
```

---

### Post by Pumalite on 2008-01-08
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

---

### Post by scurry7 on 2008-01-08
I need help also :confused:
I have a very very similar issue. My install was working fine (after much work, but it was working).
this is what I did:
```
apt-get remove linux-image-2.6.22-14-generic nfs-common nfs-kernel-server python-wxversion python-wxgtk2.8 python-wxtools
aptitude update
aptitude upgrade
aptitude install linux-image-2.6.22-14-generic
exit
```
now when I boot I get:
Error 15: File not found

I am booting into windoz and have both ext2 partitions mounted as drive letters, what can i check? did i kill my kernel? what did i do?

---

### Post by Pumalite on 2008-01-08
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by scurry7 on 2008-01-08
Thanks Pumalite (ive seen you all over ubuntuforums.org) 
My /boot/initrd.img-2.6.22-14-generic is missing. 

from a post I found it looks like i can mkinitrd, but if i cant boot then how would i do a mkinitrd?

:confused:

---

### Post by Pumalite on 2008-01-08
If it's a new installation, I'd reinstall.

---

### Post by scurry7 on 2008-01-08
i've been using it for about a month.  I have a bunch of progs that i like installed (i will lose those huh?). is it difficult to fix?

---

### Post by Pumalite on 2008-01-08
You can use AptOnCD to save your programs, but it's not worth the trouble. You can do everything again and be assured you are OK., and it's fun.

---

### Post by scurry7 on 2008-01-08
okay, re-install it is...:(
what do you think caused it (besides my stupidity)?

---

### Post by Pumalite on 2008-01-08
Read the link I gave you. All the possibilities are there.

---

