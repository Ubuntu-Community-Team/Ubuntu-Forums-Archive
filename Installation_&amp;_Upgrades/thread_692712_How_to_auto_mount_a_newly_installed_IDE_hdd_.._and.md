---
title: "How to auto mount a newly installed IDE hdd .. and some other mounting questions"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by keplenk on 2008-02-10
Hi all,

I'm new to ubuntu and I'm loving it!

The questions that I'll be asking are not problems.  For pros, these questions are probably too noobish :)

I know, I could try to do some searches in google or forums but I'm having difficulties auto mounting OTHER partitions and Newly installed hdds.

Ok, ill start:

I have 2 hard drives.  One SATA and one IDE.  Both are 80gb.  My SATA (OS drive) contains 3 Oses.

My SATA hdd contains 3 partitions:

1) Windows XP (NTFS)
2) Leopard 10.5 OSX86 (HFS+)
3) Ubuntu 7.10 (ext3)

My 2nd IDE hdd only has 1 partition and its NTFS

My system is configured as AHCI in BIOS.  (XP was installed with Hack ICH9 drives)

Everything is working fine.  I triple boot using Grub 1.5.

Initially, when I installed my OSes.  My IDE hdd (data) was removed.  I just plugged it in after installing all 3 oses.

When I boot to Ubuntu I only see one hard drive automounted (?) in the Desktop named sda1 (Windows XP partition)

It doesnt see my Leopard and IDE hdd at startup.  On the other hand, If I go to Nautilus > Computer > I can see all of them (looks like a USB icon) .. If I right-click those and click "Mount Volume". Its seems ok. But they are all READ-ONLY.  Changing permissions gives me an error.

1) How can I auto-mount my MacOsX Leopard partition and my 80gb IDE data hdd?

2) I was hoping to change the "read-only" access to "Read and Write" for both Leopard and IDE (NTFS) data. 

I dont know if this is possible to my Leopard partition, but just let me know if its impossible.

*BTW, I can write to my Windows XP NTFS partition without any problems.

These are my fstab and fdisk -l :

fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6aac97e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4dfa4df9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sdb2            5738        8287    20482875   af  Unknown
/dev/sdb3            8288        9664    11060752+  83  Linux
/dev/sdb4            9665        9729      522112+  82  Linux swap / Solaris
```


fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2350148d-7532-44fc-a524-4671004079f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=12EC3CDFEC3CBEB3 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=47AD-B9F6  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=a6275e5f-478e-4e9c-8b12-0bdf1ebcd58a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0      
```

Thank you very much!!!

---

### Post by keplenk on 2008-02-10
bump!

Anyone?

Thanks :D

---

### Post by keplenk on 2008-02-11
bump # 2

---

### Post by Salpiche on 2008-02-11
have you tried creating a mount point on media and then adding the drive to fstab to mount to that mount point?

```

sudo mkdir /media/your-added-drive

```

then 
```

sudo gedit /etc/fstab

```

on fstab add a line 
```

/dev/your-added-drive      /media/your-added-drive  NTFS(if it is NTFS or HSF+) defaults 0 0 

```

then
```

sudo mount -a

``` 
to mount all drives


if you want read-write make sure that you do a 
```

sudo chmod 0777 /media/your-added-drive

```

---

