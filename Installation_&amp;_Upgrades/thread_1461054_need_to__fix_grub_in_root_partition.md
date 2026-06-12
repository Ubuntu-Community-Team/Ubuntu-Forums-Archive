---
title: "need to  fix grub in root partition"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2010-04-23
I made a clone copy of my hard drive.

I have XP, w98, ubuntu, fedora, debian leny on the PC.
I am booting with grub (legacy) to a special boot (grub partition) with menu and all OS are chanloaded from there.

After the clonig of the hard disk, I can boot via the boot(grub) partition XP, w98, fedora (it has grub2 on its root) , but I can not boot to ubuntu and debian which have both grub legacy.

I manged to boot the partitions with suppergrzb disk, but was so far not able to repair or reinstall the grub in the root partition of neither ubuntu nor debian leny.

When I am in the ubuntu, what commads to use to install the grub back to the own root?

---

### Post by ottosykora on 2010-04-23
here the results of the boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #16 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda12 and 
                       looks at sector 544985457 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #12 for 
                       /boot/grub/grub.conf.
    Operating System:  Fedora release 12 (Constantine) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda13 and 
                       looks at sector 564835981 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #13 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda14: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda14 and 
                       looks at sector 602094823 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #14 for 
                       /boot/grub/menu.lst.
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda15: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda16: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 320.1 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spuren, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x0287cbea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      2,634,660    45,206,909    42,572,250   7 HPFS/NTFS
/dev/sda2                  63     2,634,659     2,634,597  1b Hidden W95 FAT32
/dev/sda3          45,206,910    99,056,789    53,849,880  17 Hidden HPFS/NTFS
/dev/sda4          99,056,790   625,137,344   526,080,555   f W95 Ext d (LBA)
/dev/sda5          99,056,853   103,153,364     4,096,512   6 FAT16
/dev/sda6         103,153,428   144,119,114    40,965,687   b W95 FAT32
/dev/sda7         144,119,178   174,851,459    30,732,282   b W95 FAT32
/dev/sda8         174,851,523   297,909,359   123,057,837   b W95 FAT32
/dev/sda9         297,909,423   461,756,294   163,846,872   b W95 FAT32
/dev/sda10        461,756,358   533,004,569    71,248,212   7 HPFS/NTFS
/dev/sda11        533,004,633   541,615,409     8,610,777  83 Linux
/dev/sda12        541,615,473   553,889,069    12,273,597  83 Linux
/dev/sda13        553,889,133   598,389,119    44,499,987  83 Linux
/dev/sda14        598,389,183   620,944,379    22,555,197  83 Linux
/dev/sda15        620,944,443   624,976,694     4,032,252  82 Linux swap / Solaris
/dev/sda16        624,976,758   625,137,344       160,587  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       86E4B03BE4B02EF5                       ntfs       DOWNLOAD                      
/dev/sda11                                              ext3       KN                            
/dev/sda12       27302775-541a-4e97-b925-cd9d20105548   ext4       FED12                         
/dev/sda13       9f857745-92e3-4dab-946c-eb68c78dd338   ext3       UBUNTU                        
/dev/sda14       2ef56b56-d4b0-4658-8cd1-aa808ad57785   ext3       DEBIAN                        
/dev/sda15                                              swap                                     
/dev/sda16       90f9658e-7f1f-426d-9d2f-5545a3aad575   ext2       GRUB                          
/dev/sda1        72845448845410C9                       ntfs       XP                            
/dev/sda2        4AD4-3A25                              vfat       W98                           
/dev/sda3        15E01C16BAEB09D1                       ntfs       W7                            
/dev/sda5        4AD4-479B                              vfat       DATA8                         
/dev/sda6        C0F9-6FDA                              vfat       DATA                          
/dev/sda7        0BCD-AD37                              vfat       INSTPATH                      
/dev/sda8        A176-29F5                              vfat       VM                            
/dev/sda9        56A1-EC48                              vfat       BKUP-SW                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda13       /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=otto)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\windows

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\windows="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


