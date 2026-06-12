---
title: "Broken Partition table"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by rockstar on 2006-09-24
I've been surfing this forum a lot lately and I've determinend my problem.  I partitionend my Hard Drive in a way that it has four partitions on it.  A 20 gig NTFS for windows, a SWAP, a 10 gig UBUNTU partition and the rest as FAT32 for storage.

I've done about everything possible with GRUB and trying to get Windows and Ubuntu to boot harmoniously, so I think some how the actual Partition Table of the Hard Drive is broken.  In Fdisk and CFdisk the drive letters keep changing and the STA# also change as well.

I'm afraid I'm going to have to back up and wipe the whole drive and start from scratch.

Does anyone have any other ideas?

---

### Post by rockstar on 2006-09-24
Here's all that I've done

[http://www.ubuntuforums.org/showthread.php?t=263213](http://www.ubuntuforums.org/showthread.php?t=263213)

---

### Post by jonjonz on 2006-09-24
I believe that GRUB is limited to addressing the first 8GB of multi GB disks.  This is because GRUB depends on the old DOS based bios that cannot address anything higher.  

The following will not work with GRUB

1st partition:   100GB Windows
2nde partition    100GB Linux

Grub will give a error 18 that it cant find the sector or some such when trying to boot Linux

This will work:

1st partition     6 GB windows
2nd partition     184 GB Linux

Because Grub can address the beginning of both partitions.

I am fairly new to all this, so if this is incorrect I hope someone will enlighten us, but I hope it helps you.

---

### Post by WildcatRay on 2006-09-25
> **jonjonz said:**
> I believe that GRUB is limited to addressing the first 8GB of multi GB disks.  This is because GRUB depends on the old DOS based bios that cannot address anything higher.  

The following will not work with GRUB

1st partition:   100GB Windows
2nde partition    100GB Linux

Grub will give a error 18 that it cant find the sector or some such when trying to boot Linux

This will work:

1st partition     6 GB windows
2nd partition     184 GB Linux

Because Grub can address the beginning of both partitions.

I am fairly new to all this, so if this is incorrect I hope someone will enlighten us, but I hope it helps you.
Hi,

I just installed Win2K Pro on a 100 GB partition of a 160 GB HDD. Then I let Ubuntu automatically partition the remaining free space (~60 GB). Everything was fine until I tried booting from GRUB into Windows. I received a BSOD with a 0x7B INACCESSIBLE_BOOT_DEVICE error. This might seem to indicate that GRUB can handle partitions beyond ~100 GB because my Ubuntu boots fine.

I'm still waiting for suggestions on how to troubleshoot my problem. See [http://www.ubuntuforums.org/showthread.php?t=263712&highlight=partition+table+problem](http://www.ubuntuforums.org/showthread.php?t=263712&highlight=partition+table+problem)

---

