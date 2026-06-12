---
title: "Messed up grub upgrade... Help Pls"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by Chengs on 2010-04-02
Hi All,
         Sorry, made my first mistake by posting my query under a different thread a little more than 24 hrs ago. Please read message #112 in this link..[http://ubuntuforums.org/showthread.php?t=1314064&highlight=sh%3Agrub%26gt%3B&page=12](http://ubuntuforums.org/showthread.php?t=1314064&highlight=sh%3Agrub%26gt%3B&page=12)

In addition to the problem described in the above link, a new one has just cropped up. Using the disk utility (by booting from 9.10 iso cd) I made sda1 bootable. Now, instead of the sh:grub> error I get the grub rescue> with the message "error: no such partition".

Am unable to revert the boot process to sda2.

Have not used my laptop for more than a month. Am desperate...

Thanks in advance 

Cheers
Chengs

---

### Post by oldfred on 2010-04-02
Welcome to the forums. 

You have wubi which is an install in the windows partition and uses the window boot loader in the MBR to boot. I do not know if it works with real old versions of windows.

You need to reinstall the windows boot loader. All versions of windows XP and before use essentially the same boot loader so you can reinstall from any of the old versions of windows. or:

From the liveCD terminal to install a generic windows boot loader:
sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

---

### Post by Chengs on 2010-04-02
Hi Oldfred,
              Thanks for the welcome & response.

Running sudo apt-get install lilo from live cd gives the following response...

ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main mbr 1.1.10-2
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main lilo 1:22.8-8ubuntu1
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr_1.1.10-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr_1.1.10-2_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1_i386.deb)  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Don't want to experiment more. Will wait for further advise.

Cheers
Chengs

---

### Post by oldfred on 2010-04-02
Have you configured universe as a Software Source in system, administration. I always check off everything and assume everyone else does.I guess I should add that note to make sure it is configured.

---

### Post by Chengs on 2010-04-03
> **oldfred said:**
> Have you configured universe as a Software Source in system, administration. I always check off everything and assume everyone else does.I guess I should add that note to make sure it is configured.


Have configured universe as source & ran sudo apt-get install lilo.  Got a Lilo configuration warning  "It seems to be your first lilo installation. It is absolutely necessary to run liloconfig8. When you complete this process execute /sbin/lilo......after this lilo won't work if you don't do this".  On continuing, at the end of the process the system showed that linux & vmlinuz could not be found. 

Executed sudo lilo -M /dev/sdX mbr. This went through successfully. On trying to reboot a "Invalid PT" message is displayed.

Find below the original settings on sda. Had inadvertently changed it to boot from sda1 & the system shows empty instead of Dell Utility. How do I remove the boot flag from sda1 & change the system to Dell Utility or vfat? 

------------------------------------------------------------------
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260    78,124,094    78,059,835   7 HPFS/NTFS

--------------------------------------------------------------------

---

### Post by oldfred on 2010-04-03
You can set boot flags with gparted, disk utility or command line:

set boot flag on for sda2 (off on others)
```
sudo sfdisk -A2 /dev/sda
```

Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.

---

### Post by Chengs on 2010-04-03
> **oldfred said:**
> You can set boot flags with gparted, disk utility or command line:

set boot flag on for sda2 (off on others)
```
sudo sfdisk -A2 /dev/sda
```Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.


The boot flag was successfully set on sda2 & removed from sda1. Now I need to change the system type of sda1 to "vfat" from "Empty"

---

### Post by Chengs on 2010-04-03
Hey Oldfred,
                 Tried re-booting, got a message saying invalid boot.ini, but the system booted into XP, got a message asking me if I wanted to un-install Supergrub, which I did successfully. Wondering if I did the right thing.

I again re-booted the system & was happy to see the screen with the options of booting from XP or Ubuntu. Choose the Ubuntu option & have landed at the infamous sh:grub> prompt. 

Rebooted the system once again & at the options screen choose XP. Now, the system does not boot into windows & displays the following message:
----------------------------------
Windows could not start because of a computer disk hardware configuration problem.

Could not read from the selected boot disk. Check boot path and disk hardware.\

Please check the windows documentation about hardware disk configuration and your hardware reference manuals for additional information. 
------------------------------------

Please help me  reset the file system on sda1 to the orginal - vfat (boot info) or Dell Utilitity (disk partition info). Also, awaiting further instructions to solve the booting problem.

Cheers

---

### Post by oldfred on 2010-04-03
With wubi this is usually the fix to get into Ubuntu:
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

I did know you had supergrub, it often figures out how to boot.

You may need to  run the windows repairs as well. I do not know if they will total rewrite the boot.ini and delete the line to boot into wubi? I would make a backup of boot.ini before trying the windows repairs, but if necessary only copy the wubi line back in.

I do not know what settings would be right for a Dell utility partition.

