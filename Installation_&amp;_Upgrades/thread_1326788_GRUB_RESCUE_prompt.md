---
title: "GRUB RESCUE prompt"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by Tufty on 2009-11-14
Help, I'm so out of my depth here!
I have a descktop with two hard drives, one has windows XP on it the other has Ubuntu 9.? on it.
I've been using them fine for the past year or so, all I do is when the grub loader comes up I choose either Ubuntu or windows and away it goes.
In the past few days however someone talked me into trying to install Ubuntu 9.10 onto an 8gig USB stick.
After failing to get it to work other ways, I loaded the 9.10 CD and installed it from there having first partitioned the stick with 7.5gig main partition and .5 gig swap partition.
It took forever to install, but eventually finished sucessfully and asked me to re-boot.
When I rebooted I got a flashing line character in the top left of the screen (which you often do see for a very short while) but this just continued flashing with nothing happening.
Eventually I removed the stick to see if that would interupt it, but it had no effect at all.
So, giving up on the idea, I decided to reboot as before without the stick installed.
Now all I can get (unless I boot from the CD) is a GRUB RESCUE prompt.
I searched online to try to find what commands there might be to this command mode & how to use them, but I can't find anything that works.
'ls' works and shows my partitions, but when I try to use the 'root' command as someone suggested, I just get command not found.

All my data is on the windows system, I really need to be able to get it booting again.

HELP!

Dave.

---

### Post by presence1960 on 2009-11-14
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.34 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Tufty on 2009-11-15
Here you go!

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=3d0e1676-2bce-44d8-b575-da15573c41bf)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbeebbeeb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,372,284   234,372,222   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 27.3 GB, 27329101824 bytes
255 heads, 63 sectors/track, 3322 cylinders, total 53377152 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f2f2f2e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    53,014,499    53,014,437  83 Linux
/dev/sdb2          53,014,500    53,367,929       353,430   f W95 Ext d (LBA)
/dev/sdb5          53,014,563    53,367,929       353,367  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000be5f5

Partition  Boot         Start           End          Size  Id System

/dev/sdc1          14,795,865    15,791,894       996,030   5 Extended
/dev/sdc5          14,811,930    15,791,894       979,965  82 Linux swap / Solaris
/dev/sdc2                  63    14,795,864    14,795,802  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="E0B8293CB8291298" LABEL="115Gig" TYPE="ntfs" 
/dev/sdb1: UUID="3f1a642f-3baf-41ef-9ec0-ea5dd2338567" TYPE="ext3" 
/dev/sdb5: UUID="9ab2fc77-b4bb-4b1d-b4ac-60a00857302f" TYPE="swap" 
/dev/sdc2: UUID="3d0e1676-2bce-44d8-b575-da15573c41bf" TYPE="ext4" 
/dev/sdc5: UUID="fe0c8468-6646-4a68-8511-1f801ca30592" TYPE="swap" 

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
/dev/sda1 on /media/115Gig type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/3f1a642f-3baf-41ef-9ec0-ea5dd2338567 type ext3 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc2 on /media/3d0e1676-2bce-44d8-b575-da15573c41bf type ext4 (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=05

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


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
# kopt=root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3f1a642f-3baf-41ef-9ec0-ea5dd2338567

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		3f1a642f-3baf-41ef-9ec0-ea5dd2338567
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		3f1a642f-3baf-41ef-9ec0-ea5dd2338567
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		3f1a642f-3baf-41ef-9ec0-ea5dd2338567
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		3f1a642f-3baf-41ef-9ec0-ea5dd2338567
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		3f1a642f-3baf-41ef-9ec0-ea5dd2338567
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		3f1a642f-3baf-41ef-9ec0-ea5dd2338567
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3f1a642f-3baf-41ef-9ec0-ea5dd2338567
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		3f1a642f-3baf-41ef-9ec0-ea5dd2338567
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		3f1a642f-3baf-41ef-9ec0-ea5dd2338567
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=9ab2fc77-b4bb-4b1d-b4ac-60a00857302f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.28-13-generic
    .0GB: boot/initrd.img-2.6.28-14-generic
    .0GB: boot/initrd.img-2.6.28-15-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.28-13-generic
    .0GB: boot/vmlinuz-2.6.28-14-generic
    .0GB: boot/vmlinuz-2.6.28-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sdc2/boot/grub/grub.cfg: ===========================

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
set root=(hd2,2)
search --no-floppy --fs-uuid --set 3d0e1676-2bce-44d8-b575-da15573c41bf
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,2)
	search --no-floppy --fs-uuid --set 3d0e1676-2bce-44d8-b575-da15573c41bf
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3d0e1676-2bce-44d8-b575-da15573c41bf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,2)
	search --no-floppy --fs-uuid --set 3d0e1676-2bce-44d8-b575-da15573c41bf
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3d0e1676-2bce-44d8-b575-da15573c41bf ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
	search --no-floppy --fs-uuid --set e0b8293cb8291298
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3f1a642f-3baf-41ef-9ec0-ea5dd2338567
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3f1a642f-3baf-41ef-9ec0-ea5dd2338567
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3f1a642f-3baf-41ef-9ec0-ea5dd2338567
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3f1a642f-3baf-41ef-9ec0-ea5dd2338567
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro single
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3f1a642f-3baf-41ef-9ec0-ea5dd2338567
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro quiet splash
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3f1a642f-3baf-41ef-9ec0-ea5dd2338567
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro single
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3f1a642f-3baf-41ef-9ec0-ea5dd2338567
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3f1a642f-3baf-41ef-9ec0-ea5dd2338567
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=3f1a642f-3baf-41ef-9ec0-ea5dd2338567 ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3f1a642f-3baf-41ef-9ec0-ea5dd2338567
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc2 during installation
UUID=3d0e1676-2bce-44d8-b575-da15573c41bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=fe0c8468-6646-4a68-8511-1f801ca30592 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc2: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by Tufty on 2009-11-15
I'm happy for anyone else reading this to help if they can. I really need to get the PC booting again ASAP.

---

### Post by presence1960 on 2009-11-15
> **Tufty said:**
> I'm happy for anyone else reading this to help if they can. I really need to get the PC booting again ASAP.

Is your machine's BIOS capable of booting from USB? If so this is what I would do. I would restore Windows bootloader to MBR of sda, then I would put GRUB 0.97 on MBR of sdb & finally GRUB 1.97 on MBR of sdc (USB disk) this way that GRUB will take over when you boot from USB. I would also put GRUB 0.97 on MBR of sdb, then set sdb as first in the hard disk boot priority in BIOS. What that will accomplish is when you boot without the flash disk GRUB (0.97) from 9.04 will take over and you can boot Jaunty or Windows. If you boot with the flash disk GRUB 1.97 will take over and you can boot Karmic.

This how I would do it. Boot your XP install disk and do [this]("http://ubuntuforums.org/showthread.php?t=1014708"), following instructions for XP. Next boot the 9.04 Live CD/USB and choose "try Ubuntu without any changes", when the desktop loads open a terminal and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

When rebooting go into BIOS and set sdb (27GB) as first disk to boot in the hard disk boot order. Save changes to CMOS and continue booting into Ubuntu 9.04. Open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```

scroll down the bottom and change the windows entry to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

Note sda becomes (hd1) because you just switched it prior to second in hard disk boot order in BIOS!
Click Save at the top on the toolbar & close file. Reboot and see if you can boot into windows. If successful you can now put GRUB 1.97 on MBR of sdc.

see this: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

remember to have your flash disk with the Ubuntu install plugged in when you do this. You want to put GRUB 2 (1.97) on MBR of sdc.

sorry about the delay, I was out all day with my daughter.

---

### Post by Tufty on 2009-11-16
Oh wow... that looks soooo complicated & full of potential ways to destroy stuff...

Before I do anything, you asked me if I can boot from USB. 
That's the whole reason all of this has happened. I CAN boot from USB as long as there is a valid bootable USB device attached.
To prove this, when I set my bios to look as USB first, and put in an ordinary memory stick the machine halts with some message like 'no boot record on disk'
So I know I CAN boot from USB, but if you read my initial message, when I set UBUNTU up on the USB stick, it set it all up OK but the WOULDN"T boot from it. It just sat with a flashing character in the top left of the screen.

Can you confirm that you fully understand this & it's possible implications. It seems that my PC WILL boot from USB but for some reason it doesn't want to boot Ubuntu from USB.

Does that change all the above possible solutions?

---

### Post by TheHimself on 2009-11-16
Well, you should first back up your data and then make your machine bootable again. 

To do the first thing you need any OS that can be run from a removable media. If you have Ubuntu live CD, that's very easy. Just boot your computer with the live CD and when the menu shows up choose 
"Try Ubuntu without any changes ...". Do NOT choose "install Ubuntu...". When Ubuntu desktop shows up, attach a flash memory stick big enough for you data to back up.
Now using file manager go to windows partition then copy your files and paste them on the flash drive. 
(if windows partition doesn't show up in the file manager you have to mount the partition. It's name is sda1 or sda2, etc. Run
```

sudo mount /dev/sda1

