---
title: "Hard Drive Migration"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by JamieKitson on 2007-11-07
Hi,

There are plenty of guides for moving a linux installation from one hard drive to another if you are prepared to re-format the drive, but I want to keep the partitions of the new drive and move an install on to it. Maybe this isn't possible with different partition numbers and the like, does anyone know?

Cheers, Jamie

---

### Post by dabl on 2007-11-07
I'd say the filesystem "splitting" scheme between partitions would have to remain the same on the new drive for your plan to work.  In other words, if "/", "swap", and "/home" are on three separate partitions on the old drive, then they'll have to be moved to three separate partitions on the new drive. Same for "/boot", "/var", "/usr" or any other parts of the Linux filesystem that are not all together with "/".

If your boot partition is not the same number (hd_,_) then /boot/grub/menu.lst won't work until you fix it.

And of course the /etc/fstab table will be wrong, until you edit it -- hopefully you're not using UUIDs, because they won't be any good on the new drive.

When I think of these issues, it seems the only way you can get started, after you move the filesystem(s), is to boot a Live CD and start fixing the menu.lst and fstab.  I'm glad it's you and not me.  I'd re-install the whole deal.  :lolflag:

---

