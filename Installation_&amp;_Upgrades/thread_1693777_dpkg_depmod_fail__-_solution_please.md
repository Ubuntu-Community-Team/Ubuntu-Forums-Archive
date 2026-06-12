---
title: "dpkg depmod fail  - solution please?"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by tukkas on 2011-02-23
I'm on 2009.10 on an old laptop. the laptop lost all power during a security update and now apt-get is completely disfunctional.
> sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg 
...
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
then

> 
:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.31-22-generic (2.6.31-22.70) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.31-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
Bus error
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.31-22-generic
dpkg: subprocess installed post-installation script returned error exit status 1

I can not fix  this error with anything i've tried in apt-get and can not uninstall the kernel either -- any help most welcome

---

