---
title: "initramfs errors (1) during dpkg or apt-get upgrade or install"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by pd12 on 2011-11-07
Whenever I do dpkg --configure -a or any apt-get upgrade/install, I get an initramfs error:

```

vubunity@vubunity-R580:/etc/xdg/autostart$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up initramfs-tools (0.99ubuntu8) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic-pae
Warning: /proc/partitions references Experimental major device 251.
Fatal: No images have been defined.
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```From other forum threads, I have tried doing /etc/fstab | grep swap and matching the UUID of the resume UUID at /etc/initramfs-tools/config.d
They were the same.
(I have some random hibernate errors, like most of the time it won't work, and in kubuntu only I have no shutdown button from the menus and must use the terminal to shutdown)

This problem happened right after I installed Ubuntu 11.10 (desktop i386) with unity; before I installed gnome, kde, (and before lxde,xfce).
This install is a fresh 11.10 install from USB (I couldn't be bothered upgrading my 10.04LTS and that one doesn't get past kubuntu loading screen after i installed kubuntu-desktop). 
The computer is a samsung laptop R580. 

Here is my /proc/partitions which may hopefully help
```

major minor  #blocks  name

 251        0    1990672 zram0
   8        0  488386584 sda
   8        1   15728640 sda1
   8        2     102400 sda2
   8        3  322591744 sda3
   8        4          1 sda4
   8        5   15591797 sda5
   8        6    9675776 sda6
   8        7   51027968 sda7
   8        8    9036792 sda8
   8        9   64625664 sda9

```
I'm more interested in where this comes from though:
```
 Fatal: No images have been defined. 
```

Almost everything else works fine, I'm using kubuntu now.

---

