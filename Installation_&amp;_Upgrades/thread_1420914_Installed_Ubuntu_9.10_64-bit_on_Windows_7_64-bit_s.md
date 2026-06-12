---
title: "Installed Ubuntu 9.10 64-bit on Windows 7 64-bit system, Locks up loading grub"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by rben13 on 2010-03-03
Hi,

At the suggestion of the person who replied to my earlier post, I've moved this to a new thread after slapping my forehead loudly.

My system originally had Windows XP set up to dual boot with Kubuntu. Then I installed Vista (this was a while back) and wound up using SuperGrub to get Windows Vista booting. I was hoping both Windows XP and Kubuntu would be available, and while I could boot into Kubuntu, something else I did messed up the display drivers and I never got around to fixing it.

Then I installed Windows 7, which went surprisingly well. Afterwards my booting was a 2 stage process, first I'd get a grub menu, then another OS selection menu, setup by Windows, I believe. But everything worked at least as well as it had with Vista.

Then, today, I decided to take the plunge and install Ubuntu. I told the installer to put the software on my removable 640G hard drive, leaving a 100G partition for Windows and using the rest for Ubuntu.

Unfortunately, now my computer won't boot properly. It locks up at the first grub menu. I'm booted off the Live CD right now, hoping someone can give me some guidance. I guess I could use Windows 7 installation CD to fix up the Windows side, but I'm not sure what to do and really don't want to spend a long time reinstalling applications. (My data is, thankfully, backed up off-line.)

Please help.

Thanks,
Ray

---

### Post by oldfred on 2010-03-03
Please post this script from a liveCD so we can see exactly what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by rben13 on 2010-03-04
Here is the info. As you can see, there's quite a lot. Thank you ahead of time for your help.

Ray

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=4e2d60b7-786e-45bc-a153-15481fee9a37)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sdi

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /NST/menu.lst /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdi1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5f5f5f5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x96ac9c0a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   586,067,967   586,065,920   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12b24b02

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   470,286,809   470,286,747  83 Linux
/dev/sdc2         470,286,810   490,223,474    19,936,665   5 Extended
/dev/sdc5         470,286,873   490,223,474    19,936,602  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4171b68c

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   210,885,254   210,883,207   7 HPFS/NTFS
/dev/sdd2         210,885,255 1,250,258,624 1,039,373,370   5 Extended
/dev/sdd5         210,885,318 1,226,498,489 1,015,613,172  83 Linux
/dev/sdd6       1,226,498,553 1,250,258,624    23,760,072  82 Linux swap / Solaris


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

Partition  Boot         Start           End          Size  Id System

/dev/sdi1    *             63     3,948,542     3,948,480   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       909c5004-58cc-4dad-88df-299aca902900   ext3                                     
/dev/sda1        06A45D6BA45D5E6D                       ntfs       Thornglatch WinXP Drive       
/dev/sdb1        F07AC5E97AC5ACA2                       ntfs       Vista-64                      
/dev/sdc1        f0ca6709-1b6e-4431-86b2-b8c1bc0e3777   ext3                                     
/dev/sdc5        9c5d01a0-bda1-4dc7-9e8b-e3a58cdee526   swap                                     
/dev/sdd1        B0BA1240BA12040E                       ntfs       WD Cavier Black 640G          
/dev/sdd5        4e2d60b7-786e-45bc-a153-15481fee9a37   ext4                                     
/dev/sdd6        c0977b77-7a67-4b3c-8b0d-8fba36bf56a2   swap                                     
/dev/sdi1        0000-0F9B                              vfat       REDUSB-2G                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdi1        /media/REDUSB-2G         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


============================== sdb1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD



#default 0		#Pick the task to be run if the user doesn't pick one within the time limit.

#timeout 10		#Give the user 10 seconds to choose a task.



#We use the "title" keyword to indicate a new entry in the menu.



#title 		Windows XP	#This is our first entry - it's number 0

find --set-root	/NTLDR  	#Search for NTLDR on all partitions. Once found, use that partition as root.

makeactive  			#Make this the active partition

chainloader /NTLDR		#Run NTLDR, the Windows XP bootloader

#If we're using a menu, we don't need to use the `boot` command - it's automatically implied.



#This is our second entry

#title		Ubuntu

#root		(hd1,1)   	#Load Ubuntu from the 2nd harddrive's 3rd partition.

#Next Line: Translate (hd1,2) to Linux notation and set that as the root partition

#kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdbc

#initrd		/boot/initrd.img-2.6.22-14-generic

#End Ubuntu entry



#That's it!


