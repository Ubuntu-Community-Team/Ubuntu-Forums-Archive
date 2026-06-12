---
title: "[Hardy] Grub error 21 problem"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by IchiNL on 2008-04-28
Hello,

I've just installed Hardy with Wubi, which is brilliant btw, but after installation Grub gives me Error 21. I did some research and found out what the problem is: I have 3 hard drives in my machine: two Raptors in Raid 0 and a IDE drive for storage. I installed Hardy on a partition of the IDE drive. Apparently Grub can't handle a Windows install on a SATA device and a Linux install on a IDE device at the same time.
Does anyone have a solution for this? The Windows boot menu lets me choose Windows XP and Ubuntu, so why even have Grub give me an option to choose the same? Is it possible to let Grub just boot Ubuntu and not bother with listing a menu?

Thanks for answering

---

### Post by pilot550 on 2008-07-13
I had almost the same problem except my 3rd drive was SATA instead of IDE. I found your post while trying to solve the same error. I just got it working so I'll share what I did in case it might work for you. I don't have a great knowledge of Linux like most of the people on here so there are probably better ways to do this, I just figured it out one step at a time so here goes.

I had my 2 Raptors in a RAID 0 with Vista x64 installed I had my third drive, a 750GB SATA WD drive, divided into 3 partitions. The first partition is NTFS, the second is a 22GB ext3 and the third is a 1GB swap. I installed Hardy Heron there. When I rebooted I got the Grub 21 error problem. Before I installed Ubuntu I made an image of my Vista install with Acronis True Image.

I didn't know how to get Grub off my RAID so I destroyed and recreated it. I then loaded my Vista image and booted into Windows. I found a free program called EasyBCD. I loaded that and clicked on "Add/Remove Entries". I clicked the Linux tab. Type: Grub, Drive: I selected my Linux partition. Make a note of the Drive number and partition number for later. I selected the box the says "GRUB isn't installed to the boot sector". Then click on "Add entry" and save it.

Now I rebooted and selected Linux from the boot loader. Then I get the "Error 26: Selected disk does not exist". Hit enter to continue. The top line where it says "Ubuntu 8.04.1, kernel...." press E to edit it. Now my top line says "root (hd2,1)". Back in EasyBCD it said my ext3 drive was 1 and my partition was 1. Press E to edit the top line. I changed it to read "root (hd1,1)". then hit enter. Press B to boot. Then it boots to Linux but it didn't permanently change it so I had to do that every time. So when you are in Linux open a terminal and type: gksudo gedit /boot/grub/menu.lst
I Scrolled all the way down to the bottom and changed all the hd2,1 entries to hd1,1. I saved it and that was it. Now everything works just the way I want.

It's a lot of steps because I really don't know what the heck I'm doing. That's how I got it to work. I hope it helps.

---

