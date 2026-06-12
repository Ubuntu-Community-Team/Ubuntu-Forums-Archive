---
title: "WinXP: hd1 , Ubuntu: hd2 - avoid grub on win hd?"
date: 2004-12-06
forum: Installation &amp; Upgrades
---

### Post by Pointwood on 2004-12-06
I have two 80GB seagate harddrives in my machine. 

Hd1: Windows XP
Hd2: Gentoo currently

Until now, I've simply used the bios to switch between the 2, but I would like to replace Gentoo with Ubuntu and I don't want Ubuntu to touch my Windows install. 

I would like Grub installed on Hd2 with a boot option for Windows so that I don't have to switch in the bios. Since Linux is still kinda new to me, I would prefer to leave my Windows install "unspoiled" :)

I don't expect this to be impossible, I just wonder whether the Ubuntu install is capable of doing this?

---

### Post by hkctr on 2004-12-06
The easiest way to do this is to make the Ununtu disk hda (primary master) and the WinXP disk hdb (slave).  Install Unbuntu with grub on hda. Nothing will change on your XP drive and it won't appear on the grub menu. 

Edit /boot/grub/menu.lst and add the following entry:

title Windows XP
    map (hd1) (hd0)
    map (hd0) (hd1)
    root (hd1,0)
    chainloader +1

This will map the slave drive to be the master and XP will boot normally using the XP boot loader.

---