```
in a terminal. Try different numbers 1,2,3 until your windows partition shows up.)

Then shot down the computer. You have your data at hand. 
The above instructions won't change anything on your hard drive. After you did this I'll tell you how to make the computer bootable.

---

### Post by presence1960 on 2009-11-16
> **Tufty said:**
> 
After failing to get it to work other ways, I loaded the 9.10 CD and installed it from there having first partitioned the stick with 7.5gig main partition and .5 gig swap partition.
It took forever to install, but eventually finished sucessfully and asked me to re-boot.


I asked if your BIOS is capable of booting from USB and if it was to follow the suggestions.

See the above, unless you worded it incorrectly you did not boot from USB, you booted a Live CD and installed Ubuntu on the flash disk. That is not the same as booting from a USB or Flash disk!

If you do not want to take any risks then leave it the way it is.

---

### Post by TheHimself on 2009-11-16
Let me add that if you want to install any kind of Linux on a USB derive (and you don't have anything on the derive) then you don't have to reboot your computer. Just use the package "unetboontin".

---

### Post by Tufty on 2009-11-16
> **presence1960 said:**
> I asked if your BIOS is capable of booting from USB and if it was to follow the suggestions.

See the above, unless you worded it incorrectly you did not boot from USB, you booted a Live CD and installed Ubuntu on the flash disk. That is not the same as booting from a USB or Flash disk!

If you do not want to take any risks then leave it the way it is.

Hi,
Sorry if it was unclear.
What I'd thought I'd said, and I'm not quite sure how else to say it, is that I installed Ubuntu ONTO the flash drive and THEN tried to boot from the flash drive, which is when this problem manifested as for some reason it just sat TRYING to boot from the USB stick, but doing nothing.

Apologies if I've caused bad feeling, that was not my intent, only to try to be absolutely certain that you understood the problem.

So in short again...
I can load a USB stick with an UBUNTU system (that works fine)
I know my BIOS DOES try to boot from the USB stick, but for some reason it gets stuck & does nothing. Once in that state trying to boot from ANYTHING (Apart from the Ubuntu ISO CD which is still boots from fine) causes "GRUB RESCUE" to come up.

---

### Post by Tufty on 2009-11-16
> **TheHimself said:**
> Well, you should first back up your data and then make your machine bootable again. 

To do the first thing you need any OS that can be run from a removable media. If you have Ubuntu live CD, that's very easy. Just boot your computer with the live CD and when the menu shows up choose 
"Try Ubuntu without any changes ...". Do NOT choose "install Ubuntu...". When Ubuntu desktop shows up, attach a flash memory stick big enough for you data to back up.
Now using file manager go to windows partition then copy your files and paste them on the flash drive. 
(if windows partition doesn't show up in the file manager you have to mount the partition. It's name is sda1 or sda2, etc. Run
```

sudo mount /dev/sda1

```
in a terminal. Try different numbers 1,2,3 until your windows partition shows up.)

Then shot down the computer. You have your data at hand. 
The above instructions won't change anything on your hard drive. After you did this I'll tell you how to make the computer bootable.

Hi TheHimself,
I can boot from the ISO CD and I can happily access all the devices on my PC, hard disks and USB stick.
I have backups of most important things, and I can see that the windows system is all still there and OK.
All I need to do is to get a good grub (as I had before) that allows me to either boot Windows or Ubuntu 

I'm presuming that before I attempted to put UBUNTU on the USB stick, the grub was on either my windows hard drive or my Ubuntu 9.04 hard drive.

That grub somehow got changed when I tried to set up the USB stick with Ubuntu.

Is there no easy way I can find & edit that grub to revert it back to how it was before?

Do I really have to start reloading the windows CD and changing things on the windows drive?

---

### Post by Tufty on 2009-11-16
> **presence1960 said:**
> I asked if your BIOS is capable of booting from USB and if it was to follow the suggestions.

See the above, unless you worded it incorrectly you did not boot from USB, you booted a Live CD and installed Ubuntu on the flash disk. That is not the same as booting from a USB or Flash disk!

If you do not want to take any risks then leave it the way it is.

I really am grateful for your help Presence1960
What set alarm bells ringing for me was when you said: "**Boot your XP install disk** and do this, following instructions for XP"

Yet when I follow the link for explanation, it says to boot from the Ubuntu install disk. Where does the Windows XP install disk come into the equation?
I certainly don't want to re-install windows.

---

### Post by TheHimself on 2009-11-16
What you need is 

:D Recovery Is Possible ;)

It's a small linux distro designed for situations like yours. You can get it from  [http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

Download the one with X and Grub and using the instructions rip it on a CD or a usb drive. Then use it to boot your computer and once the desktop came up from the menu entry "partition editors" choose Grub (if your ubuntu is <= 9.04) or GRUB 2 (if its 9.10). It's easy to use. Follow the instructions "Do this first", "Do this second", etc. You must know in which partitions your windows and linux are located. The only tricky part is locating the Linux kernel. (The default option won't work). You should look in /boot/
and among files with "vmlinuz" in their name find the one which is the last version (biggest number). Then put its exact name in place of "vmlinuz" that the Grub programs gives you as default. 

This won't do anything to your partitions.

---

### Post by Tufty on 2009-11-16
Thankyou for all the help. The solution was as follows:

1) Booted from Ubuntu 9.04 CD
2) sudo grub
3) find /boot/grub/stage1
This gave "(hd1,0)"
4) root (hd1,0)
5) setup (hd0)
6) quit
7) sudo reboot

These commands set the system back to how it was before I installed 9.10 on the USB stick.

Thanks Guys, apologies if I was a bit thick & nervous about further playing with USB stick & Windows setup CD's.

Dave.

---

### Post by presence1960 on 2009-11-16
> **Tufty said:**
> Thankyou for all the help. The solution was as follows:

1) Booted from Ubuntu 9.04 CD
2) sudo grub
3) find /boot/grub/stage1
This gave "(hd1,0)"
4) root (hd1,0)
5) setup (hd0)
6) quit
7) sudo reboot

These commands set the system back to how it was before I installed 9.10 on the USB stick.

Thanks Guys, apologies if I was a bit thick & nervous about further playing with USB stick & Windows setup CD's.

Dave.

There were no hard feelings- I am referring to a previous post on the first page of this thread. 

I said leave it the way it is if you don't want to take a risk because troubleshooting any problem involves a certain amount of risk, you never know what can happen or go wrong. Glad you got it working.

P.S. I had similar as part of my fix except i had setup (hd1) because I was going to have you put GRUB on 9.04 disk MBR and switch the boot order in BIOS. That's why I was having you restore XP's bootloader to sda. I prefer to have each OS have it's own bootloader on MBR when the OSs are installed to different hard disks.

---

### Post by presence1960 on 2009-11-16
> **Tufty said:**
> I really am grateful for your help Presence1960
What set alarm bells ringing for me was when you said: "**Boot your XP install disk** and do this, following instructions for XP"

Yet when I follow the link for explanation, it says to boot from the Ubuntu install disk. Where does the Windows XP install disk come into the equation?
I certainly don't want to re-install windows.

if you scroll down when you go to the link you will see there are instructions to restore bootloader for XP & Vista. see here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Satori80 on 2009-11-17
Okay, I just did the *exact* same dumb thing to my laptop but I'm using 9.10 and I can't seem to fix it. 

I tried that RIP cd with GRUB2 to try and fix it. Now the laptop tries to boot but I get a kernel panic because it can't seem be able to read reiserfs. How do I get it to load the initrd.img file?

I'm very tempted to go back to LILO at this point. I've never been able to make any sense of GRUB for some reason.


EDIT: Never mind! I got it. It actually was as easy as LILO :) Thanks anyway.

---

### Post by llazarte on 2009-11-18
Hi, can you help me by describing how you installed lilo?

I have the same problem. I installed 9.10 UNR and I suspect my old grub was substituted with grub2 :-(

I can boot from a USB stick with 9.04.

When I try to run grub, it complains that it cannot find /boot/grub/stage1 (which, in fact, isn't there).

And I don't find lilo on my USB distro.

Thanks for any help!

---

### Post by Satori80 on 2009-11-18
Sorry, I didn't mean I installed LILO, I meant editing grub.cfg to load initrc was as easy as using LILO. I'm still using Grub.

If 9.10 is what you have installed, you are going to have trouble using 9.04 to fix it because they do use different Grub versions. The Recovery Is Possible CD TheHimself talked about earlier in this thread is the way to go, I think. Actually, you can boot it from USB as well if you prefer.  

Once I got Kubuntu 9.10 bootable again I did "sudo apt-get install --reinstall grub-pc" to get the boot-loader back to how it was when I first installed it (grub-pc is what Ubuntu calls the Grub2 package... for some reason).

Hope that helps.

EDIT: Actually I'm new at Ubuntu -- or any pre-compiled distros for that matter -- so I'm sorry if I'm terse. I started with slackware 'way-back-when' to play around with Linux, but when I *really* started using Linux for day to day use, I started first with LFS and then moved to Gentoo, so, I must apologise that I assume a lot. 

I might be new to Ubuntu but I do know a bit about Linux so if you need any more help, please say so.

I never did use Grub until now though so I'm no expert -- and Ubuntu uses a very strange (read: non-standard) way of implementing it that I've *almost* sorted out. 

Then again... I still prefer VI to write text and bash scripts so... maybe I wouldn't be much help with Grub in and of itself, but I would be happy walk you through exactly what I did in more detail if that's what you would like. :)

But as far as I can see the Grub "rescue" prompt is a myth. It would not read any of my partitions, no offence meant to [Tufty]("http://ubuntuforums.org/member.php?u=268428"). It just didn't work at all for me and never has. It's why I've always stuck with LILO until now.

---

### Post by llazarte on 2009-11-19
Thanks, Satori80, for you answer.

> **Satori80 said:**
> Sorry, I didn't mean I installed LILO, I meant editing grub.cfg to load initrc was as easy as using LILO. I'm still using Grub.

If 9.10 is what you have installed, you are going to have trouble using 9.04 to fix it because they do use different Grub versions. The Recovery Is Possible CD TheHimself talked about earlier in this thread is the way to go, I think. Actually, you can boot it from USB as well if you prefer.  

Once I got Kubuntu 9.10 bootable again I did "sudo apt-get install --reinstall grub-pc" to get the boot-loader back to how it was when I first installed it (grub-pc is what Ubuntu calls the Grub2 package... for some reason).

Hope that helps.

EDIT: Actually I'm new at Ubuntu -- or any pre-compiled distros for that matter -- so I'm sorry if I'm terse. I started with slackware 'way-back-when' to play around with Linux, but when I *really* started using Linux for day to day use, I started first with LFS and then moved to Gentoo, so, I must apologise that I assume a lot. 

I might be new to Ubuntu but I do know a bit about Linux so if you need any more help, please say so.

I never did use Grub until now though so I'm no expert -- and Ubuntu uses a very strange (read: non-standard) way of implementing it that I've *almost* sorted out. 

Then again... I still prefer VI to write text and bash scripts so... maybe I wouldn't be much help with Grub in and of itself, but I would be happy walk you through exactly what I did in more detail if that's what you would like. :)

But as far as I can see the Grub "rescue" prompt is a myth. It would not read any of my partitions, no offence meant to [Tufty]("http://ubuntuforums.org/member.php?u=268428"). It just didn't work at all for me and never has. It's why I've always stuck with LILO until now.

**Past**: I regained access to my Netbook by booting with my old USB with Ubuntu 9.04 and reinstalling **grub** (the old one), using a backup of **menu.lst** which I had (the upgrade trashed my good menu.lst).

[LIST=1]
[*]Boot USB Ubuntu 9.04
[*]Mount my Ubuntu 9.10 partition (on my case: mount /dev/sda5 /mnt)
[*]Copy backup menu.lst to /mnt/boot/grub
[*]Edit menu.lst to reflect the new kernel (2.6.31.14)
[*]Install grub. I don't remember the exact command, but it was something like "grub-install root=/mnt /dev/sda"
[*]Reboot
[/LIST]
It did work, and this installation introduced a warning to install Grub2 once it was working. Is also created a first line on the boot menu, to chain boot to Grub2 (I suppose that will be helpful when testing if Grub2 is working).

**Future**: I suppose I will have to study Grub2 to make it work without it leaving me out of my computer. Any suggestion as to the best way to either reinstall, configure or update Grub2? Perhaps reinstall grub-pc?

Thanks again,
Leonardo

---

### Post by presence1960 on 2009-11-19
> **llazarte said:**
> 

**Future**: I suppose I will have to study Grub2 to make it work without it leaving me out of my computer. Any suggestion as to the best way to either reinstall, configure or update Grub2? Perhaps reinstall grub-pc?

Thanks again,
Leonardo

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by jpsfer on 2009-11-24
firstly, i apologize for my awful English...

I'm a begginer ubuntu user (better said, I'm trying to install it) and have got a similar problem...

I've acquired the ubuntu 9.10 CD in the ubuntu HP. My machine is a HP Pavillion DV6500 notebook, running with Windows Vista. I've tried to install ubuntu following the graphical install available in the ubuntu site. My option was to install it in a external HD, to avoid partitioning my primary HD. After the instalation was concluded, the notebook doesnt boot by the external HD, neiter by Windows anymore!! When I disconnect the external HD, appear a prompt with the following message:

no such disk
GRUB rescue>


The option to recovery Windows, supported by HP does not work anymore. So, I cant reinstall windows anymore, and my notebook has no boot!!!
please, could anyone help me???

Yours sincerely,

João Paulo

---

### Post by presence1960 on 2009-11-24
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by jpsfer on 2009-11-24
dear presence 1960

i'm very glad about your help...

i've tryied the command and the response i've obtained was
sudo: /home/ubuntu/Desktop/boot_info_script*.sh: command not found

maybe my notebook does not have this command available (sorry about my dumbness)...

---

### Post by presence1960 on 2009-11-24
> **jpsfer said:**
> dear presence 1960

i'm very glad about your help...

i've tryied the command and the response i've obtained was
sudo: /home/ubuntu/Desktop/boot_info_script*.sh: command not found

maybe my notebook does not have this command available (sorry about my dumbness)...

it seems to be that you entered the command improperly. try copying and pasting the command into terminal:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by unclesamslair on 2010-01-05
Okay, I sorta have a similar problem. I don't know if the same fix will work so I'm just gonna tell you what it is. I had xubuntu on one partition and vista on another then I repartitioned some free space between the two of them and installed mythbuntu (using the "use the largest continuous space" option) so I could mess around with it without damaging my xubuntu data. I have everything pretty much backed up since I never repartition without backing up all data (Learned that lesson a long time ago). Everything is working fine and I'm booting up perfectly from all three os's. Now I don't want the mythbuntu anymore so I delete the partition (all files backed up, I'm a stickler for that). and then when I reboot my grub won't load and I'm dropped into the grub rescue prompt.

so I ran the boot info script and this is what I got

```
============================= Boot Info Summary: ==============================

=> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive
    in partition #7 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29551006

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     75,216,336   234,436,544   159,220,209   7 HPFS/NTFS
/dev/sda2                  63    22,571,324    22,571,262   5 Extended
/dev/sda5                 126    21,527,099    21,526,974  83 Linux
/dev/sda6          21,527,163    22,571,324     1,044,162  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="C244297D442974F7" TYPE="ntfs"
sda5: UUID="6fdf1e73-d5f0-45b1-8592-82ebc2540f4f" TYPE="ext4"
sda6: UUID="3a257f33-21c8-43c8-905b-0542a24174f8" TYPE="swap"

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


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
linux /boot/vmlinuz-2.6.31-16-generic root=UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f ro   quiet splash
initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
linux /boot/vmlinuz-2.6.31-16-generic root=UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f ro single
initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f ro   quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f ro single
initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set c244297d442974f7
chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set b152c549-14fd-484a-8f1d-7def7d0b55df
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b152c549-14fd-484a-8f1d-7def7d0b55df ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set b152c549-14fd-484a-8f1d-7def7d0b55df
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b152c549-14fd-484a-8f1d-7def7d0b55df ro single
initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=3a257f33-21c8-43c8-905b-0542a24174f8 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

```

---

### Post by kansasnoob on 2010-01-05
> **unclesamslair said:**
> Okay, I sorta have a similar problem. I don't know if the same fix will work so I'm just gonna tell you what it is. I had xubuntu on one partition and vista on another then I repartitioned some free space between the two of them and installed mythbuntu (using the "use the largest continuous space" option) so I could mess around with it without damaging my xubuntu data. I have everything pretty much backed up since I never repartition without backing up all data (Learned that lesson a long time ago). Everything is working fine and I'm booting up perfectly from all three os's. Now I don't want the mythbuntu anymore so I delete the partition (all files backed up, I'm a stickler for that). and then when I reboot my grub won't load and I'm dropped into the grub rescue prompt.

so I ran the boot info script and this is what I got

```
============================= Boot Info Summary: ==============================

=> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive
    in partition #7 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29551006

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     75,216,336   234,436,544   159,220,209   7 HPFS/NTFS
/dev/sda2                  63    22,571,324    22,571,262   5 Extended
/dev/sda5                 126    21,527,099    21,526,974  83 Linux
/dev/sda6          21,527,163    22,571,324     1,044,162  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="C244297D442974F7" TYPE="ntfs"
sda5: UUID="6fdf1e73-d5f0-45b1-8592-82ebc2540f4f" TYPE="ext4"
sda6: UUID="3a257f33-21c8-43c8-905b-0542a24174f8" TYPE="swap"

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


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
linux /boot/vmlinuz-2.6.31-16-generic root=UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f ro   quiet splash
initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
linux /boot/vmlinuz-2.6.31-16-generic root=UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f ro single
initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f ro   quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6fdf1e73-d5f0-45b1-8592-82ebc2540f4f
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f ro single
initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set c244297d442974f7
chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set b152c549-14fd-484a-8f1d-7def7d0b55df
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b152c549-14fd-484a-8f1d-7def7d0b55df ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set b152c549-14fd-484a-8f1d-7def7d0b55df
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b152c549-14fd-484a-8f1d-7def7d0b55df ro single
initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=6fdf1e73-d5f0-45b1-8592-82ebc2540f4f / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=3a257f33-21c8-43c8-905b-0542a24174f8 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

```

Well you see grub2 is looking for boot files on sda7 which no longer exists:  

> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive in partition #7 for /boot/grub.

So boot any *buntu live CD and from the Live Desktop go to Terminal and:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then reboot & the first time you boot into Xubuntu go to terminal and run:

```
sudo update-grub
```

---

### Post by unclesamslair on 2010-01-05
> **kansasnoob said:**
> Well you see grub2 is looking for boot files on sda7 which no longer exists:  



So boot any *buntu live CD and from the Live Desktop go to Terminal and:

```
sudo mount /dev/sda5 /mnt && sudo mount –bind /dev /mnt/dev && sudo mount –bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then reboot & the first time you boot into Xubuntu go to terminal and run:

```
sudo update-grub
```

I only got this far.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda5/ /mnt && sudo mount -bind /dev /mnt/dev && sudo mount -bind /proc /mnt/proc && sudo chroot /mnt
mount: invalid option -- 'b'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount –bind /dev /mnt/dev && sudo mount –bind /proc /mnt/proc && sudo chroot /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ grub-install /dev/sda
grub-mkdevicemap: error: cannot open /boot/grub/device.map
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ grub-install /dev/sda5
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ 


```

I'm afraid to go any further and type ```
sudo grub-install /dev/sda5
``` and cause permanent damage.

---

### Post by kansasnoob on 2010-01-05
You got the command wrong.

Mine:

sudo mount /dev/sda5 /mnt && sudo mount –bind /dev /mnt/dev && sudo mount –bind /proc /mnt/proc && sudo chroot /mnt

Yours:

sudo mount /dev/sda5**[COLOR="Red"]/[/COLOR]** /mnt && sudo mount -bind /dev /mnt/dev && sudo mount -bind /proc /mnt/proc && sudo chroot /mnt


You also used some single- where they should be double --.

Do not try to type long commands just double-click within the code box, select copy, then paste them into the terminal.

So go back to post #27 and try again. If any part of that fails post back here.

---

### Post by kansasnoob on 2010-01-05
> **unclesamslair said:**
> I only got this far.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda5/ /mnt && sudo mount -bind /dev /mnt/dev && sudo mount -bind /proc /mnt/proc && sudo chroot /mnt
mount: invalid option -- 'b'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount –bind /dev /mnt/dev && sudo mount –bind /proc /mnt/proc && sudo chroot /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ grub-install /dev/sda
grub-mkdevicemap: error: cannot open /boot/grub/device.map
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ grub-install /dev/sda5
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ 


```

