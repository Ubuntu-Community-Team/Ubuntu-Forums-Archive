---
title: "Insallation issue"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by tronacus86 on 2013-12-26
Hello, Im new to Linus and what to check out Ububtu on and old laptop that had Vista on it. I created a bootable USB drive and installed Ubuntu on the laptop and it worked great. I then started a class in linux a few months back and switch over to Fedora 9 or 10 simply because that was what the class was  using. Well the class is over and I wanted to put Ubuntu back on my machine but it wont install. I know the USB boost drive still works because just yesterday I install ubuntu on a classmates computer using it. 
I go though all the steps and then get stuck in a endless loop. 
at the Installation Type selection I pick Erase Disk and install Ubuntu and click continue.
in the next screen I select the drive and click install now... this laptop has 2 hard drives and if tried both. after clicking  Install now it does nothing ot takes me back to the previous screen.

---

### Post by JDorfler on 2013-12-26
What version of Ubuntu are you trying to install?  If you can, try to use gparted or another disk partitioning tool to reinstall msdos partitioning table or gpt partitioning table on both your HDDs as per your motherboard specs.  This will erase all of your data.  Then try reinstalling Ubuntu.

---

### Post by fantab on 2013-12-26
Boot with your Ubuntu DVD/USB and "Try Ubuntu (without installing)" and post the output of the following:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by tronacus86 on 2013-12-26
root@ubuntu:~# sudo parted -l
Model: ATA WDC WD1600BEVS-6 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  525MB  524MB  primary  ext4         boot
 2      525MB   160GB  160GB  primary               lvm


Model: ATA WDC WD1600BEVS-6 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  160GB  160GB  primary               lvm


Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdc: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  32.0GB  32.0GB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_tronacus-lv_root: 53.7GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  53.7GB  53.7GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_tronacus-lv_swap: 5302MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  5302MB  5302MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_tronacus-lv_home: 261GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  261GB  261GB  ext4


root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f3c5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000   83  Linux
/dev/sda2         1026048   312580095   155777024   8e  Linux LVM

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf38becdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   312580095   156289024   8e  Linux LVM

Disk /dev/mapper/vg_tronacus-lv_root: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_tronacus-lv_root doesn't contain a valid partition table

Disk /dev/mapper/vg_tronacus-lv_home: 260.5 GB, 260516610048 bytes
255 heads, 63 sectors/track, 31672 cylinders, total 508821504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_tronacus-lv_home doesn't contain a valid partition table

Disk /dev/mapper/vg_tronacus-lv_swap: 5301 MB, 5301600256 bytes
255 heads, 63 sectors/track, 644 cylinders, total 10354688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_tronacus-lv_swap doesn't contain a valid partition table

Disk /dev/sdc: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee9743d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    62527487    31262720    c  W95 FAT32 (LBA)

---

### Post by fantab on 2013-12-26
You have LVM Filesystem. Ubuntu's installer by default does NOT support installing to LVM, out of the box. Fedora does. LVM, I think is reminicient from the previous Fedora install.
If you want to continue using LVM, read below:
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

If you don't want to use LVM anymore then you will have to delete all those LVM partitions and create new Ext4 partitions. You will have no problems with Ubuntu installation.

Deleting partitions and creating new partitions will destroy data on those partitions. If you have data to save then BACKUP your DATA first.

---

### Post by tronacus86 on 2013-12-27
Thank you so much for the help

---

