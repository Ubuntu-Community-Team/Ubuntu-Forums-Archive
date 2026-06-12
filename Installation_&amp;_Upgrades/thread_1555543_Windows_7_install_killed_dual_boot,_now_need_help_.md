---
title: "Windows 7 install killed dual boot, now need help fixing it."
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by juicymixx on 2010-08-18
Hey everyone,

I have a dual boot machine (Dell laptop).  Recently I upgraded the XP install on the machine to Windows 7, and in the process lost the grub startup to choose between Windows and Ubuntu.   Now when I turn the computer on it will immediately boot into Windows (after the BIOS post screen).   I was getting ready to run through the commands listed in another post in this forum:
[http://ubuntuforums.org/showthread.php?t=1480892](http://ubuntuforums.org/showthread.php?t=1480892)
when I hit the last post in that thread...   If I am unable to boot Ubuntu on my laptop, **how can I know if I had legacy grub and not grub2**?   Can I figure it out when using the live CD?

Thanks.:D

---

### Post by darkod on 2010-08-18
Since version 9.10, Ubuntu started using grub2. So, if you have/had a CLEAN install (not upgraded from previous version) of 9.10 or later, you most probably have grub2.

Another nice link for bootloaders reinstallation is:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Rubi1200 on 2010-08-18
> **juicymixx said:**
>  **how can I know if I had legacy grub and not grub2**?   Can I figure it out when using the live CD?

Thanks.:D

The answer is yes, you can figure it out.

And here is the simplest way:

Boot the LiveCD, choosing to try not install.

Click on the link at the bottom of my post and follow the instructions there.

Post the results back here.

The bootscript will tell us not only what version of GRUB is installed, but also where (something that has in the past caused problems when incorrectly installed).

Thanks.

---

### Post by juicymixx on 2010-08-18
> **Rubi1200 said:**
> The answer is yes, you can figure it out.

And here is the simplest way:

Boot the LiveCD, choosing to try not install.

Click on the link at the bottom of my post and follow the instructions there.

Post the results back here.

The bootscript will tell us not only what version of GRUB is installed, but also where (something that has in the past caused problems when incorrectly installed).

Thanks.

hmmm... I've never tried the bootinfoscript before, but it seems excellent!   As far as I can tell (from the bootinfoscript result), my Ubuntu 9.10 install is on sda6, and I'm guessing that I upgraded to it...   It's been a long time since I've used Ubuntu on this laptop (I seem to have forgotten everything about this install)!   So I'm using legacy grub (since I have a menu.lst file)... Is this correct?
grub doesn't appear to be installed on this live CD...





                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x55ca70e7

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,812,670   813,194,234   782,381,565   7 HPFS/NTFS
/dev/sda4         813,194,235   976,768,064   163,573,830   5 Extended
/dev/sda5         813,194,298   910,853,369    97,659,072  83 Linux
/dev/sda6         910,853,433   961,136,819    50,283,387  83 Linux
/dev/sda7         961,136,883   976,768,064    15,631,182  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        A2E461F8E461CF5B                       ntfs       RECOVERY                      
/dev/sda3        3C8222A98222679A                       ntfs       OS                            
/dev/sda5        0917a805-0601-4558-b02b-ca27c0ed2f53   ext3                                     
/dev/sda6        d069c893-b77f-4775-9189-8814b9586a77   ext3                                     
/dev/sda7        da1ba7ae-8044-488d-ac63-92910b19d473   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=d069c893-b77f-4775-9189-8814b9586a77 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d069c893-b77f-4775-9189-8814b9586a77

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

# Windows Vista entry
title		Windows Vista
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.10, Karmic Koala
#title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		d069c893-b77f-4775-9189-8814b9586a77
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=d069c893-b77f-4775-9189-8814b9586a77 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

# This is a set of dividers, added to seperate items
title
root

title
root

title
root

title		(scroll down for rescue options)
root

# Windows Vista Safemode entry
title		Win Safemode: choose this, then press F8
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		d069c893-b77f-4775-9189-8814b9586a77
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=d069c893-b77f-4775-9189-8814b9586a77 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		d069c893-b77f-4775-9189-8814b9586a77
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=d069c893-b77f-4775-9189-8814b9586a77 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		d069c893-b77f-4775-9189-8814b9586a77
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=d069c893-b77f-4775-9189-8814b9586a77 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		d069c893-b77f-4775-9189-8814b9586a77
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=d069c893-b77f-4775-9189-8814b9586a77 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		d069c893-b77f-4775-9189-8814b9586a77
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=d069c893-b77f-4775-9189-8814b9586a77 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		d069c893-b77f-4775-9189-8814b9586a77
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=d069c893-b77f-4775-9189-8814b9586a77 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		d069c893-b77f-4775-9189-8814b9586a77
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=d069c893-b77f-4775-9189-8814b9586a77 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		d069c893-b77f-4775-9189-8814b9586a77
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root





=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=d069c893-b77f-4775-9189-8814b9586a77 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=0917a805-0601-4558-b02b-ca27c0ed2f53 /home           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=da1ba7ae-8044-488d-ac63-92910b19d473 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 476.6GB: boot/grub/menu.lst
 476.6GB: boot/grub/stage2
 476.1GB: boot/initrd.img-2.6.28-16-generic
 476.0GB: boot/initrd.img-2.6.31-15-generic
 476.1GB: boot/initrd.img-2.6.31-17-generic
 476.0GB: boot/initrd.img-2.6.31-20-generic
 476.1GB: boot/vmlinuz-2.6.28-16-generic
 476.1GB: boot/vmlinuz-2.6.31-15-generic
 476.0GB: boot/vmlinuz-2.6.31-17-generic
 476.1GB: boot/vmlinuz-2.6.31-20-generic
 476.0GB: initrd.img
 476.1GB: initrd.img.old
 476.1GB: vmlinuz
 476.0GB: vmlinuz.old

---

### Post by juicymixx on 2010-08-18
Alright!
Thanks for the help, Rubi1200 (also thanks for taking the time to respond, darkod)...
I went ahead and did
sudo apt-get install grub
then I followed the instructions at:
[https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier](https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier)
which were very straight forward.   Everything works as expected now, with grub coming up just after the bios post.   I need to go ahead and modify my menu.lst titles just a little, but grub handed off the boot to the windows 7 bootloader just fine.   I'm mostly comfortable with legacy grub... Should I think about switching to grub2?

Thanks!:p:D

---

