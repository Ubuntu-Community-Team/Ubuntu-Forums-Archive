---
title: "Dual boot (seperate HD) problem"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by swiftstealth on 2011-05-21
I've been running ubuntu as my primary OS for about a year, but it's recently become necessary for me to use windows again. I'm opting for a dual hard drive set up. My problem is that all the walkthrough's I've seen detail how to set up a dual boot.. assuming you're doing a clean install of ubuntu. (the general gist being "install windows! install ubuntu and tell it to install to the second hard drive!" The problem is, I don't have the option of wiping the drive/reinstalling ubuntu.

So, my question is; How do I manage to set up a dual boot system if I have 2 HD's, one with an existing install of Ubuntu, and the other with a fresh install of XP.

Any help would be very much appreciated.

---

### Post by kansasnoob on 2011-05-21
Will both drives be internal drives?

What size are the drives?

---

### Post by mikewhatever on 2011-05-21
Just boot Ubuntu and run **sudo update-grub** from a terminal window. If all goes well, it will detect the second hdd Windows installation and add it to the bootloader menu.

---

### Post by Hedgehog1 on 2011-05-21
If you will be putting XP on it's own hard drive, here is one way of doing it without touching your Ubuntu install:

Disconnect the drive with Ubuntu on it, and then install XP on the second (and during install only) drive.

Once XP is loaded and you are happy with the install, reconnect the 1st drive.

The Ubuntu drive should boot, and then you can (as **mikewhatever** said) do a

```
sudo update-grub
```

An on your next reboot, grub will have both XP and Ubuutnu listed.

***The Hedge***

:KS

p.s. **kansasnoob**'s question on 'how big are the drives' does matter. Depending on the age of your system, the fist XP partition mat have to be limited to less than 137 gigs (or less than 40 gigs for even older hardware).

---

### Post by swiftstealth on 2011-05-21
Both drives are internal; the HD for Xp is 120 GB, the HD for Ubuntu is 160, so hopefully I won't run into the partition size problems. I'm almost done installing XP on the one HD, will attempt the fix proposed by mikewhatever and hedgehog1 and report back - thanks for the prompt replies!

---

### Post by Hedgehog1 on 2011-05-21
The only 'gotcha' will be if your PC decides to boot from the drive with XP first.  If it does that, you will need to run a grub-install command from an Ubuntu LiveCD/LiveUSB (one that is the same level of Ubuntu on your harddisk) to update the MBR of the XP disk instead.

***The Hedge***

:KS

---

### Post by swiftstealth on 2011-05-21
All right then. So I've got the install of Windows XP done to my satisfaction, I hooked it up as a slave and booted up my first drive. Ubuntu *can* see the windows drive, I can access anything on that hard drive.. but it won't add it to the grub bootloader (Already ran sudo-update grub twice - the XP HD doesn't appear.)

What next?

---

### Post by oldfred on 2011-05-21
You mention slave. Does you BIOS let you boot either drive or is you BIOS so old only the jumpers or location on cable select control boot drive?

Post this from Ubuntu:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by swiftstealth on 2011-05-24
Hey, sorry for the late reply, I lost internet for a couple days >.< (long story) Hopefully there are still people out there willing to help..

As requested, ran the boot info.sh script, below are the results.





```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d7bb1

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   306,520,199   306,520,137  83 Linux
/dev/sda2         306,520,200   312,576,704     6,056,505   5 Extended
/dev/sda5         306,520,263   312,576,704     6,056,442  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bfe1bfd

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   234,420,479   234,420,417   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        47dc9971-e8fe-440f-b367-ccef51efcbdb   ext3       
/dev/sda5        19c73bb8-152e-4f64-bc3e-06800e606f0b   swap       
/dev/sdb1        982C8CC12C8C9C3E                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/scd0        /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=butler)
/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=47dc9971-e8fe-440f-b367-ccef51efcbdb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=quiet splash vga=771

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=47dc9971-e8fe-440f-b367-ccef51efcbdb ro quiet splash vga=771
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=47dc9971-e8fe-440f-b367-ccef51efcbdb ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=47dc9971-e8fe-440f-b367-ccef51efcbdb ro quiet splash vga=771
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=47dc9971-e8fe-440f-b367-ccef51efcbdb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=47dc9971-e8fe-440f-b367-ccef51efcbdb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=19c73bb8-152e-4f64-bc3e-06800e606f0b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/grub/stage2
            ?? = ??             boot/initrd.img-2.6.24-19-generic
            ?? = ??             boot/initrd.img-2.6.24-19-generic.bak
            ?? = ??             boot/initrd.img-2.6.24-21-generic
            ?? = ??             boot/initrd.img-2.6.24-21-generic.bak
            ?? = ??             boot/vmlinuz-2.6.24-19-generic
            ?? = ??             boot/vmlinuz-2.6.24-21-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

-----------------------------------------------------------
```


Hedge mentioned this earlier;

> The only 'gotcha' will be if your PC decides to boot from the drive with XP first. If it does that, you will need to run a grub-install command from an Ubuntu LiveCD/LiveUSB (one that is the same level of Ubuntu on your harddisk) to update the MBR of the XP disk instead.

I'd be all right with setting XP to boot first and updating the MBR if that'd be easier..

Hell, at this point I'd be willing to reinstall ubuntu if that'd be simpler, I would just need a way to *not* lose the 100+GB of data on that hard drive.. is there a easy way to install a new version of ubuntu without losing all my saved files?

I'm just looking for the simplest solution. Any feedback is appreciated.

---

### Post by oldfred on 2011-05-24
Windows prefers to be the first drive and it thinks it is per its boot.ini.
default=multi(0[COLOR=Red])disk(0)[/COLOR]rdisk(0)partition(1)\WINDOWS

Grub's map commands are supposed to make windows think it is the first drive. But sometimes it does not work.

Paste this into menu.lst after This:
### END DEBIAN AUTOMAGIC KERNELS LIST

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```

---

### Post by swiftstealth on 2011-05-25
I'm very incompetent with linux; I'm not sure how to navigate to that using the command line. I used ubuntu's search option to find "menu.lst" in the file system, but there are two menu.lst files - which one am I supposed to edit?

[IMG]http://optimisticallypessimistic.files.wordpress.com/2011/05/screenshot.jpg[/IMG]

Alternately, if someone could tell me how to navigate to the correct menu.lst using the command line I'd be happy to do that too.

---

### Post by oldfred on 2011-05-25
You should be booted into sda. Not sure where the other menu.lst is coming from. It does make sense to have backups.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup2
gksudo gedit /boot/grub/menu.lst

---

### Post by swiftstealth on 2011-05-25
PERFECT! It's listed now!

Last thing; how do I get the grub bootscreen to pop up automatically? I'd prefer to avoid having to hit esc to get to the grub menu every time.

---

### Post by oldfred on 2011-05-26
It has been so long since grub legacy I forgot the old ways. I think it is this near the top of your menu.lst. It also looks like you adjusted timeout to 3 seconds. You can change default if you want it is set to 0 which is the first entry. You have to count lines to find the windows entry or move the windows entry way up in the menu.lst to above the start of the automagic area so it is then 0.

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

---

### Post by swiftstealth on 2011-05-28
Awesome! Thanks for the help!
:D
/marks thread as solved

---

