---
title: "Kubuntu wont boot after fresh install"
date: 2014-10-07
forum: Installation &amp; Upgrades
---

### Post by Shawn_Hawkins on 2014-10-07
I was running ubuntu 14.04 and wanted to try some different flavors so I tried xubuntu and kubuntu. I liked the interface and just about everything else about kubuntu so I clicked on install. I chose to let it wipe the system and it installed without error. 
I rebooted as per the instructions and when it rebooted I got an error. There is a lot of text and I'm on my phone. 
I took a photo of my screen, how can I upload it?
The error is from busybox, the cursor is flashing at (initramfs) — 
"could not configure common clock
Boot arms (cat/proc/cmdline)
Check root delay
Check root
Missing modules (cat/proc/modules ; is /dev

/Dev/disk/by-uuid/xxxxxxxxxxxxxxxxxxx does not exist
Dropping to a shell 

(initramfs)-

Is there a way to fix this?

---

### Post by Vladlenin5000 on 2014-10-07
The error message has a weird thing (I'll save comments for later), indeed.
First of all, where exactly - what PC - have you installed it. Please post the specs and inform which one have you installed, 32-bit or 64-bit?

---

### Post by Shawn_Hawkins on 2014-10-07
It's a 64 bit pc. Toshiba satellite 
The version is 14.04

2 x amd athlon II P320 Dual-Core Processor
2.7 GiB of Ram

The software is:
KDELibs Version: 4.13.2
QT Version: 4.8.6
Kernel Version: 3.13.0-32-generic
OS Type: 64-bit

---

### Post by Vladlenin5000 on 2014-10-07
There are many "Toshiba Satellite" models/configs out there ;) but I suspect yours is new enough to have UEFI instead of the old BIOS. If so, dual-booting or not, there are many more to consider then before: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Shawn_Hawkins on 2014-10-07
I have no idea what efi or whatever is.

This is a fresh install, no dual boot, and a bios.

So instead of sending me somewhere else, how about helping me with the problem based of the errors I got.

---

### Post by yancek on 2014-10-07
> /Dev/disk/by-uuid/xxxxxxxxxxxxxxxxxxx does not exist
Dropping to a shell 

You installed Kubuntu over Ubuntu so Kubuntu is your only operating system, is that correct?
Do you get this on boot?  The message above indicates it is looking or a disk/partition which doesn't exist, it may have changed.  Did you install the Grub bootloader with Kubuntu to the mbr, that would be the default.  It would install to the mbr of the first drive, do you have only one drive? 

Use one of the Live CDs, Kubuntu or other and go to the site below and download and run the bootinfoscript and post the output, a results.txt file, here.   Instructions are in a link in the Description box.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Vladlenin5000 on 2014-10-07
> **Shawn_Hawkins said:**
> So instead of sending me somewhere else, how about helping me with the problem based of the errors I got.

I would and I was about to but I don't feel like it anymore... Apparently you're under the impression that somehow I'm under that obligation and in order to prove you wrong this is a good-bye... And good luck.

---

### Post by Shawn_Hawkins on 2014-10-07
My brother used to pull that guilt thing on me. I you couldn't help you should have just said so.

I installed the latest stable version through unet bootin.

---

### Post by ibjsb4 on 2014-10-07
A poor attitude will get you nowhere in this forum.

---

### Post by QIII on 2014-10-07
> **Shawn_Hawkins said:**
> I have no idea what efi or whatever is.

This is a fresh install, no dual boot, and a bios.

So instead of sending me somewhere else, how about helping me with the problem based of the errors I got.

Providing a link with what may explain/help you with your problem is not "sending you somewhere else".  There is no point in anyone here recreating the wheel.

Simply saying it was not a dual boot and not UEFI would have sufficed.  By way of advice: don't make demands on volunteers about the form or manner of their volunteered help.

If you have a problem with someone else's response, please use the "Report Post" button and the Staff will deal with it appropriately.

---

### Post by Shawn_Hawkins on 2014-10-08
The link provided did not work. I am on a bios, not the other thing. 
I tried using the boot-repair utility on the default recomended setting and that didn't work. Then I tried the advanced options and had it rewrite the grub and it didn't do it either.
I'm sorry If I was rude but Im getting more and more frustrated by the minute.
Does anyone have any suggestions?

---

