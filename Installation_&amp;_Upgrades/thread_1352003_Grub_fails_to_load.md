---
title: "Grub fails to load"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by FOSman on 2009-12-11
Short version:
I'm having a similar problem to what LarCrow is having here:
[http://ubuntuforums.org/showthread.php?t=1349151&highlight=grub+load](http://ubuntuforums.org/showthread.php?t=1349151&highlight=grub+load)
However, I'm using Kubuntu 9.10, in case that makes any difference.

I've followed the suggestions in that thread with no luck so far.  However, I think I have at least discovered a clue toward the problem, which appears to be that the entry for booting to the primary drive is missing.  From here, I don't know what I need to do to fix things.  Any and all help would be appreciated.  Thanks.

Long version:
I horked my Kubuntu install, which I had been running and updating since Hardy, after trying to fix some sound issues that cropped up for me with the latest version upgrade.  So I decided to reformat and do a fresh install using the Kubuntu 9.10 i386 DVD install disk.

Everything seemed to go fine until the system tried to load grub, at which point all it says is "GRUB loading, please wait..." and does nothing.  After a couple more attempts, just to make sure I hadn't accidentally hit a key or something, I rebooted to the DVD and selected the "rescue a broken system" option, then went through the menus until it got to the choice for reinstalling grub.  I chose that and typed in "(hd0)" which was what the instructions indicated would work to install grub on the primary partition of the primary drive.  Hit enter, and after waiting a couple seconds, I got a message that said grub had been successfully installed.  So, I rebooted again, but the result was the same.  The system hung on "GRUB loading, please wait...."

I then tried the following, which was suggested in the thread I linked to above:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```
That also didn't work.

So I used the Boot Info Script linked in that thread.  Here's the results:
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 6.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 6.06.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdd1 has 
                       -1364695294 sectors.. But according to the info from 
                       the partition table , it has 2930272002 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00066431

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,445,496,569 1,445,496,507  83 Linux
/dev/sda2       1,445,496,570 1,465,144,064    19,647,495   5 Extended
/dev/sda5       1,445,496,633 1,465,144,064    19,647,432  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b6343

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    35,632,169    35,632,107  83 Linux
/dev/sdb2         228,380,040   234,436,544     6,056,505   5 Extended
/dev/sdb5         228,380,103   234,436,544     6,056,442  82 Linux swap / Solaris
/dev/sdb3          35,632,170   228,380,039   192,747,870  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    78,156,224    78,156,162   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb2d06aa7

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 2,930,272,064 2,930,272,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="c7199983-8dc6-401c-8676-b462a0f3d97b" TYPE="ext4" 
/dev/sda5: UUID="9ca18518-0bd4-41b3-a5bf-c66f6b66e9ec" TYPE="swap" 
/dev/sdb1: UUID="72fc4674-ae33-4945-a128-2dc0cdf783bd" TYPE="ext3" 
/dev/sdb3: UUID="1a20c783-43d7-4ebe-8dac-bc7048933c37" TYPE="ext3" 
/dev/sdb5: TYPE="swap" 
/dev/sdc1: LABEL="LOKI" UUID="384C-1AEF" TYPE="vfat" 
/dev/sdd1: LABEL="SAMSUNG" UUID="12F9-176B" TYPE="vfat" 

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
/dev/sdc1 on /media/LOKI type vfat (rw,nosuid,nodev,uhelper=hal,uid=999,utf8,shortname=mixed,flush)
/dev/sdb3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-1 type ext4 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdd1 on /media/SAMSUNG type vfat (rw,nosuid,nodev,uhelper=hal,uid=999,utf8,shortname=mixed,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set c7199983-8dc6-401c-8676-b462a0f3d97b
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c7199983-8dc6-401c-8676-b462a0f3d97b
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=c7199983-8dc6-401c-8676-b462a0f3d97b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c7199983-8dc6-401c-8676-b462a0f3d97b
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=c7199983-8dc6-401c-8676-b462a0f3d97b ro single 
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
menuentry "Ubuntu, kernel 2.6.15-27-386 (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 72fc4674-ae33-4945-a128-2dc0cdf783bd
	linux /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
	initrd /boot/initrd.img-2.6.15-27-386
}
menuentry "Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 72fc4674-ae33-4945-a128-2dc0cdf783bd
	linux /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
	initrd /boot/initrd.img-2.6.15-27-386
}
menuentry "Ubuntu, kernel 2.6.15-23-386 (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 72fc4674-ae33-4945-a128-2dc0cdf783bd
	linux /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
	initrd /boot/initrd.img-2.6.15-23-386
}
menuentry "Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 72fc4674-ae33-4945-a128-2dc0cdf783bd
	linux /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
	initrd /boot/initrd.img-2.6.15-23-386
}
menuentry "Ubuntu, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 72fc4674-ae33-4945-a128-2dc0cdf783bd
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, kernel 2.6.15-51-386 (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-51-386 root=/dev/hda3 ro quiet splash
	initrd /boot/initrd.img-2.6.15-51-386
}
menuentry "Ubuntu, kernel 2.6.15-51-386 (recovery mode) (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-51-386 root=/dev/hda3 ro single
	initrd /boot/initrd.img-2.6.15-51-386
}
menuentry "Ubuntu, kernel 2.6.15-29-386 (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-29-386 root=/dev/hda3 ro quiet splash
	initrd /boot/initrd.img-2.6.15-29-386
}
menuentry "Ubuntu, kernel 2.6.15-29-386 (recovery mode) (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-29-386 root=/dev/hda3 ro single
	initrd /boot/initrd.img-2.6.15-29-386
}
menuentry "Ubuntu, kernel 2.6.15-28-386 (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash
	initrd /boot/initrd.img-2.6.15-28-386
}
menuentry "Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro single
	initrd /boot/initrd.img-2.6.15-28-386
}
menuentry "Ubuntu, kernel 2.6.15-27-386 (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
	initrd /boot/initrd.img-2.6.15-27-386
}
menuentry "Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
	initrd /boot/initrd.img-2.6.15-27-386
}
menuentry "Ubuntu, kernel 2.6.15-23-386 (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
	initrd /boot/initrd.img-2.6.15-23-386
}
menuentry "Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
	initrd /boot/initrd.img-2.6.15-23-386
}
menuentry "Ubuntu, memtest86+ (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 1a20c783-43d7-4ebe-8dac-bc7048933c37
	linux /boot/memtest86+.bin 
}
menuentry "Windows 95/98/Me (on /dev/sdc1)" {
	insmod fat
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 384c-1aef
	drivemap -s (hd0) ${root}
	chainloader +1
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c7199983-8dc6-401c-8676-b462a0f3d97b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9ca18518-0bd4-41b3-a5bf-c66f6b66e9ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-16-generic-pae
    .0GB: boot/vmlinuz-2.6.31-16-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz

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
# kopt=root=/dev/hda1 ro

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
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows 95/98/Me
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1	/media/windows/ vfat	umask=000	0	0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.15-23-386
    .0GB: boot/initrd.img-2.6.15-27-386
    .0GB: boot/vmlinuz-2.6.15-23-386
    .0GB: boot/vmlinuz-2.6.15-27-386
    .0GB: boot/vmlinuz-2.6.17-10-386
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sdb3/boot/grub/menu.lst: ===========================

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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-51-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-51-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-51-386
boot

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-27-386 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows 95/98/Me
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/hdb1       /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sdb3: Location of files loaded by Grub: ===================


  18.2GB: boot/grub/menu.lst
  18.2GB: boot/grub/stage2
  18.2GB: boot/initrd.img-2.6.15-23-386
  18.2GB: boot/initrd.img-2.6.15-27-386
  18.2GB: boot/initrd.img-2.6.15-28-386
  18.2GB: boot/initrd.img-2.6.15-29-386
  18.2GB: boot/initrd.img-2.6.15-51-386
  18.2GB: boot/vmlinuz-2.6.15-23-386
  18.2GB: boot/vmlinuz-2.6.15-27-386
  18.2GB: boot/vmlinuz-2.6.15-28-386
  18.2GB: boot/vmlinuz-2.6.15-29-386
  18.2GB: boot/vmlinuz-2.6.15-51-386
  18.2GB: initrd.img
  18.2GB: initrd.img.old
  18.2GB: vmlinuz
  18.2GB: vmlinuz.old

```
From what I can tell from this, the boot entry for the primary disk (hda) is missing.  I don't know how that could happen with a fresh install, let alone if that's the reason for GRUB hanging or just a symptom.  In any case, I haven't a clue how to proceed from here.  Again, any help would be appreciated.  Thanks.

P.S.  I've been working on this for about 6 hours, now.  It's late here, and I'm getting a little bleary-eyed, so I'm going to sleep.  I'll check back in to see if anyone's responded as soon as I get a chance tomorrow (today).  That will probably be at least 12 hours from now, so please do not wait for a quick reply.  My apologies if this is an inconvenience.

---

### Post by FOSman on 2009-12-11
Sorry if it's considered rude or something for me to bump this, but I don't exactly have a (usable) operating system right now.  I think the circumstances are extenuating enough for me to be a little pushy.

---

### Post by meierfra. on 2009-12-11
> GRUB loading, please wait..." 

That sounds like a message from Grub 0.97.  So I would guess that your bios are set to boot from your 120 GB hard drive /dev/sdb. 

Try to  change your boot order in the bios, so that you boot from the 750GB hard drive /dev/sda. 

If that does not work, you can also install Grub 1.97 to the MBR of /dev/sdb:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

```

But you should really try to boot from /dev/sda. Booting from /dev/sdb will be slower.

---

### Post by FOSman on 2009-12-11
Thank you!  That got it.

**Edit:**  To be specific, I got the bios boot order sorted out.

---

### Post by meierfra. on 2009-12-11
> Thank you! 

You are welcome. 

Did you change the boot order or did you have to install Grub to /dev/sdb?

---

