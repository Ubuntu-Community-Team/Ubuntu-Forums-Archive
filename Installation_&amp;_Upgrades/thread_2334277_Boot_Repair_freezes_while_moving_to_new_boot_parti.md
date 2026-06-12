---
title: "Boot Repair freezes while moving to new /boot partition"
date: 2016-08-18
forum: Installation &amp; Upgrades
---

### Post by jnightingale3 on 2016-08-18
Hi there,

I'm trying to move grub from my 300GB / partition to a separate /boot partition using Boot Repair*. Pastebin of my initial setup here: [http://paste.ubuntu.com/23066348/](http://paste.ubuntu.com/23066348/) and after failed attempt at the new boot partition here: [http://paste.ubuntu.com/23066426/](http://paste.ubuntu.com/23066426/)

I created a new 1GB partition at the start of the drive using GParted as suggested. This partition is sda3 as it is the most recent one created.

Using boot-repair to create a new /boot partition seems to get halfway there and then hang once it reaches: 'Purge kernels then reinstall last kernel sda1 (ins). This may require several minutes....'  1 hour and 40 minutes so far, way longer than a complete reinstall of grub I did earlier today on sda1. Moving the whole sda1 partition took only about 4 hours.

Searching the web for this error shows other people who had it hanging for over 10 hours. Checking GParted during the process a couple of times, it seems that all three partitions were mounted at some point, and later only sda1 wais...perhaps a sign that it was doing something? (at /mnt/boot-sav/sdaX). But checking last access times of the latest kernel, it' doesn't seem to have been touched. 

Thanks anyone who can help me sort this!

*Backstory: I have a working setup of Lubuntu 16.04 but it has been booting very slowly, and occasionally straight to grub rescue. Boot Info (run from Lubuntu, not from Boot Repair Disk like the one linked above) suggested making a new /boot partition using Boot Repair (as latest boot files are a long way from the start of the disk), which I'm trying to do now.

---

### Post by mook765 on 2016-08-18
When you installed Lubuntu 16.04 you installed the Grub-boot-loader to sda1.
That there is a boot-loader installed on sda might be a leftover from a distribution which has been installed before you installed Lubuntu 16.04.
This boot-loader on sda might not be maintained any more because the distribution managing that is not there any more.
That was causing your boot problems.
If your system still boots you can open a terminal and run these commands:
```
sudo grub-install /dev/sda
sudo update-grub
```
This will install the boot-loader in the MBR off your drive (that is the location where the boot-loader has to be) and then update the boot-loader.
Try out and see if your problem is gone.
The above commands will not harm your system in any way.
There is normally no reason to have a separate partition for /boot.
There is a reason to open a thread in this forum before you do difficult workarounds.
Regards...

---

### Post by oldfred on 2016-08-18
Boot-Repair does not create partitions. I while it does change some entries in fstab, I do not think it would create a new /boot entry in fstab.

The message on far from start of disk is primarily for older BIOS/IDE drive systems or perhaps some older USB drives. Those systems had old BIOS that could only boot from first 137GB of a drive.

My normal suggestion is to then have a smaller / at beginning of drive and use rest of drive as /home or data partition(s). I always use 25GB for / and large data partitions myself.

---

### Post by jnightingale3 on 2016-08-18
Ok thank you both.

I've run mook's suggestion and while it still boots fine the speed is no better. There is a message (white text on black, before the Lubuntu loading screen) saying "/sda1 clean [some big number] files, [another big number] blocks."

Seeing as it's usable (and the speed is fine once it's booted) I think I'll leave it as-is until I have enough time for a fresh install, at which point I'll go for oldfred's / and /home suggestion. Need more time to read up on fstab and so on first!

Cheers!

---

