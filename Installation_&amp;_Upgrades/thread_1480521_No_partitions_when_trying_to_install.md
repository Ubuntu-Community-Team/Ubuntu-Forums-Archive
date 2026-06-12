---
title: "No partitions when trying to install"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by 2quick on 2010-05-11
Hello!

I am trying to install Ubuntu 10.04 on my Desktop and I am unable to see any partitions when trying to install.  I also checked to see if the partition manager would be able to see them and no luck there either.  I already have windows xp and OpenSuse installed on the hard drive.  Any suggestions such as boot options, etc...?  Thank you for any help!

---

### Post by srs5694 on 2010-05-11
Boot into either openSUSE or your Ubuntu install disc, open a Terminal, Konsole, or other text-mode shell, and type the following command:

```

sudo fdisk -lu

```

If you use openSUSE, make it a root shell and omit "sudo". Post the results, between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string for legibility. The output will give us details on how your partitions are laid out. Chances are the partition table has some subtle, and hopefully non-fatal, error that's causing Ubuntu's partitioner to flake out. This seems to be a common problem; there are lots of threads with similar problems.

---

### Post by AnthLee on 2010-05-11
I had the same problem of installer not seeing partitions.  I had them in gparted but not installer.  Executing sudo apt-get remove dmraid while in live cd then opening installer fixed this in my case.

---

### Post by 2quick on 2010-05-16
> **srs5694 said:**
> Boot into either openSUSE or your Ubuntu install disc, open a Terminal, Konsole, or other text-mode shell, and type the following command:

```

sudo fdisk -lu

```

If you use openSUSE, make it a root shell and omit "sudo". Post the results, between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string for legibility. The output will give us details on how your partitions are laid out. Chances are the partition table has some subtle, and hopefully non-fatal, error that's causing Ubuntu's partitioner to flake out. This seems to be a common problem; there are lots of threads with similar problems.

```
Disk /dev/sda: 2047 MB, 2047678976 bytes
64 heads, 63 sectors/track, 991 cylinders, total 3999373 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             245     3995711     1997733+   6  FAT16

```

It has a different output showing the partitions when executed in Opensuse.

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x852e852e 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1              63   276832142   138416040    7  HPFS/NTFS 
/dev/sda2       276832143   285218010     4192934   82  Linux swap / Solaris 
/dev/sda3   *   285218011   310375800    12578895   83  Linux 
/dev/sda4       310375801   488392064    89008132   83  Linux 
 
Disk /dev/sdb: 2047 MB, 2047678976 bytes 
64 heads, 63 sectors/track, 991 cylinders, total 3999373 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x00000000 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1             245     3995711     1997733+   6  FAT16 

```

Side note, to install Opensuse I had a bit of difficulties and to get it installed properly I had to use the boot option pci=nomsi  I tried that here with no luck.

Thanks!!

---

### Post by 2quick on 2010-05-16
> **AnthLee said:**
> I had the same problem of installer not seeing partitions.  I had them in gparted but not installer.  Executing sudo apt-get remove dmraid while in live cd then opening installer fixed this in my case.

I tried your option, with the same results.  No partitions found.  I am not able to see the partitions in gparted though either.

---

### Post by srs5694 on 2010-05-16
I don't see any problems with your partition tables, although it's possible I've overlooked something.

It looks like your 250GB disk isn't being detected at all by Ubuntu. This could be a driver issue. Are both disks of the same type? (Both SATA or both PATA?) If not, it could be that you're lacking a driver for the controller of the type used by the 2TB disk. If they're both of the same type, it's possible that your motherboard has two disk controllers. This is common on motherboards with lots of connectors (more than two PATA connectors or more than four SATA connectors). If so, you could try plugging the disk into another connector on the motherboard to see if that helps.

If you continue to have problems, could you please specify whether you're having problems detecting *both* disks or *only* the 2TB disk? Also please post your motherboard's make and model number (or if you're using a separate disk controller, its make and model number).

---

### Post by 2quick on 2010-05-16
> **srs5694 said:**
> I don't see any problems with your partition tables, although it's possible I've overlooked something.

It looks like your 250GB disk isn't being detected at all by Ubuntu. This could be a driver issue. Are both disks of the same type? (Both SATA or both PATA?) If not, it could be that you're lacking a driver for the controller of the type used by the 2TB disk. If they're both of the same type, it's possible that your motherboard has two disk controllers. This is common on motherboards with lots of connectors (more than two PATA connectors or more than four SATA connectors). If so, you could try plugging the disk into another connector on the motherboard to see if that helps.

If you continue to have problems, could you please specify whether you're having problems detecting *both* disks or *only* the 2TB disk? Also please post your motherboard's make and model number (or if you're using a separate disk controller, its make and model number).

The motherboard is an XFX GeForce 8200 no seperate disk controller.  There is only 1 250GB hard drive.  I swapped it around to a few of the other connections with no luck.  Also I created a USB Ubuntu drive and install via that method..no luck.  I have also tried LinuxMint and Fedora just to see... no luck.  When the partition editor comes up in the install menu it is completely blank.  Same thing with Gparted, not detecting the hard drive at all.

Thanks!

---

### Post by srs5694 on 2010-05-16
Please clarify: Post #4 specifies output from openSUSE that clearly shows the presence of a 2TB drive. Are you saying that output is from another computer, or do you mean that your computer has two disks, only one of which is 250MB in size?

Have you tried *every* SATA port on the motherboard? Check your manual for any mention of differences between the ports. I haven't been able to find detailed technical specs on the board (the XFX site is flaking out on me -- I think it relies on Flash, which I refuse to allow to pollute my system), so I don't know if it uses more than one SATA controller. If it does, it's likely that one controller handles four ports and the other handles two. That said, the board is old enough that I'd expect Ubuntu to support it -- but it apparently isn't getting detected.

---

### Post by 2quick on 2010-05-17
I have tried every slot.  Two of them do not work unless you have the RAID setting enabled in the BIOS menus, but no need for RAID for me at the moment.  The computer only has 1 hard drive connected.  I have downloaded the manual if you would like me to shoot it your direction, maybe you would see something I have missed.

---

