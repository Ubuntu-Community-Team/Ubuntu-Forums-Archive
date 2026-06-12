---
title: "New Harddrive"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by JustAnotherVagueAnon on 2008-05-28
I have just installed and formatted a new harddrive in fat32 using gparted. I am dual booting vista and hardy and the partition is recognized in vista but I don't know how to set a mount point in ubuntu. My new drive is sda. I have a backup partition and data partition set up on sda.

EDIT: My main drive is for the OSs and program files and the new drive is for backup and shared files.

output of **sudo fdisk -l:**
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfd9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38391   308375676    b  W95 FAT32
/dev/sda2           38392       38913     4192965   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19190   154139719+   7  HPFS/NTFS
/dev/sdb2           19191       19197       56227+  83  Linux
/dev/sdb3           29263       30401     9149017+   7  HPFS/NTFS
/dev/sdb4           19198       29262    80847112+   5  Extended
/dev/sdb5           19198       19445     1992028+  82  Linux swap / Solaris
/dev/sdb6           19446       29262    78855021   83  Linux

Partition table entries are not in disk order


```

Here's how my fstab looks:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a0369f42-e602-4e22-939f-85c97405ed65 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=83113965-0e0c-485a-985b-fb7360801fa8 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=22be3a91-936b-45f8-a61f-b3e66b9126d6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I know creating an entry point has something to do with fstab, but i'm not sure what to put since the content of it is different than expected.

---

### Post by ruha on 2008-05-28
have a look at this: [http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/]("http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/")

---

