---
title: "Need help installing Ubuntu, First Time. :["
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by johniv on 2008-07-01
Hey everyone! i would love to use Ubuntu but i can't manage to come past the problem i have. When i use a boot cd to try and install ubuntu, the loader bar shows up.. stays a while.. then moves to a screen full of errors.

My system is:
OS: Vista
CPU: intel Q6600
MB: ABIT IP 35 PRO
GFX: GeoForce 8800 GTS 512
CD: SATA
HD: SATA (primary) IDE (secondary)
INSTALL: ubuntu-8.04-desktop-i386

I can run Ubuntu fine within WMware or similar programs.
There is a copy of windows on the same hard drive it is trying to boot into.
Here are the errors:
[[IMG]http://img413.imageshack.us/img413/3703/img0240oo3.th.jpg[/IMG]](http://img413.imageshack.us/my.php?image=img0240oo3.jpg)

Thank you!
John

UPDATE: Scroll down for my solution
For the sake of helping anyone else with my problem:
keywords: DRDY

---

### Post by Pumalite on 2008-07-01
I'd burn a new >CD after md5sum, at 4x or less. Beyond that; you might need some boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
Try the most common ones first:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off all_generic_ide vga=0x317 vga=788 vga=789 vga=791
To be tried alone or in different combinations until you hit the right one.

---

### Post by meindian523 on 2008-07-01
Looks like a problem with Ubuntu recognizing your SATA drive.

---

### Post by theravenproject on 2008-07-01
These guys are right-listen to Pumalite friend and good luck with your Install; and No matter what you do-ALWAYS back up anything valuable on your computer before attempting to install!

---

### Post by meindian523 on 2008-07-01
theravenproject
Please use the Return aka Enter key to enhance readability of your post.

---

### Post by avtolle on 2008-07-01
@johniv, if the iso checks out, and the cd checks out after burning, I'd first try all_generic_ide boot parameter from the list Pumalite provided. That has seemingly been of help to others with similar problems.

---

### Post by meindian523 on 2008-07-01
That was the parameter I was searching for!!Thanks avtolle.

---

### Post by johniv on 2008-07-02
Hey everyone! Thanks very much.

CD was fine, hardware was fine. BIOS had SATA set up to run in IDE mode, so it was looking for IDE functionality (??) from a sata drive. I could set it to raid, but then vista wouldnt boot. Since i have two hard drives, though, i just installed it on the IDE hard drive (with the SATA drive unplugged). Works great!

Now i'm trying to get dual boot working, and i have a feeling i should make a new thread.

Thanks VERY much for your time.
John

---

### Post by madjr on 2008-07-02
> **johniv said:**
> Hey everyone! Thanks very much.

CD was fine, hardware was fine. BIOS had SATA set up to run in IDE mode, so it was looking for IDE functionality (??) from a sata drive. I could set it to raid, but then vista wouldnt boot. Since i have two hard drives, though, i just installed it on the IDE hard drive (with the SATA drive unplugged). Works great!

Now i'm trying to get dual boot working, and i have a feeling i should make a new thread.

Thanks VERY much for your time.
John

good you got it sorted.

you could always insert the CD within windows and the **Wubi** installer will pop-up and get ubuntu installed fast.

Wubi is the novice mode (no need to partition, etc.). 

else if you don't mind the traditional mode (live-CD, partitioning, etc), go for it.


what is the problem you have now with dual-boot not working ?

---

### Post by meindian523 on 2008-07-02
The problem is that the SATA drive was unplugged when you installed.Is the SATA HDD the first disk?I think you should be able to get a dual boot by installing Grub to the MBR of the first HDD,whether it's IDE/SATA.

---

### Post by johniv on 2008-07-02
Thank you for your support! 
Is that the problem? it seems logical. if you mean which is first in the boot order: then, right now, the sata is. I explain the situation better in this thread, so if you'll take a look i appreciate it. Installing Grub into the MBR of the sata sounds promicing though!
[http://ubuntuforums.org/showthread.php?t=847025](http://ubuntuforums.org/showthread.php?t=847025)
John

---

### Post by goforlinux on 2008-07-02
Would have went grub on that. Did a dual boot made another partition for linux?????

---

