---
title: "Grub: error 17 problem.."
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by xxxwindows on 2011-02-27
Hey guys!

I recently lost my mind over Windows XP and decided to go for the big one, switch to using linux. 

Unfortunately my hd went dead and the only thing I got left is my 1TB external USB drive so thats where I've been trying to install Ubuntu. I got the live dvd running fine and dandy and installed ubuntu to one of the 5 partitions I made using a windows partition software, on an old slow PC I had dusting in the closet. SO after the install the installer pushed the livedvd out and I restarted and switched boot options to use primarily the USB drive and so it did.
After that I get the Grub error 17.

So i'm running the live cd now, any help here? Im a total newb with linux and cant use the terminal to save my own life yet.. I need help with simple things such as changing directory and stuff. On some other forum/thread regarding error 17 they said its useful to post contents of "sudo fdisk -l" to help solve this so here's mine:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00ea6d00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5242    42106333+   7  HPFS/NTFS
/dev/sda2            5243      121601   934653667+   f  W95 Ext'd (LBA)
/dev/sda5            5243       18185   103964616    7  HPFS/NTFS
/dev/sda6           18186       67123   393094453+   7  HPFS/NTFS
/dev/sda7           67124      108459   332031388+   7  HPFS/NTFS
/dev/sda8          108460      121224   102534831   83  Linux
/dev/sda9          121225      121601     3028221   82  Linux swap / Solaris



the greatest of thanks in advance, -Lassi

---

### Post by oldfred on 2011-02-27
How old & slow. Some over about 5 year old systems could only boot from the first 137GB.

The error message is from grub legacy, but all the new versions of Ubuntu use grub2. So did the MBR not get updated?

To see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by xxxwindows on 2011-02-27
The computer im installing linux on is not that slow, and yeah I got an old ubuntu install DVD that a friend gave me so that must be why grub version is old too.. So now I reinstalled Ubuntu so that it uses all of the 1tb space and CHECKED [x] the option to install a loading software (grub?)! and I actually now get ERROR 2! I tried everything in the bios, switched sata and ide controllers off to no avail.. I even emulated removable hard drives as hard disks and that didnt help. But anyway here's the results as you asked:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00ea6d00

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,947,463,559 1,947,463,497  83 Linux
/dev/sda2       1,947,463,560 1,953,520,064     6,056,505   5 Extended
/dev/sda5       1,947,463,623 1,953,520,064     6,056,442  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b6d67a95-9ac2-46dc-bf12-85597568eb1d   ext3                                     
/dev/sda5        8f6dccba-4ed7-4bdf-85f4-68fe4de00eba   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b6d67a95-9ac2-46dc-bf12-85597568eb1d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b6d67a95-9ac2-46dc-bf12-85597568eb1d

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        b6d67a95-9ac2-46dc-bf12-85597568eb1d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b6d67a95-9ac2-46dc-bf12-85597568eb1d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        b6d67a95-9ac2-46dc-bf12-85597568eb1d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b6d67a95-9ac2-46dc-bf12-85597568eb1d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        b6d67a95-9ac2-46dc-bf12-85597568eb1d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b6d67a95-9ac2-46dc-bf12-85597568eb1d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8f6dccba-4ed7-4bdf-85f4-68fe4de00eba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 741.4GB: boot/grub/menu.lst
 741.3GB: boot/grub/stage2
 741.3GB: boot/initrd.img-2.6.27-7-generic
 741.3GB: boot/vmlinuz-2.6.27-7-generic
 741.3GB: initrd.img
 741.3GB: vmlinuz
```
Thanks -Lassi

---

### Post by oldfred on 2011-02-27
Boot script looks ok. But old grub was not designed for 1TB drive. We have even seen issues with very large drives with a very large / (root) partition.

I would suggest a reinstall with a small /, separate /home for most of the space and swap.

You can test theory just by using gparted to shrink root to 20GB and then see if it works.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.


Note that 8.10 is older
[https://help.ubuntu.com/community/UpgradeNotes#8.10](https://help.ubuntu.com/community/UpgradeNotes#8.10)
**8.10**

 
[LIST]
[*]Version: 8.10 (Intrepid Ibex) 
[*]EOL: April 30, 2010 
[*]See [this]("https://help.ubuntu.com/community/EOLUpgrades/Intrepid") page for upgrade information.  
[/LIST]
 
[B]
[/B]

---

### Post by xxxwindows on 2011-02-28
Ok, I'm installing 10.04.2 today. So I should just leave some unallocated space as I partition this thing in advance?

---

### Post by oldfred on 2011-02-28
With a large drive I like to leave some space unallocated, but sometimes reorganizing can be difficult.

---

