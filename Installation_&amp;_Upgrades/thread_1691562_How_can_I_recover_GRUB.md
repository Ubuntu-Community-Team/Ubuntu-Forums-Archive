---
title: "How can I recover GRUB"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by AlanAbbott on 2011-02-20
I need to run SSL and I have problems under Ubuntu (see separate post) so I tried to install windows side by side. Now only windows boots.
May present situation is as follows

ubuntu@ubuntu:~$ sudo fdisk -ll

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004162a

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       29321   235520901   83  Linux
/dev/sde2   *       30597       37179    52877947+   7  HPFS/NTFS
/dev/sde3           37180       38913    13928355    5  Extended
/dev/sde4           29322       30536     9759487+  83  Linux
/dev/sde5           37506       38913    11309728+  82  Linux swap / Solaris
/dev/sde6           37180       37483     2441817   83  Linux
/dev/sde7           37484       37505      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo parted -l

Model: ATA SAMSUNG HD322HJ (scsi)
Disk /dev/sde: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  241GB  241GB   primary   ext3
 4      241GB   251GB  9994MB  primary   ext3
 2      252GB   306GB  54.1GB  primary   ntfs            boot
 3      306GB   320GB  14.3GB  extended
 6      306GB   308GB  2500MB  logical   ext3
 7      308GB   308GB  181MB   logical   linux-swap(v1)
 5      308GB   320GB  11.6GB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label          

I am running running from a live CD. In "http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html" I read "You always need to choose a device i.e, sda, sdb, sdc from the drop down menu instead of sda1, sda2, sda3, sdb1, sdc1 unless you know exactly what you are doing (in which case you won't be looking at this guide)."
I don't see eny sda or sdc.

---

### Post by dino99 on 2011-02-20
your partitioning is not the best. What you should have:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

you need to install grub (grub-pc) on /dev/sde (that mean sde previously mounted)

sudo grub-install /dev/sde
sudo update-grub

[http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html](http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html)

---

### Post by AlanAbbott on 2011-02-20
would this mean:

mount dev/sde1/mnt
mount dev/sde2/mnt/boot
sudu grub-install /dev/sde2

before doing something wrong I prefer to ask as I have a lot of un saved data on the disk.

Alan

---

### Post by Quackers on 2011-02-20
Nope, definitely not!
Do you have a separate /boot partition for Ubuntu?

---

### Post by Rubi1200 on 2011-02-20
I recommend the following:

From either within Ubuntu or a LiveCD:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by AlanAbbott on 2011-02-20
I had Ubuntu and a Windows XP-64 that did not work, in sde2. I installed windows 7 over it and got to this situation. 
I come from DOS in 82, only passed to windows in 97 and played with coyote linux only as a router.

I have little to no experience in linux handling of drives, do not know which is the linux boot partion.

---

### Post by Quackers on 2011-02-20
Please follow the instructions one post up, so that we can get a better look at your system.

---

### Post by AlanAbbott on 2011-02-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sde

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sde2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sde3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sde7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   471,041,864   471,041,802  83 Linux
/dev/sde2    *    491,524,740   597,280,634   105,755,895   7 HPFS/NTFS
/dev/sde3         597,280,635   625,137,344    27,856,710   5 Extended
/dev/sde5         602,517,888   625,137,344    22,619,457  82 Linux swap / Solaris
/dev/sde6         597,280,761   602,164,394     4,883,634  83 Linux
/dev/sde7         602,164,458   602,517,824       353,367  82 Linux swap / Solaris
/dev/sde4         471,041,865   490,560,839    19,518,975  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sde1        957e1f7c-7ed2-4e4f-9bda-695d88c3e355   ext3                                     
/dev/sde2        96AC618FAC616AA7                       ntfs                                     
/dev/sde3: PTTYPE="dos" 
/dev/sde4        50438a07-ce44-4b77-a511-7d2bb4ad8c31   ext3                                     
/dev/sde5        e8362fd0-f3b8-4a7b-804a-251758ac35d5   swap                                     
/dev/sde6        a7e4baa5-2884-451a-9dd6-837f8e1fefdf   ext3                                     
/dev/sde7        9b2d7398-27fb-4818-ab81-3cbaf636956a   swap                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sda: No medium found
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sde1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=957e1f7c-7ed2-4e4f-9bda-695d88c3e355

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

title        Ubuntu 10.10, kernel 2.6.35-25-generic
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro  single
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro  single
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-23-generic
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-23-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro  single
initrd        /boot/initrd.img-2.6.35-23-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.32-25-generic
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic
quiet

