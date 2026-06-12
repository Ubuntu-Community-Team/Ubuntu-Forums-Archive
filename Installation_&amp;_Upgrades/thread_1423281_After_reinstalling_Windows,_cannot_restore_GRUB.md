---
title: "After reinstalling Windows, cannot restore GRUB"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by KiDroboto on 2010-03-06
Well I'll give a brief rundown of how my morning's been: LONG

Now that, that's out of the way let's get down to business. My XP installation caught a cold via an advert on an anime site I frequent (Bleach fan). So I formatted the partition and reinstalled windows XP home edition 32-bit. 

I made the mistake of filling the drive to capacity (which is a no-no apparently if you want to be able to use gparted). I just so happen to have had 2 other small ubuntu installations from previous experiments, so I deleted them and that enabled gparted to work again.

The problem I am having however is when I try to re-enable GRUB using the steps listed [here]("https://help.ubuntu.com/community/WindowsDualBoot").

Finding the stage1 designation following those steps led me to know that my hd's marking was (hd1,5). I got all the way through the steps and received an error on the last line after running the command: setup (hd1)

The error ran as follows:

Running "install /boot/grub/stage1 (hd1) (hd1) 1+17 p (hd1,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Any thoughts?

---

### Post by jerrrys on 2010-03-06
well lets see if we can make that morning even longer :D

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=restore+grub&as_qdr=all&sa=Google+Search&lang=en#945](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=restore+grub&as_qdr=all&sa=Google+Search&lang=en#945)

---

