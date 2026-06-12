---
title: "unknown filesystem type 'LVM2_member"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by das001 on 2008-01-02
In attempting to upgrade from 7.4 to 7.10 something went wrong and I can no long access the drive.  Specifically /dev/sdb5 is the problem.  I assume it was originally an ext3 filesystem.  

das@ubuntu002:~$ sudo fdisk -l
[sudo] password for das:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00034015

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59321   476495901   83  Linux
/dev/sda2           59322       60801    11888100    5  Extended
/dev/sda5           59322       60801    11888068+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49bf21e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32       30401   243947025    5  Extended
/dev/sdb5              32       30401   243946993+  8e  Linux LVM

---

### Post by paulsam on 2008-01-05
you need install lvm2

apt-get install lvm2

then reboot, and use next commands for view partitions:
   #pvs
it's display your partition lvm, example:
   /dev/sdc5  intranet lvm2 a-   372,37G    0

then display information of partition example: 
   # lvdisplay /dev/intranet

--- Logical volume ---
  LV Name                /dev/intranet/root
  VG Name                intranet
...

then mount your partition with logical volume, example:
   
# mount /dev/mapper/intranet-root /mnt/disco2

---

### Post by das001 on 2008-01-06
paulsam,

Thank you very much.Your instructions worked perfectly.

DAS

---

### Post by jtravnick on 2008-01-07
I am also trying to get an lvm partition mounted am having problems though did fdisk -l than pvs thought I got the info for what I needed to put in fstab but it is not working,

jim@jim-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e09c8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d899d89

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          25      200781   83  Linux
/dev/hdb2              26       14593   117017460   8e  Linux LVM
jim@jim-desktop:~$ pvs
jim@jim-desktop:~$ sudo pvs
  PV         VG         Fmt  Attr PSize   PFree 
  /dev/hdb2  VolGroup01 lvm2 a-   111.59G 32.00M
jim@jim-desktop:~$ sudo lvdisplay /dev/VolGroup01
  --- Logical volume ---
  LV Name                /dev/VolGroup01/LogVol00
  VG Name                VolGroup01
  LV UUID                MSUc9J-TAjc-NuPK-IOyj-g3e0-39cU-KnyDCP
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                110.56 GB
  Current LE             3538
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0
   
  --- Logical volume ---
  LV Name                /dev/VolGroup01/LogVol01
  VG Name                VolGroup01
  LV UUID                7ylHxT-2LRy-vvfX-uHRZ-1ar9-0U91-yRjqIU
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                1.00 GB
  Current LE             32
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:1
   
jim@jim-desktop:~$ sudo mount -a
mount: unknown filesystem type 'VolGroup01'
jim@jim-desktop:~$ 


Below is what I have in fstab as of right now:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=47cb1267-f6df-46f8-9214-ddaa127dace8 /               ext3    defaults,erro$
# /dev/hda5
UUID=9d0cdcb3-7b5e-40b6-8d6c-7975bea30454 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1 /storage ext3 defaults 0 0
/dev/hdb2 /fedora VolGroup01 defaults 0 0

Whats weard at least to me is hdb1 mounts fine I did change the make folder to be fedora so I can find it better.

---

