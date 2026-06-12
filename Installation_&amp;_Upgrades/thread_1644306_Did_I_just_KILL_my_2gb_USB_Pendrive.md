---
title: "Did I just KILL my 2gb USB Pendrive?"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by xiotech on 2010-12-13
Umm... I was in Disk Utility trying to format my 2gb USB Pendrive prior to creating a USB startup disk and I chose ext4 filesystem and it errored out and now the little guy is gone!!! It does not show up in the Disk Utility list anymore.

Wow... is there anyway from within Ubuntu Desktop 10.10 to simply  create a bootable Ubuntu Hard Drive???

I've got a blank 120gb drive just sitting there and it sure would be nice to just put the .iso image out on a small bootable partition with some system files and plug it in as my primary hard drive and run the installer program.

Any chance .iso on my 120gb hard drive install can be done?

Anyway to revive the 2gb Pendrive to be seen or used again? 

Would booting windows again allow me to put Fat32 back on it? 

thanks

---

### Post by amsterdamharu on 2010-12-13
When the drive is plugged in what is the output of
```
sudo fdisk -l
```

When you post the output (you can copy from terminal) then select the text and click on the # button (wrap code tags around selected text)?

---

### Post by xiotech on 2010-12-13
> **amsterdamharu said:**
> When the drive is plugged in what is the output of
```
sudo fdisk -l
```

When you post the output (you can copy from terminal) then select the text and click on the # button (wrap code tags around selected text)?

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22bd22bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6371    51175026    7  HPFS/NTFS
/dev/sda2            6372        9725    26941005    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b8aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7297    58613121   83  Linux

Disk /dev/sdc: 2012 MB, 2012217344 bytes
62 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002aabe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1022     1964253    c  W95 FAT32 (LBA)

```

I can see my 2gb Pendrive again, but it is acting strange and not accessible.

I'll restart everything and try another USB port

---

