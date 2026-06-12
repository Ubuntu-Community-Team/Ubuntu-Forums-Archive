---
title: "considering triple boot"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by mikeymikec on 2008-03-30
I'm thinking of going with Ubuntu on my main desktop's primary OS, however access to Vista would be handy (as I am a computer fixer by trade), but it hasn't served properly as my primary OS, and Windows 2000 would be handy as a backup and gaming OS.

Would the latest proper release of Ubuntu handle Vista in its boot management?

Single disk, 400GB.  I'll probably go something like 10GB Linux, 20GB Vista, 4GB Win2k, rest of disk data FAT32.

Suggestions?  My experience is mostly Windows-based but I've been running Ubuntu and XP on my laptop and I have some experience with UNIX-based operating systems, and I would regard myself as an experienced newbie in Ubuntu.

---

### Post by zvacet on 2008-03-30
[Here](http://ubuntuforums.org/showthread.php?t=327781&highlight=triple+boot)

---

### Post by housam on 2008-03-30
> **mikeymikec said:**
> 

Single disk, 400GB.  I'll probably go something like 10GB Linux, 20GB Vista, 4GB Win2k, rest of disk data FAT32.


If you'll gonna install Gutsy, ntfs format for data partition will be better and will be seen from both OS. ( Don't forget the swap partition, 1-2 GB is Ok )

---

### Post by mikeymikec on 2008-03-31
But Ubuntu can't write to NTFS partitions, correct?

Is 10GB enough for the latest release of Ubuntu with a good bit of slack?

---

### Post by forestpixie on 2008-03-31
Yes it can - there is an ntfs tool - you can get read/write with ntfs-config

---

### Post by stefangr1 on 2008-03-31
If you have a dual core system and enough memory, have you considered using vmware-server? It decreases prestations with only 7% I believe (while startup is much,much faster), and especially for simulation of problems it's very handy, since a broken machine can be replaced with a new one from a backup in just minutes. Also, if a question occurs you can start a virtual machine without first having to close your work and reboot.

---

### Post by housam on 2008-03-31
> **mikeymikec said:**
> 

Is 10GB enough for the latest release of Ubuntu with a good bit of slack?

yes it is ok

---

### Post by housam on 2008-03-31
this driver will give you full access to ext3 partitions from windows side.:[[COLOR="Red"]_http://www.fs-driver.org/_[/COLOR]]("http://www.fs-driver.org/")

the new releases of ubuntu already have the [[COLOR="Red"]_driver_[/COLOR]]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") for accessing ntfs partitions

---

### Post by phenest on 2008-03-31
I'm having problems with getting a triple boot to work. I have Ubuntu already installed and have 20GB spare unpartitioned space for XP and Vista. But XP will not install.

Current partitions:
Extended:
[INDENT]Linux Swap (Logical)[/INDENT]
[INDENT]Ubuntu Root (Logical)[/INDENT]
Primary: Ubuntu Home
20GB unpartitioned

I used the XP setup to create a 10GB partition for itself and installed. But then the hard drive complains there is something wrong with the partition table and will not boot from it.

---

### Post by housam on 2008-03-31
use [[COLOR="Red"]_this guide _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=724817")for multi-boot from **bodhi.zazen**

---

### Post by phenest on 2008-04-05
> **housam said:**
> use [[COLOR="Red"]_this guide _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=724817")for multi-boot from **bodhi.zazen**

There is nothing in that thread specific to my problem.

But I have solved it.

The 20GB partition left is big enough for XP and Vista. I first used the XP CD and installed to a 10GB partition. I then used the Vista DVD to install to the remaining 10GB. Vista finds XP and adds it to its boot manager. I then reinstall grub and manually add an entry pointing to the XP partition which brings up the Vista boot loader. So when the computer is booted, I get the choice of Ubuntu or Windows. If I choose Windows, I then get the choice of XP or Vista.

But XP MUST be on a primary partition. I think Vista works on a logical partition too.

---

