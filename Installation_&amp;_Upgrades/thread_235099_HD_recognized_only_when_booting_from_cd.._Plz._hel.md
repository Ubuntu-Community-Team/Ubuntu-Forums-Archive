---
title: "HD recognized only when booting from cd.. Plz. help"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by Brainiacen on 2006-08-12
Hi everybody

I've got big trouble installing ubuntu on my pc. First I bootet from the ubuntu live-cd and installed the system using the install utility. This went fine until I have restarted my pc. Booting didn't work, with error msg. "no disk to boot from" or sth. like that. Obviosly Grub wasn't installed in the MBR of the boot drive. 

It is very strange though, that if I boot from live-cd, all hard disks are recognized correctly, they are 4 SATA disks in total. Also if I look at sdc disk (I don't know why it is sdc in linux, because actually it is connected to the 1. SATA interface and selected for boot in BIOS) I see the three partitions that were created during install, with /dev/sdc1 having a star next to it, obviously boot partition (sdc1). 

Using live-cd I can look at my partitions using "fdisk -l" no problem. But if I mount the installed system: 

mount /dev/sdc1 /mnt/ubuntu
chroot /mnt/ubuntu
sudo su

"fdisk -l" doesn't show any partitions!!!!

I also tried 
grub
>root (hd2,0)

ERROR !!!!

this doesn't work when in chroot. 

So, ok, I then went to check /boot/grub/menu.lst while still in chroot and there everything looked fine with root=/dev/sdc1 and so on..  

Then exited chroot and here, from live-cd system I force-installed GRUB into sdc MBR, and from here the GRUB showed at boot BUT:
Now, when booting, even though GRUB shows some signs of existanse, showing me the menu, it fails to boot the system! 

The error is: Filesystem type unknown, partition type 0xf kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/sdc1 ro quiet splash

Error 17: Cannot mount selected partition
press any key to continue...

ENTER-> goes back to menu!! 

I find it really strange that the live-cd system recognizes my hard disks and the installed system fails to do so, or am I mistaken? I mean, if fdisk -l in chroot shows nothing, it's quite worrying, isn't it? 

Could somebody help me here plz.. 
Thank you

P.S. M$ will hate you for this, one less Vista user.. Because I am going Linux!! :mrgreen:

---

### Post by meng on 2006-08-12
Should it be (sd2,0) rather than (hd2,0) in the menu.lst?

---

### Post by Brainiacen on 2006-08-12
Well, I think not, becase /dev/sdc1 is 3rd hd, 1st partition, isn't it? Or am I wrong?

---

### Post by meng on 2006-08-12
sdc1 is the 3rd (c) sd (s), 1st (1) partition.

---

### Post by Brainiacen on 2006-08-12
I found somebody having the same problem, it seems to be related to the A8N-SLI Mainboard!! And only if installing on a single SATA drive.

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=353305](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=353305)

I am actually mixed up now, it seems the system would only install and boot from sda1, but not from sdc1.. Now how do I make sdc to sda? should I hysically change cables on the board? sdc is plugged to SATA port 1.. 

strange thing happening..

---

