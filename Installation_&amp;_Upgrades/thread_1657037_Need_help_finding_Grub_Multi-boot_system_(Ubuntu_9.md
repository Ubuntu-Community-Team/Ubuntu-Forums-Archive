---
title: "Need help finding Grub: Multi-boot system (Ubuntu 9.10, Kubuntu 10.10, WinXP)"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by mantisdolphin on 2010-12-31
Hi,

I'd appreciate some help with a booting mystery and thanks in advance for taking the time to follow my creative partitioning. :popcorn:  I'm trying to reclaim a couple of partitions (sdb5, sdb7) on a secondary drive for a Kubuntu 10.10 install.  Ubuntu 9.10 (upgraded in place from 9.04) is on sdb3 and I'd like to keep it there for the time being.  

**Background**: When I upgraded 9.04 to 9.10, I lost the ability to boot my system.  So I rebooted with the live CD of 9.04, reinstalled it on an unused partition (sdb7) and was back in business with Grub.   

**Now**: The problem is I installed Kubuntu 10.10 onto sdb5 and sdb7, hoping that its Grub2 would just figure things out, find all the OSes, and make happy with the MBR.  That didn't happen.

Instead, I have no Kubuntu 10.10 booting.  The boot process behaves and looks (same options) just like it did before.  :confused:

So do I just write a line for Kubuntu 10.10 into the Grub *once I find it*?  I thought the Grub menu.lst was on the unused 9.04 partition (sdb7). But I've formatted and overwritten that with Kubuntu 10.10.  Where's the real Grub!?  I don't think I'm using Grub2.  I think I'm still using the 9.04 Grub.  I just don't know where it is.

I thought it might be on sdb6 or sdb8 (I don't remember why or how those got there).  The Ubuntu Grub/Grub2 boot help files on the wiki suggest running a Live CD (I'm using a Kubuntu 10.10 Live CD) to mount the booting Ubuntu partition (once I find it).  One bit of Ubuntu wiki help said to try an fdisk -l command in a terminal: 

```
ubuntu@ubuntu:/media/disk/boot/grub$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        9118    73192140    7  HPFS/NTFS
/dev/sda3            9120        9725     4867695   db  CP/M / CTOS / ...
```

Above is my WinXP drive.  The other drive, sdb, has a couple of ubuntus on it with an NTFS partition as overflow for my WinXP drive.  

```

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000984a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12919   103771836    7  HPFS/NTFS
/dev/sdb2           39587       77825   307154705+   5  Extended
/dev/sdb3           13557       39586   209085975   83  Linux
/dev/sdb4           12920       13556     5116702+  82  Linux swap / Solaris
/dev/sdb5           58783       77825   152962897+  83  Linux
/dev/sdb6           39587       40194     4883697   83  Linux
/dev/sdb7           42198       58782   133218981   83  Linux
/dev/sdb8           40195       42197    16089066   83  Linux

Partition table entries are not in disk order


```

Any suggestions?    

Thanks!

---

### Post by wilee-nilee on 2010-12-31
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by mantisdolphin on 2010-12-31
Wow.  Thanks.  Cool script.  Bookmarked!  So I've got Grub on sda and Grub2 on sdb?  I must be booting from sda and grabbing the menu.lst from sdb3, right?  The script identifies partitions by #[number] and that's confusing me.  Can I just add a line to the menu.lst in sdb3 for Kubuntu 10.10?  Any  recommendations for better ordering this system automagically (short of an axe)?  

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #6 for /grub/stage2 and /grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb8 and 
                       looks at sector 662759193 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb3 and 
                       looks at sector 367052356 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   146,480,669   146,384,280   7 HPFS/NTFS
/dev/sda3         146,496,735   156,232,124     9,735,390  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   207,543,734   207,543,672   7 HPFS/NTFS
/dev/sdb2         635,949,214 1,250,258,624   614,309,411   5 Extended
/dev/sdb5         944,332,830 1,250,258,624   305,925,795  83 Linux
/dev/sdb6         635,949,216   645,716,609     9,767,394  83 Linux
/dev/sdb7         677,894,868   944,332,829   266,437,962  83 Linux
/dev/sdb8         645,716,673   677,894,804    32,178,132  83 Linux
/dev/sdb3         217,777,140   635,949,089   418,171,950  83 Linux
/dev/sdb4         207,543,735   217,777,139    10,233,405  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   971,530,874   971,530,812   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________
Note: sector size is 4096 (not 512)

Disk /dev/sdd: 79.8 GB, 79824777216 bytes
26 heads, 50 sectors/track, 14991 cylinders, total 19488471 sectors
Units = sectors of 1 * 4096 = 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    19,488,469    19,488,407   b W95 FAT32


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D5-0B16                              vfat       DellUtility                   
/dev/sda2        3E043ECB043E8645                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        740A95456DAD8504                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        fa8527b8-5d31-4f48-a2df-3ceb2615ac90   ext3                                     
/dev/sdb4        50408d0f-4463-4b66-a0fa-3a0e9d76e22e   swap                                     
/dev/sdb5        76de3672-c1f8-4780-8d3d-945996698dbf   ext4                                     
/dev/sdb6        611ea11a-737d-45b6-a6b8-89aa67551e21   ext3                                     
/dev/sdb7        96812fb4-5ab9-4e2d-806e-f07496f22a01   ext4                                     
/dev/sdb8        c7a5a86f-5f11-4f66-b647-6746c361c407   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B2B4A72BB4A6F151                       ntfs       FreeAgent Drive               
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        EBFD-F0DE                              vfat      IPOD                    
/dev/sdd         A88B-3652                              vfat       iPod                          
/dev/sde1        E023-2721                              vfat       PENDRIVE                      
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb8        /media/disk-1            ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb6        /media/disk-2            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb7        /media/disk-3            ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5        /media/disk-4            ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=hal,uid=999,utf8,shortname=mixed,flush)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"

