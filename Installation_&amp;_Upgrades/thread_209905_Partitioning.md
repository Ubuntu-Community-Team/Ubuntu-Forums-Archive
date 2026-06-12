---
title: "Partitioning"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by djw on 2006-07-05
I've heard that there have been problems partitioning while installing.  Is it possible to partition my remaining 58 gigs of my hard drive in the livecd?  If so how would I get Ubuntu to use those pre-partitioned parts during Install; or is it easier then I think it is?

---

### Post by Ptero-4 on 2006-07-05
AFAIK. The liveCD partitioner can partition your disk OK. What it cannot do is resize NTF$ partitions.

---

### Post by aysiu on 2006-07-06
[QUOTE=Ptero-4]AFAIK. The liveCD partitioner can partition your disk OK. What it cannot do is resize NTF$ partitions.[/QUOTE]
Could have fooled me--GParted theoretically can resize NTFS just as much as it can resize Ext3.

Now, does GParted always work the way it's supposed to? No, of course not. I think it's a lousy partitioner, but it is supposed to resize NTFS, FAT32, Ext3, Reiserfs...

Personally, I prefer and have never had problems with PCLinuxOS' DiskDrake partitioner. It was worth downloading another distro just to have a reliable partitioning tool.

---

### Post by rcarring on 2006-07-06
I found puppylinux's gparted will happily resize etc ide disks but have not tried ide disk with ntfs. Of course it doesn't work with scsi disks.

I would however go with Disk Drake, per aysiu's suggestion.

---

### Post by djw on 2006-07-06
I'm planning on making a fat32 partition for use for both Windows and Ubuntu.  Now what would I mount this partition as when installing?  I'm a linux noob so what is the difference between / and /home?

---

### Post by aysiu on 2006-07-06
You can mount it wherever you want. When I mount my Windows partition, I mount it at /windows. Some people do /music if it's a music partition. Others do /media/windows.

The difference between / and /home--/home is a folder within /

It's like asking the difference between C:\ and C:\Documents and Settings

---

### Post by az on 2006-07-06
[QUOTE=aysiu] prefer and have never had problems with PCLinuxOS' DiskDrake partitioner. It was worth downloading another distro just to have a reliable partitioning tool.[/QUOTE]
They all use the same software - GNU parted and associated tools.  They are all the same.

---

### Post by aysiu on 2006-07-06
[QUOTE=azz]They all use the same software - GNU parted and associated tools.  They are all the same.[/QUOTE]
Maybe in theory, but I haven't found that to be so in practice.

Also, even though the actual partitioning tools may be the same, the GUI that lies on top of that and the user interface are different. Sometimes GParted greys out options that should not be greyed out. That has nothing to do with the partitioning *tool*. That's a user interface error.

In either case, the end-user cares only about what works or not.

---