I'm afraid to go any further and type ```
sudo grub-install /dev/sda5
``` and cause permanent damage.

BTW we're not trying to install to:

/dev/sda5

It's:

grub-install /dev/sda

Just copy-n-paste!

---

### Post by kansasnoob on 2010-01-05
I did have to correct the --,s in my original post, sorry about that. It's good to go now!

If you tried it before I corrected it and now it says "already mounted" then run:

```
sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

And continue with:

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Sorry for the typos :(

---

### Post by unclesamslair on 2010-01-05
> **kansasnoob said:**
> BTW we're not trying to install to:

/dev/sda5

It's:

grub-install /dev/sda

Just copy-n-paste!

thanks a lot! system is booting up perfectly but now it doesn't show a takbar on bootup.

I popped up a terminal and installed tree to show me the filesystem. All my files are still there I then ran synaptic and tried to see if any packages were missing but I don't know much so now I'm stuck with another problem.

---

### Post by kansasnoob on 2010-01-05
I don't know how to restore the taskbar (aka: panel) in Xubuntu.

I'd start a new thread in the beginners:

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

Or desktop environments:

[http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

---

### Post by kansasnoob on 2010-01-05
A quick Google search showed this:

[http://www.ehow.com/how_5516495_restore-task-bar-xubuntu.html](http://www.ehow.com/how_5516495_restore-task-bar-xubuntu.html)

And this:

[https://help.ubuntu.com/community/XubuntuPanels](https://help.ubuntu.com/community/XubuntuPanels)

---

### Post by endlessracingz on 2010-02-17
I have a very similar problem to everyone except for the fact that I am using ubuntu 9.10 server.

I have attempted to try many of the fixes as posted above but I cannot for the life of me get ubuntu to boot even from a live CD. I cannot boot from the ubuntu server CD or an alternate that I also acquired.

Could someone more knowledge help. I am a complete beginner. I've used windows for most of my life and the past 5 years have been using a MAC and now I'm moving towards linux.

Thanks for anything you can do!

---

### Post by endlessracingz on 2010-02-17
Totally forgot to write my details. 

So being so new to ubuntu I had planned to make a home server using ubuntu server.

I have an old P4 system with a 3GB RAM, two 120GB HD's that are SATA. I want to have them as a Raid 0. The system will not be a dual boot system. So from my understanding my system uses fakeRaid but because I will not use it as a dual boot I will just use ubuntu's softRaid.

I followed the following instructions: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

So to paraphrase when prompted by the install CD as to activate the raid devices I opt to "No" and setup the partitions manually. 

I partitioned each drive (which are exactly the same) into (the numbers are rough) :

100 MB
3 GB
117 GB

Then configuring the softRaid I combined:
100 MB (200 MB total) partitions which which I set as my /boot
3 GB (6GB total) partitions which I set as my swap area
117 GB (234 GB total) partitions to my root or "/"

I proceed with the install and everything seems to go well. After rebooting the system I get prompted with:

GRUB loading.
error: biodisk read error
error: no such disk
grub rescue>

It is my understanding that, and I quote from the above link.

> The key is that GRUB can't be installed on the RAID device. However, the individual raw partitions that make up the RAID device look just like ordinary non-RAIDed partitions to GRUB. So you need to unmount the RAID device and install grub manually.However, in the above link it states that I should have a grub> prompt and not the grub rescue> prompt.

I haven't been able to boot to a working system to my knowledge, most likely I just don't know how to do this.

So I  **THOUGHT** I found the answer at the following:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Essentially the /boot for Grub2 cannot be a Raid0 array. Essentially I would have the /boot be on a single drive in 1 partition. There are ways according to the above link to mirror the /boot onto each drive however I personally do not need to do such.

So here I am sitting at:

HD1:
500 MB ext4 /boot
3 GB raid
117 GB raid

HD2:
500 MB ext "do not use"
3 GB raid
117 GB raid

Raid0 configured:
6 GB swap
234 GB ext4 root or "/"

and now I get the following when booting:

GRUB loading.
error: file not found
grub rescue>

---

### Post by endlessracingz on 2010-02-17
After playing with my above stated issue for hours I have found an answer.

Since I have fakeRaid I still had my two hard drives configured in an Raid array in the BIOS and this was causing all the issues. After deleting the array and setting the drives to non-raid in the BIOS, ubuntu started right up.

---

### Post by DeeLeung on 2010-03-06
First, the standard disclaimer that I am very new to Linux and Ubuntu.

I have been running 9.10 for a couple of weeks on a partition installed with the startup disc.  The original system was Windows7 RC, which I kept around in a dual-boot, again prepared via the Ubuntu disc.

The problem: after I abandoned Windows, I decided that, "Ok, the bootloader is probably on a separate partition, so I can just wipe the Windows partition," and promptly did so by deleting it and changing to ext4 (and i don't think i set it bootable).  

After a reboot, I got the Grub Rescue prompt, which all I could get out of it was "ls" returning me "hd0".

I re-started using the CD, and can see the Linux partition, but since I don't own the folders there anymore (and they are encrypted, i believe), I can't pull anything useful off.

--
Ideally, I would like to fix the boot situation, skipping dual-boot entirely, going straight into my erstwhile working installation of Ubuntu.

Possibly just as decent would be to at least access my data, back it up, and do a fresh install (and even better, but i doubt it's possible, just copy over the whole directory structure and have everything working on a whole, unpartitioned drive).


While I would like to understand the workings of Grub and how to rescue it, I will be more than happy to settle for the above-mentioned latter option.  

I really appreciate the patient and thorough tone of the messages in this thread and hope you guys can help me with an equal amount of patience.

Thanks very, very much in advance.

---

### Post by DeeLeung on 2010-03-12
Anybody out there? Can someone please say if this situation is salvageable?

---

### Post by sameer.walgude on 2010-03-12
Try this at grub rescue> prompt....

grub rescue> set prefix=(hd0,x)/boot/grub
grub rescue> insmod (hd0,x)/boot/grub/normal.mod
rescue:grub> normal


If still fails...boot up live cd...

at terminal...
sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub /dev/sda

substitute /media/{kubuntu9.10partition} with actual partition :)

If you get error message,(mapping fails), do this..

sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub -m 
/media/{kubuntu9.10partition}/boot/grub/device.map /dev/sda

All the best!

Thanks & Regards
Sameer J Walgude
[email]sameer.walgude@aol.in[/email]
+91 98191 15533

---

### Post by bonstermaze on 2010-03-18
Hi, I have a similar problem. I installed ubuntu 9.10 on an free partition on my hard drive. The installation was successful but when I restarted my laptop, it seas  :
```
GRUB loading
error: no such partion
grub rescue>
```I tried some of the commands I found on these forums.
```
grub rescue> ls
(hd0) (hd0,2) (hd0,1)
error: out of disk
grub rescue> ls (hd0)
error: out of disk
grub rescue> ls (hd0,1)
error: out of disk
grub rescue> ls (hd0,2)
error: out of disk
grub rescue> help
error: unknown command 'help'

```I also ran the script from page 1.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc6546be

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,210,239   117,210,177   7 HPFS/NTFS
/dev/sda2         117,210,240   302,793,119   185,582,880   7 HPFS/NTFS
/dev/sda3         302,793,120   488,392,064   185,598,945   5 Extended
/dev/sda5         302,793,183   480,745,124   177,951,942  83 Linux
/dev/sda6         480,745,188   488,392,064     7,646,877  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        22A8C682A8C65447                       ntfs                                     
/dev/sda2        3A44D05744D01809                       ntfs       Data                          
/dev/sda5        ac866197-8566-4ccc-959d-a2e9b46b71df   ext4                                     
/dev/sda6        215dc161-148f-4f2a-b83a-0ba3169fd05e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set ac866197-8566-4ccc-959d-a2e9b46b71df
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ac866197-8566-4ccc-959d-a2e9b46b71df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ac866197-8566-4ccc-959d-a2e9b46b71df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ac866197-8566-4ccc-959d-a2e9b46b71df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ac866197-8566-4ccc-959d-a2e9b46b71df ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 22a8c682a8c65447
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ac866197-8566-4ccc-959d-a2e9b46b71df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=215dc161-148f-4f2a-b83a-0ba3169fd05e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 158.2GB: boot/grub/core.img
 158.2GB: boot/grub/grub.cfg
 155.6GB: boot/initrd.img-2.6.31-14-generic
 155.5GB: boot/vmlinuz-2.6.31-14-generic
 155.6GB: initrd.img
 155.5GB: vmlinuz
```I don't really have a clue what this all means. Al this linux suff is new to me...

If anyone could help me, thanks in advance.

---

### Post by presence1960 on 2010-03-18
> **bonstermaze said:**
> Hi, I have a similar problem. I installed ubuntu 9.10 on an free partition on my hard drive. The installation was successful but when I restarted my laptop, it seas  :
```
GRUB loading
error: no such partion
grub rescue>
```I tried some of the commands I found on these forums.
```
grub rescue> ls
(hd0) (hd0,2) (hd0,1)
error: out of disk
grub rescue> ls (hd0)
error: out of disk
grub rescue> ls (hd0,1)
error: out of disk
grub rescue> ls (hd0,2)
error: out of disk
grub rescue> help
error: unknown command 'help'

```I also ran the script from page 1.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc6546be

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,210,239   117,210,177   7 HPFS/NTFS
/dev/sda2         117,210,240   302,793,119   185,582,880   7 HPFS/NTFS
/dev/sda3         302,793,120   488,392,064   185,598,945   5 Extended
/dev/sda5         302,793,183   480,745,124   177,951,942  83 Linux
/dev/sda6         480,745,188   488,392,064     7,646,877  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        22A8C682A8C65447                       ntfs                                     
/dev/sda2        3A44D05744D01809                       ntfs       Data                          
/dev/sda5        ac866197-8566-4ccc-959d-a2e9b46b71df   ext4                                     
/dev/sda6        215dc161-148f-4f2a-b83a-0ba3169fd05e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set ac866197-8566-4ccc-959d-a2e9b46b71df
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ac866197-8566-4ccc-959d-a2e9b46b71df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ac866197-8566-4ccc-959d-a2e9b46b71df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ac866197-8566-4ccc-959d-a2e9b46b71df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ac866197-8566-4ccc-959d-a2e9b46b71df ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 22a8c682a8c65447
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ac866197-8566-4ccc-959d-a2e9b46b71df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=215dc161-148f-4f2a-b83a-0ba3169fd05e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 158.2GB: boot/grub/core.img
 158.2GB: boot/grub/grub.cfg
 155.6GB: boot/initrd.img-2.6.31-14-generic
 155.5GB: boot/vmlinuz-2.6.31-14-generic
 155.6GB: initrd.img
 155.5GB: vmlinuz
```I don't really have a clue what this all means. Al this linux suff is new to me...

If anyone could help me, thanks in advance.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by thomra on 2010-03-18
I am having nearly the same problem.*  I cannot boot from live cd or flash drive. I tried the sudo text,  but all I get is "unknown command"*
 
*I have tried to go to my boot screne and enter boot from IDE cd-rom device with my live cd in . still nothing. *
 
*Screen reads: Strike F1 key to comtinue, F2 to run setup utility.*
*GRUB loading.  error: no such disk*
*grub rescue>*
 
*Can anyone please help?. I am new to this.*
 
*Thanks*
 
*[EMAIL="Rickthompson1@suddenlink.net"]Rickthompson1@suddenlink.net[/EMAIL]*

---

### Post by presence1960 on 2010-03-18
> **thomra said:**
> I am having nearly the same problem.*  I cannot boot from live cd or flash drive. I tried the sudo text,  but all I get is "unknown command"*
 
*I have tried to go to my boot screne and enter boot from IDE cd-rom device with my live cd in . still nothing. *
 
*Screen reads: Strike F1 key to comtinue, F2 to run setup utility.*
*GRUB loading.  error: no such disk*
*grub rescue>*
 
*Can anyone please help?. I am new to this.*
 
*Thanks*
 
*[EMAIL="Rickthompson1@suddenlink.net"]Rickthompson1@suddenlink.net[/EMAIL]*

I would refer to your motherboard or computer documentation to find out how to boot from CD. Maybe the CD is bad. Can you try booting the CD on another machine to see if it boots?

---

### Post by relaer on 2010-03-20
This 'grub rescue' error can be fixed by booting from the live cd. After the system boots you will have a choice of booting from a hard drive, select this option it will cause grub to be fixed. Next time you can boot as usual. I've used this on two different computers with dual boot. I've made a point of having current backups, because the first time this happened to me I couldn't find a solution and I ended up reinstalling the system.
Good luck.;)

---

### Post by kaspin on 2010-03-20
[FONT="Comic Sans MS"][COLOR="Blue"][SIZE="2"]Don't know how relaer's solution managed to work - it certainly didn't on my PC. I've been happily using Ubuntu 9.10 for several months, with WinXP on the same HDD, using Grub2 to boot. The grub rescue error came about after I disconnected the HDD and tried some other HDDs in it's place. When I put the original HDD back, I got the grub rescue error although nothing had been changed on the original HDD. 
As a relative newbie, I can't see what purpose the grub rescue prompt serves.The only instruction it seems to understand is "ls" (it returns (hd0)(hd0,2) and (hd0,1) on my machine), and if you then do further ls's it comes back with "error unknown file system" or "cannot get C/H/S values".   
I have booted with the Ubuntu CD, and would like to look at the file system files on the HDD, but the only Ubuntu system files that appear under "places" are those on the CD. On the other hand the WinXP files on the HDD are there.....  
Back to the drawing board.........kaspin[/SIZE][/COLOR][/FONT]

---

### Post by kaspin on 2010-03-20
[FONT="Comic Sans MS"][SIZE="2"][COLOR="Blue"]I've solved my immediate problem - as soon as I put back the second HDD, containing only non-Linuxx data, so that the PC set-up was identical to that when I took out the original HDD, Grub booted normally.
But I'd still like to know the purpose of grub rescue........kaspin[/COLOR][/SIZE][/FONT]

---

### Post by progone on 2010-05-07
[SIZE="5"]This solution works.[/SIZE]

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Its less than 5 steps.

---

### Post by oksg on 2010-06-03
Please, can anyone help me, i am linux newbie. Now i had problem from yesterday. i tried to remove ubuntu karmic on win xp. just after deleted ubuntu partition and reboot...show :

GRUB loading
ERROR: unknown filesystem
grub rescue>

i dont now, what i hv to do....

PLEASE help me...or  send email to : [email]tetimufid@yahoo.com.sg[/email]

THANKS

---

### Post by paulsmith99 on 2010-06-06
I've **solved** this for my situation after wasted hours of Googling, reboots and tearing hair out....

Background:
I reinstalled mythbuntu 10.04 due to unrelated problems, only formatting the old root partition and leaving all others untouched, rebooted and got the dreaded:
[COLOR=Navy][FONT=Courier New]error: no such device: e61482ae-XXXXXXX-XXXXXXX-XXXXXXXX.[/FONT][/COLOR]
[FONT=Courier New][COLOR=Navy]grub rescue>[/COLOR][/FONT]

I tried all the solutions on forums that describe using a Live USB, mount/bind/chroot/grub-update but to no avail. All my attempts made absolutely no difference, so I got suspicious of another cause...

I have two 500GB SATA drives, only one has a root partition (plus home and data partitions) and the other is purely for data. I wondered whether the data drive was being booted from for some daft reason, even though it must have booted from the correct drive before I reinstalled mythbuntu today and with no hardware changes.

Solution (for me):
With nothing to loose, I changed the BIOS boot order to boot from my other drive and [COLOR=Red]IT SOLVED THE PROBLEM[/COLOR]. It worked and the grub boot menu appeared as I was expecting to see all along.

It turns out that all my efforts to grub-install/grub-update was being done correctly to /dev/sda that has the root partition but I wasn't seeing the results because little did I know the BIOS was trying to boot from /dev/sdb (my data drive). I don't know why the boot order was wrong. I haven't changed the drives' SATA cables recently - still trying to work out how it worked prior to me re-installing mythbuntu earlier today :confused:

Sorry I can't give a technical reason for why it wasn't working in my case but hopefully this will lead to other people resolving this brain-ache when grub changes aren't having any effect.

I'm in a happy place now :P

---

### Post by newbuntu1 on 2010-06-23
Can someone help me with this?  Below is the output of the sh script off soundforge that someone mentioned in another post.  I kinda know what I did, I was using gparted (via the systemsrescue live cd) to re-size sda5 which was where the ubuntu ext4 (/home, etc.) was but I accidentally canceled (was on the phone at the same time and wasn't thinking) the resize while it was resizing and then i found that i only get the grub-rescue> prompt when booting back up.  I have win xp on sda1 which is probably okay.  i tried mounting sda5 and sda2 but only get a lost+found directory in sda5 and cannot even see a /home or /boot and so on; also couldn't mount sda2 to browse from sda2.  Any ideas?  How can I restore things or at least recover files, data on sda5, /home, etc. ???  Thank you in advance.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35057   281595321    7  HPFS/NTFS
/dev/sda2           35058       38914    30975527+   5  Extended
/dev/sda5           35058       38315    26169853+  83  Linux
/dev/sda6           38852       38914      494592   82  Linux swap / Solaris
root@ubuntu:~# 



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   563,190,704   563,190,642   7 HPFS/NTFS
/dev/sda2         563,190,705   625,141,759    61,951,055   5 Extended
/dev/sda5         563,190,768   615,530,474    52,339,707  83 Linux
/dev/sda6         624,152,576   625,141,759       989,184  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        76F8C9B5F8C97441                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2254952e-7de5-4382-a511-7e00f7084dad   ext4                                     
/dev/sda6        a1ba21c3-32ef-4ea4-a970-e942748e46cc   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/2254952e-7de5-4382-a511-7e00f7084dad ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/test              ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

---

### Post by saito43v3r on 2010-06-30
Greetings.
I've came across this problem too.
I've a deleted a partition of Ubuntu on my Window 7 disk manager , and i got this "grub rescue" stuff
i couldn't boot into my Window 7 now...and all my work data is inside , can anyone help me?

JJ

---

### Post by presence1960 on 2010-06-30
> **saito43v3r said:**
> Greetings.
I've came across this problem too.
I've a deleted a partition of Ubuntu on my Window 7 disk manager , and i got this "grub rescue" stuff
i couldn't boot into my Window 7 now...and all my work data is inside , can anyone help me?

JJ

You should have fixed your MBR either before or after removing Linux because GRUB is still on the MBR and has no file to look to to boot because you removed linux.

Boot the Ubuntu Live CD/USB and when the desktop loads open a terminal and run ```
sudo apt-get install lilo
``` This will install lilo to the live session only.

Next in terminal run ```
sudo lilo -M /dev/sda mbr
```

Reboot without the Live CD/USB and you should boot to windows.

Another way is to do the procedure listed [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Windows 7.

---

### Post by navdeep89 on 2010-07-07
help me frnzzzz!!!!!

i had installed ubuntu 9.04 on my PC n then i installed windows7...
what i did unwantedly is dat i deleted d partitions which wer containing ubuntu..
now when i reboot my PC , it only shows "GRUB rescue" .what shud i do now to avoid my data loss in windows partitions..????

plzz help me .... its urgent

---

### Post by Simdog1 on 2010-07-08
can some one help me with this??              




  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   602,879,999   602,877,952  83 Linux
/dev/sda2         602,882,046   625,141,759    22,259,714   5 Extended
/dev/sda5         602,882,048   611,392,515     8,510,468  82 Linux swap / Solaris
/dev/sda6         611,393,536   624,443,391    13,049,856  83 Linux
/dev/sda7         624,445,440   625,141,759       696,320  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a12007c0-f324-463e-8f96-67391704eba7   swap                                     
/dev/sda6        ba9a3739-8e23-4e16-a660-014d4c2b90bb   ext4                                     
/dev/sda7        4a7f1140-9e83-4492-a013-7a1356e852a1   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /target                  ext4       (rw,errors=remount-ro)


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=ba9a3739-8e23-4e16-a660-014d4c2b90bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4a7f1140-9e83-4492-a013-7a1356e852a1 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2d 0e 16 42 54 a2 35 4c  76 17 70 f3 f8 1d a7 d5  |-..BT.5Lv.p.....|
00000010  b4 20 3d 8e a3 23 82 4e  db 38 b3 d6 0b 04 cb f7  |. =..#.N.8......|
00000020  63 ae 44 83 58 4f 6e 45  56 5f 0d d3 19 0e 49 76  |c.D.XOnEV_....Iv|
00000030  27 77 f0 38 1d 85 33 12  76 c3 31 55 86 15 6e 0b  |'w.8..3.v.1U..n.|
00000040  8f 2d cc 21 9a d4 e0 c2  5a 7a ec d0 cb 44 f9 c2  |.-.!....Zz...D..|
00000050  ed d0 b5 c9 d6 4f 2c 03  d6 9e ae d5 8f 44 c1 3d  |.....O,......D.=|
00000060  75 41 11 a1 82 32 28 e6  d0 3a 69 f6 da 60 70 15  |uA...2(..:i..`p.|
00000070  5f 22 88 f5 e2 dd 01 50  26 af 0e b7 c7 9c f7 35  |_".....P&......5|
00000080  11 b3 92 5e 25 50 51 63  d3 70 6c a7 f3 eb db 17  |...^%PQc.pl.....|
00000090  76 31 01 5a 0a b4 cf 63  d6 65 5a cb f6 64 31 7c  |v1.Z...c.eZ..d1||
000000a0  d7 b1 05 d4 5b 2b 98 1e  9e cc 99 22 24 34 36 7b  |....[+....."$46{|
000000b0  69 a8 cf 2a 50 ab 1d 03  fb 29 6a 6e 16 c8 b9 83  |i..*P....)jn....|
000000c0  58 6f 4e 5a ce f8 bb eb  8f 26 d5 a4 89 e3 db 1e  |XoNZ.....&......|
000000d0  18 8d 17 9e fc 74 af 33  5f e8 e6 31 67 b9 f3 cb  |.....t.3_..1g...|
000000e0  23 91 cf a2 84 bd 85 29  8d 38 44 25 e5 ce f8 db  |#......).8D%....|
000000f0  7d 5b e4 10 c2 c6 3f b9  f5 bc cf b2 20 b4 a1 11  |}[....?..... ...|
00000100  97 b6 55 ec 79 6f 54 76  29 3a c9 ac ab 6d d7 1c  |..U.yoTv):...m..|
00000110  88 f5 41 f4 09 fd 59 d5  9e c7 7b b6 ab f4 c6 fd  |..A...Y...{.....|
00000120  41 36 db df 0e dd e9 13  0c 7f 61 f2 01 8c 39 f3  |A6........a...9.|
00000130  79 53 a7 56 f3 df e8 d5  ce cd 23 a5 a2 e8 7d 47  |yS.V......#...}G|
00000140  2f 50 4a be b7 da ad 64  35 dc b7 3f 2c 3f d3 ed  |/PJ....d5..?,?..|
00000150  0d 62 af 21 12 7f 8e 26  48 87 ed 49 0c eb ad e7  |.b.!...&H..I....|
00000160  28 cb d9 40 32 0f 46 44  5e b1 df 38 58 2a fc 0b  |(..@2.FD^..8X*..|
00000170  59 c5 5e 98 bd 8a 53 39  60 bb 81 a4 d2 74 97 14  |Y.^...S9`....t..|
00000180  e5 47 6e cc 4d ad 25 eb  9a a0 04 37 66 52 0e 95  |.Gn.M.%....7fR..|
00000190  3f d3 29 6c ff 5d e7 87  e7 24 14 ad 93 2a e5 17  |?.)l.]...$...*..|
000001a0  4c b8 78 f3 e5 6e c0 8f  ce 9c 64 e6 82 f9 89 70  |L.x..n....d....p|
000001b0  04 a6 71 0d e1 5b ed bb  67 d2 4a 4c b7 ad 00 fe  |..q..[..g.JL....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 04 dc 81 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 06 dc  81 00 fc 23 c7 00 00 00  |...........#....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc

---

### Post by woody_uk on 2010-08-15
I have read this thread, seeking a solution to my problem, but to no avail.
Can anyone help me please? I am rather at the end of my tether.
I installed Xubuntu under Vista - all was well until I entered an update process
which required a reboot. Now, on booting the pc, I get:

error: no such device: 00c4e25f-9eef-4f3f-9592-1c897afc41ee
grub rescue>

The only command that yields a response is:

grub rescue> ls
(hd0)
grub rescue>

so I gues I have a hard drive(!)
I see repeated references to booting from the Ubuntu LiveCD - I have tried
burning one but have struggled with that. I managed to change the boot order
so that the machine appears to attempt booting from the CD/DVD drive, though
I am not 100% sure of that even.

Any suggestions?

---

### Post by Bendominic on 2010-08-18
Pls i have this kinda problem with grub rescue and its making me go mad!!!:mad: 
pls i need a solution urgently i got loads of assignment and project to do plsssss, i just feel like hitin ma lapi con the wall right now](*,) 
**this is what rly happend**
 
I was using Windows 7 OS i later installed Ubuntu from the windows GUI bt into another partition which is NTFS formated, after the installation i restarted the system and was able to see both windows and Ubuntu on start up i selected ubuntu and it worked perfectly. I've been using both the OS (Windows and Ubuntu) for like 2 weeks now till two dayz ago i was on Ubuntu then i tried to update the ubuntu the update went succesfully but as usual it promted that the OS needs to be restarted  to complete the update. 
I then restarted the system, it didnt even reach the stage of selecting b/w the OS before it displays a command prompt screen showin
 
"eror: no such device: c1e2fb5e-c42d-4fde-......-etc
grub rescue> "
 
i tried all the commands i know from windows even "help" and "pls help" command but it only replies with "Unknown command" 
I'm not good with linux OS, so i dnt even know wre to start, bt I'm sure that the windows is still intact that the ubuntu grub rescue screen is blocking it from reaching the windows ntldr..
 
pls what can i do to get back to my Windows,i rly the data on my windows partition badly! 
 
Pls i need help form you gurus.. and I'm gonna be very gr8tful...
;)

---

### Post by presence1960 on 2010-08-18
> **Bendominic said:**
> Pls i have this kinda problem with grub rescue and its making me go mad!!!:mad: 
pls i need a solution urgently i got loads of assignment and project to do plsssss, i just feel like hitin ma lapi con the wall right now](*,) 
**this is what rly happend**
 
I was using Windows 7 OS i later installed Ubuntu from the windows GUI bt into another partition which is NTFS formated, after the installation i restarted the system and was able to see both windows and Ubuntu on start up i selected ubuntu and it worked perfectly. I've been using both the OS (Windows and Ubuntu) for like 2 weeks now till two dayz ago i was on Ubuntu then i tried to update the ubuntu the update went succesfully but as usual it promted that the OS needs to be restarted  to complete the update. 
I then restarted the system, it didnt even reach the stage of selecting b/w the OS before it displays a command prompt screen showin
 
"eror: no such device: c1e2fb5e-c42d-4fde-......-etc
grub rescue> "
 
i tried all the commands i know from windows even "help" and "pls help" command but it only replies with "Unknown command" 
I'm not good with linux OS, so i dnt even know wre to start, bt I'm sure that the windows is still intact that the ubuntu grub rescue screen is blocking it from reaching the windows ntldr..
 
pls what can i do to get back to my Windows,i rly the data on my windows partition badly! 
 
Pls i need help form you gurus.. and I'm gonna be very gr8tful...
;)

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by mac67 on 2010-08-21
I also got grub rescue prompt, and somehow I fixed the problem. I tell you what happened. I am no Ubuntu geek, so please take my following words with caution.

What I had when everything worked fine:

a) partition 1 on my pc: Vista
b) partition 2 on my pc: Kubuntu 10.4
c) a hard drive connected via USB containing Xubuntu 9.10

