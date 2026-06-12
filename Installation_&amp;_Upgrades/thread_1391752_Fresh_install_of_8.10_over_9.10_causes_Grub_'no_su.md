---
title: "Fresh install of 8.10 over 9.10 causes Grub 'no such disk' error"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by rhills on 2010-01-27
Hi,

I have a dual boot machine (Win XP + Ubuntu 9.10 on separate physical drives) which was working fine.

I now want to replace the Ubuntu 9.10 with LinuxMCE which is based on Ubuntu 8.10.  Using the LinuxMCE install disk, I did a fresh install of Ubuntu 8.10 over the top of Ubuntu 9.10 (repartitioning the whole drive).  On reboot, I now get a Grub "no such disk" error.

I have run the boot info script which produced the following RESULT.txt:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=6a59ab9e-041f-41e2-b27c-02b8ada4c1af)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe685e685

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   240,091,424   137,693,115   f W95 Ext d (LBA)
/dev/sda5         102,398,373   240,091,424   137,693,052   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b9df001

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,067,049   234,066,987  83 Linux
/dev/sdb2         234,067,050   240,107,489     6,040,440   5 Extended
/dev/sdb5         234,067,113   240,107,489     6,040,377  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15058280

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   117,226,304   117,226,242   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4CEC969EEC9681BE                       ntfs                                     
/dev/sda5        3C7CF45B7CF410FE                       ntfs       Apps                          
/dev/sdb1        98006b2a-3eb2-4845-8c5e-14aa32161a7d   ext3                                     
/dev/sdb5        b98a46e1-7346-415c-9bed-d863f559ceed   swap                                     
/dev/sdc1        0C8817C18817A7EA                       ntfs       Data                          

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

rootfs           /                rootfs     (rw)
/proc            /proc            proc       (rw)
/dev/scd1        /cdrom           iso9660    (ro,noatime)
/dev/loop0       /rofs            squashfs   (ro,noatime)


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
# kopt=root=UUID=98006b2a-3eb2-4845-8c5e-14aa32161a7d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98006b2a-3eb2-4845-8c5e-14aa32161a7d

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

