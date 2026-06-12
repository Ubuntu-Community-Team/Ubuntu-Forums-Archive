---
title: "Upgraded-Missing Grub-not booting-"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by chuck4200 on 2010-06-08
Had v9.x installed alongside Windows XP SP3 install.  Have not used it that much since install.
Got the bug to upgrade to v10.
Went through the upgrade process, everything seemed fine.
At the end of the install process asked which dev to install GRUB onto - I selected only one drive, the wrong one of course, and the reboot failed.

Boots up with:
typical error message from other posts
grub rescue>

Have LiveCD running now to post.  Ran Info_boot Script.sh - results below.

Will reinstalling v10 from Live CD fix this?  Will this use Wubi or just go through normal install process?
Or is there an easier fix to install GRUB on the correct drive to get the dual boot choice of Windows XP and Ubuntu back.

Naturally I need to get back to Windows ASAP - it's the net gateway and print server for my home/office setup. 

THIA,
Chuck
Linux noob/Old Dos/Win fart

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #256 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 281472 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc5 and 
                       looks at sector 287744 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdc5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdc5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065        32,129        16,065   5 Extended
Empty Partition
/dev/sda2              32,130   288,800,504   288,768,375   7 HPFS/NTFS
/dev/sda3    *    288,800,505   312,576,704    23,776,200   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   153,597,464   153,597,402   7 HPFS/NTFS
/dev/sdc2         153,597,465   976,751,999   823,154,535   5 Extended
/dev/sdc5         153,597,528   976,751,999   823,154,472   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 2051 MB, 2051014656 bytes
33 heads, 63 sectors/track, 1926 cylinders, total 4005888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  32     4,005,887     4,005,856   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       6d041e47-35b7-4250-90a1-dfde3c0573db   ext4                                     
/dev/sda1: PTTYPE="dos" 
/dev/sda2        7818C3B718C37324                       ntfs       Music                         
/dev/sda3        9214D8A714D89019                       ntfs       Swap                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E6704D53704D2C1D                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D80C8BED0C8BC54A                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        22B485E1B485B835                       ntfs       BIGD                          
/dev/sdc: PTTYPE="dos" 
/dev/sde1        681C-B7FE                              vfat                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/681C-B7FE         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /usepmtimer /NoExecute=OptOut 
C:\wubildr.mbr = "Ubuntu" 
=======Devices which don't seem to have a corresponding hard drive==============

sdd

---

### Post by darkod on 2010-06-08
You need to get rid of grub2 from /dev/sdc, the wubi install doesn't use it. This is not your fault, it's a bug if you go trough the upgrade process from wubi.

Boot the ubuntu cd in live mode, in terminal run:

sudo apt-get install lilo
sudo lilo -M /dev/sdc mbr

Ignore the warnings it will give you. That will install generic mbr on /dev/sdc which works just the same as windows bootloader. It should work fine after that.

---

### Post by chuck4200 on 2010-06-08
Thanks for the help.
Followed your instructions, still not booting.
New boot_info_script results below.

Should it have been dev/sda instead of dev/sdc perhaps?
Noobie observation, but Windows appears to be located on dev/sda.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 281472 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc5 and 
                       looks at sector 287744 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdc5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdc5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065        32,129        16,065   5 Extended
Empty Partition
/dev/sda2              32,130   288,800,504   288,768,375   7 HPFS/NTFS
/dev/sda3    *    288,800,505   312,576,704    23,776,200   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   153,597,464   153,597,402   7 HPFS/NTFS
/dev/sdc2         153,597,465   976,751,999   823,154,535   5 Extended
/dev/sdc5         153,597,528   976,751,999   823,154,472   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 2051 MB, 2051014656 bytes
33 heads, 63 sectors/track, 1926 cylinders, total 4005888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  32     4,005,887     4,005,856   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       6d041e47-35b7-4250-90a1-dfde3c0573db   ext4                                     
/dev/sda1: PTTYPE="dos" 
/dev/sda2        7818C3B718C37324                       ntfs       Music                         
/dev/sda3        9214D8A714D89019                       ntfs       Swap                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E6704D53704D2C1D                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D80C8BED0C8BC54A                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        22B485E1B485B835                       ntfs       BIGD                          
/dev/sdc: PTTYPE="dos" 
/dev/sde1        681C-B7FE                              vfat                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/681C-B7FE         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /usepmtimer /NoExecute=OptOut 
C:\wubildr.mbr = "Ubuntu" 
=======Devices which don't seem to have a corresponding hard drive==============

