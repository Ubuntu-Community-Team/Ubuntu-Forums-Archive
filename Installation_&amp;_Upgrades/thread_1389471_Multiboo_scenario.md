---
title: "Multiboo scenario"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by sefs on 2010-01-24
Hi i currently have a system dual booting 

1) windows xp
2) ubuntu 9.04

I just added a third system manually xubuntu 9.04

How can I make the boot menu update automatically to see this new OS xubuntu.

Thanks.

---

### Post by raymondh on 2010-01-24
> **sefs said:**
> Hi i currently have a system dual booting 

1) windows xp
2) ubuntu 9.04

I just added a third system manually xubuntu 9.04

How can I make the boot menu update automatically to see this new OS xubuntu.

Thanks.

You can chainload the new linux install in your /boot/grub/menu.lst.   see Herman's guide

[http://members.iinet.net.au/~herman546/p15.html#2._Chainloader](http://members.iinet.net.au/~herman546/p15.html#2._Chainloader)

To edit the menu.lst, open in terminal with

gksudo gedit /boot/grub/menu.lst.


If you want, download the bootinfoscript (see tutorial below) and run it to produce a results.txt file.  That'll help the forum understand what your HD contains.

[http://ubuntuforums.org/showpost.php?p=8104352&postcount=1](http://ubuntuforums.org/showpost.php?p=8104352&postcount=1)

Raymond
Raymond

---

### Post by sefs on 2010-01-24
here are the results...

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
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
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11a8ba38

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    31,455,269    31,455,207   7 HPFS/NTFS
/dev/sda2          31,455,270    52,420,094    20,964,825  83 Linux
/dev/sda3          52,420,095   302,086,259   249,666,165   5 Extended
/dev/sda5          52,420,158   276,816,014   224,395,857  83 Linux
/dev/sda6         297,780,903   302,086,259     4,305,357  82 Linux swap / Solaris
/dev/sda7         276,816,078   297,780,839    20,964,762  83 Linux
/dev/sda4         302,086,260   312,576,704    10,490,445  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F69C12429C11FDB5" TYPE="ntfs" 
/dev/sda2: UUID="d4745437-fbf7-49ae-ab0c-103b3cc3a2cc" TYPE="ext3" 
/dev/sda4: UUID="b87d4e69-4e4d-4f2d-a655-258503b0643c" TYPE="ext4" 
/dev/sda5: UUID="67db389e-fb6b-42ed-a53d-47afcc64ecb2" TYPE="ext3" 
/dev/sda6: UUID="613a072f-e718-420a-8e32-e767d6e5c27c" TYPE="swap" 
/dev/sda7: UUID="3300ad99-2887-4432-b4e1-36f1cbc4e93c" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-17-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hhhacerlin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hhhacerlin)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=d4745437-fbf7-49ae-ab0c-103b3cc3a2cc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d4745437-fbf7-49ae-ab0c-103b3cc3a2cc

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		d4745437-fbf7-49ae-ab0c-103b3cc3a2cc
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=d4745437-fbf7-49ae-ab0c-103b3cc3a2cc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		d4745437-fbf7-49ae-ab0c-103b3cc3a2cc
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=d4745437-fbf7-49ae-ab0c-103b3cc3a2cc ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, memtest86+
uuid		d4745437-fbf7-49ae-ab0c-103b3cc3a2cc
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
rootnoverify	(hd0,0)
savedefault
chainloader	+1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		oldster operating systems:
root


title		Xubuntu 9.04, kernel 2.6.28-17-generic
#uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root		(hd0,2)
chainloader	+1
#kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-17-generic
#quiet

#title		Xubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
#uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
#kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro  single
#initrd		/boot/initrd.img-2.6.28-17-generic


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=d4745437-fbf7-49ae-ab0c-103b3cc3a2cc /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=67db389e-fb6b-42ed-a53d-47afcc64ecb2 /home           ext3    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=613a072f-e718-420a-8e32-e767d6e5c27c none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  18.1GB: boot/grub/menu.lst
  18.1GB: boot/grub/stage2
  18.3GB: boot/initrd.img-2.6.28-17-generic
  18.2GB: boot/vmlinuz-2.6.28-17-generic
  18.3GB: initrd.img
  18.2GB: vmlinuz

=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b87d4e69-4e4d-4f2d-a655-258503b0643c

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, memtest86+
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=3300ad99-2887-4432-b4e1-36f1cbc4e93c /home           ext3    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=613a072f-e718-420a-8e32-e767d6e5c27c none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 156.6GB: boot/grub/menu.lst
 155.2GB: boot/grub/stage2
 154.8GB: boot/initrd.img-2.6.28-17-generic
 158.5GB: boot/vmlinuz-2.6.28-17-generic
 154.8GB: initrd.img
 158.5GB: vmlinuz

```

I am trying to chainload the third os. But not working at all.  It works if i do it without chainloading.  How would i be able to chainload.

The error i get when chainloading is 

Error 13: invalid or unsupported executable format

---

### Post by kansasnoob on 2010-01-24
Run the command:

```
df
```

Just to be sure you're booted into sda2, then run:

```
gksudo gedit /boot/grub/menu.lst
```

At the bottom you'll see:

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1


[B][COLOR="Red"]# This is a divider, added to separate the menu items below from the Debian
# ones.
title		oldster operating systems:
root


title		Xubuntu 9.04, kernel 2.6.28-17-generic
#uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root		(hd0,2)
chainloader	+1
#kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-17-generic
#quiet

#title		Xubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
#uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
#kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro  single
#initrd		/boot/initrd.img-2.6.28-17-generic
[/COLOR][/B]

```

Delete everything in red and add:

```
title		Xubuntu 9.04, kernel 2.6.28-17-generic
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet
savedefault
boot

title		Xubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro  single
initrd		/boot/initrd.img-2.6.28-17-generic
savedefault
boot
```

Be sure to click on save before closing gedit.

---

### Post by kansasnoob on 2010-01-24
Upon closer look you may need to drop the quiet:

```
title		Xubuntu 9.04, kernel 2.6.28-17-generic
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
**[COLOR="Red"]quiet[/COLOR]**
savedefault
boot

title		Xubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro  single
initrd		/boot/initrd.img-2.6.28-17-generic
savedefault
boot
```

So it would be:

```
title		Xubuntu 9.04, kernel 2.6.28-17-generic
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
savedefault
boot

title		Xubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro  single
initrd		/boot/initrd.img-2.6.28-17-generic
savedefault
boot
```

Let me know.

---

### Post by sefs on 2010-01-24
> **kansasnoob said:**
> Upon closer look you may need to drop the quiet:

```
title		Xubuntu 9.04, kernel 2.6.28-17-generic
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
**[COLOR="Red"]quiet[/COLOR]**
savedefault
boot

title		Xubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro  single
initrd		/boot/initrd.img-2.6.28-17-generic
savedefault
boot
```

So it would be:

```
title		Xubuntu 9.04, kernel 2.6.28-17-generic
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
savedefault
boot

title		Xubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		b87d4e69-4e4d-4f2d-a655-258503b0643c
root            (hd0,3)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b87d4e69-4e4d-4f2d-a655-258503b0643c ro  single
initrd		/boot/initrd.img-2.6.28-17-generic
savedefault
boot
```

Let me know.

The way you have it works i know it, but remember I want to chain load.  If i dont chainload each time the kernel is updated in that third os then i have to maunally edit the menu.lst that points to that.

I think chainloader will be more automatic where it just points to the grub/loader of the third os and auto load the most recent os?

---

### Post by kansasnoob on 2010-01-24
Even more automatic is grub2 :D

But what you want to do requires you to set Xubuntu's grub to the boot sector of that partition and then write an entry in menu.lst to boot the second grub.

I don't like that. I never have. Installing grub to a partition rather than to the mbr of a drive always seems to end up causing problems later on.

Anyway I was just doing some testing in my Jaunty (9.04) and I think I know how to convert it to Lucid's grub2 now, but I'd need to test this several times before I present it as an option :)

---

### Post by sefs on 2010-01-24
> **kansasnoob said:**
> Even more automatic is grub2 :D

But what you want to do requires you to set Xubuntu's grub to the boot sector of that partition and then write an entry in menu.lst to boot the second grub.

I don't like that. I never have. Installing grub to a partition rather than to the mbr of a drive always seems to end up causing problems later on.

Anyway I was just doing some testing in my Jaunty (9.04) and I think I know how to convert it to Lucid's grub2 now, but I'd need to test this several times before I present it as an option :)

agreed with keeping grub in the mbr as opposed to the partiton. 

Thank for the info. Will look out for your results with grub2 on jaunty.

---

