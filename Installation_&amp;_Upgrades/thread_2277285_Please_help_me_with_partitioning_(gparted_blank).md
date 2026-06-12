---
title: "Please help me with partitioning (gparted blank)"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by HCLivess on 2015-05-07
Hello, I have this device Tronsmart Draco AW80 (armhf) and I have no idea how to make use of the actual internal eMMC 32GB card. I tried removing all partitions except the boot yesterday, but it resulted in a system failure. Can someone please give me a guide on how to proceed in this particular case? Other people are also asking, and we are just noobs with this. Thank you very much! When I try open gparted, it says that everything is unallocated, so I cannot use that.
[FONT=arial]
```
[/FONT]root@allwinner:/home/linaro# fdisk -l

Disk /dev/mmcblk0: 31.3 GB, 31268536320 bytes
1 heads, 16 sectors/track, 3816960 cylinders, total 61071360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *    10657792    61136895    25239552    b  W95 FAT32
/dev/mmcblk0p2           73728      106495       16384    6  FAT16
/dev/mmcblk0p3               1    10551296     5275648    5  Extended
/dev/mmcblk0p5          106496      139263       16384   83  Linux
/dev/mmcblk0p6          139264      172031       16384   83  Linux
/dev/mmcblk0p7          172032    10657791     5242880   83  Linux


Partition table entries are not in disk order


Disk /dev/mmcblk0boot1: 4 MB, 4194304 bytes
4 heads, 16 sectors/track, 128 cylinders, total 8192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mmcblk0boot1 doesn't contain a valid partition table


Disk /dev/mmcblk0boot0: 4 MB, 4194304 bytes
4 heads, 16 sectors/track, 128 cylinders, total 8192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mmcblk0boot0 doesn't contain a valid partition table
root@allwinner:/home/linaro#


[FONT=arial]
```

```
[COLOR=#666666]root@allwinner:/home/linaro# mount
/dev/root on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
devtmpfs on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
selinuxfs on /sys/fs/selinux type selinuxfs (rw,relatime)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=linaro)
/dev/mmcblk0p2 on /media/linaro/Volumn type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)[/COLOR]
```
```
[COLOR=#666666]root@allwinner:/home/linaro# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       5.0G  1.8G  3.0G  38% /
devtmpfs        1.4G   12K  1.4G   1% /dev
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            273M  348K  273M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.4G     0  1.4G   0% /run/shm
none            100M  4.0K  100M   1% /run/user
/dev/mmcblk0p2  128M  7.2M  121M   6% /media/linaro/Volumn[/COLOR]
```

[/FONT]```
root@allwinner:/home/linaro# parted /dev/mmcblk0
GNU Parted 2.3
Using /dev/mmcblk0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Error: Can't have a partition outside the disk!
(parted)
```

---

### Post by dino99 on 2015-05-08
A few things grabbed around eMMc