sdd

---

### Post by chuck4200 on 2010-06-08
Reran the original instructions.
I get this message when I run the apt-get install lilo command
Should I ignore of complete the instructions as follows?

Chuck

 LILO configuration                                                        &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; It seems to be your first LILO installation. It is absolutely necessary   &#9474; 
 &#9474; to run liloconfig(8)  (should be liloconfig(number eight-no emoticon)  when you complete this process and execute           &#9474; 
 &#9474; /sbin/lilo after this.                                                    &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; LILO won't work if you don't do this.                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>

---

### Post by darkod on 2010-06-08
No, you don't need to run it again. There is also grub2 installed on the partition, /dev/sdc1, I missed it the first time, sorry.

You said you selected only the disk, not all partitions on it. Run this fix on /dev/sdc1, so that's partition #1 on disk /dev/sdc:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

That should get rid of grub2 there.

---

### Post by chuck4200 on 2010-06-08
Darko,

Thanks for your patience thus far.  I agree with the author the Ubuntu repository needs to be update to use the apt-get method.  Unzipping the tar, navigating and executing was a pain.

This is the log from testdisk_static 
It did not give me the various screen options
I'm thinking the easiest thing to do is to use Windows CD and the fixboot method.

I like Ubuntu, but these kinds of problems are what keeps noobs and novices in windows!!!!
Learning the Linux vernacular and the command line syntax with terminal can be daunting.
At this point, and half a work day wasted, I just want to get Windows back and fight this battle another day.
Any suggestions?

Tue Jun  8 15:45:58 2010
Command line: TestDisk

TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 2.6.32-21-generic (#32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010)
Compiler: GCC 4.3 - May  6 2009 14:40:08
ext2fs lib: 1.41.4, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
User is not root!
Hard disk list
Disk /dev/sr0 - 733 MB / 699 MiB - CHS 358116 1 1 (RO), sector size=2048 - _NEC DVD_RW ND-3550A

Partition table type (auto): Intel
Media is opened in read-only.
Disk /dev/sr0 - 733 MB / 699 MiB (RO) - _NEC DVD_RW ND-3550A
Partition table type: Intel

Analyse Disk /dev/sr0 - 733 MB / 699 MiB - CHS 358116 1 1 (RO)
Current partition structure:

Partition sector doesn't have the endmark 0xAA55

---

### Post by darkod on 2010-06-08
You can use the XP cd to boot with it, enter Recovery Console and try to repair the boot process. But I am not sure what that will do to wubi, because wubi install is inside windows.

If you need instructions how to use the recovery console:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I see testdisk reported it is not run as root, maybe that's why it offered different screens. It should be run with:

sudo testdisk

for maximum permissions.

---

### Post by darkod on 2010-06-08
As far as I know, testdisk is available but in the (universe) repository. But I think the live mode doesn't have it enabled by default, in System-Administration-Software Sources.

Here is an example screenshot from my hdd installed ubuntu, not live mode.

---

### Post by chuck4200 on 2010-06-08
Testdisk does not appear to work using the LiveCD, the only thing  available is the testdisk_static, and that only gets you a log file as  in my previous post.

Retried the sudo lilo -M on dev/sdc1 - would  not let me modify it.

Tried the Windows CD fixboot and fixmbr in  Troubleshoot post to restore.
At some point, don't recall when it  began, the only thing that I get now  is Invalid Boot.ini message.    

Then tried the bootcfg /list  (none found) and /rebuild. Can not find a Windows installation.  It  appears that the GRUB upgrade process from within Windows has HOSED my  system and many others.

I strongly suggest if you have a dual  boot system, DO NOT UPGRADE from within the 9,xx program.  

Probably  best to use a LiveCD or install a new version over the old to upgrade  to 10.04 if you are using a dual boot system.  Especially DO NOT upgrade  from within the Wubi 9.xx install program.  I think the only safe  upgrade method is from a dedicated box to Ubuntu.  I think the option to  upgrade from within should be disabled.  Be especially careful if you  have more than one HDD with multiple partitions.

This has really  soured my opinion of Ubuntu and Linux.  It's been a nightmare of syntax  and disparate posts on forum threads with the same problems, and no good  solutions. 

What started with a half hour upgrade now will be  days to rebuild my system. Although I have an older backup image, I may  have to reinstall XP to get to the image file.  

If there are any other suggestions before I resort to drastic measures, please suggest them.

---

### Post by darkod on 2010-06-08
OK, hold on. No need for drastic measures, not yet.
I know you're pi**ed, I would be too. But you need to focus.

First of all, if you tried the sudo lilo command I gave, you don't use it on a partition, not on /dev/sdc1. It should not have a number in the device name. Just /dev/sdc is the disk, the MBR of the hdd. /dev/sdc1 is the first partition on it.

You didn't succeed to run testdisk from the live mode? Any reason it said why?

---

### Post by darkod on 2010-06-08
PS. Also, to avoid any confusion during the windows repair process, I would power down, and disconnect all disks except your XP disk. Leave just that disk connected.

Then boot with the XP cd again in Recovery Console and run the commands in this order:

fixboot
fixmbr

The order also matters. If that didn't work, let us know what the problem is.

For example, if it complains about invalid boot.ini, we can get a new default boot.ini online. I know a link.

---

### Post by chuck4200 on 2010-06-08
Darko,

Extracting the testdisk.tar for Linux v6.11.3 (either i386 version) only gives you testdisk_static and photorec_static as the executables.  There are testdisk.1 and photorec.1, but it shows them as binaries when you try to run them.

I have two ATA's and one SATA HDD's with multiple partitions on each drive.  Can't remember exactly, it's been awhile since I looked under the hood on this PC.

The SATA is showing as dev/sdc, but the boot drive is/should be dev/sda.  As a SATA, it often show up first, before the ATA drives.
I may have incorrectly installed GRUB on the dev/sdc.  I'm thinking the issue is how to get the windows boot.ini fixed on dev/sda.

I found a copy (12/2009) of boot.ini for windows XP Professional on my C: drive (dev/sda). 
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /usepmtimer /NoExecute=OptOut 
C:\wubildr.mbr = "Ubuntu"

Did run the lilo on dev/sdc as previously suggested early on.
Then tried it with dev/sdc1, and also dev/sda - which both gave unable to modify errors - locked, or something to that effect.

Will try the lilo -M again, and then power down and unplug the second drive.


Here's the current fdisk listing:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb9504e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2           2        8032+   5  Extended
/dev/sda2               3       17977   144384187+   7  HPFS/NTFS
/dev/sda3   *       17978       19457    11888100    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6d376d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f0bda7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sdc2            9562       60800   411577267+   5  Extended
/dev/sdc5            9562       60800   411577236    7  HPFS/NTFS

***(Temporary Flashdrive)***
Disk /dev/sde: 2051 MB, 2051014656 bytes
33 heads, 63 sectors/track, 1926 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb8761ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        1927     2002928    6  FAT16

---

### Post by darkod on 2010-06-08
I thought you also tried to enable the universe repository and install testdisk from there. In live mode, look in System-Administration-Software Sources. If the universe repository is not enabled, enable it. After that it will ask you to update the sources.

Then you should be able to install and run it with:

sudo apt-get install testdisk
sudo testdisk

---

### Post by chuck4200 on 2010-06-08
I'm just a Linux noobie! Longtime DOS/Win guy - early 80's. Not used to all these permissions and freedoms..........    Getting to and cracking my box is a chore.........  Finished the lilo routine on dev/sdc    Disconnected the two other drives Ran bootcfg /scan - nothing there  Ran Chcdsk /r to repair in case  Ran fixboot - restored boot - Y  Ran fixmbr - restored mbr - Y    Rebooted   Invalid Boot.ini file Booting from C:\Windows  Just hangs there.  What next Dr. Darko?  I'm about to go ballistic, lost a days work already...............

---

### Post by darkod on 2010-06-08
I got a new boot.ini to make it simpler for you. :) But I had to compress it in archive because it won't let me attach it otherwise.

