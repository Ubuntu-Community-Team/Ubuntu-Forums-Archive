---
title: "Two Linux installations on one disk"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by anton on 2008-06-11
I'd like to create a partition on my hard disk to play around with other Linux distro's.  Is there a SAFE newbie-friendly way of doing this without screwing up my existing Ubuntu installation?  Or should I rather buy an additional hard disk?

---

### Post by Habbit on 2008-06-11
It mostly depends on what the other distro does. You could damage your Ubuntu installation in two possible ways:
[LIST][*]Overwriting its partitions. Just make sure the new distro installer does not try to format anything it should not
[*]Screwing up the bootloader. Avoiding this may be a bit trickier. If the GRUB installation set up by Ubuntu is in the MBR (hd0), then set the new GRUB at a safe place like your new root's boot sector i.e. (hd0,5) or whatever. You may have some problems chainloading each other, but you'll most probably work it out without causing havoc.[/LIST]

A distro I like tinkering with is Gentoo, since it as a completely "do-it-yourself" installation and does not force you to install a bootloader - I had it side-by-side with Ubuntu for a long time and there were absolutely no problems.

---

### Post by Pumalite on 2008-06-11
Is your Ubuntu ia a primary or logical partition. Post a screenshot of gparted

---

### Post by anton on 2008-06-11
Thanks, both of you.  I've decided to not do this for now -- I've just added KDE to Ubuntu, and that gives me enough variety!

What I am considering is adding Vista to my Windows drive, i.e. so that I have both XP and Vista on one disk and Ubuntu on the other disk.  Can I do that without messing up Grub or, alternatively, restore Grub once Vista is installed?

---

### Post by Pumalite on 2008-06-11
After installing Vista; you will have to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

