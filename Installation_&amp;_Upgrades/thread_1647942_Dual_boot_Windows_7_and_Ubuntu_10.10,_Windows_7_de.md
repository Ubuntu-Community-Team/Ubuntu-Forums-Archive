---
title: "Dual boot Windows 7 and Ubuntu 10.10, Windows 7 default"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by ratman1 on 2010-12-18
Hello

I am trying to dual boot a full installation of Ubuntu (not Wubi), but have Windows 7 load by default.

Normally when I dual boot Ubuntu with windows 7 (windows 7 installed first) Ubuntu will load by default after about 8 seconds. How can i change it so that Windows 7 will load by default?

Also, is it possible to get Ubuntu to show up in the windows boot loader as if it is a Wubi install, although it is a full install?

Thanks in advance,
James

---

### Post by cottfcfan on 2010-12-18
I'd leave as is, and just use startup-manager to load windows as the default os.

---

### Post by noah++ on 2010-12-18
> **ratman1 said:**
> Normally when I dual boot Ubuntu with windows 7 (windows 7 installed first) Ubuntu will load by default after about 8 seconds. How can i change it so that Windows 7 will load by default?
In **/boot/grub/grub.cfg**, *set default="n"* makes the *n+1*st listed operating system in the GRUB menu the default. It is probably set to *0*, and Ubuntu is probably the first OS listed. Perhaps changing that to *1* will give you what you want.

**Edit:** Using startup-manager is the more disciplined and perhaps easier way to do this.
> Also, is it possible to get Ubuntu to show up in the windows boot loader as if it is a Wubi install, although it is a full install?Install [EasyBCD]("http://neosmart.net/dl.php?id=1") in Windows. It's pretty intuitive to add a Linux entry to the Windows BL.

---

### Post by bcbc on 2010-12-18
startup-manager is static so the next time you install a kernel you have to remember to reset it, or it will boot something else - perhaps run memtest.

as noah++ said, easybcd can boot ubuntu from the windows boot manager.

You can also use drs305's [Grub2 Title Tweaks thread]("http://ubuntuforums.org/showthread.php?t=1287602") - or [Meierfra's guide]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu") 

I've used Meirfra's guide - it works well - but recently I just used drs305's tweaks to do what I want (put windows at the top of the list).

---

