---
title: "Inst Win 7 (32b) on new Disk and space for UBUNTU on it"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by AlanAbbott on 2011-03-07
My system as now is:
```
raam@raam-desktop:~$ sudo fdisk -l
[sudo] password for raam: 

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004162a

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       29321   235520901   83  Linux
/dev/sde2   *       30597       37179    52877947+   7  HPFS/NTFS
/dev/sde3           37180       38913    13928355    5  Extended
/dev/sde4           29322       30536     9759487+  83  Linux
/dev/sde5           37506       38913    11309728+  82  Linux swap / Solaris
/dev/sde6           37180       37483     2441817   83  Linux
/dev/sde7           37484       37505      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

raam@raam-desktop:~$ sudo parted /dev/sde -l
Model: ATA SAMSUNG HD322HJ (scsi)
Disk /dev/sde: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  241GB  241GB   primary   ext3
 4      241GB   251GB  9994MB  primary   ext3
 2      252GB   306GB  54.1GB  primary   ntfs            boot
 3      306GB   320GB  14.3GB  extended
 6      306GB   308GB  2500MB  logical   ext3
 7      308GB   308GB  181MB   logical   linux-swap(v1)
 5      308GB   320GB  11.6GB  logical   linux-swap(v1)


Error: /dev/sdf: unrecognised disk label                                  

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                    

```

I want to install Windows 7 HM 32Bit on the new Drive, Set up a partition for it, another to be seen by the other windows (64b) and work space for Ubuntu.

I request a guide line as how to go about this.

---

### Post by Mark Phelps on 2011-03-07
One thing at a time tends to work better ...

1) Installing Win7

Connect ONLY the new drive, no other drive. Insert Win7 DVD in drive. Boot from that DVD, install Win7 -- do NOT provide a product key at this time.

2) Create Win7 Repair CD

Once Win7 is working, use Backup feature to create and burn Win7 Repair CD.  This will come in handy later.

3) Shrink Win7 OS

Using Win7 Disk Management utility, shrink the Win7 OS partition to create room for other partitions on the drive.

4) Create NTFS Data Partition

Using Win7 Disk Management utility, create shared NTFS data partition.

5) Set up access to Win7 from GRUB

Reconnect other drives. Set boot to drive containing GRUB.  Boot into Ubuntu.

Open terminal and run "sudo update-grub".  Will regenerate the GRUB menu, adding an entry for Win7.

BTW, once you have everything working in Win7, only then, activate it.  BY not providing a product key during install, you have 30 days of usage prior to activation.

---

### Post by AlanAbbott on 2011-03-08
I've postponed Win 7-32 as I've got SSL working under Win7-64, which was my max priority, since I cannot get it working under UBUNTU I've being testing alternatives.

Thank you very much.

Alan

---