[http://www.cnx-software.com/2014/11/09/tronsmart-draco-aw80-meta-review/](http://www.cnx-software.com/2014/11/09/tronsmart-draco-aw80-meta-review/)
[http://www.cnx-software.com/2015/02/04/latest-ubuntu-14-10-image-for-tronsmart-draco-aw80-supports-hardware-video-decoding/](http://www.cnx-software.com/2015/02/04/latest-ubuntu-14-10-image-for-tronsmart-draco-aw80-supports-hardware-video-decoding/)

[http://www.3daudiosense.com/blog/beaglebone-black-building-kernel-and-deploying-it-with-new-system-distributionflashing-onboard-emmc-from-microsd-card](http://www.3daudiosense.com/blog/beaglebone-black-building-kernel-and-deploying-it-with-new-system-distributionflashing-onboard-emmc-from-microsd-card)
[http://www.eliteraspberries.com/blog/2013/09/installing-debian-on-the-beaglebone-black.html](http://www.eliteraspberries.com/blog/2013/09/installing-debian-on-the-beaglebone-black.html)

---

### Post by HCLivess on 2015-05-08
I found this guide and thought it would be useful, but I am not sure how exactly to use it, because my system has a different partitioning and I don't want to delete anything important in the process. Do you think I could use it, do you think any of these partitions can be removed? From the sudo history I see that the Chinese tried to unmount/rm some of these without success.

[http://jan.alphadev.net/blog/2013/growing-the-rpi-root-partition/](http://jan.alphadev.net/blog/2013/growing-the-rpi-root-partition/)

---

### Post by dino99 on 2015-05-08
armhf is heavily developed, so following a too old thread (2013) can bring some ideas but i'm feeling that lot of things have also changed since that date. So better to google around recent posts (google 'search tools' > 'last year') and use recent kernels as they also add android support

---

### Post by HCLivess on 2015-05-08
I thought anyone with Linux experience could solve this just by looking at it :D

---

### Post by grahammechanical on 2015-05-08
I have a little Linux experience and all I am is confused. I see this

> I tried removing all partitions except the boot yesterday, but it resulted in a system failure.

It is my understanding that removing or deleting all partitions except the boot partition would naturally mean that the OS was deleted. And that would most definitely result in system failure. But what kind of system failure? You do not say. Failure to get a boot menu? Failure to load to a login screen? Failure to load to a working desktop.

But you also show printouts from commands that show that you have partitions. So, I am confused. How can there be partitions when all partitions but boot have been removed? On the other hand, if all partitions were indeed removed then Gparted would indeed show a blank as reported in the thread title.

It is clear that my understanding of Linux is too little to help me understand the situation and what you are trying to do. I am, after all, just another Ubuntu user.

Regards.

---

### Post by HCLivess on 2015-05-08
> **grahammechanical said:**
> I have a little Linux experience and all I am is confused. I see this



It is my understanding that removing or deleting all partitions except the boot partition would naturally mean that the OS was deleted. And that would most definitely result in system failure. But what kind of system failure? You do not say. Failure to get a boot menu? Failure to load to a login screen? Failure to load to a working desktop.

But you also show printouts from commands that show that you have partitions. So, I am confused. How can there be partitions when all partitions but boot have been removed? On the other hand, if all partitions were indeed removed then Gparted would indeed show a blank as reported in the thread title.

It is clear that my understanding of Linux is too little to help me understand the situation and what you are trying to do. I am, after all, just another Ubuntu user.

Regards.

Hello. I re-flashed the system to have it brand new. I wrongly assumed that boot=OS. GParted does not work when partitions are there.

---

### Post by yancek on 2015-05-08
The output you posted in the original post indicated there was no valid partition table and GParted does work when there are partitions.  That is what the purpose of the software is.  You can create a valid partition table, create, delete and resize partitions as well as move them.  You can't do it when the partitions are mounted and you can easily unmount from GParted.

---

### Post by HCLivess on 2015-05-08
Good to know, I thought that the error with invalid parition table was somehow connected to the fact that the partitions are on the eMMC. Is there an easy way to fix the parition table?

---

### Post by HCLivess on 2015-05-09
this command looks good, ill try mount mmcblk0p1  

root@allwinner:/var/spool/cron/crontabs# lsblk
NAME         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
mmcblk0boot0 179:16   0     4M  1 disk
mmcblk0boot1 179:32   0     4M  1 disk
mmcblk0      179:0    0  29.1G  0 disk
&#9500;&#9472;mmcblk0p1  179:1    0    24G  0 part
&#9500;&#9472;mmcblk0p2  179:2    0    16M  0 part /media/linaro/Volumn
&#9500;&#9472;mmcblk0p3  179:3    0     1K  0 part
&#9500;&#9472;mmcblk0p5  179:5    0    16M  0 part
&#9500;&#9472;mmcblk0p6  179:6    0    16M  0 part
&#9492;&#9472;mmcblk0p7  179:7    0     5G  0 part /

---

### Post by HCLivess on 2015-05-10
cannot mount this, im helpless

---

