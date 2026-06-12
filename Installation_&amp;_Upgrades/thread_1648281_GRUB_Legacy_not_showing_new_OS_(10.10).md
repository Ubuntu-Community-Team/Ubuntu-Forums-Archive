---
title: "GRUB Legacy not showing new OS (10.10)"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by metra on 2010-12-18
Hi all,

My laptop came with Vista and I added Linux Mint 6 (based on Ubuntu 8.10 Intrepid Ibex) all is good for a year or so. Added Ubuntu 10.10 to my desktop, loved it, wanted to add it to my laptop...oops.

Installed the main version from a LiveCD, did the the easy multi-OS installation.

GRUB-0.97 is what boots my system though looking at boot script I do have GRUB2 somewhere. 

Currently, my boot options are:

1. Mint 6
2. Mint 6 (recovered)
3. Mint 6
4. Mint 6 (recovered)
5. memtest 86+

Other operating systems

6. Vista/Longhorn loader
7. Vista/Longhorn loader

[IMG]http://img258.imageshack.us/img258/263/gparted.png[/IMG]

Sda7 is where Ubuntu should be installed. GPARTED says its ext3 file system and bootscript says ext4.

I did find the forum post on [purging and installing GRUB2]("http://ubuntuforums.org/showthread.php?t=1581099&highlight=grub+ubuntu+loading") though I'm not sure if that's what I need to do, or try to reinstall Ubuntu w/o also doing partition resizing at the same time.


The output from my bootscript:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 667863520 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa6e935e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    82,654,424    82,654,362   7 HPFS/NTFS
/dev/sda2         950,702,080   976,766,975    26,064,896   7 HPFS/NTFS
/dev/sda3          82,654,486   950,694,569   868,040,084   5 Extended
/dev/sda5          82,654,488   243,952,218   161,297,731  83 Linux
/dev/sda6         932,476,923   950,694,569    18,217,647  82 Linux swap / Solaris
/dev/sda7         243,953,664   907,900,927   663,947,264  83 Linux
/dev/sda8         907,902,976   932,474,879    24,571,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4BA40AA6202D99BC                       ntfs                                     
/dev/sda2        52807BE8807BD0C9                       ntfs       RECOVERY                      
/dev/sda5        b54a4904-f8fc-4444-a23c-906c367c4639   ext3                                     
/dev/sda6        506d8655-43cd-461e-a7fe-b1cd2dfea098   swap                                     
/dev/sda7        81aa19da-9725-4e8c-9f5f-1ccf66216b8c   ext4                                     
/dev/sda8        9b7aa802-9497-40c5-afe7-c26e746028d2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda5 ro

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
# defoptions=quiet splash ROOTFLAGS=syncio

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=/dev/sda5 ro quiet splash ROOTFLAGS=syncio 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Linux Mint 6, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro quiet splash ROOTFLAGS=syncio 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b54a4904-f8fc-4444-a23c-906c367c4639 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=506d8655-43cd-461e-a7fe-b1cd2dfea098 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdax	/home/us/Data 	ext3	relatime	0	2


=================== sda5: Location of files loaded by Grub: ===================


  62.0GB: boot/grub/menu.lst
 103.2GB: boot/grub/stage2
 103.3GB: boot/initrd.img-2.6.27-14-generic
 103.3GB: boot/initrd.img-2.6.27-7-generic
 103.3GB: boot/vmlinuz-2.6.27-14-generic
 103.3GB: boot/vmlinuz-2.6.27-7-generic
 103.3GB: initrd.img
 103.3GB: initrd.img.old
 103.3GB: vmlinuz
 103.3GB: vmlinuz.old
```

So, any ideas on how to fix this?

---

### Post by Sef on 2010-12-18
```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 667863520 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

```

I would not worry about it, if all is working correctly. 

My guess about what is happening is that it tries to boot from sda1 first, and since it cannot, it then defaults to sda5 which boots up the OS.

---

### Post by oldfred on 2010-12-18
Grub legacy was not good at finding other systems. But you have grub installed to the windows partition. Windows has to have its code in the NTFS partition.

    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1 [/COLOR]

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Also check for /boot/grub in addition to /Boot 

Grub legacy was not very good about finding or setting up boot stanzas for other system. We often had to manually add or adjust any setttings. Grub2 is much better at finding other systems. Since you have many systems, I would upgrade to grub2.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Did you run script from Ubuntu? If not, then that maybe why you cannot see the ext4 partitions correctly.

---

### Post by metra on 2010-12-19
@sef the problem is the invisible Ubuntu 10.10 OS in Grub

@oldfred I'll try to install Grub 2 and see what happens.

Thanks to both of you, I'll post the results.

---

### Post by metra on 2010-12-19
Replacing Grub Legacy w/ 2 worked! 

Though I didn't ever get the GUI the walkthrough, I wasn't able to select [*]/sda, and it looked like as though something went wrong.

Thank you both for looking at my bootscript and confirming that it was grub.

Out of curiosity what happened on the final command?

```

Creating config file /etc/default/grub with new version
Configuring grub-pc
-------------------

The grub-pc package is being upgraded.  This menu allows you to select which devices you'd like grub-install to be automatically run for, if any.

It is recommended that you do this in most situations, to prevent the installed GRUB from getting out of sync with other components such as grub.cfg or 
with newer Linux images it will have to load.

If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.
[More] ^[[D^[[B

Note: It is possible to install GRUB to partition boot records as well, and some appropriate partitions are offered here.  However, this forces GRUB to 
use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.

  1. /dev/sda (500107 MB, ST9500325AS)  2. - /dev/sda7 (339940 MB, /)

(Enter the items you want to select, separated by spaces.)

GRUB install devices: [*]/dev/sda

GRUB install devices:  *

GRUB install devices: 1


Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/1006-A87E: No such file or directory
ls: cannot access /media/1006-A87E: No such file or directory
ls: cannot access /media/1006-A87E: No such file or directory
ls: cannot access /media/1006-A87E: No such file or directory
ls: cannot access /media/1006-A87E: No such file or directory
ls: cannot access /media/1006-A87E: No such file or directory
ls: cannot access /media/1006-A87E: No such file or directory
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
Found Linux Mint 6 Felicia - Main Edition (6) on /dev/sda5
done

```

---

### Post by oldfred on 2010-12-19
Before you ran the grub2 update, did you mount something to /media/1006-A87E? That maybe why you had that error?

Have you tried booting all the choices to make sure they work? That is the real test.

---