title        Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.10, kernel 2.6.31-21-generic
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.10, kernel 2.6.31-21-generic (recovery mode)
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.10, kernel 2.6.28-18-generic
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.10, kernel 2.6.28-18-generic (recovery mode)
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.10, kernel 2.6.28-13-generic
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 10.10, kernel 2.6.28-13-generic (recovery mode)
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 10.10, memtest86+
uuid        957e1f7c-7ed2-4e4f-9bda-695d88c3e355
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Professional x64 Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a7e4baa5-2884-451a-9dd6-837f8e1fefdf ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a7e4baa5-2884-451a-9dd6-837f8e1fefdf ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, memtest86+ (on /dev/sda6)
root        (hd0,5)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e8362fd0-f3b8-4a7b-804a-251758ac35d5 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=9b2d7398-27fb-4818-ab81-3cbaf636956a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sde1: Location of files loaded by Grub: ===================


   9.5GB: boot/grub/menu.lst
   9.4GB: boot/grub/stage2
   9.5GB: boot/initrd.img-2.6.28-13-generic
   9.4GB: boot/initrd.img-2.6.28-18-generic
   9.4GB: boot/initrd.img-2.6.31-21-generic
   9.5GB: boot/initrd.img-2.6.32-25-generic
   9.5GB: boot/initrd.img-2.6.35-22-generic
   9.4GB: boot/initrd.img-2.6.35-23-generic
   9.5GB: boot/initrd.img-2.6.35-24-generic
   9.5GB: boot/initrd.img-2.6.35-25-generic
   9.4GB: boot/vmlinuz-2.6.28-13-generic
   9.4GB: boot/vmlinuz-2.6.28-18-generic
   9.4GB: boot/vmlinuz-2.6.31-21-generic
   9.5GB: boot/vmlinuz-2.6.32-25-generic
   9.4GB: boot/vmlinuz-2.6.35-22-generic
   9.4GB: boot/vmlinuz-2.6.35-23-generic
   9.4GB: boot/vmlinuz-2.6.35-24-generic
   9.5GB: boot/vmlinuz-2.6.35-25-generic
   9.5GB: initrd.img
   9.5GB: initrd.img.old
   9.5GB: vmlinuz
   9.4GB: vmlinuz.old

