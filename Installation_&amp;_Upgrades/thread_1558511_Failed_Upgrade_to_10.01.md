---
title: "Failed Upgrade to 10.01"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by L0key on 2010-08-22
I'm very new to the Linux world and have managed to get myself in trouble. I had installed Ubuntu 8.04 and partitioned my drive to share 500gB with Windows XP. All was good. When I saw that Ubuntu 10.01 was available I downloaded it to update the 8.04. Ididn't want to have to redo all my configurations so told installer not to update config files. No entry in GRUB no boot. Tried to re-install 8.04 to replace 10.01 and get back to intial state. Current state Ubuntu won;t boot, XP still OK but don't know how to clean up my mess. I've attached a copy of a boot info script I ran.

Thanks for any help you can give.

 ```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b6a9b6a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   376,370,819   376,370,757   7 HPFS/NTFS
/dev/sda2         376,370,820   976,768,064   600,397,245   5 Extended
/dev/sda5         376,370,883   378,330,749     1,959,867  82 Linux swap / Solaris
/dev/sda6         378,330,813   976,768,064   598,437,252  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A4E80E59E80E29DE                       ntfs                                     
/dev/sda5        da85057c-63e3-4387-9259-3e3c022ecf62   swap                                     
/dev/sda6        d9fb88c1-e1c0-4309-9886-49a4d8293d5f   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro single
initrd        /boot/initrd.img-2.6.24-27-generic

#title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro quiet splash
#initrd        /boot/initrd.img-2.6.24-26-generic
#quiet

3title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
3root        (hd0,5)
3kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro single
#initrd        /boot/initrd.img-2.6.24-26-generic

#title        Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-25-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro quiet splash
#initrd        /boot/initrd.img-2.6.24-25-generic
#quiet

#title        Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic (recovery mode)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-25-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro single
#initrd        /boot/initrd.img-2.6.24-25-generic

#title        Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro quiet splash
#initrd        /boot/initrd.img-2.6.24-24-generic
#quiet

#title        Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro single
#initrd        /boot/initrd.img-2.6.24-24-generic

#title        Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro quiet splash
#initrd        /boot/initrd.img-2.6.24-23-generic
#quiet

#title        Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro single
#initrd        /boot/initrd.img-2.6.24-23-generic

#title        Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro quiet splash
#initrd        /boot/initrd.img-2.6.24-16-generic
#quiet

#title        Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic (recovery mode)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f ro single
#initrd        /boot/initrd.img-2.6.24-16-generic

#title        Ubuntu 8.04.4 LTS, memtest86+
#root        (hd0,5)
#kernel        /boot/memtest86+.bin
#quiet

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


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d9fb88c1-e1c0-4309-9886-49a4d8293d5f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=da85057c-63e3-4387-9259-3e3c022ecf62 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 436.1GB: boot/grub/menu.lst
 436.2GB: boot/grub/stage2
 436.2GB: boot/initrd.img-2.6.24-27-generic
 436.2GB: boot/initrd.img-2.6.24-27-generic.bak
 436.2GB: boot/initrd.img-2.6.32-24-generic
 436.1GB: boot/vmlinuz-2.6.24-27-generic
 436.2GB: boot/vmlinuz-2.6.32-24-generic
 436.2GB: initrd.img
 436.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 

```

---

### Post by clrg on 2010-08-22
What happens when you try to boot Ubuntu? Any error messages?

---

### Post by jocko on 2010-08-22
It looks like your grub is only aware of your old 8.04 kernels, while the boot info script claims that you have kernels from both 8.04 and 10.04 in the /boot directory your /dev/sda6 partition. This is only expected given the fact that you told the installer to keep your old configuration files instead of generating new ones.

When you tried to reinstall 8.04, did you really let the partitioner format the partition? If not, you have a mix of 8.04 and 10.04, which is doomed to fail (I don't even think the ubuntu installer will finish the install on a filesystem that already contains files from a previous install)...

The quick and easy solution (and possibly the only solution):
1. Make sure you back up any data that you want to keep.
2. Make a fresh install (if you haven't already, I suggest you get a 10.04.1 CD from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download")).
This means you make sure the installer formats the partition, to remove any trace of the mess you have now. And next time you upgrade, let the installer upgrade the entire OS, including the configuration files.

---

### Post by L0key on 2010-08-22
The 10.01 upgrade never asked about partioning, but whe I tried to re-install by 8.04 from CD it did show a 10.01 and a 8.04 partion.

Anyway I'll have to get an exteranal drive and find out how to backup the system, my Ubuntu book is kind of vauge on how to backup the Windows and Linux partions (not to mention how to restore same!). I have to see if I can burn a CD from the Ubuntu live cd and then have a try at this one more time. Clearly I need to learn a lot more about what's "under the hood" Ubuntu if I'm going to stay with this as my main OS.

Thank you very much for your help. 

;)

---

### Post by clrg on 2010-08-22
Quick and dirty tutorial:

1. Boot from a live cd
2. Mount your ubuntu partitions
3. Copy everything of value to your external disk
4. Done :)

---

