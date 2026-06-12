---
title: "uncertain on drapper install on USB hard drive"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by superprad on 2006-09-12
Hi: I'm having a similar issue. I have a 250G external HDD and I formated about 60G for installing ubuntu and some swap. For some reason it was'nt able to create ext3 filesystem..it was erroring. So i created ext2 and linux swap(i assume this should still be ok to install ubuntu).


Device Boot Start End Blocks Id System
/dev/sda1 1 7600 61046968+ 83 Linux
/dev/sda2 7601 7858 2072385 82 Linux swap / Solaris

Now when i reach the partitioning phase in the installer. I choose
- manually edit the partition table.
- then i select /dev/sda and it shows the above and another line with free space(which i'm planning to format later for tons of data i need for storage).
- at this point it came to a next page where

there is a table for pointing the /dev/'s to different mounts

which one do I point to as root partition at this point? i mean ('/') . At the bottom it says it needs atleadt 2G or something.

By default /dev/sda1(60G) is pointing to some /media/usbdrive or something and /dev/sda2 is pointing to 'swap' and '/' is pointed from /dev/hda1(which is the boot partition for my internal.

Should I continue with defaults or what do i have to do now?
oh and I'm running drapper..

how do i continue the install process without formatting the already formatted sda..its slightly confusing when the defaults say '/' is mounted to/dev/hda1.. if i continue will it effect my current grub on my internal.

---