I upgraded Xubuntu 9.10 to Xubuntu 10.4, without removing the pc hard disk (BIG ERROR!). This was the result:

1) when switching on the pc with USB connected, the grub from external hard disk started, giving all boot options (Vista, Kubuntu, Xubuntu);
2) when switching on the pc without USB connection, I got the grub-rescue prompt

So, I used step 1 to boot Kubuntu, disconnected the USB hard disk and looked for a solution. After google-ing "grub rescue prompt" and reading many suggestions containing long procedures, I found a short one, and thus I tried the following:

1) Opened a terminal
2) wrote "sudo dpkg reconfigure grub-pc"
3) just said "OK" to anything was prompted

and it worked! Now everything is OK again.

I am NOT claiming that the "sudo dpkg reconfigure grub-pc" is the solution to all grub rescue issues. I just want to tell you my experience. Hope it can help.

---

### Post by ubankan0819 on 2010-08-21
> **Tufty said:**
> I'm happy for anyone else reading this to help if they can. I really need to get the PC booting again ASAP.

   Such a problem I faced last week. I couldn't get my hd with ubuntu 9.10 to mount.  When starts my pc was showing:  GRUB loading error:unknown filesystem grub rescue>  I used 'Super Grub Disk bootable cd' and loged on to Ubuntu 9.10.  Then I typed &quot;sudo grub-install  /dev/sda&quot;  Result came out:  Searching for GRUB installation directory ... found: /boot/grub Installing GRUB to /dev/sda as (hd0)... Installation finished. No error reported. This is the contents of the device map /boot/grub/device.map. Check if this is correct or not. If any of the lines is incorrect, fix it and re-run the script `grub-install'.  (hd0)    /dev/sda  Now my pc is loading perfectly.

