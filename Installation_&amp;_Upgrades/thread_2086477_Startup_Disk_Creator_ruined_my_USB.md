---
title: "Startup Disk Creator ruined my USB"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by patagriff on 2012-11-21
Startup Disk Creator ruined my USB drive. Now I cannot mount it, even with gparted. I downloaded Ubuntu 12.10 and used SDC (I don't see how I could have used it improperly. There's like 2 steps.) Machine wount boot from it. Can't mount it. What should I do?

---

### Post by darkod on 2012-11-21
Is this a usb hdd or usb stick?

You can connect it and see if it's recognized at all, try:
sudo parted -l (small L)

That should list all disks with their partitions including usb hdds/sticks.

---

### Post by patagriff on 2012-11-21
patrick@patrick-Aspire-5515:~$ sudo parted -l (small L)
bash: syntax error near unexpected token `('
patrick@patrick-Aspire-5515:~$ sudo parted -l 
[sudo] password for patrick: 
Model: ATA WDC WD1600BEVT-2 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  157GB  157GB   primary   ext4            boot
 2      157GB   160GB  2949MB  extended
 5      157GB   160GB  2949MB  logical   linux-swap(v1)


Model: Generic USB 2.0 (scsi)
Disk /dev/sdb: 2073MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2073MB  2073MB  primary               boot, lba


Error: /dev/sr0: unrecognised disk label

---

### Post by darkod on 2012-11-21
There it is, /dev/sdb, a 2GB stick. But it doesn't seem to have any filesystem on it.

If you don't have any important data on it, and I guess you don't because you just wanted to overwrite it with the ubuntu install files, simply make a new msdos table. After that you can use Gparted to create new FAT32 partition. The start up disc is best to have FAT32.

To make new empty table with parted:
```
sudo parted /dev/sdb
mklabel msdos
quit
```

---