========================== sda12/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,11)
#          kernel /boot/vmlinuz-version ro root=/dev/sda12
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda12
default=0
timeout=5
splashimage=(hd0,11)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.32.10-90.fc12.i686)
	root (hd0,11)
	kernel /boot/vmlinuz-2.6.32.10-90.fc12.i686 ro root=UUID=27302775-541a-4e97-b925-cd9d20105548 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=sg-latin1 rhgb quiet
	initrd /boot/initramfs-2.6.32.10-90.fc12.i686.img
title Fedora (2.6.32.9-70.fc12.i686)
	root (hd0,11)
	kernel /boot/vmlinuz-2.6.32.9-70.fc12.i686 ro root=UUID=27302775-541a-4e97-b925-cd9d20105548 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=sg-latin1 rhgb quiet
	initrd /boot/initramfs-2.6.32.9-70.fc12.i686.img
title Fedora (2.6.32.9-67.fc12.i686)
	root (hd0,11)
	kernel /boot/vmlinuz-2.6.32.9-67.fc12.i686 ro root=UUID=27302775-541a-4e97-b925-cd9d20105548 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=sg-latin1 rhgb quiet
	initrd /boot/initramfs-2.6.32.9-67.fc12.i686.img
title Other
	rootnoverify (hd0,0)
	chainloader +1

=============================== sda12/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Sat Dec 26 16:47:54 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=27302775-541a-4e97-b925-cd9d20105548 /                       ext4    defaults        1 1
UUID=9581e2cf-fec4-45d5-bb55-e16d053a3fb1 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda12: Location of files loaded by Grub: ===================


 277.4GB: boot/grub/grub.conf
 277.4GB: boot/grub/menu.lst
 279.0GB: boot/grub/stage2
 282.8GB: boot/initramfs-2.6.32.10-90.fc12.i686.img
 282.7GB: boot/initramfs-2.6.32.9-67.fc12.i686.img
 282.9GB: boot/initramfs-2.6.32.9-70.fc12.i686.img
 282.3GB: boot/vmlinuz-2.6.32.10-90.fc12.i686
 282.4GB: boot/vmlinuz-2.6.32.9-67.fc12.i686
 282.1GB: boot/vmlinuz-2.6.32.9-70.fc12.i686

========================== sda13/boot/grub/menu.lst: ==========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue blink-white/magenta

#A splash image for the menu
splashimage=(hd0,12)/boot/grub/splashimages/menu-sta.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=/dev/sda13 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,12)

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 9.10, kernel 2.6.31-17-generic
root            (hd0,12)
kernel          /boot/vmlinuz-2.6.31-17-generic root=/dev/sda13 ro quiet splash
initrd          /boot/initrd.img-2.6.31-17-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root            (hd0,12)
kernel          /boot/vmlinuz-2.6.31-17-generic root=/dev/sda13 ro  single
initrd          /boot/initrd.img-2.6.31-17-generic



title		Ubuntu 9.10, kernel 2.6.31-16-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.31-16-generic root=/dev/sda13 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.31-16-generic root=/dev/sda13 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic



title		Ubuntu 9.10, memtest86+
root		(hd0,12)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda13      /               ext3    relatime,errors=remount-ro 0       1
/dev/sda15      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda13: Location of files loaded by Grub: ===================


 288.1GB: boot/grub/menu.lst
 289.1GB: boot/grub/stage2
 289.2GB: boot/initrd.img-2.6.31-16-generic
 289.2GB: boot/initrd.img-2.6.31-17-generic
 289.2GB: boot/vmlinuz-2.6.31-16-generic
 289.2GB: boot/vmlinuz-2.6.31-17-generic
 289.2GB: initrd.img
 289.2GB: initrd.img.old
 289.2GB: vmlinuz
 289.2GB: vmlinuz.old