Download the attachment, right-click, Extract Here. You should see a new boot.ini in the same folder.

In Places open your XP partition, rename the original boot.ini in boot.ini.bck for example. Copy this new downloaded boot.ini to your XP partition.

Restart and keep fingers crossed for XP to load. :)

---

### Post by chuck4200 on 2010-06-08
Thanks Dr. Darko for all your patience and help.

I think this has been resolved somewhere between blind luck, my Linux ignorance and forgetfulness about my system architecture.

I was able to get the full testdisk v6.11.1 installed enabling the universe setting as you mentioned.  I followed the instructions to Backup BS, the two Boot Sectors were not identical.

Three HDD's with multiple partitions on them, complicated it on my end.  The boot drive as you correctly kept pointing me to is/was dev/sdc.  For several reasons, old DOS thinking, the new SATA drive and others, I was thinking the first drive (dev/sda) was my boot drive. 

I kept selecting this drive as my boot drive in the boot up selection process, and not the SATA (dev/sdc).  Although the boot sectors were not identical, and GRUB created the original problem, it was driving me nuts.

Until I was able to use testdisk, I did not realize this.  After fixing the boot sector issue and selecting the correct drive for booting, I am now back running Windows.  I also had to enter BIOS setup and designate the SATA as the first drive when a restart failed.

So - there were many lessons learned today on both sides - Windows and Linux configurations.  

I could not boot into Ubuntu from the bootloader however.  Said the kernel needed to be loaded.  Will try the GRUB fix, and a reinstall of 10.x using LiveCD after I complete a back up the C: partition!

Perhaps as a side note for noobies, and in working with noobs, adding a few lines of explanation about their HDD configuration might be helpful.  The confusion of dev/sdX and the comparison to Win HDD designations is most confusing at first.  

For example - if dev/sdc had been equated as my SATA and being the boot drive, I might have been able to realize the mistakes I was making much sooner.  In Windows Recovery Console it is designated as Drive E:....   Most people have one drive, so it is not an issue, but for me with 3 drives (2 ATA, 1 SATA), I was lost.  Unplugging two of the drives, the SATA boot drive was missing, so I was running fixboot and fixmbr on the wrong drive the whole time.  Boot selecting the wrong drive made matters worse.

Unless you have some suggestions to recover or reinstall Ubuntu, I willl mark this as resolved.  So in this case, what was obvious to an experienced user was beyond my comprehension, thus a few more lines of explanation is always helpful.

Thanks again Darko.
):P

PS I might even be able to help someone out with similar problems!!!!!!!!!!!!!

---

### Post by darkod on 2010-06-08
I'm glad it worked out OK at the end. I'm not too much into Linux myself (yet) but I think the drive/partition designation is more correct than what MS uses, so I use it too. For example, MS calling even partition drives in My Computer is making hell of a confusion when talking to long term users. Most of the times C:, D:, etc are only partitions, but sometimes they can really be separate physical disks. :)

Meanwhile I think I figured out why you couldn't start the downloaded testdisk, but I was waiting to see what you will come back with. When you unpacked it and got the testdisk_static file, in terminal you only need to navigate to the folder where the file is and execute with:

sudo ./testdisk_static

