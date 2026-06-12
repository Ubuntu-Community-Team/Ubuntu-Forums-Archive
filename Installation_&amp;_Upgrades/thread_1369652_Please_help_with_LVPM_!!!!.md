---
title: "Please help with LVPM !!!!"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by eyadhafez on 2010-01-01
Hello....
I used LVPM to transfer my ubuntu from install inside windows to a separate partition but i can't boot to my new installation i tried every howto i found to solve the problem but there is no use 
I love ubuntu please help me with this 
Here is my booting info 
```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr.mbr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb6/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x74268b97

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   976,768,064   874,369,755   f W95 Ext d (LBA)
/dev/sda5         102,398,373   976,768,064   874,369,692   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x53705370

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sdb2         102,398,310   488,375,999   385,977,690   5 Extended
/dev/sdb5         102,398,373   204,796,619   102,398,247   7 HPFS/NTFS
/dev/sdb6         204,796,683   235,528,964    30,732,282   7 HPFS/NTFS
/dev/sdb7         235,529,028   307,194,929    71,665,902  83 Linux
/dev/sdb8         307,194,993   488,375,999   181,181,007   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: UUID="c8494eaa-e804-4134-be44-016a41caaaa3" TYPE="ext3" 
/dev/sda1: UUID="82701D48701D43F7" LABEL="Windows 7" TYPE="ntfs" 
/dev/sda5: UUID="389892409891FD16" LABEL="Big Storage" TYPE="ntfs" 
/dev/sdb1: UUID="F8A40F35A40EF642" TYPE="ntfs" 
/dev/sdb5: UUID="004C05C14C05B308" TYPE="ntfs" 
/dev/sdb6: UUID="B018F14818F10DDA" TYPE="ntfs" 
/dev/sdb7: UUID="6f07c6b0-54f1-4119-b17e-34d3aad2c77c" TYPE="ext3" 
/dev/sdb8: UUID="543410F93410E032" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/loop0 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/sdb5 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb6 on /media/sdb6 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eyad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eyad)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb7 on /media/sdb7 type ext3 (rw)
/dev/sr1 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=eyad)
/dev/sdb8 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


==================== sda5/ubuntu/disks/boot/grub/menu.lst: ====================

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
default		2

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst



======================== sda5/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

=================== sda5: Location of files loaded by Grub: ===================


  52.4GB: ubuntu/disks/boot/grub/menu.lst
  52.4GB: ubuntu/disks/boot/initrd.img-2.6.28-16-generic
  52.4GB: ubuntu/disks/boot/initrd.img-2.6.31-14-generic
  52.4GB: ubuntu/disks/boot/initrd.img-2.6.31-15-generic
  52.4GB: ubuntu/disks/boot/vmlinuz-2.6.28-16-generic
  52.4GB: ubuntu/disks/boot/vmlinuz-2.6.31-14-generic
  52.4GB: ubuntu/disks/boot/vmlinuz-2.6.31-15-generic

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc          proc         defaults                      0  0  
/host/ubuntu/disks/root.disk  /              ext3         loop,errors=remount-ro        0  1  
/host/ubuntu/disks/boot       /boot          none         bind                          0  0  
/host/ubuntu/disks/swap.disk  none           swap         loop,sw                       0  0  
/dev/scd0                     /media/cdrom0  udf,iso9660  user,noauto,exec,utf8         0  0  
/dev/scd1                     /media/cdrom1  udf,iso9660  user,noauto,exec,utf8         0  0  
/dev/sda5                     /media/D Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda1                     /media/C Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda6                     /media/sda6    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sda7                     /media/F Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda1                     /media/sda1    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sda5                     /media/sda5    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda7                     /media/sda7    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sdb1                     /media/sdb1    vfat         dmask=227,user                0  0  
/dev/sdb5                     /media/sdb5    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda2                     /media/sda2    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda3                     /media/sda3    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sdb6                     /media/sdb6    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sdb7                     /media/sdb7    ntfs         nls=iso8859-1,umask=000,user  0  0  

================= sda5/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz

================================ sdb1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

c:\wubildr.mbr="Ubuntu" 


==================== sdb6/ubuntu/disks/boot/grub/menu.lst: ====================

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
default		2

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sdb7
root (hd1,6)
configfile /boot/grub/menu.lst



======================== sdb6/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

=================== sdb6: Location of files loaded by Grub: ===================


 104.8GB: ubuntu/disks/boot/grub/menu.lst
 104.8GB: ubuntu/disks/boot/initrd.img-2.6.28-16-generic
 104.8GB: ubuntu/disks/boot/initrd.img-2.6.31-14-generic
 104.8GB: ubuntu/disks/boot/initrd.img-2.6.31-15-generic
 104.8GB: ubuntu/disks/boot/vmlinuz-2.6.28-16-generic
 104.8GB: ubuntu/disks/boot/vmlinuz-2.6.31-14-generic
 104.8GB: ubuntu/disks/boot/vmlinuz-2.6.31-15-generic

============================= sdb6/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc          proc         defaults                      0  0  
/host/ubuntu/disks/root.disk  /              ext3         loop,errors=remount-ro        0  1  
/host/ubuntu/disks/boot       /boot          none         bind                          0  0  
/host/ubuntu/disks/swap.disk  none           swap         loop,sw                       0  0  
/dev/scd0                     /media/cdrom0  udf,iso9660  user,noauto,exec,utf8         0  0  
/dev/scd1                     /media/cdrom1  udf,iso9660  user,noauto,exec,utf8         0  0  
/dev/sda5                     /media/D Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda1                     /media/C Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda6                     /media/sda6    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sda7                     /media/F Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda1                     /media/sda1    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sda5                     /media/sda5    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda7                     /media/sda7    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sdb1                     /media/sdb1    vfat         dmask=227,user                0  0  
/dev/sdb5                     /media/sdb5    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda2                     /media/sda2    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda3                     /media/sda3    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sdb6                     /media/sdb6    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sdb7                     /media/sdb7    ntfs         nls=iso8859-1,umask=000,user  0  0  

================= sdb6/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== sdb7/boot/grub/menu.lst: ===========================

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
default		8

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=  ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=  ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz root=/dev/hda3 ro
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=  ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst



# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title UnknownOS
root (hd1,5)
makeactive
chainloader +1
boot


title Windows 7 (loader)
root (hd1,0)
makeactive
chainloader +1
boot


=============================== sdb7/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sdb7
UUID=     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sdb6
UUID=       /media/drv0                defaults      0   0


=================== sdb7: Location of files loaded by Grub: ===================


 120.5GB: boot/grub/menu.lst
 120.5GB: boot/grub/stage2
 120.5GB: boot/initrd.img-2.6.28-16-generic
 120.5GB: boot/initrd.img-2.6.31-14-generic
 120.5GB: boot/initrd.img-2.6.31-15-generic
 120.5GB: boot/initrd.img-2.6.31-16-generic
 120.5GB: boot/vmlinuz-2.6.28-16-generic
 120.5GB: boot/vmlinuz-2.6.31-14-generic
 120.5GB: boot/vmlinuz-2.6.31-15-generic
 120.5GB: initrd.img
 120.5GB: initrd.img.old
 120.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 31 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |.1..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 80 fa 33 c0 8e d8  8e d0 bc 00 7c b8 30 08  |....3.......|.0.|
00000040  8e c0 fb b8 00 b8 8e e8  e8 1d 00 b9 03 00 32 f6  |..............2.|
00000050  b8 28 02 2e 8a 16 32 7c  bb 00 01 50 cd 13 72 03  |.(....2|...P..r.|
00000060  58 cd 13 ea 00 01 30 08  60 b9 e8 03 33 db 66 65  |X.....0.`...3.fe|
00000070  c7 07 00 00 00 00 83 c3  04 e2 f3 b4 02 32 ff 33  |.............2.3|
00000080  d2 cd 10 61 c3 60 b4 a0  f6 e4 32 ff d1 e3 03 d8  |...a.`....2.....|
00000090  8a 14 0a d2 74 09 65 89  17 46 83 c3 02 eb f1 61  |....t.e..F.....a|
000000a0  c3 50 61 72 61 67 6f 6e  00 4c 6f 61 64 69 6e 67  |.Paragon.Loading|
000000b0  2e 2e 2e 2e 00 4d 42 52  20 52 65 76 69 73 69 6f  |.....MBR Revisio|
000000c0  6e 20 30 00 ef ee fe ff  ef ee fe ff ef ee fe ff  |n 0.............|
000000d0  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
000000e0  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
000000f0  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000100  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000110  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000120  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000130  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000140  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000150  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000160  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000170  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000180  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000190  ef ee fe ff ef ee fe ff  3a 00 00 00 3c 00 00 00  |........:...<...|
000001a0  00 00 00 00 00 00 00 00  fb ce f5 0a cf a0 a3 7b  |...............{|
000001b0  00 00 00 00 3b 59 2e 1f  97 8b 26 74 ef ee 80 01  |....;Y....&t....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 27 79 1a 06 00 00  |......?...'y....|
000001d0  c1 ff 0f fe ff ff 66 79  1a 06 db d2 1d 34 00 00  |......fy.....4..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

umount: /host: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

---

### Post by eyadhafez on 2010-01-02
Please guys i need your help!!!!!

---

### Post by eyadhafez on 2010-01-05
hello anyone there ?????


some help to the new ubuntu user please..........

---

### Post by dinamic1 on 2010-01-15
LVPM has been tested on installs created by Wubi 8.04, Wubi 7.10,  Wubi 7.04, and Lubi 7.04.

what Wubi version have you used?


:(

---

