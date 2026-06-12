---
title: "Adding an external HD partition to LVM"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by Arminius Chieftan on 2011-03-09
I have  an external hard drive (500GB)  that I partitioned and would like to use the second partition to add extra storage space on the computer running 10.04 server (100 GB HD). /dev/sdc2 is the partition I would like to add via LVM to the 100GB HD; dev/sdc1 contains data I already use.

```
root@SERVER1:# blkid
/dev/sda1: UUID="3fbfabe1-7173-4f83-9c9d-08effabd0a25" TYPE="ext2" 
/dev/sda5: UUID="Wq94xh-ZDhl-XG0Q-X4Ic-AxUZ-A6Hr-TQTZYx" TYPE="LVM2_member" 
/dev/mapper/SERVER1-root: UUID="3f0e70c2-ade1-438f-97fb-744660693554" TYPE="ext4" 
/dev/mapper/SERVER1-swap_1: UUID="3bb3387a-3f91-41ff-af54-4976cd24c3fa" TYPE="swap" 
/dev/sdc1: LABEL="Maxtor" UUID="1f9bd8f1-8ed1-49f3-a639-1d9f7c7582e2" TYPE="ext4" 
``````
root@SERVER1:~# lvscan
  ACTIVE            '/dev/SERVER1/root' [91.33 GiB] inherit
  ACTIVE            '/dev/SERVER1/swap_1' [1.40 GiB] inherit

``````
root@SERVER1:~# fdisk -l

Disk /dev/sda: 99.8 GB, 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060efb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       12137    97239041    5  Extended
/dev/sda5              32       12137    97239040   8e  Linux LVM

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064546

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       28820   231495648+  83  Linux
/dev/sdc2           28821       60673   255859222+   5  Extended

```

```
root@SERVER1:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/SERVER1-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=3fbfabe1-7173-4f83-9c9d-08effabd0a25 /boot           ext2    defaults        0       2
/dev/mapper/SERVER1-swap_1 none            swap    sw              0       0
UUID=1f9bd8f1-8ed1-49f3-a639-1d9f7c7582e2 /mnt/fire ext4 defaults 0 0

```

---

### Post by Arminius Chieftan on 2011-03-09
I think I solved this... first make sure that the partition on the external HD is formatted correctly. I used GParted to format the partition as a Linux LVM filesystem.

Once I connected the external HD to the 10.04 server I ran fdisk -l to ensure that the partition was recognised, the new partition was label /dev/sdd5. 

I then used the **vgextend** command to add the new partition on /dev/sdd5 to the Volume Group SERVER1 that already existed on the server.
```
root@SERVER1:~# vgextend SERVER1 /dev/sdd5
  No physical volume label read from /dev/sdd5
  Wiping swap signature on /dev/sdd5
  Physical volume "/dev/sdd5" successfully created
  Volume group "SERVER1" successfully extended

```And this was the outcome.

```
root@SERVER1:~# fdisk -l

Disk /dev/sda: 99.8 GB, 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060efb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       12137    97239041    5  Extended
/dev/sda5              32       12137    97239040   8e  Linux LVM

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064546

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       28820   231495648+  83  Linux
/dev/sdd2           28821       60673   255859222+   5  Extended
/dev/sdd5           28821       60673   255857664   82  Linux swap / Solaris

```

---

