---
title: "Will Kubuntu 9.10 CD partition my C: drive?"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by tlinux on 2010-01-20
I've just downloaded and burned to a CD the 64-bit version of Kubuntu 9.10. I want to install it as a dual boot setkup along with Windows 7. If I run this CD will it allow me to partition the C: drive or will it wipe out Windows 7?

If I need to partition the C: drive before installing Kubuntu, is there a free program for partitioning?

Thank you.

---

### Post by darkod on 2010-01-20
If win7 is taking up your whole hdd, you need to shrink the win7 partition for how much space you want allocated for ubuntu. Win7 Disk Management tool can do this for you from within windows.

Once you have the unallocated space, DO NOT create ntfs partition because linux does not use them as system partitions. Just leave the space as unallocated and during kubuntu install select Use Largest Available Free space and it will set up kubuntu in that space.

---

### Post by presence1960 on 2010-01-20
> **darkod said:**
> If win7 is taking up your whole hdd, you need to shrink the win7 partition for how much space you want allocated for ubuntu. Win7 Disk Management tool can do this for you from within windows.

Once you have the unallocated space, DO NOT create ntfs partition because linux does not use them as system partitions. Just leave the space as unallocated and during kubuntu install select Use Largest Available Free space and it will set up kubuntu in that space.

+1

Use windows to shrink it's partition. There is a known bug when resizing Vista/Windows 7 with an outside partitioning utility such as gparted. See [here]("http://bugzilla.gnome.org/show_bug.cgi?id=379482") for more info. If you resize windows Vista or 7 with another utility you run the chance of making windows unbootable until you repair it with the windows install DVD.

---

