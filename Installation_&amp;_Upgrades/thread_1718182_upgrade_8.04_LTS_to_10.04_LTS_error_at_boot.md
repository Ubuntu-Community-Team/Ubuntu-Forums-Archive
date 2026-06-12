---
title: "upgrade 8.04 LTS to 10.04 LTS error at boot"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by prezbedard on 2011-03-30
I am posting from using my 8.04 lts live cd

I just upgraded from 8.04LTS to 10.04LTS when it boots I get this error

> error occurred mounting ntfs

press S to skip or m to manually repair

When I press S it just stays on the splash boot screen forever.


I press M I can get more info but not sure if it is related but I get this message:

udev[268]:SYS{}=will be removed in a future udev version, please use ATTR = to match event device or ATTRS = to match a parent device in /etc/udev rules.d/85-brltty.rules:30

there are a number of these errors all the same except the number at the end.

Here is the file
```
# udev rules file for brltty
#

ACTION!="add", GOTO="brltty_rules_end"
SUBSYSTEM!="usb_device", GOTO="brltty_rules_end"

# Alva
SYSFS{idVendor}=="06b0", SYSFS{idProduct}=="0001", RUN+="/lib/brltty/brltty.sh -b al -d usb:"

# Baum
SYSFS{idVendor}=="0403", SYSFS{idProduct}=="fe71", RUN+="/lib/brltty/brltty.sh -b bm -d usb:"
SYSFS{idVendor}=="0403", SYSFS{idProduct}=="fe72", RUN+="/lib/brltty/brltty.sh -b bm -d usb:"
SYSFS{idVendor}=="0403", SYSFS{idProduct}=="fe73", RUN+="/lib/brltty/brltty.sh -b bm -d usb:"
SYSFS{idVendor}=="0403", SYSFS{idProduct}=="fe74", RUN+="/lib/brltty/brltty.sh -b bm -d usb:"
SYSFS{idVendor}=="0403", SYSFS{idProduct}=="fe75", RUN+="/lib/brltty/brltty.sh -b bm -d usb:"

# FreedomScientific
SYSFS{idVendor}=="0f4e", SYSFS{idProduct}=="0100", RUN+="/lib/brltty/brltty.sh -b fs -d usb:"
SYSFS{idVendor}=="0f4e", SYSFS{idProduct}=="0111", RUN+="/lib/brltty/brltty.sh -b fs -d usb:"
SYSFS{idVendor}=="0f4e", SYSFS{idProduct}=="0112", RUN+="/lib/brltty/brltty.sh -b fs -d usb:"

# HandyTech
SYSFS{idVendor}=="0921", SYSFS{idProduct}=="1200", RUN+="/lib/brltty/brltty.sh -b ht -d usb:"
#SYSFS{idVendor}=="0403", SYSFS{idProduct}=="6001", RUN+="/lib/brltty/brltty.sh -b ht -d usb:"

# Papenmeier
SYSFS{idVendor}=="0403", SYSFS{idProduct}=="f208", RUN+="/lib/brltty/brltty.sh -b pm -d usb:"

# Voyager
SYSFS{idVendor}=="0798", SYSFS{idProduct}=="0001", RUN+="/lib/brltty/brltty.sh -b vo -d usb:"

LABEL="brltty_rules_end"
```

and here is my fstab file I do have several ntfs partitions as this is a dual boot system btw windows boots fine.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b /               ext3    defaults,,errors=remount-ro 0       1


# /dev/hda1


/media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/hdb1
/media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb2

                      /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=6e258be1-05a5-409f-be55-abd0f203a514 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by Hedgehog1 on 2011-03-30
We need to get a look at what shape your partitions are in.

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-30
Once you have posted the script results, you can try this while we have a look the your systems 'innards':

Comment out every partition that isn't '/' (root) and reboot:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b /               ext3    defaults,,errors=remount-ro 0       1


# /dev/hda1


[COLOR="Red"]#[/COLOR]/media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/hdb1
[COLOR="Red"]#[/COLOR]/media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb2

