---
title: "Cannot read floppy drive"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by gordon3913 on 2007-11-21
I updated to 7.10 and I am unable to read my floppy drive .
A message comes up that says it is not a block device.

Everything looks alright in fstab but it still won't mount.

It will mount in Windows.

---

### Post by rmemm on 2007-11-21
Is there a chance that you were using a symlink to reference it and it's not there after the upgrade.  I think the floppy is usually /dev/fd0.  See if this file is there and that FSTAB references it.

If both are correct -- then very strange.

Rob

---

