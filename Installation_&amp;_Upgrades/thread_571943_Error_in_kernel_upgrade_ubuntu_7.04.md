---
title: "Error in kernel upgrade ubuntu 7.04"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by panc88 on 2007-10-09
Dear All,

I launched the following command

sudo apt-get upgrade

and here is the output in the command line:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.20-16-386 (2.6.20-16.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.20-16-386
Failed to create initrd image.
dpkg: error processing linux-image-2.6.20-16-386 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.20-16-386
E: Sub-process /usr/bin/dpkg returned an error code (1)


How can I solve this issue? I tried to look for a similar error in the forums with no success.

Many thanks to anyone who can help


Ciao

---

### Post by 5-HT on 2007-10-10
> **panc88 said:**
> 
gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.20-16-386
Failed to create initrd image.


Looks like there's no room left on /boot to create the initial ramdisk.

> **panc88 said:**
> 
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs. 

May be worth checking out as well.
cheers,

---

