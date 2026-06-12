---
title: "Unable to load Ubuntu Server 14.04.3 with Promise FastTrak TX2650 configured as RAID1"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by robbo2 on 2015-09-29
Hi Guys,

I am very new to linux and hope that you guys will be able to help me out.

I have TWO 1TB drives configured as RAID 1 using the PROMISE RAID BIOs setup. 
POP in the installation disc and started the installation, using the 'Guided' partition method. 
Towards the end of installation for the Ubuntu Server 14.04.3 LTS, it prompts me that 'GRUB was unable to install'.
I continued with the installation till it prompts for a restart.

Upon restart, the ubuntu server will not load.
i booted the system using the Ubuntu Desktop disk and below is the fdisk:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cfac2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1819107327   909552640   83  Linux
/dev/sda2      1819109374  1953124351    67007489    5  Extended
/dev/sda5      1819109376  1953124351    67007488   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cfac2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1819107327   909552640   83  Linux
/dev/sdb2      1819109374  1953124351    67007489    5  Extended
/dev/sdb5      1819109376  1953124351    67007488   82  Linux swap / Solaris

Disk /dev/mapper/pdc_caceedaej: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cfac2

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_caceedaej1            2048  1819107327   909552640   83  Linux
/dev/mapper/pdc_caceedaej2      1819109374  1953124351    67007489    5  Extended
/dev/mapper/pdc_caceedaej5      1819109376  1953124351    67007488   82  Linux swap / Solaris

Disk /dev/mapper/pdc_caceedaej1: 931.4 GB, 931381903360 bytes
255 heads, 63 sectors/track, 113234 cylinders, total 1819105280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_caceedaej1 doesn't contain a valid partition table
fdisk: unable to read /dev/mapper/pdc_caceedaej2: Inappropriate ioctl for device
```

Can anyone help me to make it boot?
Thanks Guys.

---

### Post by robbo2 on 2015-09-29
anybody ?

---

### Post by robbo2 on 2015-10-01
Anybody can help?

---

### Post by dino99 on 2015-10-01
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

