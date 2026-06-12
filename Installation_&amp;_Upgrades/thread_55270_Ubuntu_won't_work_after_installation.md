---
title: "Ubuntu won't work after installation"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by ItIsMe on 2005-08-08
I've installed Ubuntu 5 times now and each time it installs perfectely but when it restarts the computer after the installations is finished it says

Missing Operating System

Does anyone know how to fix it?

---

### Post by tonym on 2005-08-08
It sounds like the installation of the grub bootloader didn't work properly.  What is your disk configuration?  Where did you tell the installer to install grub?

---

### Post by ItIsMe on 2005-08-09
[QUOTE=tonym]It sounds like the installation of the grub bootloader didn't work properly.  What is your disk configuration?  Where did you tell the installer to install grub?[/QUOTE]

I currently have three partitions. One with Windows XP on it, another that works on XP but just has whatever I want on it and the third partition is Ubuntu. I installed the GRUB onto the same partition with Ubuntu but it keeps coming up with the same message.

---

### Post by tonym on 2005-08-09
Identify which partition is active.  You can do this by running fdisk from Windows or by booting the Ubuntu install disk,   use Alt/F2 to get another session and run cfdisk.

If your Ubuntu partition is not the active disk then make it so and reboot.

If it is then it sounds as if grub wasn't installed properly.

I'm not at a Linux machine so can't check this but you need to boot up via grub but interupt the process and get the grub command prompt.  I think you can do this with the install disk.  Once you have got the command prompt and assuming Ubuntu is on /dev/hda3,  enter:

root (hd0,2)
setup (hd0,2)
reboot

Then see what happens.

---

### Post by ItIsMe on 2005-08-10
[QUOTE=tonym]Identify which partition is active.  You can do this by running fdisk from Windows or by booting the Ubuntu install disk,   use Alt/F2 to get another session and run cfdisk.

If your Ubuntu partition is not the active disk then make it so and reboot.

If it is then it sounds as if grub wasn't installed properly.

I'm not at a Linux machine so can't check this but you need to boot up via grub but interupt the process and get the grub command prompt.  I think you can do this with the install disk.  Once you have got the command prompt and assuming Ubuntu is on /dev/hda3,  enter:

root (hd0,2)
setup (hd0,2)
reboot

Then see what happens.[/QUOTE]

The Ubuntu partition was set to active and when GRUB installed it didn't have any error messages. How do I boot up using GRUB? It comes up with the Missing Operating System message before GRUB starts.

---

### Post by RyderDarkcrow on 2005-08-10
sounds very similar to the problem i am having right now too... 

after the first part of the installation (the reboot after GRUB is installed), it just reboots into windows xp like it normally does. 

I will try your advice and see if it works for me too.... helping two people at once. I hope you will feel all warm and fuzzy :)

---

### Post by RyderDarkcrow on 2005-08-10
nah still no good... i wasnt able to access a terminal when i pressed alt-f2 after the install cd loaded up

i dont know whether i should open up a new thread with a more detailed account of my problem.. or just keep an eye on this one

---

### Post by xodeus on 2005-08-10
I'm used to install GRUB to te MBR and never get those problems. If you want your NT Bootloader back if you don't want linux anymore then restore it from your XP installation CD.

---

### Post by CrakrJaky on 2005-08-14
I am having this same problem....I don't want to give up here...any new advice?

---

### Post by CrakrJaky on 2005-08-14
NM...problem solved

---

### Post by recce101 on 2005-08-14
[QUOTE=CrakrJaky]NM...problem solved[/QUOTE]
What did you do that fixed it?

---

### Post by dStrom on 2005-08-17
CarJacky, can you post what you used to resolve the issue?

---