=========================== sde6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a7e4baa5-2884-451a-9dd6-837f8e1fefdf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a7e4baa5-2884-451a-9dd6-837f8e1fefdf

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a7e4baa5-2884-451a-9dd6-837f8e1fefdf
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a7e4baa5-2884-451a-9dd6-837f8e1fefdf ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a7e4baa5-2884-451a-9dd6-837f8e1fefdf
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a7e4baa5-2884-451a-9dd6-837f8e1fefdf ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a7e4baa5-2884-451a-9dd6-837f8e1fefdf
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro single 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro single 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=957e1f7c-7ed2-4e4f-9bda-695d88c3e355 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, memtest86+ (on /dev/sda1)
root        (hd0,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Professional x64 Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sde6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=a7e4baa5-2884-451a-9dd6-837f8e1fefdf /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9b2d7398-27fb-4818-ab81-3cbaf636956a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sde6: Location of files loaded by Grub: ===================


 307.1GB: boot/grub/menu.lst
 307.1GB: boot/grub/stage2
 307.3GB: boot/initrd.img-2.6.28-11-generic
 306.6GB: boot/vmlinuz-2.6.28-11-generic
 307.3GB: initrd.img
 306.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sda sdb sdc sdd 
```

As indicatted by Rubi1200 (thank you in advance for your help)

Alan

---

### Post by Quackers on 2011-02-20
Windows bootloader is installed to the mbr of the drive. However, the Windows boot files include some files for XP, but the installed version appears to be Windows Vista or Windows 7. I presume nothing boots at the moment. Is that correct?

You appear to have Ubuntu 10.10 installed to the sde1 partition, but you also appear to be using grub legacy, whereas Ubuntu 10.10 used grub2 by default. You also appear to have Ubuntu 9.04 installed to sde6 partition.

Do you have a Windows Vista/7 installation disc or repair disc?

---

### Post by AlanAbbott on 2011-02-20
1. NO. I can only boot Windows 7, I get no options.
2. I had Ubuntu 9.04 and upgrated to 10.10.
3. YES. I have Windows 7 installation disc.

I'm booting from a Ubuntu 10.10 installation disc.

Alan

---

### Post by Quackers on 2011-02-20
Ok, you can boot Win 7.
You appear to have installed 10.10 to a separate partition, not upgraded from 9.04.
As a result you have grub legacy installed (or at least some bits of it). What I would suggest is, from the live cd desktop go to the site below and follow the "Why chroot" instructions to purge and re-install grub, mounting the sde1 partition and installing grub to sde (not sde1)

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you get stuck anywhere, or you're not sure you're doing the right thing, just ask here. It's better to get it right first time, if you can.

---

### Post by AlanAbbott on 2011-02-21
I ran all the commands I interpreted I had to run from [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) I took out the DVD before rebooting and I got an error. Should I do it all over and let the closing of the live ubuntu open the DVD.
And before closing mail myself the log of the hole process so that it is available to scrutinise.
My disk looks exactly the same a before I started.

 ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004162a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29321   235520901   83  Linux
/dev/sda2   *       30597       37179    52877947+   7  HPFS/NTFS
/dev/sda3           37180       38913    13928355    5  Extended
/dev/sda4           29322       30536     9759487+  83  Linux
/dev/sda5           37506       38913    11309728+  82  Linux swap / Solaris
/dev/sda6           37180       37483     2441817   83  Linux
/dev/sda7           37484       37505      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD322HJ (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  241GB  241GB   primary   ext3
 4      241GB   251GB  9994MB  primary   ext3
 2      252GB   306GB  54.1GB  primary   ntfs            boot
 3      306GB   320GB  14.3GB  extended
 6      306GB   308GB  2500MB  logical   ext3
 7      308GB   308GB  181MB   logical   linux-swap(v1)
 5      308GB   320GB  11.6GB  logical   swsusp


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label            
```

Alan

---

### Post by Quackers on 2011-02-21
Please re-run the boot script and post the results.
Were any errors reported anywhere along the procedure in that guide? If so, what?

---

### Post by AlanAbbott on 2011-02-21
I re-ran as you suggested and this is the log 
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004162a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29321   235520901   83  Linux
/dev/sda2   *       30597       37179    52877947+   7  HPFS/NTFS
/dev/sda3           37180       38913    13928355    5  Extended
/dev/sda4           29322       30536     9759487+  83  Linux
/dev/sda5           37506       38913    11309728+  82  Linux swap / Solaris
/dev/sda6           37180       37483     2441817   83  Linux
/dev/sda7           37484       37505      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD322HJ (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  241GB  241GB   primary   ext3
 4      241GB   251GB  9994MB  primary   ext3
 2      252GB   306GB  54.1GB  primary   ntfs            boot
 3      306GB   320GB  14.3GB  extended
 6      306GB   308GB  2500MB  logical   ext3
 7      308GB   308GB  181MB   logical   linux-swap(v1)
 5      308GB   320GB  11.6GB  logical   swsusp


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
mount: mount point /mnt/temp/dev does not exist
mount: mount point /mnt/temp/dev/pts does not exist
mount: mount point /mnt/temp/proc does not exist
mount: mount point /mnt/temp/sys does not exist
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp /mnt/temp/boot
ubuntu@ubuntu:~$ sudo mount /dev/sdXY /mnt/temp  # Mount the main Ubuntu partition. Example: sudo mount /dev/sda5 /mnt/temp
mount: special device /dev/sdXY does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sde1 /mnt/temp  # Mount the main Ubuntu partition. Example: sudo mount /dev/sda5 /mnt/temp
mount: special device /dev/sde1 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp  # Mount the main Ubuntu partition. Example: sudo mount /dev/sda5 /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp  # Mount the main Ubuntu partition. Example: sudo mount /dev/sda5 /mnt/temp
mount: /dev/sda1 already mounted or /mnt/temp busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp/boot  # Mount the /boot partition. Example: sudo mount /dev/sda6 /mnt/temp/boot
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update   # ***
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Get:2 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://linux.dropbox.com maverick Release.gpg                              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com/ubuntu/ jaunty/partner Translation-en
Hit http://ar.archive.ubuntu.com maverick Release.gpg                
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US 
Hit http://linux.dropbox.com maverick Release                                  
Get:3 http://dl.google.com stable Release [1,347B]                             
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://archive.canonical.com/ubuntu/ jaunty/partner Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                   
Ign http://archive.canonical.com/ lucid/partner Translation-en
Ign http://archive.canonical.com/ lucid/partner Translation-en_US
Hit http://archive.canonical.com maverick Release.gpg
Ign http://archive.canonical.com/ maverick/partner Translation-en
Ign http://archive.canonical.com/ maverick/partner Translation-en_US
Hit http://archive.canonical.com jaunty Release
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://ar.archive.ubuntu.com maverick-updates Release.gpg
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://linux.dropbox.com maverick/main amd64 Packages                      
Hit http://archive.canonical.com lucid Release                                 
Hit http://archive.canonical.com maverick Release                              
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://ar.archive.ubuntu.com maverick-security Release.gpg       
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en 
Get:4 http://dl.google.com stable/main amd64 Packages [1,089B]       
Hit http://archive.canonical.com jaunty/partner Sources                  
Hit http://archive.canonical.com jaunty/partner amd64 Packages           
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://ar.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://archive.canonical.com lucid/partner Sources               
Hit http://archive.canonical.com lucid/partner amd64 Packages
Hit http://archive.canonical.com maverick/partner Sources
Hit http://archive.canonical.com maverick/partner amd64 Packages
Hit http://ar.archive.ubuntu.com maverick Release
Hit http://ar.archive.ubuntu.com maverick-updates Release
Hit http://ar.archive.ubuntu.com maverick-security Release
Hit http://ar.archive.ubuntu.com maverick/main Sources
Hit http://ar.archive.ubuntu.com maverick/restricted Sources
Hit http://ar.archive.ubuntu.com maverick/universe Sources
Hit http://ar.archive.ubuntu.com maverick/multiverse Sources
Hit http://ar.archive.ubuntu.com maverick/main amd64 Packages
Hit http://ar.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://ar.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://ar.archive.ubuntu.com maverick/multiverse amd64 Packages
Hit http://ar.archive.ubuntu.com maverick-updates/main Sources
Hit http://ar.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://ar.archive.ubuntu.com maverick-updates/universe Sources
Hit http://ar.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://ar.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://ar.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://ar.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://ar.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Hit http://ar.archive.ubuntu.com maverick-security/main Sources
Hit http://ar.archive.ubuntu.com maverick-security/restricted Sources
Hit http://ar.archive.ubuntu.com maverick-security/universe Sources
Hit http://ar.archive.ubuntu.com maverick-security/multiverse Sources
Hit http://ar.archive.ubuntu.com maverick-security/main amd64 Packages
Hit http://ar.archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://ar.archive.ubuntu.com maverick-security/universe amd64 Packages
Hit http://ar.archive.ubuntu.com maverick-security/multiverse amd64 Packages
Fetched 2,705B in 4s (580B/s)
Reading package lists... Done
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
After this operation, 5,906kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 222591 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
rmdir: failed to remove `/boot/grub': No such file or directory
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/2,240kB of archives.
After this operation, 5,906kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 222312 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98+20100804-5ubuntu3_amd64.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98+20100804-5ubuntu3) ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 9.04 (9.04) on /dev/sda6
done
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 9.04 (9.04) on /dev/sda6
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys /boot; do sudo umount /mnt/temp$i ; done
umount: /mnt/temp/dev/pts: not mounted
umount: /mnt/temp/dev: not mounted
umount: /mnt/temp/proc: not mounted
umount: /mnt/temp/sys: not mounted
ubuntu@ubuntu:~$ 

```
 now I will reboot after sending this. ALAN

---

### Post by AlanAbbott on 2011-02-21
I rebooted and this was the GRUB that came-up, see attached photos, I do not have 10.10 and with it all my programs and files.

How can I pick these up?

Alan

---

### Post by Quackers on 2011-02-21
I asked for the boot script, not fdisk output.
Isn't kernel 2.6.35-25 an Ubuntu 10.10 kernel? Have you tried booting the top item in the grub menu?

---

### Post by AlanAbbott on 2011-02-22
All back to normal. I've got 10.10 running with all my mails, files and programs.
What baffled me was that when I first finished I thought I booted the first entry but I must of restarted the live ubuntu still in memory but with no drive to get executables from and all went dead.
I wrongly thought the first entry did not work.

Thank you all very much for you invaluable help and time you have spent with my problem, dino99; Quackers that followed me out to the end, and Rubi1200.

Now I will branch-out to another possible solution to get SSL Extender running as does not work under Win 64 and I have little space left. So I will get a second disk and try to install Win 7-32bit on it and run side by side with Ubuntu and Win 7-64.

Alan :P:P

---

### Post by Quackers on 2011-02-22
Niiiiiiiiice :-)
You're welcome.

---

