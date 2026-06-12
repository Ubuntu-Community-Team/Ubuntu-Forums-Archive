---
title: "GRUB - want it to re-run the detection done at installation"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by sandyscott on 2007-05-18
Hi,

I've had fiesty running on my machine for a little bit now, but I decided to have a play with Ubutu Studio, so I've downloaded it, installed it to and External hard disk, and told it to write its version of grub to the MBR of the first hard disk.

It didn't, and left the version of GRUB installed by Fiesty in situ, without any options to boot Studio.

What I'd like to do is re-run the installation of GRUB as it occurs in the installer, where it finds all the hard OS's, even those on external hard drives, and sets them up accordingly.

I've tried simply running the installer again, but this doesn't work as you are prevented from installing grub (by jumping out into the installation menu before the partitioner) as the installer thinks you havn't set up a base system.


What should I do?

Any help much appreciated.


Sandy Scott


PS. I'm using the alternate installer (Fiesty LiveCD does not boot into a GUI on my laptop), with one internal SATA hard disk, on which Fiesty and Windows reside, and a USB external hard disk,with the Studio partition and other NTFS partitions.

I can see the contents of the Studio partition (and its /boot/grub/menu.lst file) when I boot into Fiesty, if that helps

---