[COLOR="Red"]#[/COLOR]                      **/media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1**
# /dev/hda3
[COLOR="Red"]#[/COLOR]UUID=6e258be1-05a5-409f-be55-abd0f203a514 none            swap    sw              0       0
[COLOR="Red"]#[/COLOR]/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
[COLOR="Red"]#[/COLOR]/dev/           /media/floppy0  auto   rw,user,noauto  0       0
```


***The Hedge***

:KS

---

### Post by prezbedard on 2011-03-31
Here is the output of the script.I'll try that, 

```
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc
 => No boot loader? is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sde has 
                       19488470 sectors.. But according to the info from the 
                       partition table , it has 155907768 sectors.
    Mounting failed:
mount: /dev/sde already mounted or FD/sde busy

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf527f527

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   307,194,929   102,398,310  83 Linux
/dev/sda3         307,194,930   309,299,444     2,104,515  82 Linux swap / Solaris
/dev/sda4         309,299,445   350,265,194    40,965,750  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb79cb79

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    61,721,729    61,721,667   7 HPFS/NTFS

/dev/sdb2          61,721,730    78,108,029    16,386,300   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500 MB, 500563968 bytes
16 heads, 32 sectors/track, 1909 cylinders, total 977664 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32       977,663       977,632   e W95 FAT16 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2056 MB, 2056781824 bytes
16 heads, 32 sectors/track, 7846 cylinders, total 4017152 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc7d8acae

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  32     4,017,151     4,017,120   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C8E837BBE837A71A                       ntfs                                     
/dev/sda2        8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b   ext3                                     
/dev/sda3        6e258be1-05a5-409f-be55-abd0f203a514   swap                                     
/dev/sda4        ea74e98c-b036-4738-b205-b3c106ba5f2a   ext3                                     
/dev/sdb1        72943A249439EB6D                       ntfs                                     
/dev/sdb2        EAECB05FECB02829                       ntfs       My Drive                      
/dev/sdc1        B40D-1178                              vfat       KINGSTON                      
/dev/sdd1        9F20-A57A                              vfat       TravelDrive                   
/dev/sde1        3141-5926                              vfat       PAUL'S IPOD                   
/dev/sde         A88B-3652                              vfat       iPod                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sde1        /media/PAUL'S IPOD       vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdd1        /media/TravelDrive       vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdc1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda2        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro quiet splash 
initrd		/boot/initrd.img-2.6.32-30-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro  single
initrd		/boot/initrd.img-2.6.32-30-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.24-28-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro  single
initrd		/boot/initrd.img-2.6.24-28-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.22-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro quiet splash 
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro  single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.20-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro quiet splash 
initrd		/boot/initrd.img-2.6.20-17-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.20-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro  single
initrd		/boot/initrd.img-2.6.20-17-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.17-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro quiet splash 
initrd		/boot/initrd.img-2.6.17-12-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro  single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro  single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b ro  single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 10.04.2 LTS, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b /               ext3    defaults,,errors=remount-ro 0       1


# /dev/hda1


/media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/hdb1
/media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb2

                      /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=6e258be1-05a5-409f-be55-abd0f203a514 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

=================== sda2: Location of files loaded by Grub: ===================


 114.1GB: boot/grub/menu.lst
 114.2GB: boot/grub/stage2
 114.1GB: boot/initrd.img-2.6.17-10-generic
 114.1GB: boot/initrd.img-2.6.17-11-generic
 114.1GB: boot/initrd.img-2.6.17-12-generic
 114.1GB: boot/initrd.img-2.6.17-12-generic.bak
 114.2GB: boot/initrd.img-2.6.20-17-generic
 114.1GB: boot/initrd.img-2.6.20-17-generic.bak
 114.2GB: boot/initrd.img-2.6.22-16-generic
 114.2GB: boot/initrd.img-2.6.22-16-generic.bak
 129.9GB: boot/initrd.img-2.6.24-28-generic
 129.9GB: boot/initrd.img-2.6.24-28-generic.bak
 114.2GB: boot/initrd.img-2.6.32-30-generic
 114.2GB: boot/vmlinuz-2.6.17-10-generic
 114.2GB: boot/vmlinuz-2.6.17-11-generic
 114.1GB: boot/vmlinuz-2.6.17-12-generic
 114.1GB: boot/vmlinuz-2.6.20-17-generic
 114.1GB: boot/vmlinuz-2.6.22-16-generic
 129.8GB: boot/vmlinuz-2.6.24-28-generic
 129.9GB: boot/vmlinuz-2.6.32-30-generic
 114.2GB: initrd.img
 129.9GB: initrd.img.old
 129.9GB: vmlinuz
 129.8GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