---

### Post by cpcpcp on 2010-08-22
my Acer  netbook with 10.4 installed will now only book from USB distro stick otherwise Grub rescue pops up. Despite my bet efforts all my data is still in place. When it first happened I installed 9.10 followed by 10.4 netbook version I confuse myself and the install by having a SD disk which confused the installation.
Here is teh result of boot info script 

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    14,983,167    14,981,120  83 Linux
/dev/sda2          14,985,214    15,759,359       774,146   5 Extended
/dev/sda5          14,985,216    15,759,359       774,144  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,047     7,817,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        1b6747b0-3fdd-4bf8-a61c-c84731eb3bba   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        409bf295-8888-4a4d-b477-25f9643d800d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0C7D-1D30                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=409bf295-8888-4a4d-b477-25f9643d800d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/core.img
   5.0GB: boot/grub/grub.cfg
   5.9GB: boot/initrd.img-2.6.32-21-generic
   6.0GB: boot/initrd.img-2.6.32-24-generic
   5.6GB: boot/vmlinuz-2.6.32-21-generic
   5.8GB: boot/vmlinuz-2.6.32-24-generic
   6.0GB: initrd.img
   5.9GB: initrd.img.old
   5.8GB: vmlinuz
   5.6GB: vmlinuz.old 
```

As you can see it is a fine old mess.
Simple suggestions for a confused old soul please

---

### Post by Duke57 on 2010-09-02
Please help! I'm stuck at Grub Rescue prompt after attempting install of Ubuntu 10.04 on my brother's 7 yr-old Compaq SR1040 desktop which has XP. Wanted both OS's.
 
Attached is Boot Info Script results text file. I can't boot windows at all. I'm concerned that SDA2 not mounting. I can boot Ubuntu from CD.
 
When I boot from hard drive, I'm stuck with grub rescue prompt. Doesn't seem like any commands I enter, other than "ls" works.
 
I'm in remote area in NH with limited Internet access. I was hoping Ubuntu could be used to speed up dial-up use. I will have to drive to a library in town to get to working computer to receive or post any further messages.
 
Thanks for help!

---

### Post by mclovin91 on 2010-09-07
Got Grub Rescue error after trying to Dual Boot 10.04 and Windows 7. I'm completely new to Ubuntu so I'm lost at this point.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdi

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 222590176 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       40962047 sectors, but according to the info from 
                       fdisk, it has 40963701 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   303,706,111   303,704,064  83 Linux
/dev/sda2         303,708,158   312,498,175     8,790,018   5 Extended
/dev/sda5         303,708,160   312,498,175     8,790,016  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    40,965,749    40,963,702   7 HPFS/NTFS
/dev/sdc2          40,965,750    81,915,434    40,949,685   7 HPFS/NTFS
/dev/sdc3          81,915,435   625,137,344   543,221,910   7 HPFS/NTFS


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdi1                  63   976,768,064   976,768,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ba547310-9ca5-4517-b85a-6c5fa54ea192   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c572eeab-24ef-44a6-a326-ac34c388f385   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        34B4ADEAB4ADAF34                       ntfs                                     
/dev/sdc2        4D13831F6B95A8A5                       ntfs                                     
/dev/sdc3        0D1BB505762CE05B                       ntfs       Storage                       
/dev/sdc: PTTYPE="dos" 
/dev/sdi1        AA9D-F0BC                              vfat       My Book                       
/dev/sdi: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdi1        /media/My Book           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/Ubuntu 10.04.1 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set ba547310-9ca5-4517-b85a-6c5fa54ea192
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set ba547310-9ca5-4517-b85a-6c5fa54ea192
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ba547310-9ca5-4517-b85a-6c5fa54ea192
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=ba547310-9ca5-4517-b85a-6c5fa54ea192 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ba547310-9ca5-4517-b85a-6c5fa54ea192
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=ba547310-9ca5-4517-b85a-6c5fa54ea192 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ba547310-9ca5-4517-b85a-6c5fa54ea192
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ba547310-9ca5-4517-b85a-6c5fa54ea192
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ba547310-9ca5-4517-b85a-6c5fa54ea192 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c572eeab-24ef-44a6-a326-ac34c388f385 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 113.9GB: boot/grub/core.img
  49.5GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.32-24-generic
 113.9GB: boot/vmlinuz-2.6.32-24-generic
    .6GB: initrd.img
 113.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 
```