============================= sdb6/grub/menu.lst: =============================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=611ea11a-737d-45b6-a6b8-89aa67551e21

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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
savedefault
boot

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		611ea11a-737d-45b6-a6b8-89aa67551e21
kernel		/vmlinuz-2.6.28-11-generic root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		611ea11a-737d-45b6-a6b8-89aa67551e21
kernel		/vmlinuz-2.6.28-11-generic root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		611ea11a-737d-45b6-a6b8-89aa67551e21
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.31-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.31-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-9-rt (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-9-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.31-9-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.28-14-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, memtest86+ (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		unknown Linux distribution (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.35-22-generic=/dev/sdb5 
root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro   quiet splash
initrd	/boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		unknown Linux distribution (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz root=/dev/sdb5 
savedefault
boot


=================== sdb6: Location of files loaded by Grub: ===================


 329.2GB: grub/menu.lst
 329.3GB: grub/stage2
 326.0GB: initrd.img-2.6.28-11-generic
 326.0GB: vmlinuz-2.6.28-11-generic

=========================== sdb7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 76de3672-c1f8-4780-8d3d-945996698dbf
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d5-0b16
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3e043ecb043e8645
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-9-rt (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 611ea11a-737d-45b6-a6b8-89aa67551e21
	linux /vmlinuz-2.6.28-11-generic root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro quiet splash
	initrd /initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 611ea11a-737d-45b6-a6b8-89aa67551e21
	linux /vmlinuz-2.6.28-11-generic root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro single
	initrd /initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 611ea11a-737d-45b6-a6b8-89aa67551e21
	linux /memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 /               ext4    errors=remount-ro 0       1
/dev/sdb8       /boot           ext4    defaults        0       2
# /usr was on /dev/sdb5 during installation
UUID=76de3672-c1f8-4780-8d3d-945996698dbf /usr            ext4    defaults        0       2
# swap was on /dev/sdb4 during installation
UUID=50408d0f-4463-4b66-a0fa-3a0e9d76e22e none            swap    sw              0       0

=================== sdb7: Location of files loaded by Grub: ===================


 390.1GB: boot/grub/core.img
 381.5GB: boot/grub/grub.cfg
 347.3GB: boot/initrd.img-2.6.35-22-generic
 347.2GB: boot/vmlinuz-2.6.35-22-generic
 347.3GB: initrd.img
 347.2GB: vmlinuz

============================= sdb8/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 76de3672-c1f8-4780-8d3d-945996698dbf
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos8)'
search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
	linux	/vmlinuz-2.6.35-22-generic root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d5-0b16
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3e043ecb043e8645
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-9-rt (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sdb8: Location of files loaded by Grub: ===================


 339.3GB: grub/core.img
 339.3GB: grub/grub.cfg
 330.7GB: initrd.img-2.6.35-22-generic
 330.7GB: vmlinuz-2.6.35-22-generic

=========================== sdb3/boot/grub/menu.lst: ===========================

# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Tue Jul 28 17:06:47 2009
#
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.21343'.  You can restore it like this.
# dd if=/boot/grub/mbr.sda.21343 of=/dev/sda bs=512 count=1
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
gfxmenu /boot/grub/deep_stage1
# End GRUB global section
# Other bootable partition config begins
  title Windows (on /dev/sda2)
  map (hd0,0) (hd0,1)
  map (hd0,1) (hd0,0)
  rootnoverify (hd0,1)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Other bootable partition config begins
  title Windows (on /dev/sdb1)
  map (hd0) (hd1)
  map (hd1) (hd0)
  rootnoverify (hd1,0)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/sdb3)
  root (hd1,2)
  kernel /boot/vmlinuz root=/dev/sdb3 ro vga=normal
# Linux bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/sdb5)
  root (hd1,4)
  kernel /boot/vmlinuz root=/dev/sdb5 ro vga=normal
# Linux bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/sdb6)
  root (hd1,5)
  kernel /boot/vmlinuz root=/dev/sdb6 ro vga=normal
# Linux bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/sdb7)
  root (hd1,6)
  kernel /boot/vmlinuz root=/dev/sdb7 ro vga=normal
# Linux bootable partition config ends
# Other bootable partition config begins
  title Windows (on /dev/sdc1)
  map (hd0) (hd2)
  map (hd2) (hd0)
  rootnoverify (hd2,0)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Linux bootable initrd config begins
  title Linux initrd /tmp/boot/boot/initrd.img-2.6.28-13-generic (on /dev/sdb3)
  root (hd1,2)
  kernel /boot/vmlinuz root=/dev/sdb3 ramdisk_size=20632 root=/dev/ram0 rw
  initrd /tmp/boot/boot/initrd.img-2.6.28-13-generic
# Linux bootable initrd config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd1,2)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/sdb3)
root (hd1,2)
setup (hd1,2)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)
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
# kopt=root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fa8527b8-5d31-4f48-a2df-3ceb2615ac90

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

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-9-rt
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-9-rt
quiet

title		Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-9-rt

title		Ubuntu 9.10, kernel 2.6.28-14-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.10, memtest86+
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb4 during installation
UUID=50408d0f-4463-4b66-a0fa-3a0e9d76e22e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 187.9GB: boot/grub/menu.lst
 187.9GB: boot/grub/stage2
 187.8GB: boot/initrd.img-2.6.28-14-generic
 187.9GB: boot/initrd.img-2.6.31-14-generic
 187.9GB: boot/initrd.img-2.6.31-15-generic
 188.0GB: boot/initrd.img-2.6.31-16-generic
 187.9GB: boot/initrd.img-2.6.31-17-generic
 187.9GB: boot/initrd.img-2.6.31-19-generic
 187.9GB: boot/initrd.img-2.6.31-20-generic
 187.9GB: boot/initrd.img-2.6.31-21-generic
 187.9GB: boot/initrd.img-2.6.31-22-generic
 188.0GB: boot/initrd.img-2.6.31-9-rt
 187.8GB: boot/vmlinuz-2.6.28-14-generic
 188.0GB: boot/vmlinuz-2.6.31-14-generic
 187.9GB: boot/vmlinuz-2.6.31-15-generic
 187.9GB: boot/vmlinuz-2.6.31-16-generic
 187.9GB: boot/vmlinuz-2.6.31-17-generic
 188.0GB: boot/vmlinuz-2.6.31-19-generic
 187.9GB: boot/vmlinuz-2.6.31-20-generic
 187.8GB: boot/vmlinuz-2.6.31-21-generic
 187.9GB: boot/vmlinuz-2.6.31-22-generic
 188.0GB: boot/vmlinuz-2.6.31-9-rt
 187.9GB: initrd.img
 187.9GB: initrd.img.old
 187.9GB: vmlinuz
 187.8GB: vmlinuz.old


```

---

### Post by drs305 on 2010-12-31
A good solution would be to boot into your 10.10 installation on sdb - it actually doesn't matter which sdb partition it is on for the following commands:
```
sudo grub-install /dev/sdb
sudo update-grub
```
This will ensure the MBR on sdb correctly points to your sdb partition on which you are currently running Ubuntu.


Change the BIOS to boot the sdb drive (640GB) first.

Once you have rebooted and found everything is on the menu, you can then install the Windows bootloader on the (former) sda drive*. Although G2 should see and boot Windows from the sdb menu, having the sda MBR point to Windows is a good backup. Should sdb G2 fail, you can change the BIOS to point to sda so you can at least boot Windows. 

To set up the sda drive to boot Windows only:
```
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR="Red"]sda[/COLOR] mbr
```
Disregard the messages the commands generate, as you are not really fully installing lilo.

* Important: I wrote the part about Windows based on your current setup for clarity. **However, if you have changed the BIOS order, the Windows drive has probably become [COLOR="Red"]sdb[/COLOR] and you will need to change the lilo commands accordingly.** Verify the designation before running the commands.

If I've confused you, just forget the lilo part for now and stop after running "update-grub" and changing the BIOS boot order.

---

### Post by presence1960 on 2010-12-31
> **mantisdolphin said:**
> Wow.  Thanks.  Cool script.  Bookmarked!  So I've got Grub on sda and Grub2 on sdb?  I must be booting from sda and grabbing the menu.lst from sdb3, right?  The script identifies partitions by #[number] and that's confusing me.  Can I just add a line to the menu.lst in sdb3 for Kubuntu 10.10?  Any  recommendations for better ordering this system automagically (short of an axe)?  

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #6 for /grub/stage2 and /grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb8 and 
                       looks at sector 662759193 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb3 and 
                       looks at sector 367052356 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   146,480,669   146,384,280   7 HPFS/NTFS
/dev/sda3         146,496,735   156,232,124     9,735,390  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   207,543,734   207,543,672   7 HPFS/NTFS
/dev/sdb2         635,949,214 1,250,258,624   614,309,411   5 Extended
/dev/sdb5         944,332,830 1,250,258,624   305,925,795  83 Linux
/dev/sdb6         635,949,216   645,716,609     9,767,394  83 Linux
/dev/sdb7         677,894,868   944,332,829   266,437,962  83 Linux
/dev/sdb8         645,716,673   677,894,804    32,178,132  83 Linux
/dev/sdb3         217,777,140   635,949,089   418,171,950  83 Linux
/dev/sdb4         207,543,735   217,777,139    10,233,405  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   971,530,874   971,530,812   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________
Note: sector size is 4096 (not 512)

Disk /dev/sdd: 79.8 GB, 79824777216 bytes
26 heads, 50 sectors/track, 14991 cylinders, total 19488471 sectors
Units = sectors of 1 * 4096 = 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    19,488,469    19,488,407   b W95 FAT32


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D5-0B16                              vfat       DellUtility                   
/dev/sda2        3E043ECB043E8645                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        740A95456DAD8504                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        fa8527b8-5d31-4f48-a2df-3ceb2615ac90   ext3                                     
/dev/sdb4        50408d0f-4463-4b66-a0fa-3a0e9d76e22e   swap                                     
/dev/sdb5        76de3672-c1f8-4780-8d3d-945996698dbf   ext4                                     
/dev/sdb6        611ea11a-737d-45b6-a6b8-89aa67551e21   ext3                                     
/dev/sdb7        96812fb4-5ab9-4e2d-806e-f07496f22a01   ext4                                     
/dev/sdb8        c7a5a86f-5f11-4f66-b647-6746c361c407   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B2B4A72BB4A6F151                       ntfs       FreeAgent Drive               
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        EBFD-F0DE                              vfat      IPOD                    
/dev/sdd         A88B-3652                              vfat       iPod                          
/dev/sde1        E023-2721                              vfat       PENDRIVE                      
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb8        /media/disk-1            ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb6        /media/disk-2            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb7        /media/disk-3            ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5        /media/disk-4            ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=hal,uid=999,utf8,shortname=mixed,flush)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"

============================= sdb6/grub/menu.lst: =============================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=611ea11a-737d-45b6-a6b8-89aa67551e21

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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
savedefault
boot

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		611ea11a-737d-45b6-a6b8-89aa67551e21
kernel		/vmlinuz-2.6.28-11-generic root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		611ea11a-737d-45b6-a6b8-89aa67551e21
kernel		/vmlinuz-2.6.28-11-generic root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		611ea11a-737d-45b6-a6b8-89aa67551e21
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.31-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.31-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-9-rt (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-9-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.31-9-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.28-14-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 9.10, memtest86+ (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		unknown Linux distribution (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.35-22-generic=/dev/sdb5 
root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro   quiet splash
initrd	/boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		unknown Linux distribution (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz root=/dev/sdb5 
savedefault
boot


=================== sdb6: Location of files loaded by Grub: ===================


 329.2GB: grub/menu.lst
 329.3GB: grub/stage2
 326.0GB: initrd.img-2.6.28-11-generic
 326.0GB: vmlinuz-2.6.28-11-generic

=========================== sdb7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 76de3672-c1f8-4780-8d3d-945996698dbf
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set 96812fb4-5ab9-4e2d-806e-f07496f22a01
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d5-0b16
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3e043ecb043e8645
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-9-rt (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 611ea11a-737d-45b6-a6b8-89aa67551e21
	linux /vmlinuz-2.6.28-11-generic root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro quiet splash
	initrd /initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 611ea11a-737d-45b6-a6b8-89aa67551e21
	linux /vmlinuz-2.6.28-11-generic root=UUID=36f753ff-9747-4284-b188-e545cec0f692 ro single
	initrd /initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 611ea11a-737d-45b6-a6b8-89aa67551e21
	linux /memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 /               ext4    errors=remount-ro 0       1
/dev/sdb8       /boot           ext4    defaults        0       2
# /usr was on /dev/sdb5 during installation
UUID=76de3672-c1f8-4780-8d3d-945996698dbf /usr            ext4    defaults        0       2
# swap was on /dev/sdb4 during installation
UUID=50408d0f-4463-4b66-a0fa-3a0e9d76e22e none            swap    sw              0       0

=================== sdb7: Location of files loaded by Grub: ===================


 390.1GB: boot/grub/core.img
 381.5GB: boot/grub/grub.cfg
 347.3GB: boot/initrd.img-2.6.35-22-generic
 347.2GB: boot/vmlinuz-2.6.35-22-generic
 347.3GB: initrd.img
 347.2GB: vmlinuz

============================= sdb8/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 76de3672-c1f8-4780-8d3d-945996698dbf
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos8)'
search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
	linux	/vmlinuz-2.6.35-22-generic root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=96812fb4-5ab9-4e2d-806e-f07496f22a01 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set c7a5a86f-5f11-4f66-b647-6746c361c407
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d5-0b16
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3e043ecb043e8645
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-9-rt (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro single
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set fa8527b8-5d31-4f48-a2df-3ceb2615ac90
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sdb8: Location of files loaded by Grub: ===================


 339.3GB: grub/core.img
 339.3GB: grub/grub.cfg
 330.7GB: initrd.img-2.6.35-22-generic
 330.7GB: vmlinuz-2.6.35-22-generic

=========================== sdb3/boot/grub/menu.lst: ===========================

# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Tue Jul 28 17:06:47 2009
#
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.21343'.  You can restore it like this.
# dd if=/boot/grub/mbr.sda.21343 of=/dev/sda bs=512 count=1
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
gfxmenu /boot/grub/deep_stage1
# End GRUB global section
# Other bootable partition config begins
  title Windows (on /dev/sda2)
  map (hd0,0) (hd0,1)
  map (hd0,1) (hd0,0)
  rootnoverify (hd0,1)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Other bootable partition config begins
  title Windows (on /dev/sdb1)
  map (hd0) (hd1)
  map (hd1) (hd0)
  rootnoverify (hd1,0)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/sdb3)
  root (hd1,2)
  kernel /boot/vmlinuz root=/dev/sdb3 ro vga=normal
# Linux bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/sdb5)
  root (hd1,4)
  kernel /boot/vmlinuz root=/dev/sdb5 ro vga=normal
# Linux bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/sdb6)
  root (hd1,5)
  kernel /boot/vmlinuz root=/dev/sdb6 ro vga=normal
# Linux bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/sdb7)
  root (hd1,6)
  kernel /boot/vmlinuz root=/dev/sdb7 ro vga=normal
# Linux bootable partition config ends
# Other bootable partition config begins
  title Windows (on /dev/sdc1)
  map (hd0) (hd2)
  map (hd2) (hd0)
  rootnoverify (hd2,0)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Linux bootable initrd config begins
  title Linux initrd /tmp/boot/boot/initrd.img-2.6.28-13-generic (on /dev/sdb3)
  root (hd1,2)
  kernel /boot/vmlinuz root=/dev/sdb3 ramdisk_size=20632 root=/dev/ram0 rw
  initrd /tmp/boot/boot/initrd.img-2.6.28-13-generic
# Linux bootable initrd config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd1,2)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/sdb3)
root (hd1,2)
setup (hd1,2)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)
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
# kopt=root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fa8527b8-5d31-4f48-a2df-3ceb2615ac90

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

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-9-rt
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-9-rt
quiet

title		Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.31-9-rt

title		Ubuntu 9.10, kernel 2.6.28-14-generic
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.10, memtest86+
uuid		fa8527b8-5d31-4f48-a2df-3ceb2615ac90
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=fa8527b8-5d31-4f48-a2df-3ceb2615ac90 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb4 during installation
UUID=50408d0f-4463-4b66-a0fa-3a0e9d76e22e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 187.9GB: boot/grub/menu.lst
 187.9GB: boot/grub/stage2
 187.8GB: boot/initrd.img-2.6.28-14-generic
 187.9GB: boot/initrd.img-2.6.31-14-generic
 187.9GB: boot/initrd.img-2.6.31-15-generic
 188.0GB: boot/initrd.img-2.6.31-16-generic
 187.9GB: boot/initrd.img-2.6.31-17-generic
 187.9GB: boot/initrd.img-2.6.31-19-generic
 187.9GB: boot/initrd.img-2.6.31-20-generic
 187.9GB: boot/initrd.img-2.6.31-21-generic
 187.9GB: boot/initrd.img-2.6.31-22-generic
 188.0GB: boot/initrd.img-2.6.31-9-rt
 187.8GB: boot/vmlinuz-2.6.28-14-generic
 188.0GB: boot/vmlinuz-2.6.31-14-generic
 187.9GB: boot/vmlinuz-2.6.31-15-generic
 187.9GB: boot/vmlinuz-2.6.31-16-generic
 187.9GB: boot/vmlinuz-2.6.31-17-generic
 188.0GB: boot/vmlinuz-2.6.31-19-generic
 187.9GB: boot/vmlinuz-2.6.31-20-generic
 187.8GB: boot/vmlinuz-2.6.31-21-generic
 187.9GB: boot/vmlinuz-2.6.31-22-generic
 188.0GB: boot/vmlinuz-2.6.31-9-rt
 187.9GB: initrd.img
 187.9GB: initrd.img.old
 187.9GB: vmlinuz
 187.8GB: vmlinuz.old


```

If you make sdb (640 GB) hard disk first to boot in the hard disk boot priority in BIOS you will be all set to go.

---

### Post by mantisdolphin on 2011-01-01
Changing the boot drive did it.  I'm zipping around in Kubuntu 10.10 now.  Lots of polish in this OS to enjoy.  Thanks everyone!

---

### Post by presence1960 on 2011-01-01
> **mantisdolphin said:**
> Changing the boot drive did it.  I'm zipping around in Kubuntu 10.10 now.  Lots of polish in this OS to enjoy.  Thanks everyone!

Glad you got it working! Enjoy Ubuntu.

---

