---
title: "[SOLVED] Upgrade Dependancy Problem"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by stuart264 on 2008-11-28
Can any wise person please offer advice about what I do to fix this error message as I am really stumped as to what is happening and my version of ubuntu refuses to upgrade

> stuart@stuart-linux:~$ sudo dpkg --configure -a
[sudo] password for stuart:
Setting up linux-image-2.6.27-10-generic (2.6.27-10.20) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-10-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-10-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-10-generic:
 linux-restricted-modules-2.6.27-10-generic depends on linux-image-2.6.27-10-generic; however:
  Package linux-image-2.6.27-10-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-10-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-10-generic; however:
  Package linux-image-2.6.27-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-10-generic; however:
  Package linux-restricted-modules-2.6.27-10-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.10.13); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.10.13); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-10-generic
 linux-restricted-modules-2.6.27-10-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

---

### Post by dstew on 2008-11-28
This looks like [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193439"). It seems that during installation, the grub-set-default program was run without the correct argument, and when update-grub is run during the configuration of your new kernel, the process expr gives an error, because /boot/grub/default is empty.

You can try to fix it by running **sudo set-grub-default 0** from a command line. That should create a /boot/grub/default file that sets the first menu item as the default.

---

### Post by stuart264 on 2008-12-01
Thanks that fixed it

---

