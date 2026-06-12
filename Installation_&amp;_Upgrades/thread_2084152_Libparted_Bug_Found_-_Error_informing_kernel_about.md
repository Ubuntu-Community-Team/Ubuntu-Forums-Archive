---
title: "Libparted Bug Found - Error informing kernel about modifications to partition"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by Mr_JMM on 2012-11-14
Hi Again,

Somehow I managed to bork something and now everytime I try to use Gparted Libparted Bug Found - I get the following error:
Error informing the kernel about modifications to partition /dev/sda4 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda4 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
Trying to perform any task other than labelling partitions results in GParted crashing.
Also, trying to install any other distro's fails when at the partition stage. Currently, only Ubuntu runs (the original Linux OS, all others were removed).

This happens regardless of how I access GParted.

fdisk (via booted Ubuntu session): ```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           81920    20561919    10240000    7  HPFS/NTFS/exFAT
/dev/sda3   *    20561920   146391039    62914560    7  HPFS/NTFS/exFAT
/dev/sda4       146393087   488396799   171001856+   5  Extended
/dev/sda5       146393088   150586446     2096679+  82  Linux swap / Solaris
/dev/sda6       150589440   151638015      524288   83  Linux
/dev/sda7       151640064   176811389    12585663   83  Linux
/dev/sda8       225044480   488396799   131676160   83  Linux
/dev/sda9       176814080   189396991     6291456   83  Linux
/dev/sda10      189399040   214564863    12582912   83  Linux
/dev/sda11      214566912   225042431     5237760   83  Linux

Partition table entries are not in disk order

```

blkid (via booted Ubuntu session): ```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0615" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="AAB6D921B6D8EEB7" TYPE="ntfs" 
/dev/sda3: LABEL="WINDOWS" UUID="E4144F86144F5AA6" TYPE="ntfs" 
/dev/sda5: UUID="9f08f683-1ce1-41a5-bce7-18a944fff1ce" TYPE="swap" 
/dev/sda6: LABEL="LinuxBoot" UUID="9665c622-b5e7-4d40-9c0c-d016a46cf9a0" TYPE="ext4" 
/dev/sda7: LABEL="UbuntuRoot" UUID="66d71d79-1a1d-4a4b-beaa-05536a4c2dea" TYPE="ext4" 
/dev/sda8: LABEL="LinuxHome" UUID="8941143b-2bb7-4ce5-8780-c7e01049646c" TYPE="ext4" 

```

Any ideas how I fix this?

Many thanks.

---

### Post by Mr_JMM on 2012-11-14
Update: I may have fixed this.

I forgot to check at each stage so I'm not sure hich of the following fixed this issue but as it stands, I think both of these steps should be done as a matter of course (hindsight).

1. Since I have an extended partition containing many logical partitions including swap and boot, I used a USB install of GParted to add the label "lba".

2. I booted into Windows Vista and ran chkdsk /f twice. The first time showed a lot of errors / bad sectors but the second run was clean.

Since these steps, touch wood, I haven't had the libparted error again.

---

