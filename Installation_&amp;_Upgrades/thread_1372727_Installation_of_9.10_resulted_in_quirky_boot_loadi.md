---
title: "Installation of 9.10 resulted in quirky boot loading"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by cAlpha on 2010-01-04
So, the quick and dirty:  I installed Ubuntu 8.04 early last year and stuck with it until some of the bugs had been worked out of 9.10, after which I did a clean installation of it.  

During installation, I remember being asked about keeping a back-up for my previous 8.04 installation and I selected yes (figuring better safe than sorry).  So, despite uninstalling 8.04 within Vista before installing 9.10, I now (oddly) am able to boot into either Vista, Ubuntu 8.04 OR Ubuntu 9.10.  

Aesthetics aside, I don't much care that 8.04 is still present.  Installing 9.10 complicated the bejesus out of my boot process though.  It currently boots as such:

First screen options:
Ubuntu 8.04 
Ubuntu 8.04 (safe)
Vista

Clicking on Vista gives:
Ubuntu 
Vista

Clicking on Ubuntu THEN gives the screen I'd like to pop up initially 
Ubuntu 9.10 
Ubuntu 9.10 (safe)
Ubuntu 8.04
Ubuntu 8.04 (safe)
Vista

It's like some kind of terribly uninteresting Choose Your Own Adventure book.

Can anyone help me to get my bootloader in a slightly more user-friendly form?

---

### Post by presence1960 on 2010-01-04
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by cAlpha on 2010-01-05
Thanks for your reply, presence.  

Contents pasted below:
```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2             145,408    21,116,927    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,116,928   129,142,727   108,025,800   7 HPFS/NTFS
/dev/sda4         129,146,535   156,296,384    27,149,850   5 Extended
/dev/sda5         129,146,661   139,412,069    10,265,409   7 HPFS/NTFS
/dev/sda6         139,412,133   155,477,069    16,064,937  83 Linux
/dev/sda7         155,477,133   156,296,384       819,252  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0716" TYPE="vfat" 
sda2: UUID="C8B2A09FB2A0938A" LABEL="RECOVERY" TYPE="ntfs" 
sda3: UUID="52A2A3C3A2A3A9C5" LABEL="OS" TYPE="ntfs" 
sda3/Wubi: UUID="7c84d0e5-064a-436f-8c7a-bada9b98270d" TYPE="ext4" 
sda5: UUID="166540D27756A805" LABEL="File Share" TYPE="ntfs" 
sda6: UUID="dda8c9c4-b665-44ad-82d2-e94f93c25e7c" SEC_TYPE="ext2" TYPE="ext3" 
sda7: UUID="09dbc09b-def3-4fb6-8b25-ae9c48c3be74" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
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


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 52a2a3c3a2a3a9c5
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 52a2a3c3a2a3a9c5
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 52a2a3c3a2a3a9c5
	chainloader +1
}
menuentry "Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set dda8c9c4-b665-44ad-82d2-e94f93c25e7c
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro quiet splash
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set dda8c9c4-b665-44ad-82d2-e94f93c25e7c
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro single
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 8.04.2, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set dda8c9c4-b665-44ad-82d2-e94f93c25e7c
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

/dev/sda5 /media/File\040Share ntfs defaults 0 0
#/dev/sda3 /media/OS ntfs defaults 0 0

================= sda3/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)
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


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=09dbc09b-def3-4fb6-8b25-ae9c48c3be74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3	/media/OS ntfs-3g defaults,locale=en_US.utf8 0 0
#UUID=52A2A3C3A2A3A9C5  /media/OS ntfs-3g defaults,locale=en_US.utf8 0 0 
/dev/sda5	/media/File\040Share ntfs-3g defaults,locale=en_US.utf8 0 0

=================== sda6: Location of files loaded by Grub: ===================


  71.3GB: boot/grub/menu.lst
  71.3GB: boot/grub/stage2
  71.3GB: boot/initrd.img-2.6.24-23-generic
  71.3GB: boot/initrd.img-2.6.24-23-generic.bak
  71.3GB: boot/vmlinuz-2.6.24-23-generic
  71.3GB: initrd.img
  71.3GB: vmlinuz
```

