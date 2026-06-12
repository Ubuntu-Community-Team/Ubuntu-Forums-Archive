---
title: "Feisty: Partition not detected"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by amartani on 2007-04-22
I have Edgy installed on hda5, with /home on hdb1.
I installed Feisty on hda6 (sda6), but hdb1 (sdb1) was not detected.
ls /dev/hd* returns nothing, ls /dev/sdb* returns only /dev/sdb. sda partitions have no problem. It looks like the partitions on sdb don't exist. But parted can detect it, and Edgy have no problem using it.
```
# ls /dev/sd*
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sdb

# parted /dev/sdb print

Disk /dev/sdb: 40.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  40.1GB  40.1GB  primary  reiserfs          

Information: Don't forget to update /etc/fstab, if necessary.
```

Where is my sdb1?

---

### Post by pepsi_max2k on 2007-04-22
not related to any of this is it? [http://ubuntuforums.org/showthread.php?t=413745](http://ubuntuforums.org/showthread.php?t=413745)

---

### Post by amartani on 2007-04-22
I don't think so. Parted and the livecd installer detected the partition correctly, also including it in fstab. But, after reboot, fsck failed, and the system starts in maintance mode. Commenting the fstab line boots the system with no problems, but I can't mount the partition.

---

### Post by amartani on 2007-04-23
the livecd can see the partition correctly, but as hdb1. Is it a bug on libata? How can I disable libata?

---

### Post by amartani on 2007-04-26
up..

---

