---
title: "/Boot Partition (Dual Booting)"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by guimaster on 2010-11-21
Hey all,
 
 I am going to be dual booting with Windows XP on my new netbook. I know that I will be required to re-install XP before I will have to reinstall Linux.

 My question is about the /boot partition option. If I was to create a /boot partition, would that prevent Windows from erasing Grub when I reinstall Windows? I have been Googling and I can't find an answer so I figure it won't work but I better ask as it would make life a whole lot easier.

 Thanks!

---

### Post by garvinrick4 on 2010-11-21
> **guimaster said:**
> Hey all,
 
 I am going to be dual booting with Windows XP on my new netbook. I know that I will be required to re-install XP before I will have to reinstall Linux.

 My question is about the /boot partition option. If I was to create a /boot partition, would that prevent Windows from erasing Grub when I reinstall Windows? I have been Googling and I can't find an answer so I figure it won't work but I better ask as it would make life a whole lot easier.

 Thanks! If you have linux on your machine now you can make a partition in gparted for Windows and install and then reinstall grub to mbr from linux to boot both
from grub2's boot menu. When windows first then linux grub2 is installed with linux and
is done. Just easier when windows in installed first is all.
 Making seperate boot partition would not really accomplish anything on your netbook
that I know of.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by kansasnoob on 2010-11-21
> I am going to be dual booting with Windows XP on my new netbook. I know that I will be required to re-install XP before I will have to reinstall Linux.


Huh? Where did you get that idea?

> My question is about the /boot partition option. If I was to create a /boot partition, would that prevent Windows from erasing Grub when I reinstall Windows?

Uh ............ NO! A separate /boot is seldom needed and generally only creates problems.

Since it's a Netbook I assume you'll be using a Live USB, is that right?

If so do you have the Live USB yet?

If so post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then we'll know more about what you're starting with ;)

---

