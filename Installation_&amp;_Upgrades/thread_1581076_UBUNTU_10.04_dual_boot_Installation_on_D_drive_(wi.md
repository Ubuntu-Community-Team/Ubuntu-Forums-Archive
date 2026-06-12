---
title: "UBUNTU 10.04 dual boot Installation on D drive (without windows installer CD)"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by instant_k on 2010-09-24
Hi
I am a **windows xp** user currently.
I have 4 partitions of my hard drive..of which only D:/ is having the max free space amongst others. ie **25 GB free of total 39 GB.**

How to install ubuntu as a dual boot without --i mean if i install it on D:/ do i **need to delete all files** (that include useful windows program files) on D:/

Isnt it possible to still install ubuntu on D: **without deleting existing files **and as a dual boot--without using wubi.
**OR**
Is there **any way to move those windows files simply on E or F** and still not harming the programs that they use-- as I **cant afford to create a new partition..**



Please note that I **dont have windows XP installer CD**..so I dont want any harm to windows during ubuntu installation.
I used ubuntu 9.10 previously (64 bit version) with wubi..but was dissatisfied as 64 bit was not compatible with most programs.Although **I uninstalled wubi** from "ADD OR REMOVE PROGRAMS" but **I can still see the GRUB** on startup with **UBUNTU** option (although ubuntu does not open since i deleted it).
Will this grub pose any prob in fresh install.

sorry for being so descriptive..but I have so many doubts on ubuntu....

BTW MY **CONFIG** IS:
**Intel Core 2 Duo CPU**
e4600 @2.40GHz
2.40GHz, **0.99 GB RAM**

---

### Post by pricetech on 2010-09-24
I'm guessing that one of your partitions is a recovery partition, which you wouldn't want to lose since you don't have install media.

If your programs are installed on "D" then you must have a very small C drive, which makes me wonder how the silly thing was set up in the first place.

Does your computer include a recovery disk maker of some kind ??  If so, that would be the logical first step.

Any idea why you  have 4 partitions to begin with ??

---

### Post by instant_k on 2010-09-24
See  these partitions were not set up by me.. They were as it is when I bought the PC.
My C: has 26 GB capacity but is mostly filled because of a large no. of software..so i started installing them on D: , E: and F which had 39, 39 and 46GB capacity respectively.
I dont have recovery disc maker and my E and F drives contain very important files which I dont want to harm in any way...

Lets suppose I Free entire D:... will that be enough to install Ubuntu - as dual boot--**without posing any threat to windows or existing files?** ...Or should I install with **wubi?**--the safest way. The only reason I m against wubi is that BSODs on windows imply no Ubuntu as well

---

### Post by ajgreeny on 2010-09-24
Can you please run the ubuntu live CD and in terminal run the command ```
sudo fdisk -l
```and copy the output back here.

Also it will help if you run **gparted** from the **System ->Administration** menu, and when it has opened, hit **Alt+Print screen** buttons and send the screenshot as an attachment.

All this will give a much better indication of your current partition setup, and the best way forward for you.

---

### Post by pricetech on 2010-09-24
> **instant_k said:**
> without posing any threat to windows or existing files?

Back everything up.  No matter what you do or how you do it, you risk losing files.

Here's what I'd do:
Move the data to an external drive so you can extend your XP partition to about half the drive, leaving the other half for Ubuntu.

Restore the data to the XP drive, but keep it synchronized with the external drive as a regular backup.

You can access XP's NTFS partition with Ubuntu, so your files will be accessible in both OSes.  XP however can't access your Ubuntu drive.

That gives you a dual boot with backed up data.  There's no way around being stuck if XP gets corrupted though since you don't have media.

---

