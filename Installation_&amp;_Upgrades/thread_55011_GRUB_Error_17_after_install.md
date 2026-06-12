---
title: "GRUB Error 17 after install"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by david_1982 on 2005-08-07
Hi,

I've been trying to install Ubuntu over the last couple of days but can't seem to get around the Error 17 problem at boot. Having searched the forums, I've discovered lots of others seem to be having similar problems, but I can't seem to find a solution.

My system has three hard discs: a SATA drive (my C: drive in Windows XP) and two IDE discs. I want to install Ubuntu on to my IDE slave.

During the installation, I select /dev/hdb as the drive to install to, and it creates /dev/hdb1 as ext3 and /dev/hdb5 as swap. The first couple of times I installed Ubuntu, I chose to install GRUB to the MBR. When I rebooted my PC booted straight into Windows XP, until I re-jigged my boot order in BIOS so the IDE master was first. I then got an Error 17 from GRUB at Stage 1.5.

So I reinstall Ubuntu, again to /dev/hdb, but this time I say to install GRUB to /dev/hdb1 - thinking if I change my boot order so it boots off this drive it will work. Well, I got a step further - I got the GRUB menu. Selecting the Ubuntu option though results in Error 17 still. The full message was:

```
root(hd1,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash

Error 17
```
I also get a similar, but different, error if I select Windows XP from the GRUB menu. This can be solved later though as I can get into XP by changing my boot order.

When GRUB installs to the MBR, does it install to to the first partition of the IDE master? The only thing I haven't tried is to install GRUB to my SATA drive (Windows' drive C:). If I do this and it doesn't work, will it break XP?

Any help would be much appreciated!

---

### Post by david_1982 on 2005-08-07
Well I appear to have fixed the problem by reinstalling Ubuntu with LILO as the bootloader. Not quite the fix I was after but it works nonetheless. It doesn't present me with a menu though. I'll have to work that one out next...

---

