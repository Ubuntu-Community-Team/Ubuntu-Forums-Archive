---
title: "How to remove 1 ubuntu installed from 2?"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by tyling81 on 2010-03-30
Hi, all, for my personal curiosity I had installed two ubuntu  in my netbook, ASUS EEE PC 901. With very limited hard drive capacity available (12 GB), is that a way to remove one of the ubuntu I'd installed? As it could free up more storage? Please advise, thanks!

---

### Post by bigsmitty64 on 2010-03-30
Yes, there is always a way. :) But I'm sure people are gonna want to know which 2 versions you installed, and in what order you installed them.  I'm not real familiar with gparted (drive partitioner)yet but it works well I'm told, and is already preinstalled (on most). I believe its a matter of figuring out which partition is the one with the distro you want to remove and then shrinking that partition. But don't do anything until you hear from some other folks here who may have way more to offer. I'm still learning this also but have been a few rounds with it! But I always had windows to fall back on. Not anymore!

I'll follow this thread and learn right along with you.

---

### Post by tyling81 on 2010-03-30
That sound silly, perhaps. But I had installed the same version of Ubuntu(9.04) in my Netbook, Therefore It doesn't matter which one should be removed, and my objective is to release more storage. Thank for you opinion/advices Big Smith!

---

### Post by oldfred on 2010-03-30
Only one of them probably the last install is in the MBR for booting. If you delete that one then you will have to use the liveCD to reinstall grub. If you know in advance you can reinstall grub from the copy you want to keep and not have any issues.

Which to delete may depend on where they are on the drive.

```
sudo fdisk -l 
```

---

### Post by tyling81 on 2010-03-30
Hi Fred, I run this command sudo fdisk -l
it shown as below

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd00c2c26

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  82  Linux swap / Solaris

Disk /dev/sdb: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ce62d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         607     4875696   83  Linux
/dev/sdb2             608         981     3004155    5  Extended
/dev/sdb5             934         981      385528+  82  Linux swap / Solaris
/dev/sdb6             608         911     2441817    b  W95 FAT32
/dev/sdb7             912         933      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order


If I would like to remove /dev/sda
What command should I used to ensure that the free up storage will mount into my /dev/sdb

Thanks

---

### Post by oldfred on 2010-03-30
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

$ sudo mkdir /Data
$ sudo mount /dev/sda1 /Data
where sda1 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions.

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

This is my entry in fstab to mount my data partition. I had to create the mount points fred & data in local. You can mount anywhere you want either directly in /home or other places.
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2

---

