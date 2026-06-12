---
title: "Multiple USB devices to mount"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-11
I have an extern HDD and an iPod. I have this in my fstab file:

/dev/sda2       /media/ipod     vfat    user,umask=000,noauto   0 0
/dev/sdb1       /media/maxtor   vfat    user,umask=000,noauto   0 0

That way I can access the drives in konqueror without being in root mode.

The problem is that I have to edit this file each time I forget to connect
my iPod or if my extern HDD is turned of.

Is there some smart way to get access to USB drivers through konqueror even
if I have them turned off or disconnected on startup in various
combinations?

I can only make it work if I always decide on one kind of setup (both
connected, one of them connected etc.).

---

