---
title: "grub --&gt; can not boot windows"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by dragonfly on 2005-04-13
Fresh Install.
Installed XP first on slave drive.  Created 256MB NTFS to boot XP on hd0

Installed Hoary second on master drive (hd0).  
Added to grub

title xp
root (hd1,0)
makeactive
chainloader +1


error I get is unkown file system when trying to boot xp.

Could somebody help, please?

---

### Post by dragonfly on 2005-04-13
some more info:

mount /dev/hdd1 /mnt/xp -t ntfs works fine

changed grub therefore to:

title xp
root (hd2,0)
makeactive
chainloader +1


still get unknown file system

HELP, please

---

### Post by dragonfly on 2005-04-13
actually with hd2,0 and hd3,0 device does not exist
hd1,0 unknown file system
xp on hdd1 mounts fine

master disk hda ubuntu
slave disk hdd xp

don't get it
why can't grub boot it

---

