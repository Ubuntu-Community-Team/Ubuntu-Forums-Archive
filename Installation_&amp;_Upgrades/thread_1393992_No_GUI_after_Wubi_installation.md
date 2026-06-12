---
title: "No GUI after Wubi installation"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by SQ_Minion on 2010-01-30
I'm trying to dual-boot Windows 7 (64-bit, Home Premium) with Ubuntu 9.10. My hard drive was being stubborn, so I decided to just install through Wubi, off a Live CD. The installation seemed to run just fine, no abnormalities, but when I try to boot Ubuntu at startup, it just goes to the Grub command line. This is probably a nonproblem and I'm just utterly ignorant or all things Linux, but I would appreciate some help getting to GNOME. Thanks in advance.

---

### Post by garvinrick4 on 2010-01-30
> **SQ_Minion said:**
> I'm trying to dual-boot Windows 7 (64-bit, Home Premium) with Ubuntu 9.10. My hard drive was being stubborn, so I decided to just install through Wubi, off a Live CD. The installation seemed to run just fine, no abnormalities, but when I try to boot Ubuntu at startup, it just goes to the Grub command line. This is probably a nonproblem and I'm just utterly ignorant or all things Linux, but I would appreciate some help getting to GNOME. Thanks in advance.

You know with WUBI it really does not take that long just to go to Windows C: drive and there
will be a folder called Ubuntu right next to Users. Open it and select uninstall. 

Put CD back in tray select Wubi install when pops up and take the 12 minutes or so to install.

It is just as easy as going through a fix with a live CD and mounting your Windows install and fixing Wubi.

Use the uninstall and not the ADD and REMOVE programs in Windows it makes sure it removes everything from Windows 7 boot manager called bcd.

---

### Post by SQ_Minion on 2010-01-30
I know how to uninstall it, and have uninstalled and reinstalled several times. Each time GNOME won't come up after installation, only the Grub command line.

---

### Post by meierfra. on 2010-01-31
You are probably hit by a big in Grub 2. See this link for the details and  how to solve the problem:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

