---
title: "How to triple boot ?"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2009-12-05
I have a dual booting machine with

sda1: Windows XP
sda2: FAT32 

sdb1: Ubuntu 8.04, /
sdb2: Ubuntu 8.04, /home
sdb3: Ubuntu 8.04, /usr/local
sdb4: Ubuntu 8.04, swap  (logic partition)

Now I'd like to install 9.10 on a new primary partion on sdb. I did so and chose installing bootloader on sdb1 in the last step of configuration of installation. Now when I restart, I only see Windows XP and Ubuntu 8.04 as before. How do I get 9.10 in the list at booting ?

---

### Post by some-what-Gnu-2-networks on 2009-12-05
Are You sure that "sbd" is bootable? If it is select it from your mobo's boot options

---

### Post by presence1960 on 2009-12-05
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Physicist on 2009-12-05
Here is the RESULTS.txt
```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 208441746 on boot drive #1 for 
                       core.img and on partition #4 for /boot/grub.
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd956d956

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   286,712,054   184,313,745   f W95 Ext d (LBA)
/dev/sda5         102,398,373   286,712,054   184,313,682   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *    125,949,600   145,484,639    19,535,040  83 Linux
/dev/sdb2             112,455   125,949,599   125,837,145  83 Linux
/dev/sdb3         145,484,640   207,977,489    62,492,850   5 Extended
/dev/sdb5         204,073,758   207,977,489     3,903,732  82 Linux swap / Solaris
/dev/sdb6         145,484,766   204,073,694    58,588,929  83 Linux
/dev/sdb4         207,977,490   237,280,049    29,302,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AEBCB619BCB5DC51" LABEL="win" TYPE="ntfs" 
/dev/sda5: UUID="BC5C68C75C687DD0" LABEL="Data" TYPE="ntfs" 
/dev/sdb1: LABEL="/" UUID="75fc84de-bcc2-4ba5-9126-a9e279719c8f" TYPE="ext3" 
/dev/sdb2: LABEL="/home" UUID="491ab5ad-fd7f-4d42-8890-7d7f71a6fc00" TYPE="ext3" 
/dev/sdb4: UUID="c4f6e795-58de-4234-9aac-0a1f50fe3439" TYPE="ext4" 
/dev/sdb5: TYPE="swap" UUID="068b8772-4433-4b03-a125-f428d4aa306e" 
/dev/sdb6: LABEL="usrbin" UUID="b785e524-c068-441a-8a15-26eefe9a1c67" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-26-generic/volatile type tmpfs (rw)
/dev/sdb2 on /home type ext3 (rw,relatime)
/dev/sdb6 on /usr/local type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/meng/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=meng)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root




=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=491ab5ad-fd7f-4d42-8890-7d7f71a6fc00 /home           ext3    relatime        0       2
# /dev/sdb6
UUID=b785e524-c068-441a-8a15-26eefe9a1c67 /usr/local      ext3    relatime        0       2
# /dev/sdb5
UUID=068b8772-4433-4b03-a125-f428d4aa306e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  67.3GB: boot/grub/menu.lst
  67.3GB: boot/grub/stage2
  67.4GB: boot/initrd.img-2.6.24-26-generic
  67.4GB: boot/initrd.img-2.6.24-26-generic.bak
  67.3GB: boot/vmlinuz-2.6.24-26-generic
  67.4GB: initrd.img
  67.3GB: vmlinuz


```


> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by presence1960 on 2009-12-05
> **Physicist said:**
> Here is the RESULTS.txt
```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 208441746 on boot drive #1 for 
                       core.img and on partition #4 for /boot/grub.
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd956d956

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   286,712,054   184,313,745   f W95 Ext d (LBA)
/dev/sda5         102,398,373   286,712,054   184,313,682   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *    125,949,600   145,484,639    19,535,040  83 Linux
/dev/sdb2             112,455   125,949,599   125,837,145  83 Linux
/dev/sdb3         145,484,640   207,977,489    62,492,850   5 Extended
/dev/sdb5         204,073,758   207,977,489     3,903,732  82 Linux swap / Solaris
/dev/sdb6         145,484,766   204,073,694    58,588,929  83 Linux
/dev/sdb4         207,977,490   237,280,049    29,302,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AEBCB619BCB5DC51" LABEL="win" TYPE="ntfs" 
/dev/sda5: UUID="BC5C68C75C687DD0" LABEL="Data" TYPE="ntfs" 
/dev/sdb1: LABEL="/" UUID="75fc84de-bcc2-4ba5-9126-a9e279719c8f" TYPE="ext3" 
/dev/sdb2: LABEL="/home" UUID="491ab5ad-fd7f-4d42-8890-7d7f71a6fc00" TYPE="ext3" 
/dev/sdb4: UUID="c4f6e795-58de-4234-9aac-0a1f50fe3439" TYPE="ext4" 
/dev/sdb5: TYPE="swap" UUID="068b8772-4433-4b03-a125-f428d4aa306e" 
/dev/sdb6: LABEL="usrbin" UUID="b785e524-c068-441a-8a15-26eefe9a1c67" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-26-generic/volatile type tmpfs (rw)
/dev/sdb2 on /home type ext3 (rw,relatime)
/dev/sdb6 on /usr/local type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/meng/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=meng)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root




=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=491ab5ad-fd7f-4d42-8890-7d7f71a6fc00 /home           ext3    relatime        0       2
# /dev/sdb6
UUID=b785e524-c068-441a-8a15-26eefe9a1c67 /usr/local      ext3    relatime        0       2
# /dev/sdb5
UUID=068b8772-4433-4b03-a125-f428d4aa306e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  67.3GB: boot/grub/menu.lst
  67.3GB: boot/grub/stage2
  67.4GB: boot/initrd.img-2.6.24-26-generic
  67.4GB: boot/initrd.img-2.6.24-26-generic.bak
  67.3GB: boot/vmlinuz-2.6.24-26-generic
  67.4GB: initrd.img
  67.3GB: vmlinuz


```
I am assuming your 9.10 went on sdb4, which is a problem because it is saying unknown filesystem for that partition.

You also installed the GRUB 1.97 (9.10) to the boot sector of your hardy partition.

You have no partition for 9.10 nor any boot files for 9.10

You want to install GRUB 2 to /dev/sdb not sdb1. Then after installation of 9.10 go into BIOS and make sdb first hard disk to boot so GRUB 2 takes over on boot. When you get to the Ready to Install window of the installation click the Advanced button and select /dev/sdb to install GRUB to. see pic below.

---

### Post by Physicist on 2009-12-05
> **presence1960 said:**
> I am assuming your 9.10 went on sdb4, which is a problem because it is saying unknown filesystem for that partition.

You also installed the GRUB 1.97 (9.10) to the boot sector of your hardy partition.


Do I need to try to remove this ?

> **presence1960 said:**
> 
You have no partition for 9.10 nor any boot files for 9.10

Isn't db4 the partition ? I think I have the boot files for 9.10 incorrectly installed into sdb1 where where 8.04's boot files located.

> **presence1960 said:**
> 
You want to install GRUB 2 to /dev/sdb not sdb1. Then after installation of 9.10 go into BIOS and make sdb first hard disk to boot so GRUB 2 takes over on boot. When you get to the Ready to Install window of the installation click the Advanced button and select /dev/sdb to install GRUB to. see pic below.

In the Boot Sequence option of my BIOS configuration, I only see

1. Onboard or USB CD-ROM Drive
2. Onboard SATA Hard Drive
Onboard IDE Hard Drive (not present)
...
3. USB Device (not present)


There doesn't seem to be a way to boot from sdb instead of sda. How to configure this ? Also, I'd like to see 8.04, WinXP, and 9.10 all listed at booting time.

---

### Post by presence1960 on 2009-12-06
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 208441746 on boot drive #1 for 
                       core.img and on partition #4 for /boot/grub.
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

[COLOR="Red"]sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'[/COLOR]
```

The red above is your main problem right now. For some reason the Live Cd can't mount sdb4. You did boot the 9.10 Live CD when you ran the script, correct?

---

### Post by Physicist on 2009-12-06
> **presence1960 said:**
> ```
============================= Boot Info Summary: ==============================