========================== sda14/boot/grub/menu.lst: ==========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout		15

# Pretty colours
color cyan/blue blink-white/blue

#A splash image for the menu
splashimage=(hd0,13)/boot/grub/splashimages/gnome-debblue.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=/dev/sda14 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,13)

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.26-2-686
root		(hd0,13)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sda14 ro quiet splash
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root		(hd0,13)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sda14 ro single
initrd		/boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda13.
title		Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda13)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.28-16-generic root=/dev/sda13 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda13.
title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda13)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.28-16-generic root=/dev/sda13 ro single 
initrd		/boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda13.
title		Ubuntu 9.04, memtest86+ (on /dev/sda13)
root		(hd0,12)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda14/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda14      /               ext3    errors=remount-ro 0       1
/dev/sda15      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda14: Location of files loaded by Grub: ===================


 308.2GB: boot/grub/menu.lst
 308.2GB: boot/grub/stage2
 308.1GB: boot/initrd.img-2.6.26-2-686
 308.1GB: boot/initrd.img-2.6.26-2-686.bak
 308.1GB: boot/vmlinuz-2.6.26-2-686
 308.1GB: initrd.img
 308.1GB: vmlinuz

============================= sda16/grub/menu.lst: =============================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue blink-white/blue

#A splash image for the menu
splashimage=(hd0,15)/grub/splashimages/gentleblue.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=/dev/sda13 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,12)

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Windows XP
hide 		(hd0,1)
unhide		(hd0,0)
rootnoverify	(hd0,0)
safedefault
makeactive
chainloader +1

title		Ubuntu 9.10
root		(hd0,12)
chainloader +1


title		Debian Leny
root		(hd0,13)
chainloader +1

title           Fedora12
root            (hd0,11)
chainloader +1


title		W98/DOS
unhide		(hd0,1)
hide		(hd0,0)		
rootnoverify	(hd0,1)
safedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


#title		Windows XP
#rootnoverify	(hd0,0)
#safedefault
#makeactive
#chainloader +1

=================== sda16: Location of files loaded by Grub: ===================


 319.9GB: grub/menu.lst
 319.9GB: grub/stage2
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 30 00 02 40 02 00  |.<.MSWIN4.0..@..|
00000010  02 00 02 00 00 f8 fb 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  d8 81 3e 00 80 00 29 9b  47 d4 4a 44 41 54 41 38  |..>...).G.JDATA8|
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |      FAT16   .3|
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

### Post by oldfred on 2010-04-23
You want the drive, partition version, If you can boot any linux you do not need the liveCD:

1. Boot your computer up with Live CD
2. Open a terminal window (or switch to a tty ).
3. Type 'sudo grub'.
   Should get text of which last line is "grub>"
4. Type "find /boot/grub/stage1".
   You'll get a response like "(hd0,1)".
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)" ( what you got in step #4 hard disk + boot partition )
6. Type
       "setup (hd0)", to install GRUB to MBR, prefered method
OR     "setup (hd0,1)" ([COLOR=Red]whatever your hard disk + partition #[/COLOR] is)
                       to install GRUB to a  partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

The above is only for grub legacy (0.97) Grub2 does not like to be in a partition and requires --force on the standard grub2 instructions.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ottosykora on 2010-04-24
OK, many problems could have been avoided on my side, if I had better observed what I anyway know already.
The numbering of sda starts with 1 and the numbering of grub with 0.
I placed somewhere an attmpt to hide (hd0,3) which would be the whole extended partition, in which also the grub-boot partition is included. This had exciting symptoms as result. This was fun to recover all that ! , lost partition table after all that playing, lot of work with testdisk, but all back now, not one byte of data lost.

And with grub legacy in a separate partition, I have now on the same laptop, same disk:
w7
XP
w98se
ubuntu
debian
fedora

so 6 entries in primary menu.lst !

Fun

---

