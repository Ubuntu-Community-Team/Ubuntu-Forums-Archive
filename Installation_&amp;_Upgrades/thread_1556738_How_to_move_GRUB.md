---
title: "How to move GRUB?"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by OmahaVike on 2010-08-19
i had an existing install of 10.04 and added a new hard drive.  installed 8.04 (having stability issues with 64 bit 10.04) on the new drive.  now i want to pull that new hard drive and revert back to 10.04.

Question:  i seem to recall from my dapper days that simply pulling the newly installed drive causes all kinds of nightmares.  i believe that installing a new buntu on a new drive moves the boot pointer to the new drive.  how do i point it back to my original drive?

thanks so much for all help!

---

### Post by presence1960 on 2010-08-19
Pull the new hard disk and then boot from the Ubuntu 10.04 Live CD. Boot to the desktop then follow [these instructions]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") to reinstall GRUB 2 for 10.04. If you have a problem(s) then do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by OmahaVike on 2010-08-25
thank you SO much presence.  that script is awesome.  will you be kind to lend a hand to look at the output for me?

note that the grub menu.lst from sdd1 appears to be the correct one i wish to use.  the one off sdf1 is my old old old old 8.04 one that i don't really care about anymore -- just keep the drive around in case i forgot some old data.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #5 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on boot drive #5 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sde
 => Grub 2 is installed in the MBR of /dev/sdf and looks for 
    (UUID=dfd7c2e0-1658-4abe-a256-aaf981ff3a78)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdf2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdf2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf2 starts at sector 182273490.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   976,768,064   976,768,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   490,207,409   490,207,347   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   781,417,664   781,417,602  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   224,829,674   224,829,612  83 Linux