### Post by presence1960 on 2010-03-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by KiDroboto on 2010-03-06
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for /boot/grub/stage2.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa93ec49c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf7e8b76

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,113,047,459 1,113,047,397   7 HPFS/NTFS
/dev/sdb2       1,113,047,460 1,250,258,624   137,211,165   5 Extended
Extended  partition  linking to another extended partition
/dev/sdb5       1,113,047,586 1,239,543,269   126,495,684  83 Linux
/dev/sdb6       1,249,905,258 1,250,258,624       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        866451456451395F                       ntfs       Media                         
/dev/sdb1        7AE863F5E863ADD7                       ntfs       Windoze                       
/dev/sdb5        80b1776f-46a2-41e3-a5c7-4951b3e8733c   ext3                                     
/dev/sdb6        37e7d437-e35a-413b-b261-9bee9380244f   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5        /mnt/root                ext3       (rw)
/dev             /mnt/root/dev            none       (rw,bind)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=80b1776f-46a2-41e3-a5c7-4951b3e8733c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=80b1776f-46a2-41e3-a5c7-4951b3e8733c

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

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        80b1776f-46a2-41e3-a5c7-4951b3e8733c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=80b1776f-46a2-41e3-a5c7-4951b3e8733c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        80b1776f-46a2-41e3-a5c7-4951b3e8733c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=80b1776f-46a2-41e3-a5c7-4951b3e8733c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        80b1776f-46a2-41e3-a5c7-4951b3e8733c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=80b1776f-46a2-41e3-a5c7-4951b3e8733c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        80b1776f-46a2-41e3-a5c7-4951b3e8733c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=80b1776f-46a2-41e3-a5c7-4951b3e8733c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        80b1776f-46a2-41e3-a5c7-4951b3e8733c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=461f1175-2378-48d8-a27a-6a835d045000 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=461f1175-2378-48d8-a27a-6a835d045000 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, memtest86+ (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=80b1776f-46a2-41e3-a5c7-4951b3e8733c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=c4c36eb2-b0d0-47da-8c04-812897147875 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 621.6GB: boot/grub/menu.lst
 629.8GB: boot/grub/stage2
 621.7GB: boot/initrd.img-2.6.28-11-generic
 621.8GB: boot/initrd.img-2.6.28-18-generic
 621.7GB: boot/vmlinuz-2.6.28-11-generic
 621.7GB: boot/vmlinuz-2.6.28-18-generic
 621.8GB: initrd.img
 621.7GB: initrd.img.old
 621.7GB: vmlinuz
 621.7GB: vmlinuz.old

```

Here's the results! Thanks for the quick responses and I apologize for the late ones from myself, went out to clear my head a bit and relax a little.

---

### Post by presence1960 on 2010-03-06
I would put GRUB on MBR of sdb then make sdb first disk to boot in the hard disk boot order in BIOS. Then boot into Ubuntu and repair the MBR of sda to a windows MBR.

First reinstall GRUB on MBR of sdb. Boot the ubuntu 9.04 Live CD/USB & choose "try ubuntu without any changes." When the desktop loads open a terminal and do this:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd1,4)"
4. Type "setup (hd1)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

Go into BIOS and set sdb (640 GB) disk as first to boot in the hard disk boot order. Save changes to CMOS and continue booting. Choose Ubuntu from the GRUB menu. When the desktop loads open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```That is a lowercase L in .lst

Scroll down to this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```

Change it to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
chainloader     +1
```

Then remove this underneath the above: 

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=461f1175-2378-48d8-a27a-6a835d045000 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=461f1175-2378-48d8-a27a-6a835d045000 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, memtest86+ (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/memtest86+.bin  
savedefault
boot
```

Click Save on top toolbar and close file.

Now to fix the MBR on sda to a windows MBR. In terminal run ```
sudo apt-get install lilo
```Ignore the warning. next in terminal run ```
sudo lilo -M /dev/sda mbr

```

Reboot and you should be good to go.

---

### Post by KiDroboto on 2010-03-07
> **presence1960 said:**
> I would put GRUB on MBR of sdb then make sdb first disk to boot in the hard disk boot order in BIOS. Then boot into Ubuntu and repair the MBR of sda to a windows MBR.

First reinstall GRUB on MBR of sdb. Boot the ubuntu 9.04 Live CD/USB & choose "try ubuntu without any changes." When the desktop loads open a terminal and do this:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd1,4)"
4. Type "setup (hd1)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

Go into BIOS and set sdb (640 GB) disk as first to boot in the hard disk boot order. Save changes to CMOS and continue booting. Choose Ubuntu from the GRUB menu. When the desktop loads open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```That is a lowercase L in .lst

Scroll down to this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```Change it to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
chainloader     +1
```Then remove this underneath the above: 

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=461f1175-2378-48d8-a27a-6a835d045000 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=461f1175-2378-48d8-a27a-6a835d045000 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, memtest86+ (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/memtest86+.bin  
savedefault
boot
```Click Save on top toolbar and close file.

Now to fix the MBR on sda to a windows MBR. In terminal run ```
sudo apt-get install lilo
```Ignore the warning. next in terminal run ```
sudo lilo -M /dev/sda mbr

```Reboot and you should be good to go.

I get an error at the very end of the grub command line instructions, I'm posting a screenshot of it. I will continue on past this and see if it works still, but previously when I got this error Grub gives an error that it cannot load my partition. I will post again shortly with the results of continuing these instructions. Thank you again for your time, patience and help!

---

### Post by KiDroboto on 2010-03-07
Ok after finishing the grub commands I rebooted and changed the boot sequence. Upon doing so, Grub comes up and freezes at:

GRUB Loading stage1.5

---

### Post by KiDroboto on 2010-03-07
Quick update:

I can log into the partition using the Super Grub Disk, however if I do not use it I get errors in GRUB.

---

### Post by meierfra. on 2010-03-07
> Extended  partition  linking to another extended partition

Your partition table is slightly messed up. But it should be easy to fix. Boot into Ubuntu with Supergrub


```
sudo fdisk /dev/sdb
```

Press "w".  That rewrites the partition table. Reboot (using Supergrub) so that the changes take effect. Then use presence960 instruction to reinstall Grub.

---

### Post by KiDroboto on 2010-03-07
Somehow or another using supergrub to load again resolved the issue, Grub's back up and working for booting into both Ubuntu and XP. Thanks much for all the advice and help! I'm defintely glad I joined this forum, and I will be taking down notes of all of this as well. 

Ubuntu for life! :guitar:

---

### Post by meierfra. on 2010-03-07
Yes, if you use SuperGrub to install Grub to the MBR you are able to boot.  But  your partition table is still messed up (for example gparted will see your whole hard drive as unallocated)  So I recommend to  carry out my instruction from my last post.

---

### Post by KiDroboto on 2010-03-07
> **meierfra. said:**
> Yes, if you use SuperGrub to install Grub to the MBR you are able to boot.  But  your partition table is still messed up (for example gparted will see your whole hard drive as unallocated)  So I recommend to  carry out my instruction from my last post.

I will still follow those directions, I have to run to the store for a bit but when I get back I will run the fdisk command. Yeah I was a bit surprised that gparted can still see my partitions (I figured my partition table was wonky with all the tinkering I've had to do yesterday and today).

---

### Post by presence1960 on 2010-03-07
Glad you got it working, enjoy ubuntu. 

P.S. Thanks meierfra!

---

### Post by KiDroboto on 2010-03-07
Thanks again so much! I went through and did the fix in order to fix the partition table and everything's smooth (in addition to a non-cluttered GRUB menu). Off to go finish installing windows apps and then back into Ubuntu \\:D/

---

