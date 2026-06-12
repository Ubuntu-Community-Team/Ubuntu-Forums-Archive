---
title: "uh oh...no swap file, big boot partition only"
date: 2005-08-26
forum: Installation &amp; Upgrades
---

### Post by pixxelle on 2005-08-26
I installed Ubuntu after some problems with Kubuntu and KDE.

I have discovered that I haven't any swap file (!) and the entire installation is all in one partition, the booting one. Grub is working fine with my XP dual boot. I am sure I missed something along the way when reinstalling and telling the installer to redo partitions over the original Kubuntu install.

Can I save this install or do I have to start over again? (Usually takes me three times to get an OS install right! ](*,) )I would also like to have a separate partition for /home at least. I think the only reason I can run OK now is because I have a lot of RAM, 1.5 GB.

In PartitionMagic8 (Win XP) I have made a Linux swap file on hda5. I don't have any free space on the hdb (physical) disk where Ubuntu resides.  Can I get Ubuntu to see it on hda? Does it see it already? fstab doesn't list it so far.

My current partition table is this: (whole system)

```
Disk /dev/hda: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        1918    15366172+   7  HPFS/NTFS
/dev/hda3            2273        2534     2104515    f  W95 Ext'd (LBA)
/dev/hda5            2273        2534     2104483+  82  Linux swap / Solaris 

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            1914        3588    13454406    7  HPFS/NTFS
/dev/hdb2            3589        4863    10241437+   7  HPFS/NTFS
/dev/hdb3               1        1913    15366141   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25574   205423123+   7  HPFS/NTFS
/dev/sda2           25575       30401    38772877+   f  W95 Ext'd (LBA)
/dev/sda5           25575       30401    38772846    b  W95 FAT32
```

Thanks for the assistance and suggestions.

---

### Post by [pl]ice on 2005-08-26
hey, i used once partition magic to create swap. linux automatically found it after reboot, u can also change size of partitions, that should do it, not sure how to do it under linux, w/o wiping stuff...

---

### Post by pixxelle on 2005-08-26
Thanks,

I added an entry for the swap file I made into fstab and I think it's being seen after a reboot. It shows in system monitor (although it shows no actual usage, just the size which is 2GB)

I was looking into the Parted app  for native support for resizing, etc. but need more info/knowledge about possible gotchas.

I might try a resize in PartitionMagic, again being cautious about the possibility of data loss. I need to keep the existing  NTFS partitions intact.

---

