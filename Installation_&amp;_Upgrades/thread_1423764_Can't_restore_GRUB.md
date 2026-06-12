---
title: "Can't restore GRUB"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Vostrocity on 2010-03-07
After installing Vista (downgraded from 7 RC), I booted into Ubuntu LiveCD to restore GRUB following the [instruction ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")on the Ubuntu documentation. I did what it said to do, but when I rebooted again it went straight into Windows. When I tried holding down the Esc key while booting as suggested in the docs, my system just restarts. And Windows bluescreened a few times while booting, but I'm not worried about that. I just need to get back into Ubuntu.

---

### Post by meierfra. on 2010-03-07
If you have more than one hard drive, change the boot order in the Bios.

If that did  not cure your problem: Follow the [instructions]("http://bootinfoscript.sourceforge.net") to run the boot info script and post the RESULTS.txt.

---

### Post by Vostrocity on 2010-03-07
Well here's one massive output.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 84155303 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    71,826,614    71,826,552   5 Extended
/dev/sda5                 126    71,826,614    71,826,489   7 HPFS/NTFS
/dev/sda2          71,826,615   133,259,174    61,432,560  83 Linux
/dev/sda3    *    133,259,175   194,691,734    61,432,560   7 HPFS/NTFS
/dev/sda4         194,691,735   234,436,544    39,744,810   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        5fb4f898-89ed-4333-813e-ed6e54a982bc   ext3       Linux                         
/dev/sda3        AE10698010694FFF                       ntfs                                     
/dev/sda4        10876CBC3F9D9467                       ntfs       Sandbox                       
/dev/sda5        6E51D52B37939B70                       ntfs       Files                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /media/cdrom             iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5fb4f898-89ed-4333-813e-ed6e54a982bc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5fb4f898-89ed-4333-813e-ed6e54a982bc

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

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		5fb4f898-89ed-4333-813e-ed6e54a982bc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=5fb4f898-89ed-4333-813e-ed6e54a982bc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		5fb4f898-89ed-4333-813e-ed6e54a982bc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=5fb4f898-89ed-4333-813e-ed6e54a982bc ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		5fb4f898-89ed-4333-813e-ed6e54a982bc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=5fb4f898-89ed-4333-813e-ed6e54a982bc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		5fb4f898-89ed-4333-813e-ed6e54a982bc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=5fb4f898-89ed-4333-813e-ed6e54a982bc ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, memtest86+
uuid		5fb4f898-89ed-4333-813e-ed6e54a982bc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda2
UUID=5fb4f898-89ed-4333-813e-ed6e54a982bc  /              ext3         relatime,errors=remount-ro  0  1  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda5                                  /media/sda5    ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sda4                                  /media/sda4    ntfs         nls=iso8859-1,noauto        0  0  
/dev/sda3                                  /media/sda3    hfsplus      noauto                      0  0  

=================== sda2: Location of files loaded by Grub: ===================


  43.1GB: boot/grub/menu.lst
  43.2GB: boot/grub/stage2
  43.8GB: boot/initrd.img-2.6.31-17-generic
  45.3GB: boot/initrd.img-2.6.31-19-generic
  43.6GB: boot/vmlinuz-2.6.31-17-generic
  45.3GB: boot/vmlinuz-2.6.31-19-generic
  45.3GB: initrd.img
  43.8GB: initrd.img.old
  45.3GB: vmlinuz
  43.6GB: vmlinuz.old

```

---

### Post by meierfra. on 2010-03-07
> => Windows is installed in the MBR of /dev/sda

 > Boot sector info:  Grub 0.97 is installed in the boot sector of sda2


You installed Grub to the boot sector of the Ubuntu partition,  instead to the MBR.  To fix it, boot from the Ubuntu LiveCD (version 9.04 or older) open a terminal.

```
sudo grub
```

and at the "grub>" prompt:

```
root (hd0,1)
setup (hd0)
quit
```

Reboot and you should get the Grub menu and should be able  to boot into Ubuntu and Vista from the Grub menu.

---

### Post by Vostrocity on 2010-03-07
Thanks, that works great. I was under the impression that GRUB was supposed to be installed on your Linux partition.

---

