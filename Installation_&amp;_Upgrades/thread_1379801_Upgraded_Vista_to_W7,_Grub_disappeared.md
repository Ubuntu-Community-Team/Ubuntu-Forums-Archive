---
title: "Upgraded Vista to W7, Grub disappeared"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by kunks112 on 2010-01-12
I boot Ubuntu Hardy, and W7 from two separate drives.

I recently upgraded from Vista to W7 and my mbr seemed have been overwritten and all I am able to view is windows boot loader. ( I have 2 windows 7 drives, one was the RC, but that drive is removed and being used elsewhere for the time being)

I've tried loading from the live disk then
```
sudo grub
find /boot/grub/stage1
root (hd1,0)  [hd1,0 from previous command]
setup (hd1)
quit
sudo reboot
```

But this had no effect. 

Here is my bootscript info

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bf61bf5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,051,199   586,051,137   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009aac1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   955,498,004   955,497,942  83 Linux
/dev/sdb2         955,498,005   976,768,064    21,270,060   5 Extended
/dev/sdb5         955,498,068   976,768,064    21,269,997  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="40BC2AF2BC2AE1E0" TYPE="ntfs" 
/dev/sdb1: UUID="77b246ea-bbd0-44a0-917f-cd50693b584c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="62132145-d060-460c-afeb-3d7dd27bfadc" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash xforcevesa

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=77b246ea-bbd0-44a0-917f-cd50693b584c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=62132145-d060-460c-afeb-3d7dd27bfadc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 209.6GB: boot/grub/menu.lst
 209.5GB: boot/grub/stage2
 209.5GB: boot/initrd.img-2.6.24-16-generic
 209.6GB: boot/initrd.img-2.6.24-16-generic.bak
 209.6GB: boot/initrd.img-2.6.24-24-generic
 209.5GB: boot/initrd.img-2.6.24-24-generic.bak
 209.5GB: boot/initrd.img-2.6.24-25-generic
 209.5GB: boot/initrd.img-2.6.24-25-generic.bak
 209.6GB: boot/initrd.img-2.6.24-26-generic
 209.5GB: boot/initrd.img-2.6.24-26-generic.bak
 209.6GB: boot/vmlinuz-2.6.24-16-generic
 209.6GB: boot/vmlinuz-2.6.24-24-generic
 209.6GB: boot/vmlinuz-2.6.24-25-generic
 209.5GB: boot/vmlinuz-2.6.24-26-generic
 209.6GB: initrd.img
 209.5GB: initrd.img.old
 209.5GB: vmlinuz
 209.6GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ls: cannot access /dev/mapper: No such file or directory
```

Thanks in advance for help

Mike

edit* When I changed my boot order in my bios, my grub menu appeared, however I got the error 17: Cannot mount selected partition.

---

### Post by presence1960 on 2010-01-13
> **kunks112 said:**
> I boot Ubuntu Hardy, and W7 from two separate drives.

I recently upgraded from Vista to W7 and my mbr seemed have been overwritten and all I am able to view is windows boot loader. ( I have 2 windows 7 drives, one was the RC, but that drive is removed and being used elsewhere for the time being)

I've tried loading from the live disk then
```
sudo grub
find /boot/grub/stage1
root (hd1,0)  [hd1,0 from previous command]
setup (hd1)
quit
sudo reboot
```

But this had no effect. 

Here is my bootscript info

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bf61bf5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,051,199   586,051,137   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009aac1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   955,498,004   955,497,942  83 Linux
/dev/sdb2         955,498,005   976,768,064    21,270,060   5 Extended
/dev/sdb5         955,498,068   976,768,064    21,269,997  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="40BC2AF2BC2AE1E0" TYPE="ntfs" 
/dev/sdb1: UUID="77b246ea-bbd0-44a0-917f-cd50693b584c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="62132145-d060-460c-afeb-3d7dd27bfadc" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash xforcevesa

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=77b246ea-bbd0-44a0-917f-cd50693b584c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=62132145-d060-460c-afeb-3d7dd27bfadc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 209.6GB: boot/grub/menu.lst
 209.5GB: boot/grub/stage2
 209.5GB: boot/initrd.img-2.6.24-16-generic
 209.6GB: boot/initrd.img-2.6.24-16-generic.bak
 209.6GB: boot/initrd.img-2.6.24-24-generic
 209.5GB: boot/initrd.img-2.6.24-24-generic.bak
 209.5GB: boot/initrd.img-2.6.24-25-generic
 209.5GB: boot/initrd.img-2.6.24-25-generic.bak
 209.6GB: boot/initrd.img-2.6.24-26-generic
 209.5GB: boot/initrd.img-2.6.24-26-generic.bak
 209.6GB: boot/vmlinuz-2.6.24-16-generic
 209.6GB: boot/vmlinuz-2.6.24-24-generic
 209.6GB: boot/vmlinuz-2.6.24-25-generic
 209.5GB: boot/vmlinuz-2.6.24-26-generic
 209.6GB: initrd.img
 209.5GB: initrd.img.old
 209.5GB: vmlinuz
 209.6GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ls: cannot access /dev/mapper: No such file or directory
```

