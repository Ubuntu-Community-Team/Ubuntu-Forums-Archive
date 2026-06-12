---
title: "Grub doesnt see vista ultimate."
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by ew16301 on 2007-09-04
Im trying to do a dual boot of Vista Ultimate and Ubuntu 7.10, tribe 5. I install vista first, and I partition 2 drives as NTFS (1 for the OS, 1 for extra stuff). I leave the rest blank. Once vista is installed I then add Ubuntu, using guided partitioning to use the rest of the free space. When it installs and boots, grub doesnt list vista at all.

Here are the results of:

```
sudo fdisk -l
```

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5100    40960000    7  HPFS/NTFS
/dev/sda2            5100       16573    92160000    7  HPFS/NTFS
/dev/sda3   *       16574       19332    22161667+  83  Linux
/dev/sda4           19333       19457     1004062+   5  Extended
/dev/sda5           19333       19457     1004031   82  Linux swap / Solaris

```

and

```
grub> geometry (hd0)
```

```

drive 0x80: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

```

Ive also editied my menu.lst to use:

```

title Vista0
rootnoverify (hd0, 0)
makeactive
chainloader + 1

```

which comes up as "Unrecognized device string". Any help would be appricated.

---

### Post by confused57 on 2007-09-04
I believe you have an extra space in (hd0, 0) and chainloader + 1,   should be:
```
title Vista0
rootnoverify (hd0,0)
makeactive
chainloader +1
```

---

### Post by soma4me on 2007-09-04
Hi,

Base on your partition list, partition 0 appears to be Vista Recovery disk, partition 1 is where Vista resides.    May be you should try this

> [FONT="Courier New"]rootnoverify (hd0,1)[/FONT]

---

### Post by Bethrine on 2007-09-04
> **soma4me said:**
> Hi,

Base on your partition list, partition 0 appears to be Vista Recovery disk, partition 1 is where Vista resides.    May be you should try this

I'm a newb, but I just got vista to boot and I use (hd0,0) to boot it and, and, yes, it appears to be the "backup" . Hope that is helpful.

---

