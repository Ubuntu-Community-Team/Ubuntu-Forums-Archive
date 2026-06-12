---
title: "Upgrade Gone Wrong May Have Lost Important Files"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by rpete on 2010-08-27
Hi,  I have had Hardy Heron 8.04 since 2008. Few problems, but when the red arrow indicated updates I clicked on it and it was for an upgrade to 10.04.  I decided to upgrade but it didn't go well.  I ended up with a black screen and white letters. I didn't know what to do.  I don't know many commands.  I posted here but got no response.  I had no access to the Internet.  I decided to reinstall Ubuntu 8.04 from the CD.  At one point it asked me about a 10GB partition.  I didn't really understand it at that point but clicked ok.  When I got the computer running again I noticed that it was a new partition with 7 GB free space.  What happened to all my precious other files?  

sudo fdisk -l give this information (I don't know how to copy the screen to this message).

/dev/sda1  Start 1  End 37589  ID 83  System Linux
/dev/sda2       37590   38913     5          Extended
/dev/sda5       37590    37599    82        Linux Swap Solaris
/dev/sda6       37600    38851    83        Linux
/dev/sda7       38852     38913   82        Linux Swap Solaris

I am panicking because I read a similar thread about a Windows/Ubuntu partition and the person was worried about losing all Windows files.  I did back up the files on an external hard drive but not recently.  Losing them would mean I had to make up a lot of work.

Please help!

---

### Post by rpete on 2010-08-27
Hi, I also noticed a difference immediately after reinstall.  On Terminal my computer was now called laptop whereas before it was dell-desktop

Richard

---

### Post by oldfred on 2010-08-28
Did you do an in place upgrade or a new install?

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by rpete on 2010-08-28
Hi, I have that .txt on my desktop and will cut and paste it here. 



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       192717 sectors.. But according to the info from the 
                       partition table , it has 603867221 sectors.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x88000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   603,867,284   603,867,222  83 Linux
/dev/sda2         603,867,285   625,137,344    21,270,060   5 Extended
/dev/sda5         603,867,348   604,027,934       160,587  82 Linux swap / Solaris
/dev/sda6         604,027,998   624,141,314    20,113,317  83 Linux
/dev/sda7         624,141,378   625,137,344       995,967  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-0A06                              vfat       DellUtility                   
/dev/sda5        99b76948-ea5a-446b-a3dd-836cb69491d2   swap                                     
/dev/sda6        2faaad04-2fa0-4a53-a048-1e2bed7990d5   ext3                                     
/dev/sda7        f71ec9cf-74fb-4c92-8b00-bd412039237e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


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
# kopt=root=UUID=2faaad04-2fa0-4a53-a048-1e2bed7990d5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2faaad04-2fa0-4a53-a048-1e2bed7990d5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2faaad04-2fa0-4a53-a048-1e2bed7990d5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2faaad04-2fa0-4a53-a048-1e2bed7990d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=f71ec9cf-74fb-4c92-8b00-bd412039237e none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 313.4GB: boot/grub/menu.lst
 313.4GB: boot/grub/stage2
 313.4GB: boot/initrd.img-2.6.24-16-generic
 313.4GB: boot/initrd.img-2.6.24-16-generic.bak
 313.4GB: boot/vmlinuz-2.6.24-16-generic
 313.4GB: initrd.img
 313.4GB: vmlinuz

---

### Post by oldfred on 2010-08-28
This just must be your reinstall. If you reinstalled over your old install then nothing is left. You also seem to have an issue on sda1. It shows vfat in one place and type 83 linux in another. Was sda1 your original linux install and it was a Dell utility before that as it looks very large for just a utility partition.

You may want to review partitions with testdisk, if sda1 has some of your data it may let you repair or recovery some of it.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by rpete on 2010-08-28
Hi, Being unfamiliar with partitions, I am dumbfounded that a 10GB partition would wipe out all of the data. Also the start and end seem to indicate the reinstall on sda7 or 6? was separate from the original sda1.  I shake my head wondering how I could let this happen? All I wanted was an upgrade.  When I got a black screen, no GUI I didn't know what to do.  

Testdisk needs 25 lines and asks me to enlarge the terminal How do I do that? You state this application may allow me to recover "some" no chance of all?


Richard

---

### Post by oldfred on 2010-08-28
If your original install was in sda1 and you have not written into it testdisk should recover the entire thing. It may not be bootable but you may even be able to copy all data and possibly chroot into it and repair it.

I do not know testdisk as I fortunately have not needed it. Are you in a low graphics mode. Can you install drivers to get to better graphics? Or use liveCD and download testdisk to it.

Something changed sda1 to be a Dell Utility partition and recover its boot sector. That looks like it maybe way what it was before you made it a Linux partition. Maybe just making it type 83 will work but I think test disk is the best solution.

---

### Post by rpete on 2010-08-28
Thanks.  I will go with TestDisk and let you know if it works.  Keeping my fingers crossed.  

Richard

---