I forgot which version of windows. You can run the repair from your windows CD. If you need more instructions on windows repair post back.

---

### Post by Chengs on 2010-04-03
> **oldfred said:**
> With wubi this is usually the fix to get into Ubuntu:
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

I did know you had supergrub, it often figures out how to boot.

You may need to  run the windows repairs as well. I do not know if they will total rewrite the boot.ini and delete the line to boot into wubi? I would make a backup of boot.ini before trying the windows repairs, but if necessary only copy the wubi line back in.

I do not know what settings would be right for a Dell utility partition.

I forgot which version of windows. You can run the repair from your windows CD. If you need more instructions on windows repair post back.

Need to reset the sda1 to vfat first. This is to bring the system back to how it was originally before I messed it up. Was removing supergrub a mistake?

In the fix for grub2 problem the solution mentioned is to boot into windows & replace wubilr but the hassel is I cannot boot into windows xp. Also, need details to repair windows but the problem is I have to hunt for the windows installation cds.

Cheers

---

### Post by Chengs on 2010-04-08
Have managed to locate the reinstallation CD of windows.

Before I proceed further, could someone help me change the system type of sda1 to vfat or fat16. Had used the Disk utility to change sda1 to make it bootable & check if the booting problem could be sorted out. Now, am able to go into Disk utility & change it so as to make it not bootable but am unable to change the type from Empty to any other.

---

### Post by oldfred on 2010-04-09
If diskutility or gparted will not let you change type, I see many partition related repairs with testdisk. I have not used testdisk.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

I have seen some repairs of partitions with sfdisk. What does 
```
sudo sfdisk -l /dev/sda
```
This will list valid types:
sfdisk -T
I do not know the exact way to change it - this tells more than I know.
man sfdisk

---

### Post by Chengs on 2010-04-22
Hi Oldfred,
               Sorry, was travelling for the past 10 days & therefore could not attend to the problem.

Have managed to change /dev/sda1 to fat16 file system using sfdisk command. The orginal file system was vfat. Is vfat & fat16 file system the same? If not, than what is the id number of vfat? I figured out that the id number of fat16 is 6.

Can proceed to tackle the booting problem once the above is sorted out. The orginal /dev/sda1 partition was as follows:

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /grub/menu.lst /boot/grub/core.img /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

-----------------------------------------------------------------------------------

Have messed up my notebook so much that I want to proceed one step at a time to minimize any further chaos. 

Thanks

P.S: After posting the above, tried rebooting the notebook & was glad to see the menu with the options of booting into Windows xp or Ubuntu. On choosing Windows, was relieved to see windows load up successfully. On rebooting & choosing the Ubuntu option was taken to the infamous sh:grub> prompt. At last, feel that some progress has been made.

---

### Post by oldfred on 2010-04-22
Did you install the fix from back in post #9, since you had the other issues you may have missed it?

---

### Post by Chengs on 2010-04-23
After booting into windows, noticed that /dev/sda1 that was set to fat16(id 6) file system type, using the fsdisk command, was appearing as a separate  drive. On going through the results of the old bootinfo script noticed that the file system type was vfat(id de). So, used fsdisk & reset it to the original.

Installed the fix suggest in Post 9. Now, the following message is being displayed before the sh:grub prompt:

Try (hd0,0) FAT16 No WUBLDR
Try (hd0,1) NTFS5 : It is not possible to boot from the ubuntu image. Please verify that the ubuntu installer was not removed. If that is not the case, please check that the Windows file system  is not corrupted. Reboot into windows and run chkdsk /r. Then try again.

How do I recover from this?

Cheers

---

### Post by oldfred on 2010-04-23
Did you put the wubi file in the correct place, it sounds like it is missing. I do not have wubi so I do not know these errors.

---

### Post by Chengs on 2010-04-25
According to my original boot info (pasted at the end), Grub2 is installed in MBR of /dev/sda & looks in partition #1. Also, besides mention of sda1, sda2 there is a sda2/Wubi entry.

My doubts:

1) Should wubldr be in /dev/sda1 instead of /dev/sda2? 

2) What is this sda2/Wubi reference with file system ext3?

3) Fdisk lists only /dev/sda1 & /dev/sda2. Should there not be another partition with ext3 file system?

4) GParted shows three entries, sda1, sda2 & an unallocated partition of 7.84mb. Is this ext3?

Thanks in advance,

Cheers

-------------------------------------------------------------------------------------


                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /grub/menu.lst /boot/grub/core.img /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /NTLDR /NTDETECT.COM 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /grub/core.img 
                       /boot/grub/core.img

sda2/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260    78,124,094    78,059,835   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,015,230     2,015,168   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       bc05778a-67b9-4505-8c92-c5dee8209763   ext3                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        07D3-0712                              vfat       DellUtility                   
/dev/sda2        98C87F09C87EE542                       ntfs                                     
/dev/sdb1        01D3-6A61                              vfat       IBALL                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/IBALL             vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

