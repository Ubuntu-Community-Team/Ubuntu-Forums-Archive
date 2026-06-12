---
title: "Need help to fix this broken dependency"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by wjp.reg on 2008-03-07
I ran into a problem of insufficient space on my /boot partition and so apt-get could not complete installation of a new kernel update.  I figured I could free-up the space by removing older versions, but this wouldn't complete because of the aforementioned issue.

So I manually deleted everything but the most recent two image files and system maps, and ran "dpkg --configure -a" and all seemed well..

Well, not so..  here is the problem output 

> wolf@ubuntu-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-5-generic linux-ubuntu-modules-2.6.24-8-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 23.0MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 117981 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-5-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-5-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-5-generic
Cannot find /lib/modules/2.6.24-5-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-5-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-5-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-8-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-8-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-8-generic
Cannot find /lib/modules/2.6.24-8-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-8-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-8-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-5-generic
 linux-ubuntu-modules-2.6.24-8-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any suggestions?

---

### Post by ssj3strife on 2008-03-08
Have you tried creating dummy files for apt to delete? Try a command like this:

sudo touch /boot/System.map-2.6.24-8-generic

Not sure if that will help, but it's worth a shot.

---

### Post by wjp.reg on 2008-03-08
Thanks, but my impatience got the best of me and I decided to reinstall instead; I keep a separate /home partition so I should be ok :-)

---

### Post by odin_doma2 on 2008-05-08
> **ssj3strife said:**
> Have you tried creating dummy files for apt to delete? Try a command like this:

sudo touch /boot/System.map-2.6.24-8-generic

Not sure if that will help, but it's worth a shot.
Great idea!!!!
Thnx a lot!\\:D/

---