---

### Post by cristian.ene on 2011-02-24
Hmm... i have a problem too... after using gparted... to delete my ntfs part, and increase my linxu partition, moving (by copying or deletin)  SWAP and one other partition, used for system... 

i ended up having "[PHP]Error: file not foud.
grub rescue>[/PHP]

---

### Post by wilfgilbert on 2011-03-06
Hi, I just tried to install ubuntu onto my laptop by installing onto an  SD card. The installation seems to run successfully and then prompts me  to reboot. However once I do so I get nothing but a grub rescue prompt,  the sd card is still in. This now means I can't access the ubuntu I just  installed and I also can't access the windows partition. As you can  imagine I'm a little worried :razz:. 

Please bear in mind I'm new to this and may come across as a bit dim!

I tried running a script I found on another forum here (link to script here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/))

and got this result: ```
 Boot Info Script 0.55    dated February 15th, 2010                      ============================= Boot Info Summary: ==============================   => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in      partition #1 for (,msdos1)/boot/grub.  => No boot loader is installed in the MBR of /dev/sdb  sda1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:   /bootmgr /boot/bcd  sda2: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:   /bootmgr /Boot/BCD  sda3: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files/dirs:   /Windows/System32/winload.exe  sda4: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sdb1: _________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:  Ubuntu 10.10     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sdb2: _________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:    sdb5: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    =========================== Drive/Partition Info: =============================  Drive: sda ___________________ _____________________________________________________  Disk /dev/sda: 320.1 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sda1               2,048    41,945,087    41,943,040  27 Hidden HPFS/NTFS /dev/sda2    *     41,945,088    42,149,887       204,800   7 HPFS/NTFS /dev/sda3          42,149,888   333,653,984   291,504,097   7 HPFS/NTFS /dev/sda4         333,653,985   625,137,344   291,483,360   7 HPFS/NTFS   Drive: sdb ___________________ _____________________________________________________  Disk /dev/sdb: 7948 MB, 7948206080 bytes 245 heads, 62 sectors/track, 1021 cylinders, total 15523840 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sdb1               2,048    14,753,791    14,751,744  83 Linux /dev/sdb2          14,755,838    15,521,791       765,954   5 Extended /dev/sdb5          14,755,840    15,521,791       765,952  82 Linux swap / Solaris   blkid -c /dev/null: ____________________________________________________________  Device           UUID                                   TYPE       LABEL                           /dev/loop0                                              squashfs                                  /dev/sda1        828E78DB8E78C8E5                       ntfs       RECOVERY                       /dev/sda2        76787A037879C303                       ntfs       SYSTEM                         /dev/sda3        01CBA5163B8003E0                       ntfs                                      /dev/sda4        01CBA51778D559B0                       ntfs                                      /dev/sda: PTTYPE="dos"  /dev/sdb1        f95855f5-1582-44e9-9b67-194cb79524a3   ext4                                      /dev/sdb2: PTTYPE="dos"  /dev/sdb5        53435190-112d-491b-b017-89bf6d930324   swap                                      /dev/sdb: PTTYPE="dos"   ============================ "mount | grep ^/dev  output: ===========================  Device           Mount_Point              Type       Options  aufs             /                        aufs       (rw) /dev/sr0         /cdrom                   iso9660    (ro,noatime) /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sda3        /media/01CBA5163B8003E0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)   =========================== sdb1/boot/grub/grub.cfg: ===========================  # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga }  insmod part_msdos insmod ext2 set root='(hd1,msdos1)' search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3 if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=640x480   load_video   insmod gfxterm fi terminal_output gfxterm insmod part_msdos insmod ext2 set root='(hd1,msdos1)' search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3 set locale_dir=($root)/boot/grub/locale set lang=en insmod gettext if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     insmod part_msdos     insmod ext2     set root='(hd1,msdos1)'     search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3     linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=f95855f5-1582-44e9-9b67-194cb79524a3 ro   quiet splash     initrd    /boot/initrd.img-2.6.35-27-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     insmod part_msdos     insmod ext2     set root='(hd1,msdos1)'     search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3     echo    'Loading Linux 2.6.35-27-generic-pae ...'     linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=f95855f5-1582-44e9-9b67-194cb79524a3 ro single      echo    'Loading initial ramdisk ...'     initrd    /boot/initrd.img-2.6.35-27-generic-pae } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" {     insmod part_msdos     insmod ext2     set root='(hd1,msdos1)'     search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3     linux16    /boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" {     insmod part_msdos     insmod ext2     set root='(hd1,msdos1)'     search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3     linux16    /boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Windows Vista (loader) (on /dev/sda1)" {     insmod part_msdos     insmod ntfs     set root='(hd0,msdos1)'     search --no-floppy --fs-uuid --set 828e78db8e78c8e5     chainloader +1 } menuentry "Windows 7 (loader) (on /dev/sda2)" {     insmod part_msdos     insmod ntfs     set root='(hd0,msdos2)'     search --no-floppy --fs-uuid --set 76787a037879c303     chainloader +1 } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ###  =============================== sdb1/etc/fstab: ===============================  # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sdb1 during installation UUID=f95855f5-1582-44e9-9b67-194cb79524a3 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sdb5 during installation UUID=53435190-112d-491b-b017-89bf6d930324 none            swap    sw              0       0  =================== sdb1: Location of files loaded by Grub: ===================      2.8GB: boot/grub/core.img    2.7GB: boot/grub/grub.cfg    1.7GB: boot/initrd.img-2.6.35-27-generic-pae    2.8GB: boot/vmlinuz-2.6.35-27-generic-pae    1.7GB: initrd.img    2.8GB: vmlinuz
```

