---
title: "Hmmm - computer repair shop messed up my linux installation"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by Kitteridge on 2010-06-16
Dear all,

Thanks for reading. I've just had to get my PC repaired and, although I warned the repair shop that the system was a linux machine (I have GRUB and dual boot Vista when I have to use Windows), they attempted to 'repair the disks' as part of the service and messed up the linux installation (Windows, of course, still runs fine). When I collected the PC, they said, 'Sorry, we don't really do linux here'. I was terrified that they had managed to wipe the whole partition, and was ready to get angry with them, but fortunately, that's not the case.

The problem is that, now when I try to boot into linux, it initially hangs, then goes to a purple splash screen saying that /tmp is missing - do I want to repair etc.. Repairing does no good and I'm not skilled enough to fix this manually. I've managed to boot using a 10.04 live cd, access the linux partition and I can confirm that the /tmp directory is present (phew)

I guess my question is, what do you think is missing so that I can rescue the old installation, or, perhaps, what can I do to find out what is missing...

As I said, I've managed to boot with a live cd and am in the process of backing up important data before I proceed (I know, I should have done this before the computer breaks down :-)) 



I ran boot info script from the live cd so that the experts can have a look, if they like:

Thanks for reading!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

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
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   752,227,559   752,227,497  83 Linux
/dev/sda2    *    752,227,560   957,024,179   204,796,620   7 HPFS/NTFS
/dev/sda3         957,024,180   976,768,064    19,743,885   5 Extended
/dev/sda5         957,024,243   976,768,064    19,743,822  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        fe1d92eb-9451-49eb-aab6-a0d249dfae27   ext3                                     
/dev/sda2        1FF6F4DB3DD63795                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        d77c6a7d-abeb-422f-bb2b-35d681ea4fa7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2248B74448B7160F                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4A323B33323B237D                       ntfs       New Volume                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/fe1d92eb-9451-49eb-aab6-a0d249dfae27 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
# kopt=root=UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fe1d92eb-9451-49eb-aab6-a0d249dfae27

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        fe1d92eb-9451-49eb-aab6-a0d249dfae27
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        fe1d92eb-9451-49eb-aab6-a0d249dfae27
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        fe1d92eb-9451-49eb-aab6-a0d249dfae27
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        fe1d92eb-9451-49eb-aab6-a0d249dfae27
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        fe1d92eb-9451-49eb-aab6-a0d249dfae27
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        fe1d92eb-9451-49eb-aab6-a0d249dfae27
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-14-generic
uuid        fe1d92eb-9451-49eb-aab6-a0d249dfae27
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-14-generic (recovery mode)
uuid        fe1d92eb-9451-49eb-aab6-a0d249dfae27
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27 ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        fe1d92eb-9451-49eb-aab6-a0d249dfae27
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title    Windows Vista
root    (hd0,1)
makeactive
chainloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda1 :
UUID=fe1d92eb-9451-49eb-aab6-a0d249dfae27    /    ext3    relatime,errors=remount-ro    0    1
#Entry for /dev/sdb1 :
UUID=2248B74448B7160F    /media/2248B74448B7160F_    ntfs    defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077    0    0
#Entry for /dev/sda5 :
UUID=d77c6a7d-abeb-422f-bb2b-35d681ea4fa7    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0



=================== sda1: Location of files loaded by Grub: ===================


 318.9GB: boot/grub/menu.lst
 314.8GB: boot/grub/stage2
 337.1GB: boot/initrd.img-2.6.27-14-generic
 314.8GB: boot/initrd.img-2.6.28-18-generic
 367.5GB: boot/initrd.img-2.6.32-21-generic
 318.9GB: boot/initrd.img-2.6.32-22-generic
 314.8GB: boot/vmlinuz-2.6.27-14-generic
 314.8GB: boot/vmlinuz-2.6.28-18-generic
 314.8GB: boot/vmlinuz-2.6.32-21-generic
 318.9GB: boot/vmlinuz-2.6.32-22-generic
 318.9GB: initrd.img
 367.5GB: initrd.img.old
 318.9GB: vmlinuz
 314.8GB: vmlinuz.old

```

---

### Post by Kitteridge on 2010-06-16
Hi Guys,

Running fsck for a second time seemed to do the trick - it's all working fine again.

Thanks for reading.

---

