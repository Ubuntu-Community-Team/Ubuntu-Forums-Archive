---
title: "Issue with initramfs-tools after upgrading to 20.04 LTS"
date: 2021-03-14
forum: Installation &amp; Upgrades
---

### Post by begorrah on 2021-03-14
So after I went on an 16.04 ---> 18.04 ----> 20.04 update journey, a few crucial packages were corrupted/missing. I was able to patch linux-firmware, linux-image-gemeric and linux-generic, but I am still unable to get initramfs-tools to update correctly. 

Here's what I get after running sudo apt-get autoremove:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.136ubuntu6.4) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.136ubuntu6.4) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-67-generic
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.4.0-67-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Something similar happens when I try update or upgrade.

I suspect it's an issue with space in my /boot partition, but I'm unsure of what to delete, or where to go from there. Right now my /boot looks like this:

```
config-5.4.0-66-generic      memtest86+.elf
config-5.4.0-67-generic      memtest86+_multiboot.bin
efi                          System.map-5.4.0-66-generic
grub                         System.map-5.4.0-67-generic
initrd.img-5.4.0-66-generic  vmlinuz
initrd.img-5.4.0-67-generic  vmlinuz-5.4.0-66-generic
lost+found                   vmlinuz-5.4.0-67-generic
memtest86+.bin               vmlinuz.old

```

This is my first time posting here; I'm not the most Linux-literate person, so any help would be appreciated.

[FONT=Verdana]
[/FONT]

---

### Post by Impavidus on 2021-03-15
When a release upgrade goes wrong, it's usually better to try a fresh install instead of fixing it. And I wouldn't even attempt a double release upgrade. A fresh install is much faster and more reliable. Are you sure you want to fix this?

I'm not really familiar with the "Error 24 : Write error : cannot write compressed block". It seems different from "No space left on device". Do you actually have a /boot partition and, if so, how big is it and how full?

---

### Post by k-elf on 2021-03-19
Same issue here, but after an [FONT=courier new]apt update[/FONT] / [FONT=courier new]apt upgrade[/FONT]
Check your free space on /boot by using [FONT=courier new]sudo df | grep boot[/FONT]
and see if you have at least 60000 (kB ) left.

I had to remove some old versions (like 5.4.0-65) with [FONT=courier new]apt purge vmlinuz-5.4.0-65-generic[/FONT]  and after this it worked fine. (Finishing up with [FONT=courier new]rm *5.4.0-65*[/FONT]  and a final [FONT=courier new]apt autoremove[/FONT] to remove some left-overs.)

All well now at my system.

---

