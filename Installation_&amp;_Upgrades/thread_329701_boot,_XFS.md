---
title: "/boot, XFS"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by thechris on 2007-01-02
XFS is supported on /boot.  the installer will not allow XFS on /boot or /.  i have:
/dev/sda2 -- /boot -- ext2
/dev/sda6 -- /  -- xfs

the installer tells me that i must place /boot on a non xfs partition.  this is not true, and I even have a non-xfs /boot partition.

if kubuntu doesn't support XFS, i can't really concider it for use.  i will try the alternate installer.

does anyone know how to get xfs working?  also, where is reiserfs?  is kubuntu trying to be an ext3-only distro?

---

### Post by kidders on 2007-01-02
> **thechris said:**
> is kubuntu trying to be an ext3-only distro?Hehe. Although I haven't seen it myself, you might have encountered a glitch in the installer. Try messing around with your filesystem choices *after* installation. You shouldn't have any problems. :-)

---

### Post by thechris on 2007-01-03
works fine in the alternate installer.  it is just a bug on the graphical installer.

---

