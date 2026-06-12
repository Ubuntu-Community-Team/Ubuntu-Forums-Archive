---
title: "Can I choose which partition to Install the GRUB files on?"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by andrewwg94 on 2008-10-11
i know that part of grub is in the mbr, and the other is usually in ubuntu's root partition. I want to install those grub files in a diffrent partition. Is that possible? can i put them in the windows partition? if not, can i just make a small new partition to put grub in it?

---

### Post by caljohnsmith on 2008-10-11
> **andrewwg94 said:**
> i know that part of grub is in the mbr, and the other is usually in ubuntu's root partition. I want to install those grub files in a diffrent partition. Is that possible? can i put them in the windows partition? if not, can i just make a small new partition to put grub in it?
Sure you can make a dedicated Grub partition, but usually an easier way is to make a ~200 MB partition and mount that as /boot during the Ubuntu install process; that partition will then contain all the kernel and boot files, including Grub. Or if you want to use Grub inside of an NTFS partition (Windows), you can install "grub4DOS", which coincidentally is how I have my machine set up at the moment.

But first, why do you want to put the Grub files in another partition? In order to best help you, it would be best if you state your ultimate goal in addition to what you are thinking of doing. :)

Also, just so I can get an idea of your setup, please post:
```
sudo fdisk -lu
```

---

### Post by andrewwg94 on 2008-10-12
> **caljohnsmith said:**
> Sure you can make a dedicated Grub partition, but usually an easier way is to make a ~200 MB partition and mount that as /boot during the Ubuntu install process; that partition will then contain all the kernel and boot files, including Grub. Or if you want to use Grub inside of an NTFS partition (Windows), you can install "grub4DOS", which coincidentally is how I have my machine set up at the moment.

But first, why do you want to put the Grub files in another partition? In order to best help you, it would be best if you state your ultimate goal in addition to what you are thinking of doing. :)

Also, just so I can get an idea of your setup, please post:
```
sudo fdisk -lu
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb3cf5238

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41945714    20972826    7  HPFS/NTFS
/dev/sda2        75939255   156296384    40178565    7  HPFS/NTFS
/dev/sda3        41945715    75939254    16996770    5  Extended
/dev/sda5        41945778    44949869     1502046   82  Linux swap / Solaris
/dev/sda6        44949933    75939254    15494661   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 17.2 GB, 17245863936 bytes
255 heads, 63 sectors/track, 2096 cylinders, total 33683328 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcae7cae7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    33672239    16836088+   7  HPFS/NTFS

i'm just trying to keep the boot files as safe as possible

---

### Post by caljohnsmith on 2008-10-12
> **andrewwg94 said:**
> i'm just trying to keep the boot files as safe as possible
I would recommend going with a /boot partition then. Do you want to reinstall and do that like I described before, or do you want to keep your current install? Either way, you'll need to make a ~200 MB partition for mounting as /boot; you can do that from the Live CD by running:
```
gksudo gparted
```
And use Ubuntu's gparted partition editor to make the new partition.

---

