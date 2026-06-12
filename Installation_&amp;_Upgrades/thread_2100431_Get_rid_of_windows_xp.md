---
title: "Get rid of windows xp ???"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by dlw1146 on 2013-01-01
netbook currently dual booted with wxp.
How do I get rid of xp without disturbing ubuntu?
sda is divided into sda1 and sda2. sda1 has boot on it.
can i  move boot to sda2?

thanks,
dlw

---

### Post by darkod on 2013-01-01
If you are using the grub/grub2 bootloader, all the files it needs are on the ubuntu partitions. You don't need to move anything from the XP partition, except personal data you have there and want to keep.

After that you can simply use Gparted to delete the windows partition, and in terminal run:
sudo update-grub

so that grub2 deletes the entry from the boot menu once windows is gone.

Later you can consider expanding the ubuntu partition(s) to use the unallocated space from the deleted XP partition. But note that any resizing has some risk, so you will need to make a full backup of ubuntu first.

You can also simply create new partition from the unallocated space and use it like that attached to a mount point you will create.

---

