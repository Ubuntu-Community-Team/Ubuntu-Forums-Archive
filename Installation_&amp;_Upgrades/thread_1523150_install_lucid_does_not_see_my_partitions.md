---
title: "install lucid does not see my partitions"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by ChipUser on 2010-07-03
Hello,

I have a dual boot system with Win7 and Ubuntu 9.10. Karmic was upgraded from 9.04 and still has grub1

I want to install 10.04 over the 9.04 (fresh install). I'm using the Desktop edition iso, burnt on a CD. When it gets to the partition selection it says that there is no OS on my comp and offers to install over the whole disk. At this point I cancelled the installation and went in my old 9.10 to check my partitions. Using fdisk they appear normal, but GParted sees my disk as unpartitioned.

Here is some info on my system:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8d32665

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,385,929     8,385,867   7 HPFS/NTFS
/dev/sda2    *      8,385,930    62,910,539    54,524,610   7 HPFS/NTFS
/dev/sda3          62,910,540   377,479,304   314,568,765   7 HPFS/NTFS
/dev/sda4         377,479,305   488,408,129   110,928,825   f W95 Ext d (LBA)
/dev/sda5         377,479,368   385,479,674     8,000,307  82 Linux swap / Solaris
/dev/sda6         385,479,738   488,392,064   102,912,327  83 Linux

/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3000C7A900C7747E                       ntfs       SWAP                          
/dev/sda2        90A0D9DEA0D9CABC                       ntfs       WIN                           
/dev/sda3        68746003745FD284                       ntfs       DATA                          
/dev/sda5        7b330892-6efe-4385-95b3-e21aa54874d8   swap                                     
/dev/sda6        f8f540e9-9d5e-435d-97ac-318e9617a5be   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

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
default        4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=f8f540e9-9d5e-435d-97ac-318e9617a5be ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f8f540e9-9d5e-435d-97ac-318e9617a5be

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
# howmany=1

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

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        f8f540e9-9d5e-435d-97ac-318e9617a5be
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=f8f540e9-9d5e-435d-97ac-318e9617a5be ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        f8f540e9-9d5e-435d-97ac-318e9617a5be
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=f8f540e9-9d5e-435d-97ac-318e9617a5be ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, memtest86+
uuid        f8f540e9-9d5e-435d-97ac-318e9617a5be
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=f8f540e9-9d5e-435d-97ac-318e9617a5be /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7b330892-6efe-4385-95b3-e21aa54874d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 199.5GB: boot/grub/menu.lst
 199.5GB: boot/grub/stage2
 199.0GB: boot/initrd.img-2.6.28-13-generic
 199.3GB: boot/initrd.img-2.6.31-14-generic
 199.0GB: boot/initrd.img-2.6.31-15-generic
 199.0GB: boot/initrd.img-2.6.31-16-generic
 199.0GB: boot/initrd.img-2.6.31-17-generic
 199.0GB: boot/initrd.img-2.6.31-19-generic
 199.0GB: boot/initrd.img-2.6.31-20-generic
 199.1GB: boot/initrd.img-2.6.31-21-generic
 199.2GB: boot/initrd.img-2.6.31-22-generic
 199.0GB: boot/vmlinuz-2.6.28-13-generic
 199.1GB: boot/vmlinuz-2.6.31-14-generic
 199.0GB: boot/vmlinuz-2.6.31-15-generic
 199.0GB: boot/vmlinuz-2.6.31-16-generic
 199.0GB: boot/vmlinuz-2.6.31-17-generic
 199.0GB: boot/vmlinuz-2.6.31-19-generic
 199.1GB: boot/vmlinuz-2.6.31-20-generic
 198.9GB: boot/vmlinuz-2.6.31-21-generic
 199.1GB: boot/vmlinuz-2.6.31-22-generic
 199.2GB: initrd.img
 199.1GB: initrd.img.old
 199.1GB: vmlinuz
 198.9GB: vmlinuz.old

```

---

### Post by darkod on 2010-07-03
```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total [COLOR=Red]488397168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8d32665

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,385,929     8,385,867   7 HPFS/NTFS
/dev/sda2    *      8,385,930    62,910,539    54,524,610   7 HPFS/NTFS
/dev/sda3          62,910,540   377,479,304   314,568,765   7 HPFS/NTFS
/dev/sda4         377,479,305   [COLOR=Red]488,408,129[/COLOR]   110,928,825   f W95 Ext d (LBA)
/dev/sda5         377,479,368   385,479,674     8,000,307  82 Linux swap / Solaris
/dev/sda6         385,479,738   488,392,064   102,912,327  83 Linux

[COLOR=Red]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]
```

This seems to be your problem. Somehow the end point of the extended partition sda4 is set beyond the total number of sectors the hdd has.
But I'm not sure what exactly to do. Maybe using testdisk to sort out/repair the partition table.
Gparted is designed when such an error is detected, it just ignores the partition table that's why it's showing the disk like with no partitions.

---

### Post by ChipUser on 2010-07-03
Thank you, I didn't see that before. I used another partitioning tool to resize the logical partition.

I'm going to try install 10.04 now.

---

