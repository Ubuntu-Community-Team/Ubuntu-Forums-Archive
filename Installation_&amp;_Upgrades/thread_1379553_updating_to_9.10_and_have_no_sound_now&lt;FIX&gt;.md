---
title: "updating to 9.10 and have no sound now&lt;FIX&gt;"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by fcrowder on 2010-01-12
This is the fix that worked for me I did not write this but I thought would pass it along.
This is the original web site [http://xpapad.wordpress.com/2009/12/31/fixing-sound-after-upgrading-to-ubuntu-9-10-karmic-koala/](http://xpapad.wordpress.com/2009/12/31/fixing-sound-after-upgrading-to-ubuntu-9-10-karmic-koala/)
 
I recently upgraded from Ubuntu Jaunty (9.04) to Karmic (9.10), and the sound stopped working. As a matter of fact, no sound card was detected. Searching around, it turned out that the problem lied with a wrong kernel version, which actually stems from an apparent bug in the new grub boot loader that ships with Karmic. Even though I&#8217;m using Ubuntu, this might affect other distributions that use the same boot loader. If you face a similar problem, try the following:
 

First, check your kernel version:
[LIST]
[*]*sudo uname -r*
[/LIST]If you see a version below 2.6.31, do the following:
[LIST]
[*]Delete your old /boot/grub/menu.lst file. Due to an apparent bug, grub will not overwrite it during distribution upgrade or subsequent upgrade-grub commands.
[*]Run* sudo update-grub*. A new menu.lst will be generated, now pointing to the right kernel.
[*]Install grub on your MBR. First make sure which device holds your MBR (most probably /dev/sda, but it might be /dev/hda if you have an old IDE disk), then run: *sudo grub-install /dev/sda* (replace with the proper device)
[*]Reboot.
[/LIST]

---

### Post by kslavens17 on 2010-02-04
Thank you VERY much!!  This worked where so many other solutions did not.

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