---

### Post by prezbedard on 2011-03-31
It won't let me edit either with the live cd or the recovery option when I press M. The fs seems to be read only.

---

### Post by Hedgehog1 on 2011-03-31
Yeah - you need to mount the hard drive and edit that fstab.

Here is how (based on the partitions on your listing):

```
sudo mount /dev/sda2 /mnt
```

```
gksudo gedit /mnt/etc/fstab
```

I can also explain the issue.  You were referring to partitions by "/dev/**hd**a1", and after the upgrade, they were referred to as "/dev/**sd**a1".  It is is best to use UUID's of the drives in fstab to avoid these issues.

So, your fstab file should look like this to get rolling:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda2
UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b /       ext3    errors=remount-ro 0  1
#/dev/sda3
UUID=6e258be1-05a5-409f-be55-abd0f203a514 none    swap    sw                0  0
#/dev/sda4
UUID=ea74e98c-b036-4738-b205-b3c106ba5f2a /home   ext3    defaults          0  2

#/dev/sda1 (NTFS)
#UUID=C8E837BBE837A71A            /media/NTFS1     ntfs    defaults          0  0
#/dev/sdb1 (NTFS)
#UUID=72943A249439EB6D            /media/NTFS2     ntfs    defaults          0  0
#/dev/sdb2 (NTFS)
#UUID=EAECB05FECB02829            /media/NTFS3     ntfs    defaults          0  0

/dev/cdrom        /media/cdrom0    auto user,noauto,exec      0  0
#/dev/floppy       /media/floppy0   auto rw,user,noauto        0  0
```

I was assuming that **/dev/sda4** is your **/home**, if it's not please change the mount point.

Once these are working, then add in the 3 NTFS partitions that I have identified with UUIDs.

***The Hedge***

:KS

p.s. Do you still have a floppy drive?  If not the floppy line can be removed

---

### Post by prezbedard on 2011-03-31
Thanks for the response and possible solution. I will try this when I get home tonight.

I can preform the mnt from within the live cd ?

also fstab  went from referring the partitions using hd to sd back when I upgraded to 8.04 LTS if I remember correctly.

---

### Post by Hedgehog1 on 2011-03-31
These commands are **indeed** meant for running from the LiveCD/LiveUSB:
 
 
```
sudo mount /dev/sda2 /mnt
```
 
```
gksudo gedit /mnt/etc/fstab
```
 
 
***The Hedge***
 
:KS

---

### Post by prezbedard on 2011-03-31
Well I edited fstab so only the root fs and swap weren't commented out. I booted and it didn't have the error. However it also just stayed at the boot splash screen forever. I decided to try the recovery selection under it got to login prompt but am unable to get a gui session going. I think maybe 10.04 is a bit much for this machine. It is after all 9 years old though it ran 8.04 well. I think I might just backup my home dir and reinstall 8.04. I'll go to 10.04 LTS when I can afford to build a new box. I at least learned some things from the troubleshooting.

Thanks for the help.

---

### Post by Hedgehog1 on 2011-03-31
> **prezbedard said:**
> Well I edited fstab so only the root fs and swap weren't commented out. I booted and it didn't have the error. However it also just stayed at the boot splash screen forever. I decided to try the recovery selection under it got to login prompt but am unable to get a gui session going. I think maybe 10.04 is a bit much for this machine. It is after all 9 years old though it ran 8.04 well. I think I might just backup my home dir and reinstall 8.04. I'll go to 10.04 LTS when I can afford to build a new box. I at least learned some things from the troubleshooting.
 
Thanks for the help.
 
You plan seams very resonable.  If 8.04 was working, better to run that until you can upgrade your hardware.  You will enjoy 10.04 LTS, it is a very nice release; that that is for another day.
 
***The Hedge***
 
:KS

---

### Post by prezbedard on 2011-04-01
ok I seem to have run into an unexpected error upon the reinstall of 8.04 LTS
I installed on the same partition as before formatting it as ext 3. on the first reboot after the install is finished I get "loading grub error 18"

Here is menu.lst

```
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
# kopt=root=UUID=1d7bd482-0faf-42f6-81a5-ce877b178892 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1d7bd482-0faf-42f6-81a5-ce877b178892 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1d7bd482-0faf-42f6-81a5-ce877b178892 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1d7bd482-0faf-42f6-81a5-ce877b178892 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=6e258be1-05a5-409f-be55-abd0f203a514 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Hedgehog1 on 2011-04-01
My knowledge of Ubuntu begins with 10.10 and Grub2.

