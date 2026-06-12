---
title: "Unistalling Ubuntu"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by vghaisas on 2010-08-23
Dear Ubuntu Users,

Even though there is currently no need or requirement to do so, I want to know how to uninstall Ubuntu. It makes me uncomfortable to know that I have something on my system that I can't undo.

Anyway, I have a dual-boot system running Windows-XP (P.S. I don't have an installation disk for this!) and Ubuntu Lucid Lynx side by side. Suppose I wanted to uninstall Ubuntu and restore Windows to its original condition (remember I dont have the installation CD) what could I do?

Also, I am a complete newbie in partitioning, editing the MBR and rewriting boot files by hand so is there any simple way?

P.S. Is there any way to reinstall Ubuntu so that I have Windows-XP and a fresh new Lucid Lynx Ubuntu running side-by-side again?

---

### Post by clrg on 2010-08-23
If you want to remove Ubuntu, use a live CD. First, delete the Ubuntu partition, and secondly, extend the Faildows partition to fill up the gap.

WARNING: This is a possibly destructive action. Back up all your data before you attempt any of this. 

If you don't want to take the risk of corrupting Faildows' filesystems, reinstall it properly.


If you later want to reinstall Ubuntu, download and burn an installation CD and follow the instructions. There's an option to make a dualboot system.

---

### Post by vghaisas on 2010-08-23
clrg,

Is there any difference between a live CD and a bootable ubuntu USB?

As to backing up all my data, is that really necessary? I have no important files on Ubuntu, all of them are on XP.
And another thing, how do I reinstall XP when I don't have the installation CD?

P.S. Faildows is Windows right? :p

---

### Post by clrg on 2010-08-23
The dfference between a CD and a USB drive is that you're using a USB dive. Ubuntu doesn't care where it gets installed from.

Again, this could break your partitioning and render Faildows unbootable (if M$ would share their NTFS specs, this wouldn't be a problem, btw). 

IF you destroy any data while removing either OS, you are responsible for it. I advise you to make a backup.

---

