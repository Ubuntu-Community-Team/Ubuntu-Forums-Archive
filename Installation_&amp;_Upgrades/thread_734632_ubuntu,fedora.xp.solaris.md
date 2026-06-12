---
title: "ubuntu,fedora.xp.solaris"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by junaid.kollam on 2008-03-24
I want to install xp and solaris in my ubuntu and fedora installed system.Help me

---

### Post by Rocket2DMn on 2008-03-25
I'm not sure what's gonna happen when you install SunOS Solaris, that's quite an exploration you're going on there.  
Before you install windows xp, you need to make room on the hard drive for it (and solaris if you so choose), by resizing partitions with GParted on the Ubuntu LiveCD or using the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) .  Alternatively you can install both to a separate hard disk.  ALWAYS backup your data before fiddling with partitions, you never know what might happen (either because you screw up or the resizing gets messed up).
When you install windows xp it will overwrite the MBR, so you will have to recover GRUB - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
That's all I got for you, good luck on Solaris.

---

