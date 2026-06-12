---
title: "Move ubuntu to another partition/HD?"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by dwhsix on 2005-11-09
I've got Ubuntu installed on a partition on 1 hard drive.  I'd like to move it to a new (bigger) partition on another hard drive entirely... what would be the easiest way to go about doing that?  I'd rather not reinstall from scratch unless I have to...

Thanks!

---

### Post by Remmelas on 2005-11-10
can be kind of difficult to do without installing from scratch, but basically, 
cp -ax / /mnt/destination
will get everything from your current install to the new partition, provided you mount it at /mnt/destination
but, then, you have to modify /mnt/destination/etc/fstab to point to the correct root file system, modify /mnt/destination/boot/grub/menu.lst to have an entry for you new partition, and then reinstall grub manually to understand it needs to find the menu.lst file on the new partition instead of the old one.
I'm sure i'm over simplifying this, but, if you have a high speed connection, i'd highly recommend for simplicities sake using the installer to lay down a new install.

---

### Post by DrumScum on 2008-01-05
> **Remmelas said:**
> can be kind of difficult to do without installing from scratch, but basically, 
cp -ax / /mnt/destination
will get everything from your current install to the new partition, provided you mount it at /mnt/destination
but, then, you have to modify /mnt/destination/etc/fstab to point to the correct root file system, modify /mnt/destination/boot/grub/menu.lst to have an entry for you new partition, and then reinstall grub manually to understand it needs to find the menu.lst file on the new partition instead of the old one.
I'm sure i'm over simplifying this, but, if you have a high speed connection, i'd highly recommend for simplicities sake using the installer to lay down a new install.

I just moved my Debian Etch to a different partition with this approach, and it worked like a charm.

Basically I just did
[LIST]
[*]cp -ax /* /destination/partition
[*]changed grub's menu.lst accordingly
[*]changed the device to be mounted at / in fstab
[/LIST]
All done in less than 15 minutes.

---

