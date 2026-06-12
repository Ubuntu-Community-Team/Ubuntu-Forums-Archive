---
title: "Grub Killed Windows!"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by Whatnext on 2010-05-12
Hi there smart folks, would appreciate some advice on a problem.

I installed Ubuntu on a flash drive today. When I rebooted, neither Xp (on the hard drive) or Ubuntu (on the flash) would load. I reinstalled Ubuntu and in 'advanced settings' I pointed the bootloader to the flash drive (as default is hd0, my XP drive). Now, Ubuntu flash works fine, but I can't access XP! 

I suspect some bootloader files from the first install are gumming up XP. What files should I search for and remove?

Thanks for reading, thanks for helping.

P.S. I don't have a windows recovery disc, also I installed 9.04 on the flash

EDIT: more info: when I tried to load XP, it said, "grub loading ... error 21 or 18 (I forget which)

---

### Post by confused57 on 2010-05-13
This should restore your ability to boot Windows on your internal drive:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

See the section on installing lilo.

---

### Post by Whatnext on 2010-05-13
I followed the directions in your link, here is where a problem arose:

matt@SYS:~$ echo "SET grub-pc/install_devices $drive" | sudo debconf-communicate10 grub-pc/install_devices doesn't exist
matt@SYS:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lilo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lilo has no installation candidate
matt@SYS:~$ sudo lilo -M /dev/sda mbr
sudo: lilo: command not found
matt@SYS:~$ 

Thoughts?

P.S. thanks

---

### Post by confused57 on 2010-05-13
Somebody should be able to see what's going on with your system & can help you if you post the output of the boot.info script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It's possible with your first install you installed grub to the partition with Windows.

Added:  You might try the instructions for installing lilo from the 9.04 live cd, rather than from your flash 9.04 install.

---

### Post by Whatnext on 2010-05-13
Boy, this starts out legible, but quickly spins into indecipherable code-talk (to layman me at least lol) SDA is My hard drive I think, SDB the flash-Ubuntu, SDC another flash for storage. If I'm reading it correctly, XP's MBR is looking in the wrong place for boot data. I don't think I know how to fix that.

After that I get lost. Here's the text:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

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
    Operating System:  Ubuntu 9.04
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

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa9c5e7bd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,124,094    78,124,032   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000837c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    14,924,384    14,924,322  83 Linux
/dev/sdb2          14,924,385    15,695,504       771,120   5 Extended
/dev/sdb5          14,924,448    15,695,504       771,057  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x67be2ee3

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  52    31,283,909    31,283,858   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        FCB87263B8721C78                       ntfs                                     
/dev/sdb1        f14b9194-9b78-422f-8d5d-234a5e3abf23   ext3                                     
/dev/sdb5        f1d3ace1-a87a-4ebe-b140-ee85168530b6   swap                                     
/dev/sdc1        6005-FB28                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=matt)
/dev/sdc1        /media/disk-1            vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=f14b9194-9b78-422f-8d5d-234a5e3abf23 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f14b9194-9b78-422f-8d5d-234a5e3abf23

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
uuid        f14b9194-9b78-422f-8d5d-234a5e3abf23
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f14b9194-9b78-422f-8d5d-234a5e3abf23 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f14b9194-9b78-422f-8d5d-234a5e3abf23
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f14b9194-9b78-422f-8d5d-234a5e3abf23 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f14b9194-9b78-422f-8d5d-234a5e3abf23
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
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=f14b9194-9b78-422f-8d5d-234a5e3abf23 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=f1d3ace1-a87a-4ebe-b140-ee85168530b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   5.0GB: boot/grub/menu.lst
   5.0GB: boot/grub/stage2
   4.8GB: boot/initrd.img-2.6.28-11-generic
   4.9GB: boot/vmlinuz-2.6.28-11-generic
   4.8GB: initrd.img
   4.9GB: vmlinuz
```

---

### Post by confused57 on 2010-05-13
I added a comment to my previous post about installing lilo from the Ubuntu 9.04 live cd rather than from your flash drive install, which you might want to try.

Also, you could add an entry to your your menu.lst that should be able to boot Windows XP on your internal drive, which would be a temporary solution for now to boot XP. Boot into Ubuntu on your flash drive, open a terminal(Applications--->Accessories--->Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

change your XP entry to:
```
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
makeactive
map           (hd0) (hd1)
map           (hd1) (hd0) 
chainloader    +1
```
Save & quit

You might want to copy&paste the above into a terminal, rather than trying to type.  If this works, it would show that your Windows is bootable, then we can go from there.

---

### Post by confused57 on 2010-05-13
Sorry, I had a typo in the Windows entry, which I've corrected.

---

### Post by Whatnext on 2010-05-13
search cd didn't see any files named lilo

I have made the changes to the menu.lst

I assume that I will reboot to test it?

<rebooting>

I will reboot and attempt to select XP from the flash grub menu

EDIT: Attempts to start XP via flash grub resulted in the Phrase "Starting..." and then seemed to hang there. An improvement over error messages, but it didn't boot (let it "start" for a minute or two before retry)

---

### Post by confused57 on 2010-05-13
> **Whatnext said:**
> search cd didn't see any files named lilo

I have made the changes to the menu.lst

I assume that I will reboot to test it?

<rebooting>

I will reboot and attempt to select XP from the flash grub menu

Hope you saw my correction before rebooting, but you might also want to make a copy of Super Grub Disk:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

SGD is a handy boot cd to have in your arsenal to boot Windows or Linux, as well as, repair the mbr of either.

---

### Post by Whatnext on 2010-05-13
I just rebooted and noticed your correction. I'll try again with the new data.

EDIT: The corrected numbers worked and I booted into windows successfully. While I would still like to be able to boot XP independently, you've given me a good workaround. 

Unfortunately, I have to be up early in the morning for an appointment, so I can't do more tonight (I've stayed up rather later than I should have but at least things work now). 

Thanks for your help.

---

### Post by confused57 on 2010-05-13
> **Whatnext said:**
> I just rebooted and noticed your correction. I'll try again with the new data.

EDIT: The corrected numbers worked and I booted into windows successfully. While I would still like to be able to boot XP independently, you've given me a good workaround. 

Unfortunately, I have to be up early in the morning for an appointment, so I can't do more tonight (I've stayed up rather later than I should have but at least things work now). 

Thanks for your help.

Glad it worked for you, I need to get to bed also, have to get up early for an appointment.

When you try again, you might want to open Synaptic Package Manager...go to Settings--->Repositories and make sure the universe and multiverse repositories are checked, Update, then try installing lilo.

---

