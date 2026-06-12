---
title: "grub to boot a USB HDD"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by Djense on 2011-05-23
Hi,

I can find a few threads about this topic, but cannot figure out the solution to my problem...

My machine is using Ubuntu 8.04 (=> legacy grub). It is backed up regularly and I would like to check I am able to restore the backup.
This backup includes everything on the system, including /boot (the only things excluded are things like /proc, /var, /dev...).

I "restored" the backup onto an external USB HDD, setup the boot flag there and I would like to boot that. Is that possible ?

I tried several variants of grub-install, changing the menu.lst, but still no luck. For one thing, the /boot/grub/device.map only shows the main HDD, not the USB HDD, is it ok to just add it in there :
(hd1) /dev/sdb1
?

When I change the BIOS to boot from USB, it just seems to skip it.
What else do I need to do ?

Thanks in advance for the help.

---

### Post by oldfred on 2011-05-23
If your machine is older, it probably does not have a BIOS that will let you boot a USB drive. 

If you have reinstalled grub legacy to the MBR of the external drive then BIOS will see it and make it a choice if it boots USB devices. Do you see USB devices as a choice in BIOS or one time boot key?

My PC lets me boot USB and has a long list of alternatives, USB-Cd, USB-Floppy, USB-HD etc but when I use a flash drive it appears as another hard drive under my choice of which hard drives to boot.

How did you backup? If you used images that copied the UUIDs then the system will have lots of problems booting as now you have two identical UUIDs on your system (which is not possible, so system does not know what to do).

---

### Post by Djense on 2011-05-23
Oldfred,
Thank you for your help.
My machine has an option in the BIOS to boot from USB, but for some reason, that does not do anything (my guess is that there is some boot vector or something that is not setup correctly).

