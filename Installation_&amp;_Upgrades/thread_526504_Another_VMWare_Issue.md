---
title: "Another VMWare Issue"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by utahcon on 2007-08-15
I have VMWare Player installed, and configured to run my windows instance from my harddrive, however I when the instance starts it goes to my grub loader, which makes sense since it is the loader now. But it freezes and dies, I was wondering if my vmdk should be different?

```
# Disk DescriptorFile
version=1
CID=9428f535
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "windowsxp.mbr" 0
RW 156249999 FLAT "/dev/sda" 63

# The Disk Data Base 
#DDB 

ddb.toolsVersion = "6530"
ddb.adapterType = "scsi"
ddb.virtualHWVersion = "4"
ddb.geometry.sectors = "63"
ddb.geometry.heads = "255"
ddb.geometry.cylinders = "9726"
```

My windows install is on sda and my ubuntu is on sdb

Here is what I get from parted when I run it for unit s and unit cyl for sda:
sda :: unit s
```
Disk /dev/sda: 156249999s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start    End         Size        Type     File system  Flags
 1      63s      112454s     112392s     primary  fat16
 2      112455s  156232124s  156119670s  primary  ntfs         boot
```

sda :: unit cyl
```
Disk /dev/sda: 9726cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 9726,255,63.  Each cylinder is 8225kB.
Partition Table: msdos

Number  Start  End      Size     Type     File system  Flags
 1      0cyl   6cyl     6cyl     primary  fat16
 2      7cyl   9724cyl  9718cyl  primary  ntfs         boot
```

and the same for sdb

sdb :: unit s
```
Disk /dev/sdb: 488397167s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      63s         476246924s  476246862s  primary   ext3         boot
 2      476246925s  488392064s  12145140s   extended
 5      476246988s  488392064s  12145077s   logical   linux-swap

```

sdb :: unit cyl
```
Disk /dev/sdb: 30401cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 30401,255,63.  Each cylinder is 8225kB.
Partition Table: msdos

Number  Start     End       Size      Type      File system  Flags
 1      0cyl      29644cyl  29644cyl  primary   ext3         boot
 2      29645cyl  30400cyl  756cyl    extended
 5      29645cyl  30400cyl  755cyl    logical   linux-swap
```

I appreciate any help you can offer in solving this!

---

### Post by MandN on 2007-08-16
I don't know if this will help but I use a floppy image to boot my windows vm. I used this how to, [http://www.motin.eu/www/mirror/physvmware/]("http://www.motin.eu/www/mirror/physvmware/"),
to get mine running. There is a section on making a boot disk.

---

