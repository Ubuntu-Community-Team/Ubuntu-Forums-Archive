---
title: "DualBoot With Win7 Separate Hard Drive"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by TechXero on 2010-09-29
Hey There :

I need urgent help ! I have Windows 7 x64 on a RAID0 Setup and have a separate 120GB Hard Drive and want to DualBoot with Ubuntu ! 

How do I go by doing that seeing that LiveCD is not detecting Windows 7 Loader ? Please Help ! 

Twitpic : [http://twitpic.com/2t3myg](http://twitpic.com/2t3myg)

It's Urgent !!!

Thanks !

---

### Post by ronparent on 2010-09-29
Start by using the disk management utility in windows 7 to create unallocated space on your raid to install to. Then boot on the Ubuntu 10.04 live cd. This is always a good idea to find out if your system will boot without special boot parameters.

The start gparted (the Ubuntu partitioner). If you can't see the raid partitions, close it and install kpartx (from the software center, sysnaptics package manager or terminal - whichever you are more comfortable with). Then you can start gparted again to verify the raids are seen and use gparted to create an extended partition to install to (the extended partition will forestall most partitioning problems created by trying to create more than four primary partitions). If your windows setup already takes up four or more primary partitions post that here so we can find some solutions. Working from the same session you installed kpartx from, start the installer from the desktop icon. You will need to select the manual partitioning option in step 4 of 7 of the install. This will bring you to step 5 of 8. Now you need to create two partitions in the extended partition - one of probably 10-15Gb to install Ubuntu to, and a swap of at least the size of your RAM. The target for the install can be formated to either ext4, ext3 or ext2. Make sure you designate the '/' as the mount point. In step 8 of 9 select the advanced box to choose location to place the grub 2 boot loader. It is the overall raid drive, probably the first raid choice given in the pop up list. Be forewarned, even if you do it right it may not work and you will be warned of a fatal installation error at the end of the install after all you files have benn written and the system configured. This error is not fatal and can be fixed. Post here if you run into it and I can tell you how to fixit from a live cd.

This is more involved than it should be, but it is doable and we can help if you run into problems. Good luck.

---

### Post by TechXero on 2010-09-29
All done thanks works like a charm Solved !!!!!

---

### Post by ronparent on 2010-09-29
Glad to hear it. Have fun.

---