I believe you need to purge the Grub2 in the MBR, and then install the legacy grub that is carried in the 8.04 release.

This MIGHT be as easy as doing a FIXMBR for windows, and then updating grub from 8.04 - But I am honestly guessing here (and I don't like to guess when your computer is on the line)

Hopefully someone who knows 8.04 can help.

***The Hedge***

:KS

p.s. Second guess is that you might be able to install grub2 on the 8.04.

---

### Post by mörgæs on 2011-04-01
> **prezbedard said:**
> ok I seem to have run into an unexpected error upon the reinstall of 8.04 LTS

If you are reinstalling, I think you should rather give 10.04 a try, though we are dealing with an old machine. If only you have 512 MB memory you should be able to get it running.

If a full 10.04 turns out to be too heavy, you can gain some speed with Lubuntu and/or installing through this script:

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by prezbedard on 2011-04-01
> **mörgæs said:**
> If you are reinstalling, I think you should rather give 10.04 a try, though we are dealing with an old machine. If only you have 512 MB memory you should be able to get it running.

If a full 10.04 turns out to be too heavy, you can gain some speed with Lubuntu and/or installing through this script:

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

Thanks but I really do like the gnome. I'm going to try and fix the mbr when I go home later and work on this over the weekend if need be.

---

### Post by prezbedard on 2011-04-02
> **Hedgehog1 said:**
> My knowledge of Ubuntu begins with 10.10 and Grub2.

I believe you need to purge the Grub2 in the MBR, and then install the legacy grub that is carried in the 8.04 release.

This MIGHT be as easy as doing a FIXMBR for windows, and then updating grub from 8.04 - But I am honestly guessing here (and I don't like to guess when your computer is on the line)

Hopefully someone who knows 8.04 can help.

***The Hedge***

:KS

p.s. Second guess is that you might be able to install grub2 on the 8.04.

booting with an xp disk into recovery console and running fixbr got my machine to boot into windows.

I then booted again with the live cd. I found this link on restoring grub with a live cd
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD")

I followed:
> Now, you have to be really careful. You have to enter the right partition, instead of sda2 (unless it is the same) In the terminal :

  cd /
  
 
  sudo -s -H

  mount -t ext3 /dev/sda2 /mnt

  mount -t proc proc /mnt/proc

  mount -t sysfs sys /mnt/sys

  mount -o bind /dev /mnt/dev

  chroot /mnt  /bin/bash

And now, you are actually "running" Ubuntu within the Hard Drive but through Live CD's terminal.

Now we restore GRUB like that:

1) Restoration to MBR

  grub-install /dev/sda

2) Restoration to partition (example: /dev/sda2)

  grub-install /dev/sda2

In the first case (that is the most usual) you have certainly installed GRUB on MBR after you receive, in the terminal, the message that there are no errors.

After you reboot, you have your favorite bootloader restored. 

I got no errors however when I rebooted I was back to where I started with the same grub error 18.

---

### Post by prezbedard on 2011-04-02
ok well I deleted the partition this time and recreated it. installed 8.04 again and the error is still there! I don't get it.

---

### Post by mörgæs on 2011-04-02
Again, how come you don't try a fresh install of 10.04? Worst case is that you have wasted half an hour.

If this is a desktop installation, you will only have support for 8.04 until end of the month anyway.

---

### Post by prezbedard on 2011-04-02
> **mörgæs said:**
> Again, how come you don't try a fresh install of 10.04? Worst case is that you have wasted half an hour.

If this is a desktop installation, you will only have support for 8.04 until end of the month anyway.

I don't have a 10.04 disk plus I don't think my 9 y/o machine can take it after the experience with the upgrade from 8.04.

I'm running 10.04 on another machine I borrowed from work now. It is very nice not sure I like the default theme much though.

---

### Post by mörgæs on 2011-04-03
What you are seeing is the bad results of the upgrade process itself. This does not mean that a fresh install of 10.04 is slow. 
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

There are many themes available in a standard install. You don't have to follow the default.

---

