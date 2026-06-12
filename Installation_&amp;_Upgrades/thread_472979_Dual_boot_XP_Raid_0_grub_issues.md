---
title: "Dual boot XP Raid 0 grub issues"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by doxymoron on 2007-06-13
Ok here's my setup.  I currently have XP installed on two sata hard drives in raid 0 and I want to setup ubuntu and dual boot.  I've heard of the problems trying to get ubuntu in raid also, so I decided to install it onto an IDE hard drive I have connected.  I go through the install process, choose the IDE drive, everything installs fine, and I reboot.  On reboot I expect to see the grub prompt but I don't, and XP loads automatically.  It appears that grub wasnt installed because ubuntu didnt recognize that I had windows installed at all since it was on raid, is that correct?  So I go into the BIOS and look at my hard drive boot order.  For the heck of it I choose to boot the IDE drive with ubuntu, but when it goes to load it says "Cant load operating system".  I can still boot to windows when I switch back to booting the SATA drives but I need to know if there's a way to get ubuntu to install GRUB or if that's the problem at all.  Any help is appreciated.

Ryan

---

### Post by Pumalite on 2007-06-13
> **doxymoron said:**
> Ok here's my setup.  I currently have XP installed on two sata hard drives in raid 0 and I want to setup ubuntu and dual boot.  I've heard of the problems trying to get ubuntu in raid also, so I decided to install it onto an IDE hard drive I have connected.  I go through the install process, choose the IDE drive, everything installs fine, and I reboot.  On reboot I expect to see the grub prompt but I don't, and XP loads automatically.  It appears that grub wasnt installed because ubuntu didnt recognize that I had windows installed at all since it was on raid, is that correct?  So I go into the BIOS and look at my hard drive boot order.  For the heck of it I choose to boot the IDE drive with ubuntu, but when it goes to load it says "Cant load operating system".  I can still boot to windows when I switch back to booting the SATA drives but I need to know if there's a way to get ubuntu to install GRUB or if that's the problem at all.  Any help is appreciated.

Ryan

You don't mentioned it, but if you installed Feisty ( 7.04 ), Installation gives the opportunity of installing your GRUB exactly where is needed through 'Advanced' tab in step 5 or 4, I don't remember now. Nevertheless, at this point I would advice you to follow this recipe:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you have problems still, then try this:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25)

---