---

### Post by presence1960 on 2010-01-05
> **cAlpha said:**
> Thanks for your reply, presence.  

Contents pasted below:
```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2             145,408    21,116,927    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,116,928   129,142,727   108,025,800   7 HPFS/NTFS
/dev/sda4         129,146,535   156,296,384    27,149,850   5 Extended
/dev/sda5         129,146,661   139,412,069    10,265,409   7 HPFS/NTFS
/dev/sda6         139,412,133   155,477,069    16,064,937  83 Linux
/dev/sda7         155,477,133   156,296,384       819,252  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0716" TYPE="vfat" 
sda2: UUID="C8B2A09FB2A0938A" LABEL="RECOVERY" TYPE="ntfs" 
sda3: UUID="52A2A3C3A2A3A9C5" LABEL="OS" TYPE="ntfs" 
sda3/Wubi: UUID="7c84d0e5-064a-436f-8c7a-bada9b98270d" TYPE="ext4" 
sda5: UUID="166540D27756A805" LABEL="File Share" TYPE="ntfs" 
sda6: UUID="dda8c9c4-b665-44ad-82d2-e94f93c25e7c" SEC_TYPE="ext2" TYPE="ext3" 
sda7: UUID="09dbc09b-def3-4fb6-8b25-ae9c48c3be74" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
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


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 52a2a3c3a2a3a9c5
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 52a2a3c3a2a3a9c5
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 52a2a3c3a2a3a9c5
	chainloader +1
}
menuentry "Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set dda8c9c4-b665-44ad-82d2-e94f93c25e7c
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro quiet splash
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set dda8c9c4-b665-44ad-82d2-e94f93c25e7c
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro single
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 8.04.2, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set dda8c9c4-b665-44ad-82d2-e94f93c25e7c
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

/dev/sda5 /media/File\040Share ntfs defaults 0 0
#/dev/sda3 /media/OS ntfs defaults 0 0

================= sda3/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)
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


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=dda8c9c4-b665-44ad-82d2-e94f93c25e7c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=09dbc09b-def3-4fb6-8b25-ae9c48c3be74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3	/media/OS ntfs-3g defaults,locale=en_US.utf8 0 0
#UUID=52A2A3C3A2A3A9C5  /media/OS ntfs-3g defaults,locale=en_US.utf8 0 0 
/dev/sda5	/media/File\040Share ntfs-3g defaults,locale=en_US.utf8 0 0

=================== sda6: Location of files loaded by Grub: ===================


  71.3GB: boot/grub/menu.lst
  71.3GB: boot/grub/stage2
  71.3GB: boot/initrd.img-2.6.24-23-generic
  71.3GB: boot/initrd.img-2.6.24-23-generic.bak
  71.3GB: boot/vmlinuz-2.6.24-23-generic
  71.3GB: initrd.img
  71.3GB: vmlinuz
```
```
[COLOR="Red"]sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab[/COLOR]
```

Unfortunately you did not do a clean install of 9.10 to it's own partition, see above! You installed 9.10 via wubi. That's why you must choose windows to access 9.10. If you had done a clean install to a dedicated partition 9.10 would have it's own entry in the GRUB menu.

Wubi installs are booted from the windows bootloader only!

---

### Post by cAlpha on 2010-01-05
OK, what does that say about the difficulties with the way the GRUB menus are configured?  And more importantly, how do I adjust things to have the boot loader load as I'd like?    

As an aside, I ran the 9.10 installation CD from within Vista and installed onto the newly empty (after uninstalling 8.04) partition.  Should I have gone about this differently?

---

