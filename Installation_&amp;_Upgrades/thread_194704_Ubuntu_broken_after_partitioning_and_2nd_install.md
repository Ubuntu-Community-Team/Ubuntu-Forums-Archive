---
title: "Ubuntu broken after partitioning and 2nd install"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by Steven_B on 2006-06-11
Today I did some drive re-partitioning, and did a second install of ubuntu dapper into another partition, so I can experiment without breaking by stable system.  However, when I try to boot the original, it seems to stop on somthing about "failing IO sync".
I didn't modify the ubuntu partition, and the second install recognized it and added it in GRUB.  The recovery mode boot stops with the same error.
How do I fix this?  Thanks!

---

### Post by Steven_B on 2006-06-11
The last thing it says is:
"Kernel panic - not syncing: I/O error reading memory image"
It seems like grub is starting to boot it correctly, but it gets confused at the partitions being different.

---

### Post by confused57 on 2006-06-12
You could try pressing "e" for the kernel you're trying to boot, when the grub menu displays at bootup.  See if it is pointing to the correct partition on your HD, I think if you change it here, it's not permanent...

Also, you could run a LiveCD and see what your partition table looks like:

```
sudo fdisk -l
```

Least I bumped your thread, even if I couldn't come up with a solution...

---

### Post by Steven_B on 2006-06-12
sudo fdisk -l gives what I expect:
 ```
  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         433        1040     4883760    7  HPFS/NTFS
/dev/hda2            1041        3472    19535040    5  Extended
/dev/hda3            7299       12161    39062047+   b  W95 FAT32
/dev/hda4            3473        7298    30732345   83  Linux
/dev/hda5            1041        2315    10241406   83  Linux
/dev/hda6            2316        3472     9293571   83  Linux
```

Something else I saw said to do boot with a live CD and do
```
chroot /mnt/sysimage
mkinitrd /boot/initrd-2.6.15-23-386

```
Am I correct in assuming the can be done with ubuntu?

---

### Post by Steven_B on 2006-06-12
I copied the files in /boot from the working install to /boot on the not-working one, rebooted, and it worked!

---