---

### Post by hidudeashu on 2011-07-30
i m using ubuntu 10.10 & i m having windows 7 .I installed ubuntu 10.10 in pen drive while booting if i m not inserting pen drive an error is coming if i m putting pen drive boot loader is working please help how to delete that device from boot loader & boot loader will boot without using pen drive

---

### Post by YesWeCan on 2011-07-30
Is this thread like the local booting clinic? ;) I think I have counted no less than 21 posters with Grub/installer problems!

If it is of any help, one of the more common problems with the Ubuntu installer on the desktop ISO is that it defaults to installing the Grub MBR code to the sda hard disk, even if you have chosen to install Ubuntu on an entirely different disk. There are no warnings or confirmations asked for.

This causes a bizarre problem if you have tried to install Ubuntu to an external disk and then disconnect that disk because the Grub boot code on sda (usually your internal disk) cannot find files it needs on the external disk and you end up not being able to boot anything.

---

### Post by YesWeCan on 2011-07-30
> **hidudeashu said:**
> i m using ubuntu 10.10 & i m having windows 7 .I installed ubuntu 10.10 in pen drive while booting if i m not inserting pen drive an error is coming if i m putting pen drive boot loader is working please help how to delete that device from boot loader & boot loader will boot without using pen drive
An example.
I infer you have Windows7 on your internal disk and you wanted to install Ubuntu on your external pen drive because you did not want to interfere with your Windows installation? But when you installed to the pen drive the installer put the Grub MBR boot code on your Windows7 disk without you realising it - and wiped out the standard MBR code on that disk.

So you need to boot into Ubuntu on the pen drive and install the Grub code to the pen drive. Then you need to repair your Windows MBR boot code. You then need to set your bios boot order to pen drive 1st and Windows disk 2nd, so that when the pen drive is not there you boot into Windows.

---

### Post by YesWeCan on 2011-07-30
> **cristian.ene said:**
> Hmm... i have a problem too... after using gparted... to delete my ntfs part, and increase my linxu partition, moving (by copying or deletin)  SWAP and one other partition, used for system... 

i ended up having "[PHP]Error: file not foud.
grub rescue>[/PHP]
In this case the information that the Grub boot program uses to locate your root/boot partition has changed. This can happen when you move or change the name of a partition. So the Grub boot program needs to be reinstalled to the MBR area. You can do this using your live CD:

Boot live CD
[COLOR=Navy]sudo fdisk -l[/COLOR]   #to see what disks and partitions you have

[COLOR=Navy]sudo mount /dev/sdxy /mnt[/COLOR]   #where x is the disk letter and y is the partition number of the root partition (or separate boot partition if you have one) 
[COLOR=Navy]sudo grub-install --root-directory=/mnt /dev/sdx[/COLOR]

---

### Post by YesWeCan on 2011-07-30
> **wilfgilbert said:**
> Hi, I just tried to install ubuntu onto my laptop by installing onto an  SD card. The installation seems to run successfully and then prompts me  to reboot. However once I do so I get nothing but a grub rescue prompt,  the sd card is still in. This now means I can't access the ubuntu I just  installed and I also can't access the windows partition. As you can  imagine I'm a little worried :razz:. 
Hi. Your bootinfoscript output is completely unreadable - lots of carriage returns missing. You'll have to figure that out before anyone can help easily.

Again, you've probably installed the Grub code to the Windows disk MBR. I assume when you remove the SD card you still get a Grub rescue prompt?

---

### Post by YesWeCan on 2011-07-30
> **mclovin91 said:**
> Got Grub Rescue error after trying to Dual Boot 10.04 and Windows 7. I'm completely new to Ubuntu so I'm lost at this point.
So you have Ubuntu and Windows on separate disks, which is the BEST way to dual boot.
However, you have the Grub boot code in the Ubuntu disks MBR and its 10.04 OS partition. So something may be a little messed up.
And your Windows disk sdc also has Grub boot code in its MBR which is wrong - it should keep its original Windows MBR code.

1) The problem might be simply that your bios is set to boot the Windows disk first. Try it booting the Ubuntu disk first.
2) Otherwise, you need to resintall Grub to the MBR of your Ubuntu disk using your 10.04 live CD.
3) You should restore your Windows MBR to sdc by booting your Windows installation CD and using the repair options.

In general, for other reading this, it is a good precaution to disconnect your Windows disk when installing Ubuntu to another disk. It is not necessary, but it just avoids accidentally destroying your Windows MBR code; so why take the risk.

---

### Post by YesWeCan on 2011-07-30
> **Duke57 said:**
> Please help! I'm stuck at Grub Rescue prompt after attempting install of Ubuntu 10.04 on my brother's 7 yr-old Compaq SR1040 desktop which has XP. Wanted both OS's.
 
Attached is Boot Info Script results text file. I can't boot windows at all. I'm concerned that SDA2 not mounting. I can boot Ubuntu from CD.
 
When I boot from hard drive, I'm stuck with grub rescue prompt. Doesn't seem like any commands I enter, other than "ls" works.
 
I'm in remote area in NH with limited Internet access. I was hoping Ubuntu could be used to speed up dial-up use. I will have to drive to a library in town to get to working computer to receive or post any further messages.
 
Thanks for help!
Hi. This is a little tricky because your laptop is so old and so some repair options may not work. It is also tricky because you have limited access to this forum.

Fall back fix (in case the Grub reinstall fix fails to work):
This should get Windows booting again. It installs a standard MBR.
Boot the Ubuntu live CD. Then run
[COLOR=Navy]sudo apt-get install lilo[/COLOR] (just ignore warnings)
[COLOR=Navy]sudo lilo -M /dev/sda mbr[/COLOR]

Grub reinstall fix:
Boot Ubuntu live CD. Then run
[COLOR=Navy]sudo mount /dev/sdf5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

If neither work you'll have to find a Windows install CD and run the repair options.

---

### Post by YesWeCan on 2011-07-30
> **cpcpcp said:**
> my Acer  netbook with 10.4 installed will now only book from USB distro stick otherwise Grub rescue pops up. Despite my bet efforts all my data is still in place. When it first happened I installed 9.10 followed by 10.4 netbook version I confuse myself and the install by having a SD disk which confused the installation.
As you can see it is a fine old mess.
Simple suggestions for a confused old soul please
The bootinfoscript output doesn't look too messy. You seem to have lilo in the MBR of sda rather than Grub? Is this deliberate? So it is not clear to me how you are booting the Grub boot code at all.

If you want Grub in the MBR (which is normal) do this:
Boot from live 10.04 CD/USB
[COLOR=Navy]sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

---

### Post by YesWeCan on 2011-07-30
OK, that's 6 responded to. I'll take a break and wait for results :o. Hopefully at least one will work! ;)

[edit] Ha ha. I just noticed how old these posts are! Note to self: open your eyes. :p

---

### Post by progone on 2011-08-31
> **unclesamslair said:**
> I only got this far.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda5/ /mnt && sudo mount -bind /dev /mnt/dev && sudo mount -bind /proc /mnt/proc && sudo chroot /mnt
mount: invalid option -- 'b'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount –bind /dev /mnt/dev && sudo mount –bind /proc /mnt/proc && sudo chroot /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ grub-install /dev/sda
grub-mkdevicemap: error: cannot open /boot/grub/device.map
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ grub-install /dev/sda5
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ 


```

I'm afraid to go any further and type ```
sudo grub-install /dev/sda5
``` and cause permanent damage.

I wish I could boot from any liveCD or USB. My system is crashing right after I pick "Try Ubuntu" and selecting from any of my linux distros.  I can load up Vista fine thou. 

Any suggestions from grub rescue>

---

### Post by whiskers751 on 2012-03-15
Try this guide:

[http://karuppuswamy.com/wordpress/2011/09/09/how-to-fix-grub-rescue-prompt-without-live-cd-for-grub2/](http://karuppuswamy.com/wordpress/2011/09/09/how-to-fix-grub-rescue-prompt-without-live-cd-for-grub2/)

Or just reinstall GRUB:

[http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)

---

### Post by haha8808 on 2012-04-19
there is no need to do all that stuff, all you need to do if you are new to linux and dual-booting to windows is to put the burned linux CD in the tray and install it to another partition and THEN you can acces windows from that point.

---

### Post by crazysoo on 2012-05-25
check out this very good tutorial that shows how to come out from 
Grub Rescue prompt and recover your ubuntu instalation with live cd
[http://youtu.be/ZcbTgMKpVHQ](http://youtu.be/ZcbTgMKpVHQ)

---

