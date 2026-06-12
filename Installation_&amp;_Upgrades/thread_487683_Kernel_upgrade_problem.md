---
title: "Kernel upgrade problem"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by mneisen on 2007-06-29
Hi, after solving my troubles with my boot partition (see [https://bugs.launchpad.net/ubuntu/+source/partman/+bug/122563](https://bugs.launchpad.net/ubuntu/+source/partman/+bug/122563) and [http://ubuntuforums.org/showthread.php?t=484030](http://ubuntuforums.org/showthread.php?t=484030)) I still have a problem with unresolved dependencies when upgrading the kernel:

Anybody know how to fix this?

```
mneisen@farm3:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Running postinst hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ...
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks in advance!

Kind regards
Martin

---

