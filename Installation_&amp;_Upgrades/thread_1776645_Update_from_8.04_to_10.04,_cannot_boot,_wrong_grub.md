---
title: "Update from 8.04 to 10.04, cannot boot, wrong grub root ?"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by Djense on 2011-06-06
I just updated my server from Ubuntu 8.04 to 10.04 and now it cannot go past grub, at boot time, it would "give up waiting for root device", asking me to check whether I gave the right "root=..." or if I should increase the "rootdelay=..." in the command line argument and end up with the initramfs.

The machine is a Dell Poweredge 2900 with a HW RAID controller (I hope that should not matter, but just in case...).

I tried to follow the instructions [there]("http://ubuntuforums.org/showthread.php?t=224351") to make sure grub is setup correctly, but without any luck.

Below is the output from the bootinfoscript (while running on the LiveCD).

Anybody has any idea what can be the problem or what I could do to debug this ? I am running out of ideas....

Thanks !


                                                                     
  ```
                                                                   
                                                                     
                                             
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2999.0 GB, 2998960914432 bytes
255 heads, 63 sectors/track, 364602 cylinders, total 5857345536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 4,294,961,684 4,294,961,622  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 299.4 GB, 299439751168 bytes
255 heads, 63 sectors/track, 36404 cylinders, total 584843264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   567,769,229   567,769,167  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        66fd7917-10c5-462c-884f-52cf6b493b71   ext3       
/dev/sdc1        5c1e8e4f-e290-4a52-9214-341762764a68   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev             /home/ubuntu/mnt/dev     none       (rw,bind)
/dev/sdc1        /home/ubuntu/mnt         ext3       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# kopt=root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro

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

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-32-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-32-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-32-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-32-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-32-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro  single
initrd		/boot/initrd.img-2.6.32-32-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.24-28-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro  single
initrd		/boot/initrd.img-2.6.24-28-generic

title		Ubuntu 10.04.2 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/swapfile       swap            swap    defaults        0       0
# /dev/sdb1
UUID=5c1e8e4f-e290-4a52-9214-341762764a68 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=a7a6eaaf-c01d-4e52-9f04-3ee786de0772 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=66fd7917-10c5-462c-884f-52cf6b493b71    /mnt/storage    ext3 relatime,errors=remount-ro 0   1
172.16.23.3:/DataVolume/SW_Engineering    /mnt/SW_Engineering nfs
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 123.206241131 = 132.291694080  boot/grub/menu.lst                             1
 122.937636852 = 132.003282432  boot/grub/stage2                               2
 146.906264782 = 157.739400704  boot/initrd.img-2.6.24-28-generic              5
 122.952357769 = 132.019088896  boot/initrd.img-2.6.24-28-generic.bak          3
 146.928920269 = 157.763726848  boot/initrd.img-2.6.32-32-generic             43
 122.986217022 = 132.055444992  boot/vmlinuz-2.6.24-28-generic                 2
  98.532496929 = 105.798462976  boot/vmlinuz-2.6.32-32-generic                11
 146.928920269 = 157.763726848  initrd.img                                    43
 146.906264782 = 157.739400704  initrd.img.old                                 5
  98.532496929 = 105.798462976  vmlinuz                                       11
 122.986217022 = 132.055444992  vmlinuz.old                                    2

========= Devices which don't seem to have a corresponding hard drive: =========

sda 

```

---

### Post by Djense on 2011-06-06
Sorry, seems like adding the rootdelay fixes it....

---

