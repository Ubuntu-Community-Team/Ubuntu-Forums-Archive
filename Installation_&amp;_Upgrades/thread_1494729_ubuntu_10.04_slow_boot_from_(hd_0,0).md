---
title: "ubuntu 10.04 slow boot from (hd 0,0)"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by capo1949 on 2010-05-27
Hi All
My 9.01 worked fine since upgrading to 10.04 i find the boot process hangs for about 30 secs displaying 
'boot from (hd0,0)
Starting up'

I  have googled this problem and the only thing i could find is that disconnection the dvd drives sorts it! but i cannot find a workaround.

Some help would be much appreciated
graham

---

### Post by capo1949 on 2010-06-01
HI All
Would really appreciate some help here

---

### Post by darkod on 2010-06-01
Are you using grub2 and do you have multiple disks? Maybe ubuntu is installed on one disk but grub2 on another. In that case grub2 can have a delay while searching for the ubuntu disk.

---

### Post by capo1949 on 2010-06-02
Hi
Thanks for your interest.
I have a updated from jaunty , not undertaking a clean install. My grub is  0.97.
I have 2x 500 Gb drives on the system. could you advise how i ascertain where grub 0.97 is and if its on the same hard drive as OS
Thanks your help
Graham

---

### Post by darkod on 2010-06-02
Running the boot info script will show you lots of details. But this delay was more for grub2, I'm not sure for grub1 if that would be the problem.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by capo1949 on 2010-06-03
hi
Find attached the resulting file after running the script

Your comments would be appreciated

---

### Post by darkod on 2010-06-03
I can't look at attachments right now. Can you post just the content of the file? Same like copying text from a document, open the results.txt, select the text and paste here. After you paste it while it's still selected hit the # button in the toolbar above when creating the post, that will put it in CODE tags, easier to read.

---

### Post by capo1949 on 2010-06-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   470,142,224   470,142,162  83 Linux
/dev/sda2         470,142,225   488,279,609    18,137,385   5 Extended
/dev/sda5         470,142,288   488,279,609    18,137,322  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   405,576,989   405,576,927   7 HPFS/NTFS
/dev/sdb2         405,576,990   488,392,064    82,815,075   f W95 Ext d (LBA)
/dev/sdb5         416,051,433   485,323,649    69,272,217  83 Linux
/dev/sdb6         485,323,713   488,392,064     3,068,352  82 Linux swap / Solaris
/dev/sdb7         410,814,306   415,697,939     4,883,634  83 Linux
/dev/sdb8         415,698,003   416,051,369       353,367  82 Linux swap / Solaris
/dev/sdb9         405,577,116   410,460,749     4,883,634  83 Linux
/dev/sdb10        410,460,813   410,814,179       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        656dc075-ab2b-4cb8-a306-1fdc56fc3179   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b35cf490-d619-4e08-b61b-6f0344ddfb8e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb10       befdfd2c-b856-4c85-b3d7-a0899f2e7d49   swap                                     
/dev/sdb1        C2CCF6F6CCF6E417                       ntfs       DRV4_VOL1                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        cc960834-96f0-49e9-b3b5-339d309f74e4   ext3                                     
/dev/sdb6        f2abd655-8af0-4a38-a8cd-f0978d6f20f1   swap                                     
/dev/sdb7        6304b63c-de70-4022-afb6-5edc5212c728   ext3                                     
/dev/sdb8        2def1931-39ce-484d-8e5b-2b34f215d973   swap                                     
/dev/sdb9        9a5948ba-a49a-4a5d-a78c-e6057756d392   ext3                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

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
timeout		3

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
# kopt=root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=656dc075-ab2b-4cb8-a306-1fdc56fc3179

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		656dc075-ab2b-4cb8-a306-1fdc56fc3179
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6304b63c-de70-4022-afb6-5edc5212c728 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6304b63c-de70-4022-afb6-5edc5212c728 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb9.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb9)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a5948ba-a49a-4a5d-a78c-e6057756d392 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb9.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb9)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a5948ba-a49a-4a5d-a78c-e6057756d392 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb9.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb9)
root		(hd1,8)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b35cf490-d619-4e08-b61b-6f0344ddfb8e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  83.6GB: boot/grub/menu.lst
  44.9GB: boot/grub/stage2
  63.4GB: boot/initrd.img-2.6.28-11-generic
  63.4GB: boot/initrd.img-2.6.28-16-generic
  63.2GB: boot/initrd.img-2.6.28-18-generic
  63.2GB: boot/initrd.img-2.6.31-21-generic
  63.4GB: boot/initrd.img-2.6.32-22-generic
  44.8GB: boot/vmlinuz-2.6.28-11-generic
  45.7GB: boot/vmlinuz-2.6.28-16-generic
  44.9GB: boot/vmlinuz-2.6.28-18-generic
  62.9GB: boot/vmlinuz-2.6.31-21-generic
  62.8GB: boot/vmlinuz-2.6.32-22-generic
  63.4GB: initrd.img
  63.2GB: initrd.img.old
  62.8GB: vmlinuz
  62.9GB: vmlinuz.old

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=f2abd655-8af0-4a38-a8cd-f0978d6f20f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 238.3GB: boot/grub/menu.lst
 238.2GB: boot/grub/stage2
 238.2GB: boot/initrd.img-2.6.24-16-generic
 238.3GB: boot/initrd.img-2.6.24-16-generic.bak
 238.3GB: boot/initrd.img-2.6.24-19-generic
 238.3GB: boot/initrd.img-2.6.24-19-generic.bak
 238.3GB: boot/vmlinuz-2.6.24-16-generic
 238.3GB: boot/vmlinuz-2.6.24-19-generic
 238.3GB: initrd.img
 238.2GB: initrd.img.old
 238.3GB: vmlinuz
 238.3GB: vmlinuz.old

