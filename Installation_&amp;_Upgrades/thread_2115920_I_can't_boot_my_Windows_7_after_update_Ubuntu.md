---
title: "I can't boot my Windows 7 after update Ubuntu"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by xinerd on 2013-02-14
I installed both windows 7 and Ubuntu on my disk, now I can't boot windows 7. 

I think it's something wrong with greb or hard drive sequence?

chainloader +1 returns **invalid signature**.

I thought it's the reason cause the problem.

following information I think might helpful, if you need anything else, let me know.

xinerd@xinerd-ThinkPad-Linux:~$ sudo fdisk -l
[sudo] password for xinerd: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x974cbb6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   209728574   104864256    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       209728636   976771071   383521218    f  W95 Ext'd (LBA)
Partition 2 does not start on physical sector boundary.
/dev/sda5       209728638   791747648   291009505+   7  HPFS/NTFS/exFAT
Partition 5 does not start on physical sector boundary.
/dev/sda6       791748608   792180735      216064   83  Linux
/dev/sda7       792182784   824184831    16001024   82  Linux swap / Solaris
/dev/sda8       824186880   896188415    36000768   83  Linux
/dev/sda9       896190464   976771071    40290304   83  Linux


 sudo dmesg | grep sd[abc]
[    1.402354] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.402357] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.402439] sd 0:0:0:0: [sda] Write Protect is off
[    1.402442] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.402474] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.513362]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    1.514407] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.105293] EXT4-fs (sda8): orphan cleanup on readonly fs
[    3.123966] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 132742
[    3.124304] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 132740
[    3.124328] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 132672
[    3.124357] EXT4-fs (sda8): 3 orphan inodes deleted
[    3.124362] EXT4-fs (sda8): recovery complete
[    3.263837] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   13.681335] Adding 16001020k swap on /dev/sda7.  Priority:-1 extents:1 across:16001020k 
[   15.112429] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   15.306320] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
[   15.876656] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)


last time I update my ubuntu 12.4, the boot menu lose windows 7 boot entry, I solved by adding blow to file /boot/grub/grub.cfg
menuentry "Windows 7 (loader) (on /dev/sda1)"  {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    chainloader +1
}
this time after I added this line, I got above problem. 

appreciate your help.

---

### Post by oldfred on 2013-02-14
Invalid signature is often the Windows PBR or partition boot sector. NTFS has to have a NTFS boot signature even if not the boot partition. 

this will show details.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
If you have grub in PBR of NTFS:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
#OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

