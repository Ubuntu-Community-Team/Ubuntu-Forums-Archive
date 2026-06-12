---
title: "How to dual boot ubuntu &amp; xp when xp is on secondary slave?"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by Josh_D on 2011-02-15
I'm trying to add my xp drive to the boot menu but I'm having some trouble with it. I've been going over dozens of topics on many forums and I still can't get it to work (I'm new to linux/ubuntu btw).

Ok, so, I have Ubuntu 10.04 on the main drive (primary master) and xp on a second drive (secondary slave) and from what I've read sec. slave is hd3. I added the lines I found in another thread (here I think) but when I tried to boot xp it said the drive didn't exist.

Here's my menu.lst file:
```
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
timeout        5

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
# kopt=root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bdf7a504-b201-4a7d-98dc-86bd59da98c3

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

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-28-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro  single
initrd        /boot/initrd.img-2.6.32-28-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.31-22-generic
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.28-19-generic
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.27-7-generic
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.27-7-generic (recovery mode)
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 10.04.2 LTS, memtest86+
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/memtest86+.bin
quiet

title                Windows XP Home
root                (hd3,0)
makeactive
chainloader        +1
map (hd0) (hd3)
map (hd3) (hd0)

### END DEBIAN AUTOMAGIC KERNELS LIST
```sudo fdisk -l results:
```
Disk /dev/sda: 30.8 GB, 30750031872 bytes
64 heads, 63 sectors/track, 14895 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x35a935a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14894    30026272+  83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1369b026

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2480    19920568+   7  HPFS/NTFS
/dev/sdb2            2481        4865    19157512+   7  HPFS/NTFS
```

I know I've done something wrong but I have no idea what it is, I hope someone can help.

---

### Post by jimbop99 on 2011-02-15
Have you tried "update-grub" command.

Also look here for help [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Josh_D on 2011-02-15
I changed it to (hd2,0) and got the same result.

Back in Ubuntu I ran that and got this:
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-28-generic
Found kernel: /boot/vmlinuz-2.6.31-22-generic
Found kernel: /boot/vmlinuz-2.6.28-19-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```I also ran the boot info script, here are the results:
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
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.8 GB, 30750031872 bytes
64 heads, 63 sectors/track, 14895 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    60,052,607    60,052,545  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,841,199    39,841,137   7 HPFS/NTFS
/dev/sdb2          39,841,200    78,156,224    38,315,025   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        bdf7a504-b201-4a7d-98dc-86bd59da98c3   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5C22DC17D6C6434C                       ntfs                                     
/dev/sdb2        E8949C7A949C4CC6                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

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
# kopt=root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bdf7a504-b201-4a7d-98dc-86bd59da98c3

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

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-28-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro  single
initrd        /boot/initrd.img-2.6.32-28-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.31-22-generic
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.28-19-generic
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.27-7-generic
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.27-7-generic (recovery mode)
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 10.04.2 LTS, memtest86+
uuid        bdf7a504-b201-4a7d-98dc-86bd59da98c3
kernel        /boot/memtest86+.bin
quiet

title                Windows XP Home
root                (hd2,0)
makeactive
chainloader        +1
map (hd0) (hd2)
map (hd2) (hd0)

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bdf7a504-b201-4a7d-98dc-86bd59da98c3 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.7GB: boot/grub/menu.lst
   2.7GB: boot/grub/stage2
   2.7GB: boot/initrd.img-2.6.27-7-generic
   2.7GB: boot/initrd.img-2.6.28-19-generic
   2.7GB: boot/initrd.img-2.6.31-22-generic
   2.7GB: boot/initrd.img-2.6.32-28-generic
   2.8GB: boot/vmlinuz-2.6.27-7-generic
   2.8GB: boot/vmlinuz-2.6.28-19-generic
   2.7GB: boot/vmlinuz-2.6.31-22-generic
   2.8GB: boot/vmlinuz-2.6.32-28-generic
   2.7GB: initrd.img
   2.7GB: initrd.img.old
   2.8GB: vmlinuz
   2.7GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin 
```

So, what do I need to change? Is sdb1 (hd2,0), (hd2,1), (hd3,0), (hd3,1) or something else? This OS is driving me nuts, I don't know why it has to be so complicated.

---

### Post by drs305 on 2011-02-15
If I remember correctly, sdb1 would be designated as (hd1,0) in Grub. You may have been seeing references for Grub2, which changed the way the drives/partitions are designated. 

I'd be out of character if I didn't recommend you upgrade to Grub 2, which would find the Windows OS automatically.  ;-)

---

### Post by Josh_D on 2011-02-15
> **drs305 said:**
> If I remember correctly, sdb1 would be designated as (hd1,0) in Grub. You may have been seeing references for Grub2, which changed the way the drives/partitions are designated. 

I'd be out of character if I didn't recommend you upgrade to Grub 2, which would find the Windows OS automatically.  ;-)

Thanks, that worked perfectly.

---

