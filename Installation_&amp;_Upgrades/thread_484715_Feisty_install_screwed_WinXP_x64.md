---
title: "Feisty install screwed WinXP x64"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by ydiaz on 2007-06-26
Hi, first post here,

I've finally managed to install Feisty Fawn correctly, I was trying to make a dual boot with my other WinXP x64 OS but it seems in the process something went wrong, now I get a "Disk error. Press Ctrl+Alt+Del to restart message" when selecting it on Grub. I'm not very concerned since I wanted to move back to WinXP 32bit anyways and my data is safe in another partition. My question is:

How can I install a Win32 SO in the original x64 partition without screwing up Ubuntu? 

Thanks, this forum has been a of great help so far! Cheers!

---

### Post by poltiser on 2007-06-26
Hi
recently I had to change my motherboard and CPU (lightning) and I use Intel D2Coure on Asrock Motherboard. I have 8 partitions on 3 drives - one of them sata. It always had been a chalange to make it dual boot. I solved the problem using Acronis [http://www.acronis.com/homecomputing/products/diskdirector/](http://www.acronis.com/homecomputing/products/diskdirector/) to prepare the partition as well as to boot from different os. It works with WinXP(H) and Ubuntu 6.06.1AMD64 and Ubuntu 7.04AMD64 with no problem. 
It is for some reason easier to install Ubuntu on IDE drive. I am  still learning how to configure this system.
Best regards.
S.

PS. You might be able to save the fallen os - try!

---

### Post by ydiaz on 2007-06-26
Well I tried to save the WinXP installation but no luck, there's not room to work really, the message pops up immediately, leaving me no option to use F8 or anything like that. The screen simply reads:

"Starting up...

A disk error ocurred
Press Ctrl+Alt+Del to restart"

I checked the partition table using gparted and everything seems fine, the partition is there and I can mount it with no problems and is labeled boot.

The Grub lines for the Windows x64 option are:

root (hd0,0)
save default
make active
chainloader +1

I have no idea if this could be the problem... Any suggestions?

---

### Post by Enverex on 2007-06-26
Boot from the XP CD. When it get to the menu select "Repair machine using the Windows recovery console" or something along those lines. Then from that run "fixboot" and "fixmbr". After that's done boot Linux from one of the LiveCDs and reinstall GRUB on the MBR.

---

### Post by ydiaz on 2007-06-26
I finally decided to install WinXP 32bit instead of repairing the old x64 version. I assume the process is basically the same:

1- run the Windows XP CD
2- format the old x64 partition
3- install XP 32bit
4- run ubuntu livecd
5- restore grub in the MBR of the drive

I'll try that and post any trouble, thanks!

---

