---
title: "cannot boot after upgrade to 10"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by heartcore on 2010-11-14
I get this:
> udev[412]: sysfs{}= will be removed in a future udev version, please use ATT* = to match the event device,or ATTRS{}= to match a parent device in etc/udev/45-libnjb5.rules:<number>

I 've been trying for more than a month

can any body help pleasE? I hate using windows

---

### Post by Rubi1200 on 2010-11-14
Hi,
you are not giving us much to work with here.

Please post the following information:

1. computer specifications especially RAM and graphics card

2. which version did you upgrade from?

3. were there other problems prior to this or was this the only error?

4. have you tried booting into Recovery Mode?

5. do you have other operating systems installed and what?

5. how did you install Ubuntu in the first place?

Thanks.

---

### Post by heartcore on 2010-11-15
hi

1. AMD 2.3GHz 2GB RAM, Nvidia graphics card
2. upgraded through synaptic from 8.* to 10.*
3. there were no other serious errors prior to this

It is a dual boot machine with windows xp

---

### Post by Rubi1200 on 2010-11-15
Thanks for the information.

Here is what I suggest:

Boot the computer with a LiveCD and choose to try Ubuntu in live mode.

Then, chroot into the system. What this does is essentially give you control of the file-system as if you were booted normally. Then, we will do some housecleaning and hopefully get things up and running again.

Use the guide here on how to do this:
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Make sure you mount _your_ Ubuntu partition and not sda3 as in the guide (unless that happens to be the correct one :-))

Once the chroot is mounted, run the following commands in the terminal (no need for sudo):

> apt-get autoclean
apt-get clean
apt-get update
apt-get upgrade
apt-get -f install
dpkg --configure -aRun the commands one at a time and report back if you encounter errors.

Then follow the guide above to exit the chroot environment.

Reboot and hopefully you are back in business.

---

### Post by heartcore on 2010-11-15
thanx a lot man I will try this

---

### Post by drs305 on 2010-11-15
I get this a lot from my HP printer files. In your case it's the way the 45-libnjb5.rules are written.  

If you read what the message is saying, it's more or less an advisory message for now. I don't think there is much you can do about it until someone rewrites the configuration files for that package.

---

### Post by Rubi1200 on 2010-11-15
Hi heartcore,
if you have not already gone too deep into the process, it would also help us if you post the results of the boot info script from the LiveCD.

The link with instructions is at the bottom of my post.

Thanks.

---

### Post by heartcore on 2010-11-15
I followed the instructions, there were no errors but still the problem persists.

I attach the result.txt file as you suggested.

Thanks a lot for your help