```

----------------------------------------------------------------------------------------

---

### Post by oldfred on 2010-04-25
Could you please go back and put code tags around your menu.lst. You use the cursor to highlight the data and click on # in the edit panel above your message. It makes it a lot easier to scroll thru.

Did you miss my entry #2 that said wubi has to boot thru the windows boot loader. The results.txt shows grub in the MBR and you have no Ubuntu install (other than wubi). Because you have both menu.lst and core.img it looks like you tried to install both grub legacy & grub2 to the MBR. I do not know if sda1 was a bootable windows system but it shows older windows possibly win98 or DOS command.com & sys files.Script says Dell utility so that may be all it is.

It looks like you also changed sdb1 to FAT16. I think at most that should be just sda1??

First lets reinstall the windows boot loader and see if you can boot windows.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Chengs on 2010-04-26
Thanks for showing me the use of code tags.

Sdb1 is a usb device, plugged in temporarily to copy files. So, it is only sda1(dos, hidden) & sda2(ntfs,bootable).

When the system is booted, the selection menu (xp or ubuntu) is displayed. I can boot into xp. Have been using this dual boot option without any problems for more than a year. 

I am unable to proceed since I do not see a linux partition.

Cheers

---

### Post by oldfred on 2010-04-26
With wubi you do not have a linux partition, but have a file inside the windows partition root.disk.

Have you lost the choice on the windows boot? The script usually prints out boot.ini for XP systems and it shows an extra line for booting wubi. I do not have wubi so I do not know the details.

---

### Post by Chengs on 2010-04-26
My boot.ini contains the following entries:
------------------------------------------
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr = "Ubuntu"
-------------------------------------------
There are no issues booting into xp. The problem is with Ubuntu, which takes me to the sh:grub> prompt.

Am realling getting fed up trying to sort out this Ubuntu problem. Will be travelling again for 10 days & will not be able to concentrate on this hassel.

Cheers

---

### Post by Chengs on 2010-05-07
Am back after my travels. Would like to sort out this hassel at the earliest.

But, don't know where to start.

---

### Post by oldfred on 2010-05-07
Is it wubi version 9.10?

Fix for grub2 problem with wubi with 9.10
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Chengs on 2010-05-09
Hi,
    Have already replaced wubldr and tried. Get the same message as reported in post # 15.

Have messed this one up badly. 

Can you help me check where(hd0,0 or hd0,1) Wubi & Ubuntu have been installed? It's almost three months since I attempted to update Ubuntu & have been unable to resolve this string of problems.

---

### Post by oldfred on 2010-05-09
Just so we know where we are now lets rerun the boot info script.

---

### Post by Chengs on 2010-05-10
> **oldfred said:**
> Just so we know where we are now lets rerun the boot info script.

Here are the results. Looks like, I've messed the boot process & Ubuntu partition is missing. The previous results are in post # 17. sdb refers to the usb drive. Am sure you will get a better picture now.

Cheers

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /grub/menu.lst /boot/grub/core.img /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /NTLDR 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /grub/core.img /boot/grub/core.img

sda2/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260    78,124,094    78,059,835   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,015,230     2,015,168   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       bc05778a-67b9-4505-8c92-c5dee8209763   ext3                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        07D3-0712                              vfat       DELLUTILITY                   
/dev/sda2        98C87F09C87EE542                       ntfs                                     
/dev/sdb1        01D3-6A61                              vfat       IBALL                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/IBALL             vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda1/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98C87F09C87EE542

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/menu.lst
    ??GB: grub/stage2

==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
## kopt=root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
chainloader    +1


======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda2/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr = "Ubuntu"

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/core.img
    ??GB: ubuntu/disks/boot/grub/menu.lst
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-15-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-16-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-17-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-15-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-16-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-17-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 3f 00  3f 00 ff 00 3f 00 00 00  |......?.?...?...|
00000020  c5 fa 00 00 80 00 29 12  07 d3 07 44 45 4c 4c 55  |......)....DELLU|
00000030  54 49 4c 49 54 59 46 41  54 31 36 20 20 20 00 00  |TILITYFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 ff 0e 13  04 8b 0e 13 04 c1 e1 06  |{...............|
00000060  8e c1 b9 00 01 33 f6 33  ff f3 66 a5 c7 06 72 04  |.....3.3..f...r.|
00000070  45 44 8e c0 bd 00 7c e8  21 01 0f 82 bb 00 66 0f  |ED....|.!.....f.|
00000080  b7 86 16 00 66 d1 e0 66  0f b7 9e 0e 00 66 03 c3  |....f..f.....f..|
00000090  66 03 86 1c 00 66 89 86  3e 00 8b 86 11 00 c1 e8  |f....f..>.......|
000000a0  04 89 86 46 00 bb 00 05  e8 aa 00 0f 82 8a 00 ba  |...F............|
000000b0  10 00 b9 0b 00 be ec 7d  8b fb f3 a6 74 16 83 c3  |.......}....t...|
000000c0  20 4a 75 ee 66 ff 86 3e  00 ff 8e 46 00 75 d6 be  | Ju.f..>...F.u..|
000000d0  d9 7d eb 6d 66 0f b7 86  11 00 66 ba 20 00 00 00  |.}.mf.....f. ...|
000000e0  66 f7 e2 66 0f b7 8e 0b  00 66 03 c1 66 48 66 f7  |f..f.....f..fHf.|
000000f0  f1 66 01 86 3e 00 66 8b  86 3e 00 66 89 46 fc 66  |.f..>.f..>.f.F.f|
00000100  0f b7 47 1a 8b f8 2d 02  00 66 0f b6 9e 0d 00 66  |..G...-..f.....f|
00000110  f7 e3 66 01 86 3e 00 bb  00 07 c7 86 46 00 04 00  |..f..>......F...|
00000120  e8 32 00 72 14 81 c3 00  02 66 ff 86 3e 00 ff 8e  |.2.r.....f..>...|
00000130  46 00 75 ec ea 00 02 70  00 be cc 7d eb 03 be d9  |F.u....p...}....|
00000140  7d e8 02 00 eb fe ac 3c  00 74 09 b4 0e bb 07 00  |}......<.t......|
00000150  cd 10 eb f2 c3 66 8b 86  3e 00 66 33 d2 66 0f b7  |.....f..>.f3.f..|
00000160  8e 18 00 66 f7 f1 66 42  88 96 45 00 66 33 d2 66  |...f..fB..E.f3.f|
00000170  0f b7 8e 1a 00 66 f7 f1  88 96 44 00 89 86 42 00  |.....f....D...B.|
00000180  b8 01 02 8b 8e 42 00 c0  e5 06 0a ae 45 00 86 e9  |.....B......E...|
00000190  8a b6 44 00 8a 96 24 00  cd 13 c3 80 3e c2 07 06  |..D...$.....>...|
000001a0  74 29 b8 01 02 bb 00 06  b9 01 00 b6 00 8a 96 24  |t).............$|
000001b0  00 cd 13 72 16 c6 06 c2  07 06 b8 01 03 bb 00 06  |...r............|
000001c0  b9 01 00 b6 00 8a 96 24  00 cd 13 c3 44 69 73 6b  |.......$....Disk|
000001d0  20 65 72 72 6f 72 0d 0a  00 4d 69 73 73 69 6e 67  | error...Missing|
000001e0  20 27 69 6f 2e 73 79 73  27 0d 0a 00 49 4f 20 20  | 'io.sys'...IO  |
000001f0  20 20 20 20 53 59 53 00  00 00 00 00 00 01 55 aa  |    SYS.......U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 20 14 00  |.<.MSWIN4.1.. ..|
00000010  02 00 02 00 00 f8 f6 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c0 bf 1e 00 80 00 29 61  6a d3 01 4e 4f 20 4e 41  |......)aj..NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|
00000200
```

