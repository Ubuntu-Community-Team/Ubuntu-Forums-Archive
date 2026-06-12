---
title: "Dual Booting on two harddrives"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by Antlers on 2010-05-06
I have installed Ubuntu on one hard drive, and windows 7 on another hard drive.  Grub will not recognise windows.  On start up, I have the option to run windows but when I try I get error 11 cannot find device string.  
Please help me figure this out, thanks.

I am running Ubuntu 9.10.
I installed each OS on one hard drive with the other hard drive removed, then plugged them both in.  I can see the windows files on the other hard drive while running ubuntu.
I have updated grub.

Here is my boot info.


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   603,963,674   603,963,612  83 Linux
/dev/sda2         603,963,675   625,137,344    21,173,670   5 Extended
/dev/sda5         603,963,738   625,137,344    21,173,607  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b8b425e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b317de65-cc5b-42eb-b8cc-6925de2bf8ba   ext3                                     
/dev/sda5        31953637-8c10-41d4-9703-586386c4f239   swap                                     
/dev/sdb1        D028794428792B1C                       ntfs       System Reserved               
/dev/sdb2        5C267C01267BDB0A                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=b317de65-cc5b-42eb-b8cc-6925de2bf8ba

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

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.28-18-generic
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-18-generic (recovery mode)
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.10, memtest86+
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		windows 7
root            root (hd1,1)
		makeactive
		chainloader +1

# A second attempt at Windows 7, if only it would work
#
		Windows 7
		root (hd1, 0)
		savedefault
		makeactive
		chainloader +1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, kernel 2.6.28-18-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=3c9940fb-2f37-45c6-a1d9-3c33bebcf848 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=3c9940fb-2f37-45c6-a1d9-3c33bebcf848 ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3c9940fb-2f37-45c6-a1d9-3c33bebcf848 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3c9940fb-2f37-45c6-a1d9-3c33bebcf848 ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=31953637-8c10-41d4-9703-586386c4f239 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


 251.0GB: boot/grub/menu.lst
 251.1GB: boot/grub/stage2
 251.0GB: boot/initrd.img-2.6.28-18-generic
 251.0GB: boot/initrd.img-2.6.31-21-generic
 251.0GB: boot/vmlinuz-2.6.28-18-generic
 251.0GB: boot/vmlinuz-2.6.31-21-generic
 251.0GB: initrd.img
 251.0GB: initrd.img.old
 251.0GB: vmlinuz
 251.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by oldfred on 2010-05-06
Could you go back an highlight the entire reesults.txt that you posted and click on the # on the right side edit panel above as you edit. this makes it easier to review.

You windows install looks ok. You are still using grub legacy which was not as good at finding windows (as grub2 now is).

I think you need to add map commands since your windows is on sdb and windows ususally likes to be the first drive. The map commands make windows think it is first.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows 7
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by Antlers on 2010-05-06
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   603,963,674   603,963,612  83 Linux
/dev/sda2         603,963,675   625,137,344    21,173,670   5 Extended
/dev/sda5         603,963,738   625,137,344    21,173,607  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b8b425e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b317de65-cc5b-42eb-b8cc-6925de2bf8ba   ext3                                     
/dev/sda5        31953637-8c10-41d4-9703-586386c4f239   swap                                     
/dev/sdb1        D028794428792B1C                       ntfs       System Reserved               
/dev/sdb2        5C267C01267BDB0A                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=b317de65-cc5b-42eb-b8cc-6925de2bf8ba

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

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.28-18-generic
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-18-generic (recovery mode)
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.10, memtest86+
uuid		b317de65-cc5b-42eb-b8cc-6925de2bf8ba
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		windows 7
root            root (hd1,1)
		makeactive
		chainloader +1

# A second attempt at Windows 7, if only it would work
#
		Windows 7
		root (hd1, 0)
		savedefault
		makeactive
		chainloader +1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, kernel 2.6.28-18-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=3c9940fb-2f37-45c6-a1d9-3c33bebcf848 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=3c9940fb-2f37-45c6-a1d9-3c33bebcf848 ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3c9940fb-2f37-45c6-a1d9-3c33bebcf848 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3c9940fb-2f37-45c6-a1d9-3c33bebcf848 ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=b317de65-cc5b-42eb-b8cc-6925de2bf8ba / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=31953637-8c10-41d4-9703-586386c4f239 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


 251.0GB: boot/grub/menu.lst
 251.1GB: boot/grub/stage2
 251.0GB: boot/initrd.img-2.6.28-18-generic
 251.0GB: boot/initrd.img-2.6.31-21-generic
 251.0GB: boot/vmlinuz-2.6.28-18-generic
 251.0GB: boot/vmlinuz-2.6.31-21-generic
 251.0GB: initrd.img
 251.0GB: initrd.img.old
 251.0GB: vmlinuz
 251.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by oldfred on 2010-05-06
I do not see that you added the windows entry with map commands to see if it works?

---

### Post by Antlers on 2010-05-08
That worked perfectly, thank you so much!

---