edit:don't know if this helps but the boot log says
> 
swapon: /dev/disk/by-uuid/81c1923f-f9e8-44e6-bc0c-2a38ca51dfc6: swapon failed: Device or resource busy
mountall: swapon /dev/disk/by-uuid/81c1923f-f9e8-44e6-bc0c-2a38ca51dfc6 [877] terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/81c1923f-f9e8-44e6-bc0c-2a38ca51dfc6
Skipping /media/Misc at user request
 * Starting AppArmor profiles       [80G 

---

### Post by Rubi1200 on 2010-11-15
For those concerned:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
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

/dev/sda1    *             63   204,154,019   204,153,957   7 HPFS/NTFS
/dev/sda2         204,154,020   976,768,064   772,614,045   5 Extended
/dev/sda5         204,154,083   964,606,859   760,452,777  83 Linux
/dev/sda6         964,606,923   976,768,064    12,161,142  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   488,392,064   488,392,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C08C4E648C4E5556                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        aff7dab3-64cb-42f3-a5b3-113f87865802   ext3                                     
/dev/sda6        81c1923f-f9e8-44e6-bc0c-2a38ca51dfc6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7CE0984BE0980E10                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        CC99-CF6B                              vfat       My Passport                   
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /mnt                     ext3       (rw)
/dev             /mnt/dev                 none       (rw,bind)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDAWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDAWS="WinDAWS" /noexecute=optin /fastdetect /usepmtimer 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP " /noexecute=optin /fastdetect /usepmtimer 

=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout        11

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=aff7dab3-64cb-42f3-a5b3-113f87865802 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=aff7dab3-64cb-42f3-a5b3-113f87865802 ro  
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=aff7dab3-64cb-42f3-a5b3-113f87865802 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows systems
root        (hd0,0)
savedefault
makeactive
chainloader    +1




=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=aff7dab3-64cb-42f3-a5b3-113f87865802 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=81c1923f-f9e8-44e6-bc0c-2a38ca51dfc6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdc1 /media/Misc ntfs-3g defaults 0 0
#/dev/sdb1 /media/Programs ntfs-3g defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


 173.8GB: boot/grub/menu.lst
 164.9GB: boot/grub/stage2
 164.9GB: boot/initrd.img-2.6.24-19-generic
 164.9GB: boot/initrd.img-2.6.24-19-generic.bak
 164.9GB: boot/initrd.img-2.6.24-19-rt
 164.9GB: boot/initrd.img-2.6.24-19-rt.bak
 164.9GB: boot/initrd.img-2.6.24-21-generic
 165.0GB: boot/initrd.img-2.6.24-21-generic.bak
 164.9GB: boot/initrd.img-2.6.24-21-rt
 164.9GB: boot/initrd.img-2.6.24-21-rt.bak
 165.0GB: boot/initrd.img-2.6.24-22-generic
 165.0GB: boot/initrd.img-2.6.24-22-generic.bak
 165.0GB: boot/initrd.img-2.6.24-22-rt
 164.9GB: boot/initrd.img-2.6.24-22-rt.bak
 165.0GB: boot/initrd.img-2.6.24-23-generic
 165.0GB: boot/initrd.img-2.6.24-23-generic.bak
 165.0GB: boot/initrd.img-2.6.24-23-rt
 165.0GB: boot/initrd.img-2.6.24-23-rt.bak
 165.1GB: boot/initrd.img-2.6.24-24-generic
 165.1GB: boot/initrd.img-2.6.24-24-generic.bak
 165.1GB: boot/initrd.img-2.6.24-24-rt
 165.1GB: boot/initrd.img-2.6.24-24-rt.bak
 165.1GB: boot/initrd.img-2.6.24-26-generic
 165.0GB: boot/initrd.img-2.6.24-26-generic.bak
 487.7GB: boot/initrd.img-2.6.24-26-rt
 165.1GB: boot/initrd.img-2.6.24-26-rt.bak
 132.4GB: boot/initrd.img-2.6.24-27-generic
 127.6GB: boot/initrd.img-2.6.24-27-generic.bak
 105.1GB: boot/initrd.img-2.6.24-27-rt
 137.1GB: boot/initrd.img-2.6.24-27-rt.bak
 198.9GB: boot/initrd.img-2.6.24-28-generic
 487.5GB: boot/initrd.img-2.6.24-28-generic.bak
 177.0GB: boot/initrd.img-2.6.24-28-rt
 198.9GB: boot/initrd.img-2.6.24-28-rt.bak
 452.2GB: boot/initrd.img-2.6.31-11-rt
 198.9GB: boot/initrd.img-2.6.32-24-generic
 165.0GB: boot/vmlinuz-2.6.24-19-generic
 165.0GB: boot/vmlinuz-2.6.24-19-rt
 165.0GB: boot/vmlinuz-2.6.24-21-generic
 165.0GB: boot/vmlinuz-2.6.24-21-rt
 164.9GB: boot/vmlinuz-2.6.24-22-generic
 164.9GB: boot/vmlinuz-2.6.24-22-rt
 165.0GB: boot/vmlinuz-2.6.24-23-generic
 165.0GB: boot/vmlinuz-2.6.24-23-rt
 165.1GB: boot/vmlinuz-2.6.24-24-generic
 165.0GB: boot/vmlinuz-2.6.24-24-rt
 165.0GB: boot/vmlinuz-2.6.24-26-generic
 165.1GB: boot/vmlinuz-2.6.24-26-rt
 164.3GB: boot/vmlinuz-2.6.24-27-generic
 487.5GB: boot/vmlinuz-2.6.24-27-rt
 120.9GB: boot/vmlinuz-2.6.24-28-generic
 198.8GB: boot/vmlinuz-2.6.24-28-rt
 198.8GB: boot/vmlinuz-2.6.31-11-rt
 198.9GB: boot/vmlinuz-2.6.32-24-generic
 452.2GB: initrd.img
 198.9GB: initrd.img.old
 198.8GB: vmlinuz
 198.9GB: vmlinuz.old
```

---

### Post by drs305 on 2010-11-15
Here is my theory on your problems. You were once using 8.04, so the system is probably a bit old, as is the BIOS. Your Ubuntu partition starts around 100GB. When you first installed it all the boot files were probably near the start of the partition.

Now that you have upgraded, all your boot files are much further into the partition. It's possible your BIOS can't see past 137GB, which means it can't find the grub files. 

Enter your BIOS during boot and check what the BIOS thinks your disk size is. If it says it is about 137GB, see if there is a BIOS setting to enable large disks. If not, check with your motherboard/BIOS manufacturer to see if a BIOS update is available.

If not, there are things we can do if this is in fact the problem.

---

### Post by heartcore on 2010-11-15
The hard disks seem fine from the bios,

however now I got another extra error saying:

```
/dev.sda5/ : ******warning: filesystem still has errors*****
mountall: fsck / [369] terminated with status 36
mountall: filesystem has errors: /
```

---

### Post by drs305 on 2010-11-15
Boot the LiveCD. Since there are known errors, run this command and see if it fixes things:
```
sudo e2fsck -f -y -v /dev/sda5
```

---

### Post by heartcore on 2010-11-15
done that, had no errors but a new error while booting:

> Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1/' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda/, not /dev/sda1)? Or the other way around?
mountall: mount /media/misc [883] terminated with status 12
mountall: Filesystem could not be mounted: /media/Misc

I still haven't got a clue whats going on

---

### Post by drs305 on 2010-11-15
Did it boot this time?

Is sdc a thumb or removable drive? If so, remove it prior to booting. 

If you can boot or you mount your Ubuntu partition from the LiveCD (sudo mount /dev/sda5 /mnt) open your real /etc/fstab (/mnt/etc/fstab) and see if sdc1 is listed. If so, place a # symbol at the start of the line to disable mounting it and save the file.

---

### Post by heartcore on 2010-11-15
Solved at last!

Commenting # the line suggested did the trick. However I still get the [SIZE=2]> [COLOR=DimGray]
udev[412]: sysfs{}= will be removed in a future udev version, please use ATT* = to match the event device,or ATTRS{}= to match a parent device in etc/udev/45-libnjb5.rules:<number> [/COLOR][/SIZE]

But I am happy for being able to use ubuntu again after a month.

Thank you all for your help :p

---