/dev/sdd2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sdd5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   312,576,704   312,576,642  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   182,273,489   182,273,427  83 Linux
/dev/sdf2         182,273,490   240,107,489    57,834,000   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9fc4ff77-8c88-49be-9f61-36951f370896   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3d7cf150-0a22-4fe5-bd4b-ea52524ca3a9   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        123a5faa-9e91-49c2-b5d1-2e64b43c42dd   ext3                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        ff409183-9ce7-438f-ab9e-a836d977ce10   ext3                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        c567ac4b-1e8a-4889-b24d-99591975b8da   swap                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        e6cbf8e0-4e99-4c7b-bc90-82701686bc78   ext3                                     
/dev/sde: PTTYPE="dos" 
/dev/sdf1        37e86a51-a3de-4107-a481-c59c660129aa   ext3                                     
/dev/sdf2        456D-191F                              vfat                                     
/dev/sdf: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/ff409183-9ce7-438f-ab9e-a836d977ce10 ext3       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdd1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro  single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 ro  single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 10.04.1 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro quiet splash 
initrd		/boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro single 
initrd		/boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro quiet splash 
initrd		/boot/initrd.img-2.6.24-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode) (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro single 
initrd		/boot/initrd.img-2.6.24-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro single 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ff409183-9ce7-438f-ab9e-a836d977ce10 	/               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=c567ac4b-1e8a-4889-b24d-99591975b8da none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=9fc4ff77-8c88-49be-9f61-36951f370896	/storage/video	ext3	users,atime,auto,rw,nodev,exec,nosuid	0	0
UUID=3d7cf150-0a22-4fe5-bd4b-ea52524ca3a9	/storage/audio	ext3	users,atime,auto,rw,nodev,exec,nosuid	0	0
UUID=e6cbf8e0-4e99-4c7b-bc90-82701686bc78	/storage/video/football		ext3	users,atime,auto,rw,nodev,exec,nosuid	0	0
UUID=37e86a51-a3de-4107-a481-c59c660129aa	/storage/OLDUBUNTU-DYING	ext3	users,atime,auto,rw,nodev,exec,nosuid	0	0
UUID=456D-191F					/storage/OLDWINDOZE		vfat 	defaults 1 0
UUID=123a5faa-9e91-49c2-b5d1-2e64b43c42dd	/storage/other	ext3	users,atime,auto,rw,nodev,exec,nosuid   0       0


=================== sdd1: Location of files loaded by Grub: ===================


  22.3GB: boot/grub/menu.lst
  18.4GB: boot/grub/stage2
  18.4GB: boot/initrd.img-2.6.24-26-generic
  22.2GB: boot/initrd.img-2.6.24-27-generic
  24.7GB: boot/initrd.img-2.6.24-27-generic.bak
  22.4GB: boot/initrd.img-2.6.32-22-generic
  40.9GB: boot/initrd.img-2.6.32-23-generic
  35.4GB: boot/initrd.img-2.6.32-24-generic
  18.4GB: boot/vmlinuz-2.6.24-26-generic
  24.7GB: boot/vmlinuz-2.6.24-27-generic
  22.3GB: boot/vmlinuz-2.6.32-22-generic
  35.5GB: boot/vmlinuz-2.6.32-23-generic
  22.3GB: boot/vmlinuz-2.6.32-24-generic
  35.4GB: initrd.img
  40.9GB: initrd.img.old
  22.3GB: vmlinuz
  35.5GB: vmlinuz.old

=========================== sdf1/boot/grub/menu.lst: ===========================

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

# HARDY
default		0

# DAPPER
# default		11

#  XP
# default 	12

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
# kopt=root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro single
initrd		/boot/initrd.img-2.6.24-28-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=37e86a51-a3de-4107-a481-c59c660129aa ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-51-386
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/hda2 ro quiet splash
 
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-51-386 (recovery mode)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/hda2 ro single
 
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-29-386
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro quiet splash
 
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro single
 
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-28-386
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-27-386
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin 
 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin 
 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin 
 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin 
 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin 
 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single 
 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin 
 
savedefault
boot


=============================== sdf1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
# UUID=37e86a51-a3de-4107-a481-c59c660129aa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
# UUID=e6cbf8e0-4e99-4c7b-bc90-82701686bc78 /home/storage/video/football	ext3	relatime,errors=remount-ro 0
 UUID=e6cbf8e0-4e99-4c7b-bc90-82701686bc78 /home/storage/video/football	ext3	relatime,errors=remount-ro 0
# UUID=37e86a51-a3de-4107-a481-c59c660129aa /home/storage/video/football               ext3    relatime,errors=remount-ro 0       1


# /dev/sda5
UUID=d3745bd1-5bcd-4208-a6c7-4220ad8443ce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#
# pmf 2008.05.13
#
# old dapper home
UUID=123a5faa-9e91-49c2-b5d1-2e64b43c42dd /home/storage/storage ext3 defaults,noatime 0 2
#
# backups
# UUID=456D-191F /home/storage/backups ??????????
#
# dapper
#UUID=baf3841f-ff5b-423e-9ca2-84696885c28f /home/storage/dapper ext3 defaults,noatime 0 2
#
#  video SATA from server(459 gig)
#
UUID=9fc4ff77-8c88-49be-9f61-36951f370896 /home/storage/video ext3 defaults,noatime 0 2
#
#  audio SATA from server(231 gig)
#
UUID=3d7cf150-0a22-4fe5-bd4b-ea52524ca3a9 /home/storage/audio ext3 defaults,noatime 0 2
#
#
#  UNCOMMENT THE FOLLOWING FOR THE IDE DRIVES.  WILL NOT BOOT SMOOTHLY
#  WITH THESE UNCOMMENTED AND DRIVES NOT ON.
#
#  Unknown #1 IDE from server
#
#UUID=774375a4-bab1-408a-a20a-962386d7bf83 /home/storage/unknownIDE1 ext3 defaults,noatime 0 2
#
#  Unknown #2 IDE from server
#
#UUID=917e7c4d-f646-4770-a843-48bd45cda1bd /home/storage/unknownIDE2 ext3 defaults,noatime 0 2
#
#  Unknown #3 IDE from server
#
#  DON'T MOUNT THIS.  THIS IS A SWAP.
## UUID=bb1cb2e1-b830-4f76-a2e0-64dfeb80c3bf /home/storage/unknownIDE3 ext3 defaults,noatime 0 2
#
#  Unknown #4 IDE from server
#
#UUID=c77e0f36-a649-4590-932a-fc8d3ddbd741 /home/storage/unknownIDE4 ext3 defaults,noatime 0 2

#  USB group
none /proc/bus/usb usbfs devgid=1005,devmode=664 0 0

=================== sdf1: Location of files loaded by Grub: ===================


  24.8GB: boot/grub/menu.lst
  23.7GB: boot/grub/stage2
  23.8GB: boot/initrd.img-2.6.24-24-generic
  23.8GB: boot/initrd.img-2.6.24-24-generic.bak
  23.8GB: boot/initrd.img-2.6.24-25-generic
  23.8GB: boot/initrd.img-2.6.24-25-generic.bak
  23.8GB: boot/initrd.img-2.6.24-26-generic
  24.8GB: boot/initrd.img-2.6.24-26-generic.bak
  24.8GB: boot/initrd.img-2.6.24-27-generic
  24.8GB: boot/initrd.img-2.6.24-27-generic.bak
  53.0GB: boot/initrd.img-2.6.24-28-generic
  24.8GB: boot/initrd.img-2.6.24-28-generic.bak
  23.8GB: boot/vmlinuz-2.6.24-24-generic
  23.7GB: boot/vmlinuz-2.6.24-25-generic
  23.7GB: boot/vmlinuz-2.6.24-26-generic
  24.8GB: boot/vmlinuz-2.6.24-27-generic
  24.8GB: boot/vmlinuz-2.6.24-28-generic
  53.0GB: initrd.img
  24.8GB: initrd.img.old
  24.8GB: vmlinuz
  24.8GB: vmlinuz.old

================================ sdf2/menu.lst: ================================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, memtest86+ (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, memtest86+ (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, memtest86+ (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, memtest86+ (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu, memtest86+ (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1) (on /dev/hda2) (on /dev/hdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=================== sdf2: Location of files loaded by Grub: ===================


    ??GB: menu.lst

```

entirely appreciate yours, or any one else's, help in repointing to the correct drive.

---

### Post by oldfred on 2010-08-25
When you installed sdd must have been sda as its menu.lst shows hd0,0 as the install drive,partition. But now as sdd it will be hd3,0 in grub legacy partition counting.

[https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier](https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier)

#reset grub boot
[COLOR=DarkRed]sudo grub[/COLOR]
find /boot/grub/stage1 #you will get a response such as  (hd3,0)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or [COLOR=DarkRed]root (hd3,0)[/COLOR]
[COLOR=DarkRed]setup (hd3)[/COLOR]
[COLOR=DarkRed]quit[/COLOR]

You can do this from liveCD or if you can boot into your install you can run it from that. Then run from your boot run:
sudo update-grub

If that does not work we will have to do the full chroot into your partition from the liveCD.

If you move drives around you may have to reinstall grub again if the drive numbers are different.

---

### Post by presence1960 on 2010-08-25
if you put sdd (120 GB) as first in the hard disk boot order in BIOS you should boot right up. In Legacy GRUB the hard disk # [x in (hdx,y)] is not determined by the order of your disks in sudo fdisk -l or how linux reads your disk order, but rather by the order of your disks in BIOS in the hard disk boot order. This peculiar trait of Legacy GRUB has confused more than a few people. GRUB 2 has eliminated this quirk.

So if you put sdd as first hard disk to boot your menu.lst from sdd1 will be correct when it reads (hd0,0) for ubuntu.

             ```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #5 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc
 [COLOR="Red"]=> Grub 0.97 is installed in the MBR of /dev/sdd and looks on boot drive #5 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR]
 => Windows is installed in the MBR of /dev/sde
 => Grub 2 is installed in the MBR of /dev/sdf and looks for 
    (UUID=dfd7c2e0-1658-4abe-a256-aaf981ff3a78)/boot/grub.
```


To change the order boot your machine and enter Setup (BIOS). Look for the hard disk boot order menu. Set sdd as first in that order. Save changes to CMOS and continue booting. At GRUB choose ubuntu and you should be good to go.

---

### Post by OmahaVike on 2010-08-30
big thanks to the both of you.  solved.

just some follow-up comments for "the next person" who has this problem.

i tried to change the drive order in BIOS with no resolution.  unfortunately, i didn't write down my original order, so things really got messed up.  anticipating a cleanup job with six or so drives in my fstab.

anyhow, i revisited presence1960's link "follow these instructions to reinstall GRUB 2".  unfortunately, when you follow those directions and reboot, I ended up with a grub prompt.  eeek!

after poking around a little, and following the command sequence oldfred gave, i put it back together.  cheer!

one note to help people with their frustration.  THERE IS A SPACE BETWEEN root and (hdx,y).  likewise, there is a space between setup and (hd3).  so if you're writing it down on paper, don't forget that.  of course, if you're fortunate enough to have a mouse and copy/paste ability, you should have nothing to worry about.

thanks again to oldfred and presence1960.  much obliged.

---

