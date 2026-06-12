---
title: "Gparted partition resize"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by RochJer on 2011-06-30
I recently downloaded/installed Gparted as I want to resize my ubuntu to more HDD space in partition and reduce NTFS partition size. Is there any faster way to do gparted in ubuntu? I remembered in previous versions of ubuntu that gparted had MBR but I can't find info to do this.

---

### Post by nzjethro on 2011-06-30
Is the NTFS partition a Windows partition (i.e. does it have Windows installed on it), or is it just a data partition?

If it's Windows, I'd recommend shrinking from Windows rather than from Gparted. If it's just data, make sure everything is backed up and tested, and then use Gparted to shrink it, and then expand your Ubuntu partition into the unallocated space.
You should be able to unmount your NTFS partition to shrink that down, but to play around with your Ubuntu partition you are going to have to either create a GParted Live CD, or boot to Ubuntu from a Live CD and the open GParted from the Live CD environment, as you will not be able to change your Ubuntu partition while it is mounted.

---

