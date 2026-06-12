---
title: "Installer does not recognize partitions"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by _cvt_ on 2008-11-24
Hi,

   I trying to install Kubuntu 8.10 and the installer does not recognize partitions.

   I have 2 hds.

   I have installed the kubuntu 8.04 but it broke.
[LIST=1]
[*]sda2 - windows system
[*]sda4 - data
[*]sda5 - / (kubuntu 8.04)
[*]sda6 - home (kubuntu 8.04)
[*]sda7 - swap
[*]sdb1 - data
[/LIST]

   Below some commands run in the live cd:

**cat /etc/fstab**
```
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0

```

**sudo blkid**
```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="46CF-D6DD" TYPE="vfat"
/dev/sda2: UUID="98C8CB36C8CB1184" TYPE="ntfs"
/dev/sda4: UUID="00CCC1EACCC1DA54" LABEL="dados2" TYPE="ntfs"
/dev/sda5: LABEL="linux" UUID="3ddcfa8b-5809-4eb1-9d14-0acb2bdf4b49" TYPE="ext3"
/dev/sda6: LABEL="home_linux" UUID="3894f962-f9d1-4940-9c01-c08747736e69" TYPE="ext3"
/dev/sda7: TYPE="swap" UUID="ab3190b9-a454-4c8b-8d4b-7fbda74b46f3"
/dev/sdb1: UUID="CCC4B6F6C4B6E1BE" LABEL="dados" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"
```

**sudo fdisk -l**
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9af89af8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         193        5383    41696707+   7  HPFS/NTFS
/dev/sda3            5384       12160    54436252+   f  W95 Ext'd (LBA)
/dev/sda4            9300       12160    22980951    7  HPFS/NTFS
/dev/sda5            5384        7571    17575047   83  Linux
/dev/sda6            7572        9050    11880036   83  Linux
/dev/sda7            9051        9299     2000061   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14592   117210208+   7  HPFS/NTFS

```

**sudo lshw -C disk**
```
ubuntu@ubuntu:~$ sudo lshw -C disk                                              
  *-disk:0                                                                      
       description: ATA Disk                                                    
       product: Hitachi HTS54161                                                
       vendor: Hitachi                                                          
       physical id: 0                                                           
       bus info: scsi@0:0.0.0                                                   
       logical name: /dev/sda                                                   
       version: SBCO                                                            
       serial: SB2304SHG30Y6E                                                   
       size: 93GiB (100GB)                                                      
       capabilities: partitioned partitioned:dos                                
       configuration: ansiversion=5 signature=9af89af8                          
  *-disk:1
       description: ATA Disk
       product: TOSHIBA MK1234GS
       vendor: Toshiba
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: AH00
       serial: Z66NF7K0S
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5d379805
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GMA-4082N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: PT06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted

```

What I have to do to installer recognize my partitions ?

Thanks.

---

### Post by pennacook on 2008-11-24
From the livecd, does an fdisk -l show the partitions you show below?

>    
   1. sda2 - windows system
   2. sda4 - data
   3. sda5 - / (kubuntu 8.04)
   4. sda6 - home (kubuntu 8.04)
   5. sda7 - swap
   6. sdb1 - data


---

### Post by _cvt_ on 2008-11-24
Command **sudo fdisk -l** run-in in live cd add in the post.

---

