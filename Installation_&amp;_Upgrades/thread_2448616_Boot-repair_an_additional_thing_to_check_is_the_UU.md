---
title: "Boot-repair an additional thing to check is the UUID of SWAP partition"
date: 2020-08-10
forum: Installation &amp; Upgrades
---

### Post by tonystark on 2020-08-10
Restoring an Ubuntu 18.04 partition (with Acronis) to a larger Solid State Disk, I had to switch from a MBR boot to an EFI boot.

The "boot-repair" [http://help.ubuntu.co/community/Boot-Repair](http://help.ubuntu.co/community/Boot-Repair) protocol worked great AFTER I figured this out out:

Before hitting the "Recommended Repair" button, but after I had started a live session ("Try Ubuntu") it  is essential to make sure that any "Swap" partition on the new disk has the correct UUID in both /etc/fstab and /etc/initramfs-tools/conf.d/resume.  This can be accomplished by editing those files from the live session.  The live session can probably mount the disk version of Ubuntu you're trying to get to boot, somewhere under "/mnt/ubuntu" or similar.  You can get the current UUID of the partitions by running "lsblk -f" in a terminal.  You may find that /etc/fstab and /etc/initramfs-tools/conf.d/resume have the UUID of your old swap partition from the old, replaced disk.   "boot-repair" will probably run "sudo update-initramfs -u" and the UUIDs should be correct when that happens.

If boot-repair does not do an "update-initramfs", you should do it manually using chroot.

---

