---
title: "New windows partition?"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by uBrendon on 2008-04-09
Here's the thing, I was a previous Windows user and played a few games here and there and I installed  Ubuntu over everything I love Ubuntu but I want my games so I would like to make a new partition in Ubuntu for Windows XP anyone know how? One of the games is GTA:SA if I could get that working through Wine I wouldn't have to install xp. If you know a GOOD guide for noobies to do that I will also like that.

---

### Post by Rocket2DMn on 2008-04-10
If you want to setup a dual boot again, you can use the GParted LiveCD to resize your Ubuntu partition to make room for windows again - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Always make good backups of your important data before fiddling with partitions (mostly in case you screw up, though sometimes things can go bad)

After you reinstall windows, you will have to reinstall GRUB since windows will overwrite the MBR and you won't have the option to boot back into Ubuntu.  See here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) - it's OK to overwrite the windows bootloader.

It looks like GTA:SA should work in wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7677](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7677)

Here's how to install wine: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

