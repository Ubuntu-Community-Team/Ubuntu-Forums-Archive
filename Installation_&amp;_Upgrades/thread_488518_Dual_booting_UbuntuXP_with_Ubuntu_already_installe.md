---
title: "Dual booting Ubuntu/XP with Ubuntu already installed"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by MrZumma on 2007-06-30
I need to install XP for an app that will not run under WINE and needs to transfer data to a PDA that can't be configured in an XP install created in VirtualBox.  

I have two hard disks installed.  One hard disk contains the Ubuntu Feisty install and the other disk is blank.  I would like to install XP to the blank disk and have GRUB prompt me for which OS to load.  I have not found a HowTo that explains how to do what I want to do.  Only to install Unbuntu on an existing XP install.

Thanks for any direction/links/etc.!

---

### Post by confused57 on 2007-06-30
> **MrZumma said:**
> I need to install XP for an app that will not run under WINE and needs to transfer data to a PDA that can't be configured in an XP install created in VirtualBox.  

I have two hard disks installed.  One hard disk contains the Ubuntu Feisty install and the other disk is blank.  I would like to install XP to the blank disk and have GRUB prompt me for which OS to load.  I have not found a HowTo that explains how to do what I want to do.  Only to install Unbuntu on an existing XP install.

Thanks for any direction/links/etc.!
This may give you an idea of how to set your system up:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
The principle should be the same...disconnect your Ubuntu drive, connect your other drive to the primary hard drive controller...install XP, then reconnect Ubuntu as primary boot drive & XP drive as secondary.

---

### Post by MrZumma on 2007-07-04
Cool!  Thanks confused, that worked!

---

### Post by taffyman on 2007-11-13
Hi I installed Ubuntu, on a windows xp computer, forming a duel boot system,after a while Ubuntu froze, i can no longer get on the internet,access the terminal, or log out, the whole system wont function,early on i tried downloading A.V.G to investigate a might have virus, or worm, but could not install,there is nothing i can do to find out the cause of this trouble, i did instal with WUBI, AND THE SYSTEM WORKED OK FOR A WHILE, EVEN INSTALLING TURBO PRINT AND PAYING FOR THE KEY, NOW ITS U.S,AND TO SAY I AM DISAPPOINTED IS AN UNDERSTATEMENT.HAS ANYONE GOT ANY IDEAS ON WHAT MIGHT HAVE HAPPENED. MANY THANKS IN ANTISIPATION.

---

