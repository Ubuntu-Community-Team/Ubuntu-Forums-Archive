---
title: "Dual Boot Ubuntu 12.04 and Vista w/ Truecrypt"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by Alwaysonestepaway on 2012-07-14
I have a laptop with 2 separate hard drives which I want to install encrypted Ubuntu on one hard drive and Windows Vista encrypted with Truecrypt on the other.  Here is the order I installed everything.

1. Install Windows Vista on /dev/sda.

2. Install Ubuntu with encrypted full encryption on /dev/sdb.  I set the bootloader to install to /dev/sdb thinking that when I installed Truecrypt on the Vista installation it would write to the MBR and I could just hit escape to boot into Ubuntu.

3.  Download and install Truecrypt full System encryption.  Since Trucrypt says it can't dual boot I selected the option for single operating system (again thinking that I would just hit ESC and everything would work out as it should.

After all this I restarted the computer anticipating that everything had worked, which was a mistake.  The computer started into the Truecrypt bootloader as i expected and I was able to boot into windows.  When i again restarted I got the Truecrypt bootloader just like before except when I hit ESC I received an error message stating no other bootable device had been found.  In the past I have been able to dual boot Ubuntu and Vista/Truecrypt but it was on a single partitioned hard drive and it was also with an older version of Ubuntu that used the GRUB bootloader as opposed to the GRUB2.  I am not sure if I am fighting an issue with one of the changes or both.  I am definitely not a Linux expert and I am hoping I am just making a dumb mistake that lots of people will point out to me.  At this point I have been digging through the forums for answers on others posts for about 2 weeks but have not been able to find a set of commands that makes everything work.  I am pretty sure I have mixing some GRUB and GRUB2 commands although I have tried not to, maybe I should have said barely comfortable as opposed to not an expert.  

The following commands yield
[B]
ls /dev/sd*[/B]

/dev/sda  /dev/sda1  /dev/sda2  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb5

**sudo fdisk -l**
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7514460

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   461086719   230543328+   7  HPFS/NTFS/exFAT
/dev/sda2       461086720   488390655    13651968    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008962b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758   488396799   243947521    5  Extended
/dev/sdb5          501760   488396799   243947520   83  Linux


Any help would be greatly appreciated, even if it is preceded by "I can't believe you forgot to ...".   If need be I am not opposed to reinstalling both operating systems if there is a step in the installation (of OS or Truecrypt) that would make everything work.  Thanks in advance for any help.

---

