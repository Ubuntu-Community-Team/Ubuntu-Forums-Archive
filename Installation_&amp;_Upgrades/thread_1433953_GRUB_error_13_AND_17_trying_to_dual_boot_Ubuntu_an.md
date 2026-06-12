---
title: "GRUB error 13 AND 17 trying to dual boot Ubuntu and Windows 2000 pro"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by Fanarkle on 2010-03-19
Interesting problem, this.  I decided that Windows 2000 pro was getting too fat and old for my old machine (AMD 1..2GHz w/ 256Mb RAM) so I installed Ubuntu 8.04 Hardy (Good OS 3.1 dist.) on a 20Gb drive I had laying around.  I left Windows 2000 pro on the old drive and just selected "use entire drive" to format and install to the new HDD.  Also, I switched the jumpers so that the new ext3 drive would be primary master and old NTFS drive would now be primary slave.  Now when I boot to GRUB menu, selecting Ubuntu results in GRUB Error 17, and selecting Windows 2000 Pro results in GRUB Error 13.  Here's the kicker.  If I use a Windows 2000 CD to boot from, then exit out of that menu and select Ubuntu in GRUB, it is able to load just fine.  Here is fdisk and menu.lst:

userlogin@office-desktop:/boot/grub$ sudo fdisk -l

Disk /dev/sda: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25af25ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2402    19294033+  83  Linux
/dev/sda2            2403        2494      738990    5  Extended
/dev/sda5            2403        2494      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed22ed22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2494    20033023+   7  HPFS/NTFS


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
# kopt=root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro

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
# defoptions=quiet splash loglevel=0

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro quiet splash loglevel=0
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro quiet splash loglevel=0
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows 2000 Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by oldfred on 2010-03-19
these are the explanations:
[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

Did you switch jumpers before or after the install?

To see the entire boot process (which includes all the data you posted but much more).

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

And welcome to the forums;)

---

### Post by Fanarkle on 2010-03-22
Thanks oldfred!  I switched the jumpers before installing so that the linux drive is primary master and windows is primary slave.  Here is the bootinfo output.  Sorry, no highlight/code tags.  Could you give me more info on that please?  Oh and sorry about delayed reply, this is a side project and I was out of town!

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders, total 40079088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25af25ae

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    38,588,129    38,588,067  83 Linux
/dev/sda2          38,588,130    40,066,109     1,477,980   5 Extended
/dev/sda5          38,588,193    40,066,109     1,477,917  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders, total 40088160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed22ed22

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,066,109    40,066,047   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        71c0b7ff-f891-403d-93f2-b7eb8d331efb   ext3                                     
/dev/sda5        e5a445ee-da09-4672-8a4f-b05e1a334420   swap                                     
/dev/sdb1        BCA8F5C1A8F57A6A                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



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
# kopt=root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro

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
# defoptions=quiet splash loglevel=0

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro quiet splash loglevel=0
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro quiet splash loglevel=0
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows 2000 Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71c0b7ff-f891-403d-93f2-b7eb8d331efb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e5a445ee-da09-4672-8a4f-b05e1a334420 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  18.8GB: boot/grub/menu.lst
  18.8GB: boot/grub/stage2
  18.8GB: boot/initrd.img-2.6.24-19-generic
  18.9GB: boot/initrd.img-2.6.24-27-generic
  18.7GB: boot/initrd.img-2.6.24-27-generic.bak
  18.8GB: boot/vmlinuz-2.6.24-19-generic
  18.8GB: boot/vmlinuz-2.6.24-27-generic
  18.9GB: initrd.img
  18.8GB: initrd.img.old
  18.8GB: vmlinuz
  18.8GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
C:\ubnldr.mbr="Auto Super Grub Disk" 

=================== sdb1: Location of files loaded by Grub: ===================


    .4GB: boot/grub/stage2

---

### Post by oldfred on 2010-03-22
Are you booting from sda. Your script looks ok but sometimes grub has to be reinstalled.  Just be sure to follow the directions for old grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

The only strange thing is that it finds one grub file in sdb which is your windows system??

sdb
.4GB: boot/grub/stage2 	

Grub legacy info
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Fanarkle on 2010-03-23
How do I know if I am booting from sda?  Isn't that info there in the output?

That link is for Ubuntu/XP/Vista/7 but I am running Windows 2000 Pro.  Does it still apply?

---

