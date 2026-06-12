---
title: "Windows 7 not coming in menu option after installing Ubuntu"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by bargi on 2011-05-09
Hi All

I have windows 7 installed on my system.
After that I installed Ubuntu 8.XX on it.

I have made a drive empty for this purpose and use manuall installation on this drive.

When installation completed, I restart my PC but didn't saw option of Windows(or other) in boot menu.

My Ubuntu is working fine and I can see the C and D drives ( which were there before installation) and there are all files related to windows in C.

Can anybody let me know how to get Windows option in booting menu so that I can use my windows too.

It will be very helpful if it is step-by-steps.
Waiting for suggestion.

Thanks & Regards
Bargi

---

### Post by Grenage on 2011-05-09
> **bargi said:**
> Hi All

I have windows 7 installed on my system.
After that I installed Ubuntu 8.XX on it.

I have made a drive empty for this purpose and use manuall installation on this drive.

When installation completed, I restart my PC but didn't saw option of Windows(or other) in boot menu.

My Ubuntu is working fine and I can see the C and D drives ( which were there before installation) and there are all files related to windows in C.

Can anybody let me know how to get Windows option in booting menu so that I can use my windows too.

It will be very helpful if it is step-by-steps.
Waiting for suggestion.

Thanks & Regards
Bargi

Try this from a terminal:

```
sudo update-grub
```

---

### Post by coffeecat on 2011-05-09
> **bargi said:**
> After that I installed Ubuntu 8.XX on it.

Are you sure you mean one of the 2008 releases? The desktop version of 8.04 will reach its end-of-life (no more support) on 12th May (the server version is still supported) and 8.10 has been past end of life for a year now. Which did you install, 8.04 or 8.10 and desktop or server edition?

Whatever, boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. Post the contents of your RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags - you can use the # icon on the message toolbar for this. This will show us all the details we need of your setup and the contents of your boot configuration file. We can take it from there.

---

### Post by bargi on 2011-05-09
Hi 

sudo update-grub doesn't work.

the result is: 


```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb005b005

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *        206,848    81,922,047    81,715,200   7 HPFS/NTFS
/dev/sda3          81,922,048   245,762,047   163,840,000   7 HPFS/NTFS
/dev/sda4         245,762,370   312,576,704    66,814,335   f W95 Ext d (LBA)
/dev/sda5         245,764,096   304,357,845    58,593,750  83 Linux
/dev/sda6         304,367,553   312,576,704     8,209,152  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        B85CD2515CD20A50                       ntfs                                     
/dev/sda3        8E30FA7D30FA6B99                       ntfs       New Volume                    
/dev/sda5        94b008d6-1db0-4590-8b88-16b95fceaf4d   ext2                                     
/dev/sda6        1393cf5c-ce76-400b-8f57-f791b9f4aa76   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext2       (rw,relatime,errors=remount-ro)
/dev/scd0        /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=bhagwat)


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
# kopt=root=UUID=94b008d6-1db0-4590-8b88-16b95fceaf4d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94b008d6-1db0-4590-8b88-16b95fceaf4d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94b008d6-1db0-4590-8b88-16b95fceaf4d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

title Windows Vista
rootnoverify (hd0,1)
map (hd0) (hd1)
map (hd1) (h0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=94b008d6-1db0-4590-8b88-16b95fceaf4d /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=1393cf5c-ce76-400b-8f57-f791b9f4aa76 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 142.8GB: boot/grub/menu.lst
 142.8GB: boot/grub/stage2
 142.4GB: boot/initrd.img-2.6.24-19-generic
 142.5GB: boot/vmlinuz-2.6.24-19-generic
 142.4GB: initrd.img
 142.5GB: vmlinuz


```


Thanks & Regards
Bargi

---

### Post by coffeecat on 2011-05-09
Looking at the start sector of sda2, your first partition, it looks as though you deleted the Windows 7 boot partition of about 105MB which contains the Windows boot files. Or rather, did contain the Windows boot files. This would have been sda1. Your sda2 C: partition is missing the boot files which is why update-grub can't see it. And even if it did, Windows is unbootable in its present state. Did you realise you had deleted an essential partition?

All is not lost. Do you have a Windows 7 retail installation DVD or did you create a repair CD while you still had a usable Windows? If no to both, you can download the ISO for the repair CD here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Then you need to boot into it and choose 'Startup Repair' as here:

[http://windows.microsoft.com/en-US/windows7/What-are-the-system-recovery-options-in-Windows-7](http://windows.microsoft.com/en-US/windows7/What-are-the-system-recovery-options-in-Windows-7)

If that doesn't work, go to the command prompt and run the bootrec tool as described here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You would need 'bootrec /FixBoot' and/or 'bootrec /RebuildBcd'. **Do not** run '/bootrec FixMbr'. That will install Windows code to the mbr and make the situation worse.

After you've tried those bootrec options, try running 'sudo update-grub' again and see whether it detects Windows.

By the way, you didn't answer my question about which version of Ubuntu you are running, but the boot script output tells us. You have 8.04. It will become unsupported in a couple of days. Once you've repaired Windows, you need to think about upgrading or re-installing with a supported version.

---

