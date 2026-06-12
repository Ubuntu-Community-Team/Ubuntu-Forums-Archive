---
title: "Accessing Drives after a Kernel Panic"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by Valavien on 2005-04-09
Hi all,

After downloading the latest lot of updates for Hoary I can now not boot due to a kernel panic.  I thought instead of fixing it I would reinstall using the newly released cd.  However, I want to get some data out of my old home directory but don't know how to access it.  It's an xfs partition.  I already tried using the live cd but can't access the drives.  

Thanks
Valavien

---

### Post by jdong on 2005-04-09
From the liveCD, do a **sudo mount /dev/hda1 /mnt/hda1 -t xfs**, replacing hda1 with the actual root device, making sure that /mnt/hda1 already exists (or create it with mkdir).

If it still doesn't mount, it means the partition was *damaged* during the system panic. In this case, use the xfs_repair utility, but with extreme caution... It will probably start madly deleting corrupted inodes.

---

### Post by az on 2005-04-09
Can't you just boot with the old Warty kernel?

Hit escape to see the grub menu list if it does not show up...

---

