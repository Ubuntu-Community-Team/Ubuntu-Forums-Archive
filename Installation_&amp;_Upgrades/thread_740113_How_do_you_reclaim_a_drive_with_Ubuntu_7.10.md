---
title: "How do you reclaim a drive with Ubuntu 7.10?"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by sgbrix on 2008-03-30
I like to be able to start from the beginning and re-install windows/Ubuntu as dual boot, but first wipe the drive clean as in a new drive.

---

### Post by prshah on 2008-03-30
> **sgbrix said:**
> I like to be able to start from the beginning and re-install windows/Ubuntu as dual boot, but first wipe the drive clean as in a new drive.

Assuming that you just want to delete everything and not WIPE it (ie, as in a security issue), you can just boot with the gutsy live CD delete all your partitions on the hard disk drive, then boot and install Windows then boot and install gutsy.

IMPORTANT: When you boot from the live CD, it will detect and automatically activate your swap partition. You either right-click your swap partition in gparted and choose swapoff or use the command ```
sudo swapoff -a
``` in a terminal.

Any mounted partitions will not be deleted, so unmount all partitions (you can do this in the partition editor program "gparted") or simply use the "umount" command with the partition, eg,```
umount /dev/sda1
```

---

### Post by Jose Catre-Vandis on 2008-03-30
Or boot with the live cd and run gparted to sort out your partitions

---

