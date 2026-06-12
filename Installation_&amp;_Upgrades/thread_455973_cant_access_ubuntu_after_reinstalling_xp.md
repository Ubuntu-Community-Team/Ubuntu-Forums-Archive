---
title: "cant access ubuntu after reinstalling xp"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by psycho7 on 2007-05-27
I had ubuntu and xp ,and after i formatted xp's partition and reinstalled it i cant access ubuntu, the screen to select operating system is not showed anymore and i get directly to windows

---

### Post by Maeve on 2007-05-27
You'll have to install a Bootloader (GRUB).

I first thought about installing it with a Live-Linux.
Maybe this will help you:
Knoppix-CD:
[http://www.linuxforums.org/forum/installation/53739-install-grub-through-knoppix.html](http://www.linuxforums.org/forum/installation/53739-install-grub-through-knoppix.html)
Ubunto-CD:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

I can remember my first try to install GRUB with Knoppix. I needed more than one link ^^

---

### Post by Ub1476 on 2007-05-27
Simplest way for you is to reinstall Grub (Windows overwrote it) and use that as your bootloader.

Follow this guide: [Linky]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

And scroll down to ...Reinstall GRUB to the MBR... and follow it from there.

---

### Post by YousefAB on 2008-07-15
But the problem is we can't access the Ubuntu to change that file.

How can we access Ubuntu after installing XP ?

XP modifies the file so it only boots to it, so how do we go to ubuntu?

---

### Post by zipperback on 2008-07-15
Here is a step by step on how to fix it.

[http://onlyubuntu.blogspot.com/2008/06/howto-re-install-grub-after-windows.html](http://onlyubuntu.blogspot.com/2008/06/howto-re-install-grub-after-windows.html)

Hope this helps you.

- zipperback
:popcorn:

---

### Post by YousefAB on 2008-07-17
Thank You sir.

I'll try that as soon as I get time.

:)

---

