---
title: "gparted won't set root"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by fopetesl on 2007-01-06
Am in the middle of installing 6.10 over Windoze.  Trying to use gparted to set partitions:```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         638     5124703+   b  W95 FAT32
/dev/sda2             639        4709    32700307+   c  W95 FAT32 (LBA)
/dev/sda3            4710       30401   206370990    f  W95 Ext'd (LBA)
/dev/sda5            4710        7259    20482843+   b  W95 FAT32
/dev/sda6            7260        9809    20482843+  83  Linux
/dev/sda7            9810       10071     2104483+  82  Linux swap / Solaris
/dev/sda8           10072       12621    20482843+  83  Linux
/dev/sda9           12622       30401   142817818+  83  Linux
```
Have set ..sda6 as "/", ..sda7 stays as swap, ..sda8 as /boot and ..sda9 as /home.
Left the FAT partitions as is.  All I get (repeatedly) is  [SIZE="4"]! No root file system[/SIZE]
The 82/82 partitions were created by SUSE SLED10 x64 which trashed my MBR so I couldn't boot at all.](*,)

---

### Post by logos34 on 2007-01-06
Make '/' (root) a PRIMARY partition.

---

### Post by fopetesl on 2007-01-07
> logos34  	Make '/' (root) a PRIMARY partition.
It's REALLY wierd.  I used Acronis to (re)set the "/" partition as primary.
Now Ubuntu install gparted doesn't see ANY partions on the disk but:```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         638     5124703+   b  W95 FAT32
/dev/sda2             639        4709    32700307+   c  W95 FAT32 (LBA)
/dev/sda3            4710       30401   206370990    f  W95 Ext'd (LBA)
/dev/sda4            7260        9809    20482871+  83  Linux
/dev/sda5            4710        7259    20482843+   b  W95 FAT32
/dev/sda6            9810       10071     2104483+  82  Linux swap / Solaris
/dev/sda7           10072       12621    20482843+  83  Linux
/dev/sda8           12622       30401   142817818+  83  Linux
```
... sees them all!
Where to now?:confused:

---

### Post by fopetesl on 2007-01-07
Well I solved it but not in the way I'd like . . .  I installed Mandriva 2007 without a hitch.
Windoze works, LINUX works so I guess that there's a neat bug in the Ubuntu install.
Shame - I like:D Ubuntu

---

### Post by logos34 on 2007-01-07
> /dev/sda3            4710       30401   206370990    f  W95 Ext'd (LBA)
/dev/sda4            7260        9809    20482871+  83  Linux
/dev/sda5            4710        7259    20482843+   b  W95 FAT32
/dev/sda6            9810       10071     2104483+  82  Linux swap / Solaris
/dev/sda7           10072       12621    20482843+  83  Linux
/dev/sda8           12622       30401   142817818+  83  Linux

Looks like all it did was change the order inside the ext'd.

Never used acronis, but you may need to do more than just 'reset' it as a primary (can't have a primary inside an extended--maybe it's confused and defaulting to a logical).  Try to delete / first, shrink the extended partition by the size of the just deleted root, and then create a new primary outside the extended.

Ubunut is such a great distro...don't give up yet!

---

### Post by underonesun on 2007-01-07
> **fopetesl said:**
> Am in the middle of installing 6.10 over Windoze.  Trying to use gparted to set partitions:```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         638     5124703+   b  W95 FAT32
/dev/sda2             639        4709    32700307+   c  W95 FAT32 (LBA)
/dev/sda3            4710       30401   206370990    f  W95 Ext'd (LBA)
/dev/sda5            4710        7259    20482843+   b  W95 FAT32
/dev/sda6            7260        9809    20482843+  83  Linux
/dev/sda7            9810       10071     2104483+  82  Linux swap / Solaris
/dev/sda8           10072       12621    20482843+  83  Linux
/dev/sda9           12622       30401   142817818+  83  Linux
```
Have set ..sda6 as "/", ..sda7 stays as swap, ..sda8 as /boot and ..sda9 as /home.
Left the FAT partitions as is.  All I get (repeatedly) is  [SIZE="4"]! No root file system[/SIZE]
The 82/82 partitions were created by SUSE SLED10 x64 which trashed my MBR so I couldn't boot at all.](*,)

It's because the installer is broken.  The alternate install CD does work.  It is a shame that there's a need for an alternate installer, but I was grateful that someone made the alternate.

---

### Post by fopetesl on 2007-01-08
Hi logos34. TFT but note the layout with everything running OK
```
[root@localhost Desktop]# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         638     5124703+   b  W95 FAT32
/dev/sda2             639        4709    32700307+   c  W95 FAT32 (LBA)
/dev/sda3            4710       30401   206370990    f  W95 Ext'd (LBA)
/dev/sda4            7260        9809    20482871+  83  Linux
/dev/sda5            4710        7259    20482843+   b  W95 FAT32
/dev/sda6            9810       10071     2104483+  82  Linux swap / Solaris
/dev/sda7           10072       12621    20482843+  83  Linux
/dev/sda8           12622       30401   142817818+  83  Linux
```Looks remarkably similar to the after-set-root-primary-but-installer-still-fails. No?  I appreciate your comment.  Really.  But although I should have mentioned it I had already gone through the delete-recreate partitions routine.:neutral: 

underonesun, TFT also.  I guessed, (since Mandriva went without a hitch), but where is it publicised?  Seems that there will be quite a few bods like myself who are suffering needlessly:cry:   When I've completed the current project I _will_ go back to Ubuntu:)

---