Thanks in advance for help

Mike

edit* When I changed my boot order in my bios, my grub menu appeared, however I got the error 17: Cannot mount selected partition.

Keep sdb as first to boot in the hard disk boot order but when you boot do this:

When the GRUB menu comes up highlight Ubuntu and press "e" on the keyboard. Now use your arrow keys to navigate to this in that string you see (hd1,0) change it to (hd0,0) by getting the underscore on 1, hit delete key amd type 0. Now press Ctrl + x to boot into ubuntu.

When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
gksu gedit /boot/grub/menu.lst 
```
That is a lowercase L in .lst   
Scroll down to your Ubuntu entries in menu.lst and change the red in this:

```
## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=77b246ea-bbd0-44a0-917f-cd50693b584c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.3 LTS, memtest86+
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/memtest86+.bin
quiet
```

TO:

```
root     (hd0,0)
```

Now scroll down to your windows entry and change this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

TO:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

```

Click Save on top toolbar & close file. Reboot and you will be good to go.

---

### Post by kunks112 on 2010-01-13
Thank you for the reply.

When I get into my grub screen. I choose Ubunut, press "e". Then I have to press "e" again to edit. After I am done changing it to (hd0,0), I hit CRTL + x, nothing happens. I hit enter and it takes me back to a screen that looks like

```
root (hd0,0)
kernal /boot/vmlinuz-2.6.24-26-generic root= UUID.....
initrd / boot/initrd.img-2.6.24-26-generic
quiet
```

I press CRTL +x here, nothing happens. 
I got back to grub screen and the (hd0,0) changes back.

Basicall I cant load into Ubuntu by pressing CRTL + x at any screen.

---

### Post by meierfra. on 2010-01-13
"Ctr x" is for Grub 2 . In Legacy grub you have to press "b".

---

### Post by kunks112 on 2010-01-13
Excellent.
All is well now.

My thanks goes to both of you.

Mike

---

### Post by meierfra. on 2010-01-13
> All is well now.


Great. Just one more thing:
Change


# groot=(hd1,0)

in your  menu.lst  to 

# groot=(hd0,0)


Otherwise all your "(hd0,0)" will revert to "(hd1,0)" the next time "update-grub" is run, for example during kernel updates.

---

### Post by presence1960 on 2010-01-13
> **meierfra. said:**
> "Ctr x" is for Grub 2 . In Legacy grub you have to press "b".

Thanks meierfra, will make a note of that!

---

### Post by kunks112 on 2010-01-14
Thanks.

I went into my menu.lst to change the groot, however it was already set at (hd0,0)

Thanks again

---

### Post by meierfra. on 2010-01-14
From your result.txt
> ## e.g. groot=(hd0,0)
# groot=[COLOR="Red"](hd1,0)[/COLOR]


So you must of changed it, then you changed all the other "root (hd1,0)".:D

---

