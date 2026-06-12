---
title: "Failed to upgrade Kernel from 2.6.24-17 to 2.6.24-18"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by sfeone on 2008-06-06
Hi, Everyone...

A few days ago I tried the update by using 'sudo apt-get update' and 'sudo apt-get upgrade'. It showed several packages' updates and kernel upgrade from 2.6.24-17 to 2.6.24-18.
Of course I chose 'Y' and downloaded those packages and was installing them. But, suddenly I got the error message while updating the kernel.

I did lots of things but I could not resolve this problem. Some Ubuntu user recommended to me that I could install grub-splashimages so that I did. But it was also not good. Grub is being left unchanged as 2.6.24-17. Surprisingly there's no problem on booting the system with the previous kernel.

Please give me your great answer so that I can go through it.

Thanks a lot.


<<<<<<<<<< Error Message >>>>>>>>>>

sfeone@MyHome:~$ sudo apt-get install grub-splashimages
[sudo] password for sfeone:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
grub
The following NEW packages will be installed:
grub-splashimages
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 743kB of archives.
After this operation, 848kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe grub-splashimages 1.2.2 [743kB]
Fetched 743kB in 13s (55.2kB/s)
Selecting previously deselected package grub-splashimages.
(Reading database ... 219562 files and directories currently installed.)
Unpacking grub-splashimages (from .../grub-splashimages_1.2.2_all.deb) ...
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
linux-image-generic depends on linux-image-2.6.24-18-generic; however:
Package linux-image-2.6.24-18-generic is not configured yet.
linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
Package linux-image-generic is not configured yet.
linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
dependency problems - leaving unconfigured
Setting up grub-splashimages (1.2.2) ...
Errors were encountered while processing:
linux-image-2.6.24-18-generic
linux-ubuntu-modules-2.6.24-18-generic
linux-image-generic
linux-restricted-modules-2.6.24-18-generic
linux-restricted-modules-generic
linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Mr. Scott on 2008-06-06
I had a problem with the same kernel upgrade. Apparently it didn't configure properly and the boot kept failing. I booted the previous kernel and reinstalled the kernel upgrade through Synaptic. It solved my problem.

---

### Post by Sef on 2008-06-06
I upgraded through System > Administration > Upgrade Manager, and it worked.  For some reason, it would not update via the terminal.

---

### Post by Pumalite on 2008-06-06
Mine upgraded though the Terminal in all 5 computers.

---

### Post by axgriffi on 2008-06-07
I had the same problem but it turned out that my boot partition was full. After removing old kernels the upgrade proceeded without error.

---

