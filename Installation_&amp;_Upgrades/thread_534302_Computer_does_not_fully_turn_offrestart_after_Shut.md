---
title: "Computer does not fully turn off/restart after Shut Down?"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by edanastas on 2007-08-25
I think I messed up the boot loader? I was trying to setup the GRUB to dual boot using terminal commands from an online guide and now the computer does not shut down all the way. It just stalls on a blank black screen without fully shutting down.

Does anyone have enough experience to know what is wrong? :)

I have to force the computer to turn off by holding down the power button whether I am shutting down or restarting. I am using a Dell Optiplex SX270

If anyone can tell me what the problem is I will at least be able to start looking.

Thanks

---

### Post by mocoloco on 2007-08-27
If you edited the menu.lst file with gedit there should be a backup file in /boot/grub called menu.lst~ which you just have to rename.
If not the easiest thing to do now would be just re-do your grub menu.  Backup your current menu.lst file and follow the instructions [**here**]("http://ubuntuforums.org/showthread.php?t=224351"), except that you will NOT need to boot off of a live CD, since you can already boot into Ubuntu.

---

