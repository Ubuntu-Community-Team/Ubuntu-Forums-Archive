---
title: "How can i set up ubuntu to run with windows?"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by animefreak873 on 2011-11-26
ok i made my bootable usb drive.Now can you explain step by step how to make ubuntu run with windows i dont want to mess my computer up.Also how do i set ubuntu to a certain size like 50gb.
............................................................................................................................
[SIZE=4]WHAT I KNOW
[SIZE=3][SIZE=1]I know that when i boot into it theirs something on my desktop that says install ubuntu but i need your help to make sure i dont mess up.Thanks.

ps.im installing ubuntu 11.04.
[/SIZE][/SIZE][/SIZE]

---

### Post by OrangeCrate on 2011-11-26
> **animefreak873 said:**
> ok i made my bootable usb drive.Now can you **explain step by step how to make ubuntu run with windows** i dont want to mess my computer up.Also how do i set ubuntu to a certain size like 50gb.
............................................................................................................................
[SIZE=4]WHAT I KNOW
[SIZE=3][SIZE=1]I know that when i boot into it theirs something on my desktop that says install ubuntu but i need your help to make sure i dont mess up.Thanks.

ps.im installing **ubuntu 11.04.**
[/SIZE][/SIZE][/SIZE]

A good set of dual booting instructions is here:

> A user may experience problems dual-booting Ubuntu and Windows. In general, a Windows OS should be installed first, because its bootloader is very particular. A default Windows installation usually occupies the entire hard drive, so the main Windows partition needs to be shrunk, creating free space for the Ubuntu partitions...

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Natty#Dual-Booting_Windows_and_Ubuntu)

---

### Post by jerrrys on 2011-11-26
I like pictures :)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by OrangeCrate on 2011-11-26
> **jerrrys said:**
> **I like pictures** :)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Me too!

(But, he's actually asking how to dual boot Natty with Windows.)

:)

---

### Post by jerrrys on 2011-11-26
> **OrangeCrate said:**
> Me too!

(But, he's actually asking how to dual boot Natty with Windows.)

:)

This tutorial goes over the option of installing a traditional dual-boot.

that is the first line

---

### Post by Mark Phelps on 2011-11-26
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by OrangeCrate on 2011-11-26
Jerry,

Honestly, regardless as to how he titles it, I don't see where Asiyu's tutorial covers a true partitioned dual boot. It talks about Wubi and Virtual installs, and how to install Ubuntu into an empty partition on Windows, but, not how to prepare Windows 7 for a dual boot (which is quite important to do, and different from XP's requirements). 

Anyway, I think the OP has plenty of options to think about. Take care.

:)

Edit:

@OP, Mark's comments mirror what is in the link I provided. Take hints from all three of our responses, and you should be fine. Good luck.

---

