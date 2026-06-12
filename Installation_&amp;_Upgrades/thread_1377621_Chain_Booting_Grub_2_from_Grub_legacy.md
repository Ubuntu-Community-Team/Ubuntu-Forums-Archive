---
title: "Chain Booting Grub 2 from Grub legacy"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by And6ate9 on 2010-01-10
Having trouble booting karma grub2 from my grub legacy partition. Anyone Know the proper way to do this?

thanks.

---

### Post by kansasnoob on 2010-01-10
Need much more info. The best thing would be to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by And6ate9 on 2010-01-11
Once again I am trying to boot into grub2 from grub1

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda2 and looks 
                       at sector 773371880 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 400358368 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 7 Gloria - x64 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda11 and 
                       looks at sector 851213246 of the same hard drive for 
                       the stage2 file, but no stage2 files can be found at 
                       this location.
    Operating System:  Debian GNU/Linux 4.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 740387655.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28b128b1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   307,194,929   307,194,867   7 HPFS/NTFS
/dev/sda2         307,194,930   315,484,469     8,289,540  83 Linux
/dev/sda3         315,484,470   349,076,384    33,591,915  82 Linux swap / Solaris
/dev/sda4         349,076,385   967,466,429   618,390,045   5 Extended
/dev/sda5         349,076,448   412,051,184    62,974,737  83 Linux
/dev/sda6         412,051,248   518,353,289   106,302,042  83 Linux
/dev/sda7         518,353,353   581,328,089    62,974,737  83 Linux
/dev/sda8         581,328,153   687,935,429   106,607,277  83 Linux
/dev/sda9         687,935,493   719,471,024    31,535,532  83 Linux
/dev/sda10        719,471,088   751,006,619    31,535,532  83 Linux
/dev/sda11        751,006,683   782,542,214    31,535,532  83 Linux
/dev/sda12        782,542,278   814,077,809    31,535,532  83 Linux
/dev/sda13        814,077,873   967,466,429   153,388,557  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00039b08

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   740,387,654   740,387,592   7 HPFS/NTFS
/dev/sdb2         740,387,655   952,188,614   211,800,960   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2055 MB, 2055021056 bytes
16 heads, 63 sectors/track, 3981 cylinders, total 4013713 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     4,013,712     4,013,650   6 FAT16


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="8C8CFC9D8CFC834E" TYPE="ntfs" 
sda2: LABEL="grub_boot" UUID="f7449e62-0212-44ae-83ea-1150a1016368" SEC_TYPE="ext2" TYPE="ext3" 
sda3: TYPE="swap" 
sda5: LABEL="a5_Ubuntu_LTS" UUID="e35f50ab-aa4f-4748-bb4b-53c87b4a30f8" SEC_TYPE="ext2" TYPE="ext3" 
sda6: LABEL="a6_Ubuntu_home" UUID="e49222ed-6c0a-4a12-9547-5ecde2d10f9b" SEC_TYPE="ext2" TYPE="ext3" 
sda7: LABEL="a7_Mint_STR" UUID="92bd4240-e026-4abc-a321-fd97fa576cc9" SEC_TYPE="ext2" TYPE="ext3" 
sda8: LABEL="a8_MInt_home" UUID="771ff5d5-355a-44d9-9525-9e37a8aa2250" SEC_TYPE="ext2" TYPE="ext3" 
sda9: UUID="3eddeb5f-755e-43bc-8099-26661f2abcfa" TYPE="ext4" 
sda10: UUID="3e4802cd-5e92-4038-8ad5-3517e652e2bd" TYPE="ext4" 
sda11: LABEL="b11_64studio" UUID="d46a0831-3092-4b60-96c8-3dbc09f8a793" SEC_TYPE="ext2" TYPE="ext3" 
sda12: LABEL="b12_64studio_hom" UUID="8d63cd02-49cf-4149-b40d-13d7de4573e1" SEC_TYPE="ext2" TYPE="ext3" 
sda13: LABEL="b13_MyExt3Share" UUID="7239ccf1-4ad6-4288-b1bc-d9dfd7868684" SEC_TYPE="ext2" TYPE="ext3" 
sdb1: UUID="2072FC9511559F15" LABEL="zBackups" TYPE="ntfs" 
sdb2: LABEL="vfatshare" UUID="4A50-7437" TYPE="vfat" 
sdc1: SEC_TYPE="msdos" LABEL="HYENA" UUID="6011-F4ED" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/HYENA type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/zBackups type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


============================= sda2/grub/menu.lst: =============================

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
timeout		20

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
# kopt=root=UUID=8db335f4-425b-4614-bf58-ef588aa44755 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
title		Microsoft Windows 7 Ultimate
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title        Ubuntu - LTS
configfile   (hd0,4)/boot/grub/menu.lst

title        Mint - STR
configfile   (hd0,6)/boot/grub/menu.lst

title=Mint - STR test
root (hd0,6)
kernel /boot/grub/core.img

title Mnit chainloader test
root (hd0,6)
chainloader +1

title        Ubuntu - STR
configfile   (hd0,8)/boot/grub/menu.lst

title=Ubuntu - STR test
root (hd0,8)
kernel /boot/grub/core.img

title Ubuntu Chainloader test /dev/sda9
root (hd0,8)
chainloader +1

title        Art Distro 
configfile   (hd0,10)/boot/grub/menu.lst

# end configfile

=================== sda2: Location of files loaded by Grub: ===================


 157.6GB: grub/menu.lst
 157.6GB: grub/stage2

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e35f50ab-aa4f-4748-bb4b-53c87b4a30f8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e35f50ab-aa4f-4748-bb4b-53c87b4a30f8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e35f50ab-aa4f-4748-bb4b-53c87b4a30f8 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
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
chainloader	+1