Can you tell me exactly how to restore grub legacy on the external HDD ? When I am running Ubuntu from the PC HDD, I see that HDD as /dev/sda and the external USB one as /dev/sdb1. Obviously those have two different UUID too, I am not sure what arguments should be to grub-install... (or maybe that's not even the right command (?) ).

I used duplicity to do the backup, so it is file based. And I am actually trying to run that backup on a completely different machine, so there should not be any UUID conflict.

Thanks

---

### Post by oldfred on 2011-05-23
This will tell us where everything is at (with USB plugged in), & then we can give specific instructions:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If you want to read ahead this has general instruction for grub legacy, grub2 & windows boot loader reinstalls.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Djense on 2011-05-24
Here is what I got.
What is in /dev/sdb1 may be quite messed up after all the trial/errors I went through... but that's the one I would like to boot (either directly by setting the BIOS to boot the USB device or through grub on the main HDD).

Thanks a lot for your help.


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sdb1 and looks at sector 1792295143 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sdb.  Stage2 looks on partition 
                       #1 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003cd50

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63        32,129        32,067  83 Linux
/dev/sda2              32,130     4,915,889     4,883,760  83 Linux
/dev/sda3           4,915,890     5,012,279        96,390  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.3 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00050fb0

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63 3,907,024,064 3,907,024,002  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        75c85a3d-aa6c-438f-b82f-9c1b4f4a88aa   ext3       
/dev/sda2        6e62c8d0-379f-48d8-8c6f-b788c4106c95   ext3       
/dev/sda3        56b91afc-efaa-4e75-ab14-7435c8ded4ea   swap       
/dev/sdb1        0ebff6ed-9935-451a-83f8-0e8bcd08d8ea   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext3       (rw,relatime)
/dev/sda2        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb1        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


============================= sda1/grub/menu.lst: ==============================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=6e62c8d0-379f-48d8-8c6f-b788c4106c95 ro

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.24-26-generic root=UUID=6e62c8d0-379f-48d8-8c6f-b788c4106c95 ro quiet splash
initrd        /initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, USB recovered
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=0ebff6ed-9935-451a-83f8-0e8bcd08d8ea ro quiet splash
initrd        /boot/initrd.img-2.6.24-28-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.24-26-generic root=UUID=6e62c8d0-379f-48d8-8c6f-b788c4106c95 ro single
initrd        /initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/menu.lst
            ?? = ??             grub/stage2
            ?? = ??             initrd.img-2.6.24-26-generic
            ?? = ??             vmlinuz-2.6.24-26-generic

=========================== sda2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=6e62c8d0-379f-48d8-8c6f-b788c4106c95 ro

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.24-26-generic root=UUID=6e62c8d0-379f-48d8-8c6f-b788c4106c95 ro quiet splash
initrd        /initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, USB recovered
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=0ebff6ed-9935-451a-83f8-0e8bcd08d8ea ro quiet splash
initrd        /boot/initrd.img-2.6.24-28-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.24-26-generic root=UUID=6e62c8d0-379f-48d8-8c6f-b788c4106c95 ro single
initrd        /initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6e62c8d0-379f-48d8-8c6f-b788c4106c95 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=75c85a3d-aa6c-438f-b82f-9c1b4f4a88aa /boot           ext3    relatime        0       2
# /dev/sda3
UUID=56b91afc-efaa-4e75-ab14-7435c8ded4ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/grub/stage2
            ?? = ??             boot/initrd.img-2.6.24-26-generic
            ?? = ??             boot/vmlinuz-2.6.24-26-generic
            ?? = ??             initrd.img
            ?? = ??             vmlinuz

=========================== sdb1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro quiet splash
initrd        /boot/initrd.img-2.6.24-28-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro single
initrd        /boot/initrd.img-2.6.24-28-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=5c1e8e4f-e290-4a52-9214-341762764a68 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img
            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/grub/stage2
            ?? = ??             boot/initrd.img-2.6.24-23-generic
            ?? = ??             boot/initrd.img-2.6.24-23-generic.bak
            ?? = ??             boot/initrd.img-2.6.24-24-generic
            ?? = ??             boot/initrd.img-2.6.24-24-generic.bak
            ?? = ??             boot/initrd.img-2.6.24-26-generic
            ?? = ??             boot/initrd.img-2.6.24-26-generic.bak
            ?? = ??             boot/initrd.img-2.6.24-28-generic
            ?? = ??             boot/initrd.img-2.6.24-28-generic.bak
            ?? = ??             boot/vmlinuz-2.6.24-23-generic
            ?? = ??             boot/vmlinuz-2.6.24-24-generic
            ?? = ??             boot/vmlinuz-2.6.24-26-generic
            ?? = ??             boot/vmlinuz-2.6.24-28-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old



```

---

### Post by oldfred on 2011-05-24
It looks like you installed grub2 to the MBR of sdb. Not sure if grub2 will boot 8.04 or not. 

I think you need to reinstall grub legacy to sdb's MBR. Also all the UUIDs refered to in sdb's fstab do not exist. So you need to edit it with the correct UUID. You also do not have a swap on sdb. If you have lots of RAM you can get by without swap, but it still is recommended.

Are you sure this was a backup? Nothing seems to match. Your install in sda has a separate /boot & swap. The install in sdb has neither.

You do know that 8.04 Desktop expired May 12, 2011. Server only is supported until 2013.
Versions and release & support until dates:
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)

old 2006 instructions to reinstall grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sdb1 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1
root (hd1,0)
setup (hd1)

---

### Post by Djense on 2011-05-24
It is a backup... of another machine.

I want to check I can recover it so that I can upgrade to 10.04 safely... :)

Thank you for those instructions, I will try that. Will let you know how that goes.

---

### Post by Djense on 2011-05-24
Hmmm, still did not boot off the USB drive. :(

Here is what I got when I run the grub command after chroot and so on :
```
grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

So that looked all fine.

If I run the bootinfoscript, the only change is this : 
```
$ diff RESULTS.txt RESULTS1.txt 
8,10c8,9
<  => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
<     1 of the same hard drive for core.img. core.img is at this location and 
<     looks in partition 1 for /boot/grub.
---
>  => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
>     same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
```

BIOS is set to boot from USB device first...

---

### Post by oldfred on 2011-05-24
It looks like grub is installed correctly and it should start to boot. Did you also fix fstab (but it still should load grub if booting) as it will not boot with incorrect fstab.

Are you using BIOS or one time boot key (f12 on my system)? Some systems seem to require both to boot USB.

---

### Post by Djense on 2011-05-24
I also tried with F12, but it says the "boot device is not available".

I double checked with fdisk that the boot flag is set. I am wondering if the BIOS is not capable of recognizing the USB HDD for some reason ? It is a Dell machine that's not too old though...
There are some diagnostics in the BIOS, but it's all mostly with memory, it does not really check for USB devices to boot from.

About the fstab, I edited the /etc/fstab on the USB HDD as such (I don't think it gets that far anyway).
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/swapfile       swap            swap    defaults        0       0
# /dev/sdb1
UUID=0ebff6ed-9935-451a-83f8-0e8bcd08d8ea /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by oldfred on 2011-05-24
If the BIOS or f12 do not give a choice when a bootable device in in the USB ports then I do not think it will boot it. You can try plop, I have not used it. Some said it works, others have had issues.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by Djense on 2011-05-24
Is there any way to use the grub installed on /dev/sda to boot the USB HDD ?

---

### Post by oldfred on 2011-05-24
BIOS is before grub. Plop somehow works around it. Not sure if plop is not just booting and then chrooting into the install on a USB drive, but I have not installed it and followed the details.

---

### Post by Djense on 2011-06-02
Just a quick update....

Using Plop, I was able to boot the USB HDD. Plop is (really !) easy to use.

I still had to work around a couple of things on the USB image in /etc/fstab and /boot/grub/menu.lst to make everything boot correctly.
Then for some reason, I got some permissions issues, some folders got the wrong permissions but I may have messed that up before.

Anyway, I got what I needed, I checked the backup was done correctly and am able to recover it if needed.

Thanks,
Matthieu

---

### Post by oldfred on 2011-06-02
Glad you got that all figured out. Always best to know backups work before having to rely on a backup that does not work.

---

### Post by Djense on 2011-06-02
exactly... :)

Thanks again for all your help. Could not have pulled that off without it.

---