Just for info, for navigating in terminal you use like in DOS, cd to change folder, and if you need to list the content of a folder to help you if you forget a file/folder name, instead of dir you just use ls

This was only a wubi install inside windows. After you get trough the "shock" of this experience, I would consider planning a full ubuntu install, on its own partition with its own filesystem. Much better option.

Take care, you deserved a rest. :)

PS. The option to boot into wubi would be lost because of reparing the XP boot files. The data is still somewhere in the disk image that wubi is working from. But I have no idea how to look inside, except that I know that it's possible. Later if you feel like it you might google around for a way to look inside. The disk image should be X:\ubuntu\disks\root.disk, the letter depends on where you decided to install wubi.

---

### Post by FuturePusher on 2010-06-08
> **chuck4200 said:**
> Thanks Dr. Darko for all your patience and help.

I think this has been resolved somewhere between blind luck, my Linux ignorance and forgetfulness about my system architecture.

--- Snip-snip-snip... ---

Hi chuck4200,

I just skimmed this thread, but an idea popped up in my head:

I've been reading up a wee bit on the newer Grub2 (default in Ubuntu 10.04, possibly 9.10 as well, a bit uncertain on that).

I think Your issue _could_ be due to a change in it (Grub); I believe a disk's _first_ partition was adressed by Grub as "(hd*,0)" before... and now as "(hd*,1)" instead.
Thus Your Ubuntu install on the third drive's first partition (if I'm not recalling wrong here), would _have_been_ adressed as "(hd2,2)"... but in the newer Grub's configs (now "grub.cfg", before "menu.lst") it needs to be "(hd2,3)", where "Grub-internal" device designation is used...
(Drive-counting still starts with "0" for first drive, partition-counting now starts with "1" though.)


Please have a look at Your "/boot/grub/grub.cfg" in concern, specifically the "menuentry" sections and the "set root=" instruction lines in particular... if You have a prevalence of something like "set root='(hd2,2)'" rather than "set root='(hd2,3)'"... then that could very well be what's gone wrong!

It seems the newer Grub installations (like You would have initiated (possibly without even knowing it) with Ubuntu 10.04)... doesn't handle certain things entirely properly - legacy boot sector handling probably being the main problem.

---

### Post by darkod on 2010-06-08
No, it had nothing to do with it. Sorry, too tired to explain now. :)
It was all due to the install being a wubi install inside windows, and during the upgrade at one point when asked where to install grub2, all partitions were selected resulting grub2 to also be installed on the XP partition. On top of that, wubi installs don't even use grub2 on the MBR or partitions...

---

### Post by chuck4200 on 2010-06-09
> **darkod said:**
> No, it had nothing to do with it. Sorry, too tired to explain now. :)
It was all due to the install being a wubi install inside windows, and during the upgrade at one point when asked where to install grub2, all partitions were selected resulting grub2 to also be installed on the XP partition. On top of that, wubi installs don't even use grub2 on the MBR or partitions...

After this experience, Darko is correct on the origination of the problem - Wubi install inside of Windows.  However, when I responded to the where to install grub2, I only selected dev/sda, thinking first drive = boot drive.  I did not select all drives as recommended.  From other posts, it seems others with Wubi installs have the same problem.  Darko's solution/suggestion using LILO would likely fix the problem in most cases. 

Nonetheless, I don't think it would have mattered whether I had selected all drives, or just the dev/sda.  The problem appears to be with the wubi install and dual boot issue.  Had it been a dedicated partition or drive, and not a wubi install inside of Windows, I think the upgrade would have been OK.

As mentioned, part of the problem was that I had three drives, 2 IDE ATA on the first channels, and then an SATA, which was the actual boot drive.  In my BIOS settings, it was listed as ATA drives first, then SATA.  I think, not sure, there is a situation with SATA drives being listed/given higher priority than IDE ATA drives.  I recall thinking it strange the SATA drive took precedence over the IDE ATA drives when I installed or rebuilt the box. 