=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
/dev/sda5	/	        ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
/dev/sda6       /home           ext3    relatime        0       2
# /dev/sda3
/dev/sda3	none	        swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8  0       0
# /dev/sda2 
/dev/sda2 	/media/grubboot ext3   defaults,relatime  0       2
# /dev/sdb1 
/dev/sdb1       /home/raven/zBackups ntfs-3g unmask=000,uid=1000,gid=1000,auto,rw,users,locale=en_US.utf8 0 0




=================== sda5: Location of files loaded by Grub: ===================


 204.9GB: boot/grub/menu.lst
 204.9GB: boot/grub/stage2
 204.9GB: boot/initrd.img-2.6.24-23-generic
 204.9GB: boot/initrd.img-2.6.24-23-generic.bak
 204.9GB: boot/vmlinuz-2.6.24-23-generic
 204.9GB: initrd.img
 204.9GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
##      altoptions=(single-user) single
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

title		Linux Mint 7 Gloria x64, kernel 2.6.28-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Linux Mint 7 Gloria x64, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Linux Mint 7 Gloria x64, memtest86+
root		(hd0,6)
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
makeactive
chainloader	+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=92bd4240-e026-4abc-a321-fd97fa576cc9 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=771ff5d5-355a-44d9-9525-9e37a8aa2250 /home           ext3    relatime        0       2
/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sda2 
/dev/sda2 	/mnt/zGrubboot ext3   defaults,relatime  0      2
# /dev/sda13 
/dev/sda13      /media/zExt3share ext3  defaults  0      2
# /dev/sdb1 
/dev/sdb1       /media/zBackups ntfs-3g unmask=000,uid=1000,gid=1000,auto,rw,users,locale=en_US.utf8 0 0
#/dev/sdb2
/dev/sdb2 	/media/zVfatshare vfat umask=000,uid=1000,gid=1000,auto,rw,users 0 0
# This enables usb in Virtualbox in Jaunty 9.04 and above
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0





=================== sda7: Location of files loaded by Grub: ===================


 284.1GB: boot/grub/menu.lst
 276.8GB: boot/grub/stage2
 276.8GB: boot/initrd.img-2.6.28-11-generic
 276.9GB: boot/initrd.img-2.6.28-15-generic
 276.8GB: boot/vmlinuz-2.6.28-11-generic
 276.8GB: boot/vmlinuz-2.6.28-15-generic
 276.9GB: initrd.img
 276.8GB: initrd.img.old
 276.8GB: vmlinuz
 276.8GB: vmlinuz.old

========================== sda11/boot/grub/menu.lst: ==========================

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
timeout 	5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda11 ro vga=791 splash=silent

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,10)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

## ## End Default Options ##

title		64studio, kernel 2.6.21-1-multimedia-amd64
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/sda11 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

title		64studio, kernel 2.6.21-1-multimedia-amd64 (single-user mode)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/sda11 ro vga=791 splash=silent single
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

title		64studio, kernel memtest86
root		(hd0,10)
kernel		/boot/memtest86.bin

title		64studio, kernel memtest86+
root		(hd0,10)
kernel		/boot/memtest86+.bin

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
chainloader	+1


=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
/dev/sda11      /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda12
/dev/sda12      /home           ext3    defaults        0       2
# /dev/sda3
/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/sda2 
/dev/sda2 	/media/grub_boot ext3   defaults,relatime  0       2
# dev/sdb1 
/dev/sdb1       /home/raven/zBackups ntfs-3g unmask=000,uid=1000,gid=1000,auto,rw,users,locale=en_US.utf8 0 0




=================== sda11: Location of files loaded by Grub: ===================


 394.4GB: boot/grub/menu.lst
 394.4GB: boot/grub/stage2
 394.2GB: boot/initrd.img-2.6.21-1-multimedia-amd64
 394.2GB: boot/initrd.img-2.6.21-1-multimedia-amd64.bak
 394.2GB: boot/vmlinuz-2.6.21-1-multimedia-amd64
 394.2GB: initrd.img
 394.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

---

### Post by mechro on 2010-01-11
Thanks for the boot script info but there's too much info in there for me to compute. Can you narrow it down and tell me which is your Grub Legacy partition and which is the Karmic partition?

You have some configfile commands and some chainloader+1 commands in your menu.lst's. I would assume the chainloader+1 command would work best to go from Grub Legacy to Grub2 boot.

---

### Post by And6ate9 on 2010-01-11
Sorry about that.
Grub legacy is on sda2 or hd0,1
Ubuntu karmic is on sda9 or hd0,10 I guess it would be.

I have the chainloader for win7 which works
and I tried to put in a test chainloader for karmic but it didn't seem to work. I just got a black screen with a cursor.

---

### Post by mechro on 2010-01-11
Your test chainloader should work so it looks like there's a problem with your Karmic and/or Grub2 installation.

Try reinstalling Grub2 in sda9...

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by And6ate9 on 2010-01-13
ok Guys thanks. I just needed to reinstall the grub2 boot loader to sda9.  I didn't quit see how to do that on that grub page so I just reinstalled the karmic and it's fine now.

Last thing. Where can I get info on making a dedicated grub2 boot drive?

---

### Post by mechro on 2010-01-13
I'm sticking with a Legacy dedicated boot drive for now. Herman may be able to help you with setting one up for Grub2...

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by And6ate9 on 2010-01-13
You know you are probably right. I think I will do the same but just follow the grub2 updates.

Thanks

---

