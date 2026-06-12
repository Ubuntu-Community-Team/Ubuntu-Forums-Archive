---
title: "BSOD after choosing Ubuntu on Dual Boot system"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by Gr1mac3 on 2006-09-12
I've been searching other posts for days now to try and figure this thing out but nothing seems to work so I figured I'd put this issue out there in the hopes that someone can help:

System:
P4 2.8 GHz
1GB RAM
ATI X800 XT
Maxtor SATA 500GB HD

I already have WinXP Pro SP2 installed and wanted to make a dual-boot system so I can see for myself what all the buzz is about Ubuntu (and perhaps even switch over if I like it enough).

Got the 6.0.6 iso burned it, checked the cd and installed to include making the partitions on the SATA HD with the Ubuntu partioner.  At no time did the installer ask if I wanted to install GRUB - or was that the app that let me make my linux partition?

Rebooted with System Rescue CD and did the following to get the UBUNTU.BIN file.

mkdir /mnt/osshare 
mount -t msdos /dev/sda4 /mnt/osshare 
dd if=/dev/sda2 of=/mnt/osshare/ubuntu.bin bs=512 count=1 

Booted into WinXP, no problem.  Copied the UBUNTU.BIN to C:\ and added

C:\UBUNTU.BIN="Ubuntu Linux" 

so that I would get the dual boot option menu on next boot.

Rebooted, got the option menu and selected Ubuntu

_Black Screen with a blinking cursor in upper left hand corner._  

I'm not even getting a command line so I can't do an apt-get or send any commands or anything.  Have been using the Live CD to boot system and then mount the linux partition to make any changes (e.g. #'ing lines in xorg.conf to see if it would make a difference).  Problem is this won't let me install any drivers on the linux partition.  Help!!

---

### Post by Stone123 on 2006-09-12
You should use grub as boot loader 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
if not that:

I dont know much about windows part there but here is my config for bootfloppy:
[http://www.geexbox.org/forum/viewtopic.php?t=5108&highlight=loadlin](http://www.geexbox.org/forum/viewtopic.php?t=5108&highlight=loadlin)

---

### Post by Draxxon on 2006-09-20
I'm having the same sort of problem... my Ubuntu installation isn't offering at all to install GRUB.  Of course, it's possible that it's doing that automatically, but I don't know where.

I have Windows XPSP2 on my 200gig SATA drive and I'm installing Ubuntu on my other drive.  Back in the day I installed Suse 7, it offered to install GRUB to the MBR, and I did so.  Promptly after, my MBR was corrupted.  So I'm a little hesitant to install GRUB or LiLo there.  

I haven't tried to use the system rescue disk to boot into Ubuntu, but if my situation is the same as OP, maybe there isn't a point.  Is there any way to get some sort of prompt during Ubuntu install for GRUB?

---