title        Ubuntu 8.10, kernel 2.6.27-15-generic
uuid        98006b2a-3eb2-4845-8c5e-14aa32161a7d
kernel        /boot/vmlinuz-2.6.27-15-generic root=UUID=98006b2a-3eb2-4845-8c5e-14aa32161a7d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-15-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
uuid        98006b2a-3eb2-4845-8c5e-14aa32161a7d
kernel        /boot/vmlinuz-2.6.27-15-generic root=UUID=98006b2a-3eb2-4845-8c5e-14aa32161a7d ro  single
initrd        /boot/initrd.img-2.6.27-15-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        98006b2a-3eb2-4845-8c5e-14aa32161a7d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=98006b2a-3eb2-4845-8c5e-14aa32161a7d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        98006b2a-3eb2-4845-8c5e-14aa32161a7d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=98006b2a-3eb2-4845-8c5e-14aa32161a7d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        98006b2a-3eb2-4845-8c5e-14aa32161a7d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
root        (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=98006b2a-3eb2-4845-8c5e-14aa32161a7d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b98a46e1-7346-415c-9bed-d863f559ceed none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  56.8GB: boot/grub/menu.lst
  56.8GB: boot/grub/stage2
  56.8GB: boot/initrd.img-2.6.27-15-generic
  56.9GB: boot/initrd.img-2.6.27-7-generic
  56.8GB: boot/vmlinuz-2.6.27-15-generic
  56.8GB: boot/vmlinuz-2.6.27-7-generic
  56.9GB: initrd.img
  56.9GB: initrd.img.old
  56.8GB: vmlinuz

```My interpretation of this is that I have somehow got Grub 2 on the /dev/sda MBR and that this is being found by the bootloader.  I believe I need to remove this and somehow get the bootloader to find the Grub 0.97 on /dev/sdb instead.  Is this correct?

If so, how do I go about doing that?

TIA,

Rob Hills
Waikiki, Western Australia

---

### Post by darkod on 2010-01-27
You are correct. Go into BIOS and find the hard disk boot order and make /dev/sdb the first option. Both sda and sdb are the same size 123GB so it will be difficult to tell them apart in BIOS, but if you just switch places in the boot order it should do the job.

Another thing you might consider later, is reinstalling windows MBR on the MBR of /dev/sda since you have XP on that drive anyway. sdb will still have to remain first option for boot otherwise sda will just boot into XP with no option for 8.10.

---

### Post by rhills on 2010-01-27
Hi Darkod,

Thanks for the thought about changing the boot order in BIOS.  Fortunately, I'd actually recorded the BIOS ids of each of the disks so it was easy to swap the order around and on reboot, I was able to boot up Kubuntu 8.10.

Will I have to switch the disks again in BIOS, to fix the Windoze MBR or is its repair process flexible enough to ask me which disk I want to point it at?

TIA,

Rob Hills
Waikiki, Western Australia

---

### Post by darkod on 2010-01-27
Depends how you do it. If you use the windows install disc and the correct procedure for the windows version from here for example:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

it's better to make the windows disk first in boot order BEFORE starting the procedure because windows is used to install its bootloader to the disk first in boot order regardless where exactly is windows installed. So it might actually ruin your grub1 on /dev/sdb if it remains first option.

Another option for restoring windows MBR, very easy and from ubuntu is the following. I know it's working on 9.10 and 9.04 but not sure about 8.10, however it should:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be few warnings but ignore them. This uses lilo (even though LILO is not your bootloader) to install generic windows MBR on /dev/sda. Because you specify the exact disk, it makes no difference what is the current boot order. You could do this with /dev/sdb first in boot order.

---

### Post by rhills on 2010-01-28
Thanks again, Darkod,

I followed your second suggestion:

> **darkod said:**
> Another option for restoring windows MBR, very easy and from ubuntu is the following. I know it's working on 9.10 and 9.04 but not sure about 8.10, however it should:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be few warnings but ignore them. This uses lilo (even though LILO is not your bootloader) to install generic windows MBR on /dev/sda. Because you specify the exact disk, it makes no difference what is the current boot order. You could do this with /dev/sdb first in boot order.

but on trying to reboot to Windoze, I ended up with a grub error 13 "Invalid or unsupported executable format".

Some googling lead me to [this thread]("http://ubuntuforums.org/showpost.php?p=1650372&postcount=2") which helped me fix my problem.  On the second page of that thread, Catlett gave a [very succinct explanation]("http://ubuntuforums.org/showpost.php?p=1717948&postcount=13") of what his suggested fix was doing, which helped me no end.

I'm now back to a happily dual-booting system, so we can watch TV again (on Windoze) until I get Linux-MCE working :D

Many thanks,

Rob Hills
Waikiki, Western Australia

---

### Post by bricktop41 on 2010-01-28
I just installed backtrack 4 final on my dual boot laptop I have kubunt 9.10 on /dev/sda2 with Bt4 on /dev/sda1 I am getting error 15 and I really don't know where to edit the the grub menu to correct tis error I have attached the list so you guys can help me out 

Thank you 

 BEGIN AUTOMAGIC KERNELS LIST
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
# kopt=root=UUID=f34d7b46-3f5f-4443-aec1-ca46876c9a7c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f34d7b46-3f5f-4443-aec1-ca46876c9a7c

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=f34d7b46-3f5f-4443-aec1-ca46876c9a7c/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.30.9
uuid        f34d7b46-3f5f-4443-aec1-ca46876c9a7c
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=f34d7b46-3f5f-4443-aec1-ca46876c9a7c ro quiet splash 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid        f34d7b46-3f5f-4443-aec1-ca46876c9a7c
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=f34d7b46-3f5f-4443-aec1-ca46876c9a7c ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        f34d7b46-3f5f-4443-aec1-ca46876c9a7c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu, Linux 2.6.31-17-generic (on /dev/sda2)
root            (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=44f1de2c-fa26-4cc1-ac87-9477eb388a20 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=44f1de2c-fa26-4cc1-ac87-9477eb388a20 ro single 
initrd        /boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu, Linux 2.6.31-14-generic (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=44f1de2c-fa26-4cc1-ac87-9477eb388a20 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=44f1de2c-fa26-4cc1-ac87-9477eb388a20 ro single 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot

---