### Post by oldfred on 2010-03-23
No the script cannot tell which drive you use to boot. BIOS/Master settings control which MBR is used to boot. New BIOS have a setting for master/slave or boot drive that is separate from the boot device HD, floppy, CD, etc. Older IDE system have to have either jumpers for master/slave on the Hard Drive or cable select where the jumpers are set to cable select and you have the newer 3 color connectors with 80 wires that control which is master and slave.

The windows boot loader is the same for XP and before. I have heard you can use Win98 also. Windows boot loader really just look for the boot flag (active) in a partition and then jump to that partition to continue booting.

You can use a generic windows boot loader. That you can install from Ubuntu. You may have to have universe repository set to download this, It is not using lilo but using it just to install the windows boot loader into the MBR.

Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by Fanarkle on 2010-03-23
Everything about this system is old.  Would it help if I post hardware configuration?  I have two Western Digital 20Gb hard drives on IDE1 using IDE 40 conductor cable.  Linux drive has jumpers set to master, windows drive has jumpers set to slave.

Should I do lilo first, or grub?  or only one?

---

### Post by Fanarkle on 2010-03-23
Also, do I need to use lilo from LiveCD?

---

### Post by psusi on 2010-03-23
If the system is that old your bios might not be able to see beyond 2 gigs.  When installing Ubuntu, do manual partitioning and create a 50-100 mb partition at the start of the disk mounted as /boot.

---

### Post by Fanarkle on 2010-03-23
It can see beyond 2 gigs.  It was previously running Windows 2000 Pro installed on a single partition on 20Gb drive.

---

### Post by andrewthomas on 2010-03-23
> **Fanarkle said:**
> Also, do I need to use lilo from LiveCD?

> **oldfred said:**
> 


You can use a generic windows boot loader. That you can install **from Ubuntu**. You may have to have universe repository set to download this, It is not using lilo but using it just to install the windows boot loader into the MBR.

Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbrNo, you can do it from your regular installation

---

### Post by psusi on 2010-03-23
> **Fanarkle said:**
> It can see beyond 2 gigs.  It was previously running Windows 2000 Pro installed on a single partition on 20Gb drive.

That doesn't mean that the bios could see the whole drive.  Usually since it is one of the first files that windows installs and windows always allocates the first free block, the boot loader and kernel end up within the first 2 gb, so it just works... until you happen to run a defrag that moves the files above the 2 gb mark.

---

### Post by Fanarkle on 2010-03-23
When the system boots, the bios lists the drives accurately.

So should I install lilo or grub...or both?  In what order?

---

### Post by oldfred on 2010-03-23
I thought your grub in sda was ok and allowed booting. My instructions on using lilo to install a windows boot loader said sda when it should have said sdb, if that is your windows drive.

sudo lilo -M /dev/sdb mbr 	

What errors do you get now?

---

### Post by Fanarkle on 2010-03-23
If I type into console sudo lilo -M /dev/sdb mbr and reboot then the menu says:

Microsoft Windows 2000 Professional 
Auto Super Grub Disk

If I select first option, Windows 2000 Pro boots fine.
If I select second option, Auto Super Grub does its thing, and after reboot I get the original menu with the original errors described.  Won't boot into Windows or Ubuntu.

If I boot with LiveCD and enter into console:

sudo grub
find /boot/grub/stage1
(hd0,0)
root (hd0,0)
setup (hd0)
quit
sudo reboot

Then I take out the CD and get the original menu with original errors described.

Right now, the only thing that seems to work is to boot with the Windows 2000 CD in the drive and hit esc to boot from hard disk, which then goes to the GRUB menu and works fine, no errors.

---

### Post by oldfred on 2010-03-23
It seems like you are booting from sdb when you get the errors and from sda after you use the windows CD. Is that even possible the way you are set up?

The grub in sda looks correct and the grub in sdb looks like it would give the errors.

---

### Post by Fanarkle on 2010-03-24
I have no idea what is possible any more...anything else I could try?  I am contemplating switching the jumpers just to see what would happen...

---

### Post by psusi on 2010-03-24
Yea, it sounds like your bios is booting from sdb.  Go into the bios and set it to boot from sda.

---

### Post by Fanarkle on 2010-03-26
> **psusi said:**
> Yea, it sounds like your bios is booting from sdb.  Go into the bios and set it to boot from sda.

That worked!  I went into the bios and changed the boot order so that it would boot from HDD-0 instead of HDD-1 and that fixed it!

Thanks!

---

