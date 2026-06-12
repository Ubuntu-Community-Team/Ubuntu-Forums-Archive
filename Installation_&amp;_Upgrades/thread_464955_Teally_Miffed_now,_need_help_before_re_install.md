---
title: "Teally Miffed now, need help before re install"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by Borg on 2007-06-05
After the 'updates' that messed everyone around I still have problems when running the .15 kernel

Seems there ate a lot of files missing and boot problems, something about a special device that wont mount and no swap file.

I have to Ctrl+D to start.

Anyway I have decided it need a clean re install

I have 3 partition 

1Ubunto
2 Home
3 Swap

I run Xfce

Is there any way to remove or not install Konkorer browser as it's not what I like.

Is there ANY way of saving my settings, ie font sizes and stuff, before I re install or do I have to set everything up again.

Also has the offending updates been removed before I re update the clean install

Thanks

---

### Post by taurus on 2007-06-05
I bet it has something to do with /dev/sda and /dev/hda.  Do you have a PATA harddrive on your machine or do you have a SATA drive?

---

### Post by Borg on 2007-06-05
PATA IDE drives

---

### Post by taurus on 2007-06-05
Can you post

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Borg on 2007-06-05
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/hda5            2551        3825    10241406   83  Linux
/dev/hda6            3826        5100    10241406   83  Linux
/dev/hda7            5101        5361     2096451   82  Linux swap / Solaris
/dev/hda8            5362        9729    35085928+   7  HPFS/NTFS

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       15855   127355256    b  W95 FAT32
/dev/hdb2           15856       30515   117756418+   b  W95 FAT32
r@r-desktop:~$

---

### Post by taurus on 2007-06-05
How about

```
cat /etc/fstab
```

---

### Post by Borg on 2007-06-05
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda5 :
UUID=5fc879f1-83a9-402b-b46d-e5855414b419 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=1408F47508F456E8 /media/hda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hda6 :
UUID=9c4535e2-f9f3-4dd4-9cb5-aa2c40a9f314 /media/hda6 ext3 defaults 0 2
# Entry for /dev/hda8 :
UUID=8E68162368160A9B /media/hda8 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hdb1 :
UUID=4647-7E16 /media/hdb1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hdb2 :
UUID=443D-BBD7 /media/hdb2 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hdd1 :
UUID=70dd33fd-1f08-477d-a5ce-1e16ebdd4c8a /media/hdd1 ext3 defaults 0 2
# Entry for /dev/hda7 :
UUID=0f7949c8-9045-4675-b651-153ab3f6d403 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by Borg on 2007-06-05
Anyone ?

---

### Post by taurus on 2007-06-05
> **Borg said:**
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda5 :
UUID=5fc879f1-83a9-402b-b46d-e5855414b419 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=1408F47508F456E8 /media/hda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hda6 :
UUID=9c4535e2-f9f3-4dd4-9cb5-aa2c40a9f314 /media/hda6 ext3 defaults 0 2
# Entry for /dev/hda8 :
UUID=8E68162368160A9B /media/hda8 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hdb1 :
UUID=4647-7E16 /media/hdb1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hdb2 :
UUID=443D-BBD7 /media/hdb2 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hdd1 :
UUID=70dd33fd-1f08-477d-a5ce-1e16ebdd4c8a /media/hdd1 ext3 defaults 0 2
# Entry for /dev/hda7 :
UUID=0f7949c8-9045-4675-b651-153ab3f6d403 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

If I were you, I would try to use the actual partition names instead of UUIDs to see if Ubuntu can boot with the latest kernel now.

```
sudo nano -B /etc/fstab
```

```

proc /proc proc defaults 0 0
# Entry for /dev/hda5 :
/dev/hda5 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hda6 :
/dev/hda6 /media/hda6 ext3 defaults 0 2
# Entry for /dev/hda8 :
/dev/hda8 /media/hda8 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hdb1 :
/dev/hdb1 /media/hdb1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hdb2 :
/dev/hdb2 /media/hdb2 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hdd1 :
/dev/hdd1 /media/hdd1 ext3 defaults 0 2
# Entry for /dev/hda7 :
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

```

---

### Post by BorgCymru on 2007-06-05
Well I decided to do a clean install, but as per my other post that seemed to be hit by problems after the update as well.

---

