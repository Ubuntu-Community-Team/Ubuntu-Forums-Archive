---
title: "GRUBbing a RAIDed root"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by HankB on 2010-07-26
Hi folks, It's been an interesting adventure getting 10.04 installed in a RAID 1 root partition. I have finally succeeded by installing to a degraded RAID (only one disk) and then adding the second drive partition. FWIW, I installed to /dev/sdb2 and added /dev/sda2 and all seems to work. :D

Except... I need to make /dev/sda bootable. At present I can boot by using the BIOS screen to boot from the second drive. The first drive initially had 9.10 installed with /dev/sda2 as root and booted fine from that, but when I converted /dev/sda2 to the RAID configuration, it lost the ability to boot.

I've looked at some of the helpful documentation on grub2 and it is not obvious how get grub2 set up on /dev/sda. I just need to duplicate what the installer does when it installs grub2.

Here's what I have now:

second drive (boots from RAID)
```
root@tenere:~# parted /dev/sdb
GNU Parted 2.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  1018kB  1000kB                        bios_grub
 2      1018kB  4001MB  4000MB  ext4                  raid
 4      4001MB  1997GB  1993GB  ext4                  raid
 3      1997GB  2000GB  3049MB  linux-swap(v1)

(parted) quit
```

first drive (no longer boots)                                                         
```
root@tenere:~# parted /dev/sda
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA ST32000542AS (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  1018kB  1000kB
 2      1018kB  4001MB  4000MB  ext4               raid
 4      4001MB  1997GB  1993GB  ext4               raid
 3      1997GB  2000GB  3049MB

(parted) quit
```

I did see a suggestion in another post (or was it the wiki?) to install grub to the raid partition, but that seems not to work:
```
root@tenere:~# grub-install /dev/md0
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: error: embedding is not possible, but this is required when the root device is on a RAID array or LVM volume.
root@tenere:~# 
```

Perhaps this provides useful information:
```
root@tenere:~# grub-probe -v -d /dev/sdb2 
grub-probe: info: cannot open `/boot/grub/device.map'.
grub-probe: info: /dev/sdb2 starts from 1988.
grub-probe: info: opening the device /dev/sdb.
grub-probe: info: the size of /dev/sdb is 3907029168.
grub-probe: info: Partition 0 starts from 34.
grub-probe: info: Partition 1 starts from 1988.
grub-probe: info: opening /dev/sdb,2.
grub-probe: info: the size of /dev/sdb is 3907029168.
ext2
root@tenere:~#
``` 


I'd appreciate any help getting this last little bit properly configured. In the spirit of maximum redundancy, I'd like to be able to boot from either device.

Thanks!

Edit: I seem to have solved it. First I used 'parted' to set the 'bios_grub' flag for /dev/sda1 and then ran the command:
```
root@tenere:~# grub-install --modules=raid --no-floppy /dev/sda
Installation finished. No error reported.
root@tenere:~#
```

---

### Post by mucho_maze on 2011-10-16
> **HankB said:**
> 
Edit: I seem to have solved it. First I used 'parted' to set the 'bios_grub' flag for /dev/sda1 and then ran the command:
```
root@tenere:~# grub-install --modules=raid --no-floppy /dev/sda
Installation finished. No error reported.
root@tenere:~#
```

Thanks so much HankB. I had the identical problem and this solved it. Also I ran

```

grub-setup -r  ”(hd1)” /dev/sdb

```

---

