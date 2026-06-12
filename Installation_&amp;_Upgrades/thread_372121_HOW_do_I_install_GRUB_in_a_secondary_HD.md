---
title: "HOW do I install GRUB in a secondary HD?"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by nick24 on 2007-02-27
Hi there 

I am trying to install Ubuntu 6.10 on a secondary internal HD. I want Ubuntu and grub to be in the second HD. I got to the installation process where it asked me where to install GRUB and I typed hd1 (default was hd0), after installation I started my computer only to find out it won't boot in to Ubuntu. When I highlight and chose Ubuntu it takes me to this blank (black) screen and tells me to hit any key. What am I doing wrong? Please help. Thanking you in advance

---

### Post by confused57 on 2007-02-27
> **nick24 said:**
> Hi there 

I am trying to install Ubuntu 6.10 on a secondary internal HD. I want Ubuntu and grub to be in the second HD. I got to the installation process where it asked me where to install GRUB and I typed hd1 (default was hd0), after installation I started my computer only to find out it won't boot in to Ubuntu. When I highlight and chose Ubuntu it takes me to this blank (black) screen and tells me to hit any key. What am I doing wrong? Please help. Thanking you in advance
Make sure your Ubuntu entry is highlighted in your grub menu at bootup, press "e" to edit, then change the root from (hd1,0) to root (hd0,0), then press "b" to boot...this is temporary if it works, you can make it permanent in your /boot/grub/menu.lst.

If you get Ubuntu to boot, or you can do it from a live cd, open a terminal(Applications---Accessories---Terminal), enter(copy & paste):
```
sudo fdisk -l
```
The -l is a small "L"

You also might want to give a little more information about your pc setup, Windows on other HD, video card type, mobo, amount of memory, type CPU, etc.

If you're going to reinstall, as you mentioned in your other thread in the "Absolute Beginner" section...set your secondary hd as the first booted hard drive in bios, grub will see it as hd0 & should add an entry to boot Windows on hd1...to ensure that grub installs to the correct drive, you can always enter "/dev/hdb", when you make your selection.
You might want to read over this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

You might want to delete your other thread you started 8 minutes before this one, so that you don't get people posting to both threads...it's best to "bump" a thread rather than starting a new one(just click on reply & type in "bump")...try waiting at least an hour before bumping.

---

### Post by confused57 on 2007-02-28
I'm glad to hear you got everything working with your dual boot on 2 hard drives:
[http://www.ubuntuforums.org/showthread.php?t=372550](http://www.ubuntuforums.org/showthread.php?t=372550)

Selecting to boot a Windows or Ubuntu drive,using bios, is the preferred method by many people...it's all about choice & what works best for you.

---