---

### Post by oldfred on 2010-05-10
I do not have wubi but it looks like you tried installing grub legacy and grub2 and they put files into your windows partition. I just do not know for sure what files wubi has in sda2:
Boot files/dirs:
   /ubuntu/disks/boot/grub/menu.lst 
   /ubuntu/winboot/menu.lst
Next 3 required for windows:
  /boot.ini 
  /NTLDR 
  /NTDETECT.COM 

  /wubildr.mbr 
  /ubuntu/winboot/wubildr.mbr 
  /wubildr
 /ubuntu/winboot/wubildr 
 /ubuntu/disks/root.disk 
 /ubuntu/disks/swap.disk 
Grub2 files:
 /grub/core.img
 /boot/grub/core.img

i am pretty sure that all the extra files are causing issues but do not know for sure what to delete.

---

### Post by Chengs on 2010-05-10
Hey Oldfred,
                 How can I attract the attention of other experts on this forum to help me solve this problem? 

This is really becoming frustrating.

Cheers

---

### Post by oldfred on 2010-05-10
Not many here use wubi. wubi is intended for windows users who want to try Ubuntu on an extended basis, but not reformat and have to add parttitions. If they do not like it it then can be uninstalled as a windows program is uninstalled.
Most on this forum that are knowledgeable have full installs in separate partitions, so wubi issues are not as well known. 

You can review some of the other threads that have wubi in the title, but most that I have seen have been the fix for wubildr.

Even the designer of wubi thinks users will convert to a full install when the next version of Ubuntu comes out or not use it more than 6 months.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

---