[COLOR="Red"]sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'[/COLOR]
```

The red above is your main problem right now. For some reason the Live Cd can't mount sdb4. You did boot the 9.10 Live CD when you ran the script, correct?

I booted 8.04 and generated last RESULTS.txt. I now realize I misunderstood your comment. I just regenerated RESULTS.txt booting from a Ubuntu live USB built by [UNetbootin]("http://en.wikipedia.org/wiki/UNetbootin"):

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #4 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 208441746 on boot drive #1 for 
                       core.img and on partition #4 for /boot/grub.
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd956d956

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   286,712,054   184,313,745   f W95 Ext d (LBA)
/dev/sda5         102,398,373   286,712,054   184,313,682   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *    125,949,600   145,484,639    19,535,040  83 Linux
/dev/sdb2             112,455   125,949,599   125,837,145  83 Linux
/dev/sdb3         145,484,640   207,977,489    62,492,850   5 Extended
/dev/sdb5         204,073,758   207,977,489     3,903,732  82 Linux swap / Solaris
/dev/sdb6         145,484,766   204,073,694    58,588,929  83 Linux
/dev/sdb4         207,977,490   237,280,049    29,302,560  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8127 MB, 8127512576 bytes
5 heads, 32 sectors/track, 99212 cylinders, total 15874048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064    15,874,047    15,865,984   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="AEBCB619BCB5DC51" LABEL="win" TYPE="ntfs" 
/dev/sda5: UUID="BC5C68C75C687DD0" LABEL="Data" TYPE="ntfs" 
/dev/sdb1: LABEL="/" UUID="75fc84de-bcc2-4ba5-9126-a9e279719c8f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: LABEL="/home" UUID="491ab5ad-fd7f-4d42-8890-7d7f71a6fc00" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="2d8e2706-a9ce-4b43-9262-47ff066a529f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="068b8772-4433-4b03-a125-f428d4aa306e" TYPE="swap" 
/dev/sdb6: LABEL="usrbin" UUID="b785e524-c068-441a-8a15-26eefe9a1c67" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="" UUID="E568-944D" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdc1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root




=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=491ab5ad-fd7f-4d42-8890-7d7f71a6fc00 /home           ext3    relatime        0       2
# /dev/sdb6
UUID=b785e524-c068-441a-8a15-26eefe9a1c67 /usr/local      ext3    relatime        0       2
# /dev/sdb5
UUID=068b8772-4433-4b03-a125-f428d4aa306e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  64.4GB: boot/grub/menu.lst
  64.4GB: boot/grub/stage2
  64.4GB: boot/initrd.img-2.6.24-26-generic
  64.4GB: boot/initrd.img-2.6.24-26-generic.bak
  64.4GB: boot/vmlinuz-2.6.24-26-generic
  64.4GB: initrd.img
  64.4GB: vmlinuz

=========================== sdb4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,4)
search --no-floppy --fs-uuid --set 2d8e2706-a9ce-4b43-9262-47ff066a529f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,4)
	search --no-floppy --fs-uuid --set 2d8e2706-a9ce-4b43-9262-47ff066a529f
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=2d8e2706-a9ce-4b43-9262-47ff066a529f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,4)
	search --no-floppy --fs-uuid --set 2d8e2706-a9ce-4b43-9262-47ff066a529f
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=2d8e2706-a9ce-4b43-9262-47ff066a529f ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aebcb619bcb5dc51
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 75fc84de-bcc2-4ba5-9126-a9e279719c8f
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro quiet splash
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 75fc84de-bcc2-4ba5-9126-a9e279719c8f
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro single
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 75fc84de-bcc2-4ba5-9126-a9e279719c8f
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb4 during installation
UUID=2d8e2706-a9ce-4b43-9262-47ff066a529f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=491ab5ad-fd7f-4d42-8890-7d7f71a6fc00 /home           ext3    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=068b8772-4433-4b03-a125-f428d4aa306e none            swap    sw              0       0

=================== sdb4: Location of files loaded by Grub: ===================


 106.4GB: boot/grub/grub.cfg
 106.4GB: boot/initrd.img-2.6.31-16-generic-pae
 106.4GB: boot/vmlinuz-2.6.31-16-generic-pae
 106.4GB: initrd.img
 106.4GB: vmlinuz

```

---

### Post by louieb on 2009-12-06
Try adding this to your 8.04 menu.lst

```
title Ubuntu karmic
root (hd1,0)
chainloader +1
```

The version of GRUB that comes with Hardy does not have ext4 support. By chainloading you can get around that.

---

### Post by Physicist on 2009-12-06
Does it matter where I put it in my menu.lst ? For example, is the following OK ?
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title Ubuntu karmic
root (hd1,0)
chainloader +1

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=75fc84de-bcc2-4ba5-9126-a9e279719c8f ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

```


> **louieb said:**
> Try adding this to your 8.04 menu.lst

```
title Ubuntu karmic
root (hd1,0)
chainloader +1
```

The version of GRUB that comes with Hardy does not have ext4 support. By chainloading you can get around that.

---

### Post by louieb on 2009-12-06
Yes it matters. The way you have it now both it and the WIn XP entry are going to get deleted next time there is a kernel update. 

they need to go before the line 

```
### BEGIN AUTOMAGIC KERNELS LIST
```

or after the line
```
### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