However, DOS/WIN Recovery Console showed my SATA as Drive E: (3rd drive).  In XP, it is showing as Drives C: & D:   I don't recall if I manually changed the Drive letters in XP in my system tinkering, or if it was a drive letter designation by Windoze.   

The boot up process which I really had not documented before, worked fine until the 10.04 upgrade process.  Fixing the boot sector and mbr on the first ATA drive dev/sda might have messed the original boot order up.  Subsequently, on POST, when selecting the dev/sda as the boot drive only compounded the resolution by looking to the wrong drive for boot.ini.  Changing the default BIOS order, resolved that issue.

However, I am not certain that testdisk was the complete fix, but the Boot Sectors were not identical on dev/sdc.  LILO may have been enough of a fix perhaps to boot into XP had I chosen the right boot drive.  I'll never know, because I certainly won't try to duplicate that problem to find out.:confused:

However, I won't really know when the problem was actually resolved - ie using LILO or Testdisk due to the wrong boot drive selection error.  It was a "comedy" of complications, that thankfully was resolved without having to reinstall XP.  That would have a real nightmare considering all the apps with their patches and upgrades over the past two years.  

Futurechaser, 

While it would be interesting to explore the differences in the grubmenu.cfg, I can't access 10.04 via the current bootloader process.  Missing kernel problem, or some other boot up aspect.  So I will be deleting the 30 GB Wubi install today, and plan a separate partition install much later.  I'll pick and choose my battles.........!!

And I failed miserably to keep a current image of the C: partition since I plan a Win7 upgrade soon.  Otherwise, restoring the partition image would have been a snap.  I do store all my data when given the chance on Drive D:  As a former Novell admin, I do know the value of storing my data files anywhere but C: in the event of a Windoze crackup.  The first thing I do is repartition a new PC, mine or someone else to separate the data and OS. 

I really believe that if there had not been so many Unix factions and territorial infighting, had they co-developed a GUI like Ubuntu, or the old Corel GUI version long ago, Unix/Linux would be on top of the heap versus MS or Apple.  

I first got involved with Ubuntu to extend the life of an old IBM T-20 laptop from the 90's.  It strains under a full Ubuntu install due to memory and hardware, but works fine with the lighter variants.  

I like Ubuntu, and will reinstall in it's own partition or drive next time.  No more Wubi for me............  If there are no further entries for this thread, I will mark it resolved in a day or two.  Learned a lot from this though.  Told my son I had hosed my PC trying something new.  He said when are you going to learn to leave things alone......, but I replied - nothing ventured nothing gained!  ;)

---

### Post by darkod on 2010-06-09
This is just one backup solution I am currently exploring myself:
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

It is command line based (the System Rescue CD boots you into command line linux), but with your DOS experience you might like it.

One thing I really like about the FS Archiver solution mentioned, is that it allows restore to a smaller partition than the source partition, as long as the data fits of course.

Most programs for partition cloning/backup require restore to a partition of the same size or larger, than the source partition. Why, if you have very little data at the moment on your source partition?

Plus, FS Archiver (the latest version mentioned) covers ntfs and ext2/ext3/ext4, plus lots of other filesystems, so it sounds like a good all round solution. Did I mention it's free? :)

I oversized my win7 system partition when planning. It's 65GB and currently used only 28GB and I have all that I use installed. Because FS Archiver allows restore to smaller partitions, I started to explore the option to make the image file, delete the partition, create a smaller one and restore there.

---

### Post by chuck4200 on 2010-06-11
Thanks for the info on FS Archiver.  Good to know you don't have to match sizes.

I have MaxBlast5 from Seagate/Maxtor.  It's a scaled down version of Acronis and comes with the drive.  If you have at least one Seagate or Maxtor drive, it will image back up any drive or partition.    I rarely change any of the drive sizes on my primary drives C or D.  The others are all flexible and I don't image back up those. Just offload copies to an external HDD or DVD.

Thanks again for all the help and lessons.  marking this thread solved.

Chuck

---