==================== sdb1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=F07AC5E97AC5ACA2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=F07AC5E97AC5ACA2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=F07AC5E97AC5ACA2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=F07AC5E97AC5ACA2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=F07AC5E97AC5ACA2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5fe297a7-b4ed-443b-90f3-53e18ca207f8 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5fe297a7-b4ed-443b-90f3-53e18ca207f8 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5fe297a7-b4ed-443b-90f3-53e18ca207f8 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5fe297a7-b4ed-443b-90f3-53e18ca207f8 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


======================== sdb1/ubuntu/winboot/menu.lst: ========================

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

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: ubuntu/disks/boot/grub/menu.lst
    ??GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.27-9-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.27-9-generic

============================= sdb1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=9c5d01a0-bda1-4dc7-9e8b-e3a58cdee526 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 134.0GB: boot/grub/menu.lst
 134.0GB: boot/grub/stage2
 134.0GB: boot/initrd.img-2.6.27-11-generic
 134.0GB: boot/initrd.img-2.6.27-14-generic
 134.0GB: boot/initrd.img-2.6.27-7-generic
 133.9GB: boot/vmlinuz-2.6.27-11-generic
 133.9GB: boot/vmlinuz-2.6.27-14-generic
 134.0GB: boot/vmlinuz-2.6.27-7-generic
 134.0GB: initrd.img
 134.0GB: initrd.img.old
 133.9GB: vmlinuz
 133.9GB: vmlinuz.old

=========================== sdd5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd3,5)
search --no-floppy --fs-uuid --set 4e2d60b7-786e-45bc-a153-15481fee9a37
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd3,5)
	search --no-floppy --fs-uuid --set 4e2d60b7-786e-45bc-a153-15481fee9a37
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4e2d60b7-786e-45bc-a153-15481fee9a37 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd3,5)
	search --no-floppy --fs-uuid --set 4e2d60b7-786e-45bc-a153-15481fee9a37
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4e2d60b7-786e-45bc-a153-15481fee9a37 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 06a45d6ba45d5e6d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f07ac5e97ac5aca2
	chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro quiet splash
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro single
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro quiet splash
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=f0ca6709-1b6e-4431-86b2-b8c1bc0e3777 ro single
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set f0ca6709-1b6e-4431-86b2-b8c1bc0e3777
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd5 during installation
UUID=4e2d60b7-786e-45bc-a153-15481fee9a37 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=c0977b77-7a67-4b3c-8b0d-8fba36bf56a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd5: Location of files loaded by Grub: ===================


 124.0GB: boot/grub/core.img
 124.0GB: boot/grub/grub.cfg
 108.5GB: boot/initrd.img-2.6.31-14-generic
 108.5GB: boot/vmlinuz-2.6.31-14-generic
 108.5GB: initrd.img
 108.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  02 4b b2 12 00 00 80 01  |.........K......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 9b 01 08 1c 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff da 01  08 1c 99 35 30 01 00 00  |...........50...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
```

---

### Post by rben13 on 2010-03-04
Here's some additional information, now that I have had a chance to look at the script output.

[LIST]
[*]/sda is my old WinXP drive
[*]/sdb is my Windows 7 drive, still tagged as Vista on the label I actually tried to get rid of Wubi on that drive, w/o success. Wubi  didn't work for me very well. (try saying that five times fast.)
[*]/sdc is my old Ubuntu 8.10 drive which does have some stuff on it I'd like to keep. I was planning to copy that over to this new drive, then use the /sdc drive for other purposes.
[*]/sdd is my new 640G drive in my esata toaster. During the install, I partitioned it into a 100G partition for Windows and the rest for Ubuntu.
[*]/sdi is my usb flash drive
[/LIST]

I'm now reminded that I used NeoGrub a while back, in an attempt to get Windows Vista, Ubuntu, and WinXP all booting. It worked for everything but WinXP.

Ideally, I'd like to be able to boot Windows 7, Ubuntu 9.10, and Windows XP. I can live w/o Win XP.

As you can see, it's quite a mess. Your help is greatly appreciated.

Ray

---

### Post by darkod on 2010-03-04
I would first add grub2 to /dev/sdd, where your 9.10 is. Grub2 can have a delay when it has to look at another disk for ubuntu.

From 9.10 live desktop, do:

sudo mount /dev/sdd5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdd

In BIOS set to boot from /dev/sdd as first hdd choice.

The grub.cfg file looks correct. In fact, you shouldn't have any problems. Maybe just moving grub2 to /dev/sdd will solve it if the delay was too long for its liking.

---

### Post by rben13 on 2010-03-04
Ok, did that, trying to reboot now. Please cross all crossable things.

Ray

---

### Post by rben13 on 2010-03-04
That solved my problem quite nicely. Thank you very much. I can't tell you how stressed out I was getting over this. It's a bad thing when I can't get my computer gaming fix in. :)

Yet another reminder of why I love the Linux community so much.

---

