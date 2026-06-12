---
title: "ubuntu fast, ubuntu slow"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by coracle on 2012-06-09
hello
I have an Ubuntu 12.04 installation in a 16Gb pendrive that runs wonderfully fast
I tried to make an installation in a 32Gb pendrive but it failed several times so I deleted everything in the main partition and copied (rsync avH ...) everything from the installation that runs ok.
I edited /etc/fstab and /boot/grub/grub.cfg to update UUID
The new installation runs but so slowly that it is not worth using it
Any sugestion to fix this would be very apreciated

---

### Post by Basher101 on 2012-06-09
> **coracle said:**
> hello
I have an Ubuntu 12.04 installation in a 16Gb pendrive that runs wonderfully fast
I tried to make an installation in a 32Gb pendrive but it failed several times so I deleted everything in the main partition and copied (rsync avH ...) everything from the installation that runs ok.
I edited /etc/fstab and /boot/grub/grub.cfg to update UUID
The new installation runs but so slowly that it is not worth using it
Any sugestion to fix this would be very apreciated

just do a clean install instead of forcing it on another device? I had some bad experiences when using backup programs to "install" Ubuntu on another drive (be it HDD, USB, SSD)

---

### Post by coracle on 2012-06-10
thank you, Basher101, but
you mean ubuntu doesn't support restoring a backup in a different drive? can't believe that
i only want to extend the space available, without going again through the installation of web server, ddbb, php, cms, ...
not asking too much, hope somebody could advise me

---

### Post by sudodus on 2012-06-10
I suggest that you clone the nice-working pendrive to the other one using dd.

Boot from another drive, for example an internal HDD. Run ```
sudo fdisk -lu
``` to find the drive designations. And then run dd
```
sudo dd if=/dev/sdx of=/dev/sdy bs=4096
``` where you replace x and y with the appropriate drive letters, for example b and c, if your nice-working pendrive is /dev/sdb and the new one is  /dev/sdc. Recheck so that you get it right, otherwise you might destroy your nice-working pendrive or a hard drive!!!

After cloning you can use gparted (booted from another drive, for example also in this case from your internal HDD) and edit the partition table, to make the unallocated part of the drive useful (grow an existing partition or make and format a new one).

If you still get slow action, it might be because the new pen-drive is slower than the old one. I have good results using a USB 3 pendrive booting from a USB 2.0 port.

---

