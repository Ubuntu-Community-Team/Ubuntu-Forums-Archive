---
title: "dual boot XP"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by nbo10 on 2008-01-14
Hi All,
I'm running ubuntu 7.10 on my laptop and love it. I want to put ubuntu on my desktop but I also need to keep XP on the desktop. Can I install ubuntu on a external hard drive? And how do  I install a dual boot without reinstalling XP? Thanks.

---

### Post by helix_r on 2008-01-14
> **nbo10 said:**
> Hi All,
I'm running ubuntu 7.10 on my laptop and love it. I want to put ubuntu on my desktop but I also need to keep XP on the desktop. Can I install ubuntu on a external hard drive? And how do  I install a dual boot without reinstalling XP? Thanks.

You'll want to look on the internet for detailed directions. However, I can tell you the following things from performing many dual boot installs:

The most simply way to get most linux distros installed as dual boot with XP is to first have XP installed. Then, you'll want to add another hard drive and install ubuntu on the new hard drive. Unless you're dealing with an external sata drive, I think you're better off just using a plain internal drive. When you perform your install simply be sure to select the new disk and not the one with windows already on it. 

The default ubuntu installation will modify the MBR (master boot record) of the disk that boots the computer (probably the one with XP on it). This modification will make it so an application called "GRUB" will present a menu to you when the machine boots. You can use this menu to go into whichever OS you want. 

In other words there is nothing special you have to do to get a dual boot system other than to select the disk you want ubuntu to go onto.

---

