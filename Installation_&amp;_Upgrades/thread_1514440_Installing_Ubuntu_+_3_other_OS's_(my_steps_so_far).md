---
title: "Installing Ubuntu + 3 other OS's (my steps so far)"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by polar8 on 2010-06-21
Hi,

I'm trying to install Ubuntu, Windows 7, Meego, and Android x86 for a project. Here is what I have done so far:

Partition the drive into 4 primary partitions of equal size (10gb each).

Install Windows7, Android, and Meego onto separate partitions, in that order.

Then, install Ubuntu, hoping that GRUB automatically detects the other OS's and creates entries for them.

Unfortunately, the only entries in GRUB are for Ubuntu and Windows 7. How do I get to the other 2 OS's (Android and Meego) to show up?

I appreciate the help.

---

### Post by wilee-nilee on 2010-06-21
> **polar8 said:**
> Hi,

I'm trying to install Ubuntu, Windows 7, Meego, and Android x86 for a project. Here is what I have done so far:

Partition the drive into 4 primary partitions of equal size (10gb each).

Install Windows7, Android, and Meego onto separate partitions, in that order.

Then, install Ubuntu, hoping that GRUB automatically detects the other OS's and creates entries for them.

Unfortunately, the only entries in GRUB are for Ubuntu and Windows 7. How do I get to the other 2 OS's (Android and Meego) to show up?

I appreciate the help.

Looks like a comp tech college course final, if this is the case you have to do your own homework if this isn't the case then make sure this is known.

---

### Post by polar8 on 2010-06-21
> **wilee-nilee said:**
> Looks like a comp tech college course final, if this is the case you have to do your own homework if this isn't the case then make sure this is known.
 
Nope, this isn't for a class. My major is mechanical engineering. I just thought it would be interesting to have those four OS's on my laptop. I would like W7 for for CAD programs, Meego for just general messing around on the internet, Ubuntu to run Linux programs, and Android becuse I'd like to get into the Android x86 project.
 
Based on my research, I need find out what the partition names are for Meego and Android, which are the ones that aren't showing up. Then, I need to modify the GRUB file to add them as entries. This is where I'm having problems though.
 
I've been reading this article, and I'll continue to try to make it work. I'll report back here if it works for reference.
 
 
EDIT: Oops, here's the link to that article: [http://linuxers.org/howto/how-configure-grub2-ubuntu-910](http://linuxers.org/howto/how-configure-grub2-ubuntu-910)

---

### Post by kansasnoob on 2010-06-21
I'll see what I can cook up if you'll post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by polar8 on 2010-06-22
After reading some more about partitioning and GRUB, I decided to start from scratch.

Here is my partition scheme: (Using jaunty because it uses GRUB instead of GRUB2, and there are more tutorials for the former.)

sda1: Ubuntu 9.04
sda2: Windows
sda3: Extended
sda5: Swap
sda6: Android
sda7: Meego

My order of installation will be Windows>Android>Meego>Ubuntu. 

Should installing Ubuntu last allow GRUB to auto-detect all 3 other OS's? If not, what steps should I take to make sure it adds them?

Thanks for all the help.

---

