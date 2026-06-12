---
title: "Install and ugrade messup! Help!"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by imphil on 2010-03-01
Tried to install  dual boot with Ubuntu on a dedicated hard disk drive. 
The system would not boot.
I received help and scripting suggestions  here but (unwisely?) decided to juggle the SATA cables instead of  scripting a solution as suggested.

This cludge worked and the bootinfoscript is below:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => HP/Gateway is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ec44c5f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa738484c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *      6,570,585   293,041,664   286,471,080   7 HPFS/NTFS
/dev/sdb2                  63     6,570,584     6,570,522  12 Compaq diagnostics


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ac6adf8

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   468,616,049   468,615,987  83 Linux
/dev/sdc2         468,616,050   488,392,064    19,776,015   5 Extended
/dev/sdc5         468,616,113   488,392,064    19,775,952  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        88A8731EA87309C8                       ntfs       Working_Files                 
/dev/sdb1        70C4056BC405353E                       ntfs       VelociRaptor                  
/dev/sdb2        423B-2BDF                              vfat                                     
/dev/sdc1        da5afe34-5b6f-47ab-b203-e75f1bdc7125   ext3                                     
/dev/sdc5        213b7620-7f2b-4ebd-8b03-73c72987defc   swap                                     
/dev/sdd1        D23C96763C965577                       ntfs       Backups                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdd1        /media/Backups           fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=da5afe34-5b6f-47ab-b203-e75f1bdc7125 ro

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=da5afe34-5b6f-47ab-b203-e75f1bdc7125 ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=da5afe34-5b6f-47ab-b203-e75f1bdc7125 ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=da5afe34-5b6f-47ab-b203-e75f1bdc7125 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=da5afe34-5b6f-47ab-b203-e75f1bdc7125 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd2,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=da5afe34-5b6f-47ab-b203-e75f1bdc7125 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=213b7620-7f2b-4ebd-8b03-73c72987defc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 105.3GB: boot/grub/menu.lst
 105.4GB: boot/grub/stage2
 105.4GB: boot/initrd.img-2.6.24-26-generic
 105.4GB: boot/initrd.img-2.6.24-27-generic
 105.4GB: boot/initrd.img-2.6.24-27-generic.bak
 105.4GB: boot/vmlinuz-2.6.24-26-generic
 105.3GB: boot/vmlinuz-2.6.24-27-generic
 105.4GB: initrd.img
 105.4GB: initrd.img.old
 105.3GB: vmlinuz
 105.4GB: vmlinuz.oldv
```
After  playing with release 8.04 I decided to live with the "cludge" and upgrade to 9.10 before migrating stuff  over  to Ubuntu.

8.04 to 8.10 went well.

8.10 to 9.04 went seriously south leaving me with a crippled 9.04 and no  possibility of upgrading.

I  would dearly like to redo the whole works starting with 9.10 and get it right the first time.

So how do I remove Grub 0.97 from /sda and /sdb  if necessary?

Do I need to restore MBR to dev/sdb from Windows Console?

What boot sequence must I set in BIOS for the install to work properly?
Present sequence:1) sdb 2) sdc 3) sda.

Help with above or better suggestions highly appreciated!

---

### Post by imphil on 2010-03-01
Bump!

Anybody able and willing to help??

---

### Post by khelben1979 on 2010-03-01
Maybe you can find the answer you're looking for in here: [GNU GRUB Legacy FAQ]("http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12").

If you feel sick tired of the problem, get yourself a new harddrive and do a fresh install of Ubuntu 9.10.

B.t.w. there's no reason to mess around with changing [S-ATA]("http://en.wikipedia.org/wiki/S-ATA") cables as you mentioned, because S-ATA allows you to change these settings directly from inside the BIOS unlike [P-ATA]("http://en.wikipedia.org/wiki/P-ATA").

---

### Post by imphil on 2010-03-01
Thanks the FAQ answers a few of my questions.

---