=========================== sdb7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6304b63c-de70-4022-afb6-5edc5212c728 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6304b63c-de70-4022-afb6-5edc5212c728

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		6304b63c-de70-4022-afb6-5edc5212c728
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6304b63c-de70-4022-afb6-5edc5212c728 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		6304b63c-de70-4022-afb6-5edc5212c728
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6304b63c-de70-4022-afb6-5edc5212c728 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		6304b63c-de70-4022-afb6-5edc5212c728
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-12-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.28-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-24-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=6304b63c-de70-4022-afb6-5edc5212c728 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=2def1931-39ce-484d-8e5b-2b34f215d973 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 210.9GB: boot/grub/menu.lst
 210.9GB: boot/grub/stage2
 210.9GB: boot/initrd.img-2.6.28-11-generic
 211.0GB: boot/vmlinuz-2.6.28-11-generic
 210.9GB: initrd.img
 211.0GB: vmlinuz

=========================== sdb9/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9a5948ba-a49a-4a5d-a78c-e6057756d392 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9a5948ba-a49a-4a5d-a78c-e6057756d392

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9a5948ba-a49a-4a5d-a78c-e6057756d392
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a5948ba-a49a-4a5d-a78c-e6057756d392 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9a5948ba-a49a-4a5d-a78c-e6057756d392
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a5948ba-a49a-4a5d-a78c-e6057756d392 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9a5948ba-a49a-4a5d-a78c-e6057756d392
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-12-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.28-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-24-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=55acf7cc-33a8-4dc6-a89e-66e9483589e4 ro single 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cc960834-96f0-49e9-b3b5-339d309f74e4 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6304b63c-de70-4022-afb6-5edc5212c728 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6304b63c-de70-4022-afb6-5edc5212c728 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb9 during installation
UUID=9a5948ba-a49a-4a5d-a78c-e6057756d392 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb10 during installation
UUID=befdfd2c-b856-4c85-b3d7-a0899f2e7d49 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb9: Location of files loaded by Grub: ===================


 208.8GB: boot/grub/menu.lst
 208.8GB: boot/grub/stage2
 208.6GB: boot/initrd.img-2.6.28-11-generic
 208.8GB: boot/vmlinuz-2.6.28-11-generic
 208.6GB: initrd.img
 208.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

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
000001b0  00 00 00 00 00 00 00 00  00 07 3c 0b 00 00 00 01  |..........<.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 df 9c 2c 18 00 fe  |......?.....,...|
000001d0  ff ff 0f fe ff ff 1e 9d  2c 18 63 a8 ef 04 00 00  |........,.c.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

```

---

### Post by darkod on 2010-06-03
I can't see anything wrong with it. :( Not sure about that delay.

You have 4 ubuntu installations in there, but I guess you already know that. :) But I don't see a reason grub2 to be delayed because of that.

---

### Post by capo1949 on 2010-06-03
hi
Yes seen the other ubuntu installs, i am having a new laptop at the end of the month, when I have that sorted,I will clean install 10.04 on this system then and see what happens.
Thanks for the time you have spent on this it is much appreciated
Graham

---

### Post by wmwong on 2010-08-08
I have the exact same problem. Upgraded to 10.04 and it hangs at the same spot. Any thoughts appreciated!

Here is my boot summary:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   612,992,204   612,992,142  83 Linux
/dev/sdb2         612,992,205   625,137,344    12,145,140   5 Extended
/dev/sdb5         612,992,268   625,137,344    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DEE03B87E03B6545                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        63ecedb2-5534-4f3f-8c18-d98d7001b9df   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0155bd16-6de6-410c-b18b-bd13aa071e34   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=63ecedb2-5534-4f3f-8c18-d98d7001b9df

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
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-16-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.27-14-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.27-14-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
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


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=0155bd16-6de6-410c-b18b-bd13aa071e34 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   6.4GB: boot/grub/menu.lst
   6.4GB: boot/grub/stage2
   7.7GB: boot/initrd.img-2.6.27-14-generic
   6.7GB: boot/initrd.img-2.6.28-16-generic
   8.5GB: boot/initrd.img-2.6.31-21-generic
   8.5GB: boot/initrd.img-2.6.32-21-generic
   6.5GB: boot/initrd.img-2.6.32-22-generic
   6.5GB: boot/initrd.img-2.6.32-23-generic
   7.4GB: boot/initrd.img-2.6.32-24-generic
  48.7GB: boot/vmlinuz-2.6.27-14-generic
  76.2GB: boot/vmlinuz-2.6.28-16-generic
   6.7GB: boot/vmlinuz-2.6.31-21-generic
   6.9GB: boot/vmlinuz-2.6.32-21-generic
   6.6GB: boot/vmlinuz-2.6.32-22-generic
   6.4GB: boot/vmlinuz-2.6.32-23-generic
   7.4GB: boot/vmlinuz-2.6.32-24-generic
   7.4GB: initrd.img
   6.5GB: initrd.img.old
   7.4GB: vmlinuz
   6.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