### Post by garvinrick4 on 2010-01-05
Boot into your Windows install.   At command line  "bcdedit" without qoutes.

find the entry with wubildr.mbr in it and there will be a { number in here }


command line:  bcdedit/delete { put # in here } hit enter.   

Done: You will have normal linux grub boot now. 

WUBI is attached to windows bcd now it will be gone. Does not matter how it happened, it just
did, we will never know.

---

### Post by presence1960 on 2010-01-05
> **cAlpha said:**
> OK, what does that say about the difficulties with the way the GRUB menus are configured?  And more importantly, how do I adjust things to have the boot loader load as I'd like?    

As an aside, I ran the 9.10 installation CD from within Vista and installed onto the newly empty (after uninstalling 8.04) partition.  Should I have gone about this differently?

Unfortunately since you installed 9.10 inside windows you must first access windows from the GRUB menu at startup. This will pass to the windows bootloader which will give you the option of windows or Ubuntu. When you choose Ubuntu then you are given the 9.10 option. See here:

```
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    [COLOR="Red"]Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk[/COLOR]

```

If you had installed to a dedicated partition like Hardy in sda6 you would not have to access 9.10 from windows.

Sorry, but that is how wubi works. Personally I don't like wubi. One of the reasons is people tend to think it is meant to be a permanent install. It is only meant to be a trial for those unwilling to partition their hard disk until they are sure they like Ubuntu. But you already have your disk partitioned so you should have installed by booting the live CD amd doing a full install to a partition like Hardy 8.04. There is no way to do what you want with the current setup.

See here, the answer to the second question from someone who developed wubi:  [http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) NOTE the first sentence: The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user ***_[COLOR="Red"]try[/COLOR]_*** Ubuntu without risking any data loss due to disk formatting or partitioning.

---

### Post by presence1960 on 2010-01-05
> **garvinrick4 said:**
> Boot into your Windows install.   At command line  "bcdedit" without qoutes.

find the entry with wubildr.mbr in it and there will be a { number in here }


command line:  bcdedit/delete { put # in here } hit enter.   

Done: You will have normal linux grub boot now. 

WUBI is attached to windows bcd now it will be gone. Does not matter how it happened, it just
did, we will never know.

If you look at the script output he posted 9.10 IS installed within windows on sda3. It is not a dedicated install to it's own partition. Hardy 8.04 is on sda6 which is a dedicated install to it's own partition and is the OS that boots directly from GRUB. If he removes the wubilder entry in bcdedit how do you propose he boot that wubi 9.10 install?

---

### Post by cAlpha on 2010-01-05
> **garvinrick4 said:**
> Boot into your Windows install.   At command line  "bcdedit" without qoutes.

find the entry with wubildr.mbr in it and there will be a { number in here }


command line:  bcdedit/delete { put # in here } hit enter.   

Done: You will have normal linux grub boot now. 

WUBI is attached to windows bcd now it will be gone. Does not matter how it happened, it just
did, we will never know.

Seems easy enough, but will I still be able to run Vista doing that?  Can you explain how booting with work/look after doing that?  



> **presence1960 said:**
> 
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) NOTE the first sentence: The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user ***_[COLOR="Red"]try[/COLOR]_*** Ubuntu without risking any data loss due to disk formatting or partitioning.

AH!  I wasn't aware of that.  I thought installing from within Windows via wubi.exe was merely an alternative, and an equivalent at that, to booting and installing from the disk.  

Within the last hour, I've booted into 9.10 and I've run into yet another oddity (the splash screen remains in place of the wallpaper and cairo-dock loads, but nothing else, not even task bars).  So perhaps I'll just again try a fresh install, this time the proper way.  :)

---

### Post by presence1960 on 2010-01-05
> **cAlpha said:**
> Seems easy enough, but will I still be able to run Vista doing that?  Can you explain how booting with work/look after doing that?  





AH!  I wasn't aware of that.  I thought installing from within Windows via wubi.exe was merely an alternative, and an equivalent at that, to booting and installing from the disk.  

Within the last hour, I've booted into 9.10 and I've run into yet another oddity (the splash screen remains in place of the wallpaper and cairo-dock loads, but nothing else, not even task bars).  So perhaps I'll just again try a fresh install, this time the proper way.  :)

That is what I would do or live with the menu because 9.10 is inside windows and can only boot from windows bootloader. If you do what garvinrick suggests your 9.10 will become unbootable.

---

### Post by garvinrick4 on 2010-01-05
There have been many a user of WUBI who have deleted through add and remove programs in Windows instead of uninstall in WUBI folder. Leaves the WUBi attached to Windows menu entrie
in bcd. There is also a entry for Windows 7 in bcd. Not deleting that one just the WUBI entry.

I have done this myself. Look in the results of "bcdedit" without quotes and see for yourself.
I would not tell anyone to do anything I have not done myself already.

If there is no entry for WUBI in windows command line. "bcdedit then it would not be a problem would it. 

Have a nice day.

---

### Post by cAlpha on 2010-01-05
> **presence1960 said:**
> That is what I would do or live with the menu because 9.10 is inside windows and can only boot from windows bootloader. If you do what garvinrick suggests your 9.10 will become unbootable.


> **garvinrick4 said:**
> There have been many a user of WUBI who have deleted through add and remove programs in Windows instead of uninstall in WUBI folder. Leaves the WUBi attached to Windows menu entrie
in bcd. There is also a entry for Windows 7 in bcd. Not deleting that one just the WUBI entry.

I have done this myself. Look in the results of "bcdedit" without quotes and see for yourself.
I would not tell anyone to do anything I have not done myself already.

If there is no entry for WUBI in windows command line. "bcdedit then it would not be a problem would it. 

Have a nice day.

Makes sense.  I figure I'll probably just do a fresh install to be safe.  


Thanks for your help, guys.

Oh, and just FYI, the glitch I was encountering upon startup--I changed my fstab file back to the original (removing "cairo-dock -o" I'd inserted to start cairo-dock at start up) and the problem was solved. *shrug*  Whatever works.    :)

---

### Post by garvinrick4 on 2010-01-05
It is called Real-mode Boot Sector in the "bcdedit" withour quotes of 7 or Vista.
The last entry BELOW the entry that says WINDOWS BOOT LOADER.
Has nothing to do with the Windows boot it is put in by the Ubuntu Wubi.
path \ubuntu\winboot\wubildr.mbr
description Ubuntu
 
Will have an identifier { number in here}
 
bcdedit/delete { identifier # in here} 
 
 
 
Windows boot loader and Windows boot manager have there own identifier #'s

---

### Post by presence1960 on 2010-01-05
> **garvinrick4 said:**
> There have been many a user of WUBI who have deleted through add and remove programs in Windows instead of uninstall in WUBI folder. Leaves the WUBi attached to Windows menu entrie
in bcd. There is also a entry for Windows 7 in bcd. Not deleting that one just the WUBI entry.

I have done this myself. Look in the results of "bcdedit" without quotes and see for yourself.
I would not tell anyone to do anything I have not done myself already.

If there is no entry for WUBI in windows command line. "bcdedit then it would not be a problem would it. 

Have a nice day.

If you take the time to read what the OP wanted to do you would see your suggestion is not good at the time it was made. He did not originally want to delete wubi but rather fix the way 9.10 boots. The OP did not realize that wubi only works through the windows bootloader. Your suggestion came before the OP's decision to remove wubi install and do a full 9.10 install to a partition. At that point in time your suggestion would have left the OP with an unbootable wubi installation.

Now that the OP has decided to remove wubi and do a full install of 9.10 your suggestion is one of the steps necessary to remove the wubi entry from the windows bootloader.

I think if you reread the thread you will see what I am talking about.

---

