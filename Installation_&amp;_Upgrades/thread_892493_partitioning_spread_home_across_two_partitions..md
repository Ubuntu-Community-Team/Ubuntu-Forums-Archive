---
title: "partitioning: spread /home across two partitions."
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by HunkirDowne on 2008-08-17
I am trying to remember(?)/figure out how to spread a directory (folder) across two partitions.  I believe I did this several years ago with RedHat and if so it was terribly easy--seemingly so trivial I didn't take notes.

Was I dreaming?

Specifics:
I have four operating systems on one computer.  WinXP, and three different instances of Ubuntu (feisty, feisty-UCE, hardy).  I want to blow away feisty after testing and configuring hardy enough to use it more than all the others combined.  Once I do that, I will reclaim some precious space on my laptop.  I'd like to reassign the space mostly to my /home directory but also to give myself a little more breathing room for /boot.

Here are my partitions:
```

$ sudo fdisk -ul

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x82bd82bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31149260    15574599    7  HPFS/NTFS
/dev/sda2        31455270   117210239    42877485    5  Extended
/dev/sda3        31150035    31326749       88357+  83  Linux
/dev/sda4        31326750    31455269       64260   83  Linux
/dev/sda5        31455333    52468289    10506478+  83  Linux
/dev/sda6        52468353    62974799     5253223+  83  Linux
/dev/sda7        62974863    71360729     4192933+  83  Linux
/dev/sda8        71360793   113017274    20828241   83  Linux
/dev/sda9       113017338   117210239     2096451   82  Linux swap / Solaris

Partition table entries are not in disk order

```

These are my current hardy partition assignments:
```

~$ mount
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda4 on /boot type ext2 (rw,relatime)
/dev/sda8 on /home type reiserfs (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/hunkirdowne/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hunkirdowne)

```

/dev/sda5=/ for feisty-UCE so it stays.
/dev/sda6=/ for feisty (std) so it goes.

After looking at my notes, it would appear that sda6 is the only one that will be freed up. 

Here's my current disk-space for mounted partitions (1=xp, 9=swap):
```

$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7              4159844   2867492   1082708  73% /
varrun                  257508       112    257396   1% /var/run
varlock                 257508         0    257508   0% /var/lock
udev                    257508        96    257412   1% /dev
devshm                  257508        12    257496   1% /dev/shm
lrm                     257508     39760    217748  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda4                60217     46813     10191  83% /boot
/dev/sda8             20827584  16863468   3964116  81% /home
gvfs-fuse-daemon       4159844   2867492   1082708  73% /home/hunkirdowne/.gvfs
/dev/sda3                85549     19739     61393  25% /media/sda3
/dev/sda5             10506104   9409188   1096916  90% /media/sda5
/dev/sda6              5253016   3727512   1525504  71% /media/sda6

```

---

### Post by az on 2008-08-17
What you are thinking about is LVM, logical volume management.

You can start here:
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

