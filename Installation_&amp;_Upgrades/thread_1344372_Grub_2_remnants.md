---
title: "Grub 2 remnants"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Kim Foltz on 2009-12-02
I have installed Ubuntu 9.10 with Grub 2. The boot menu works but after the Windows 2000 entry it displays remnants from Ubuntu 9.04 kernel 2.6.28-16-generic. Synaptic shows 2.6.28-16-generic was removed from the computer. How do I remove the remnant from the Grub 2 menu?

---

### Post by presence1960 on 2009-12-02
> **Kim Foltz said:**
> I have installed Ubuntu 9.10 with Grub 2. The boot menu works but after the Windows 2000 entry it displays remnants from Ubuntu 9.04 kernel 2.6.28-16-generic. Synaptic shows 2.6.28-16-generic was removed from the computer. How do I remove the remnant from the Grub 2 menu?

from 9.10 open a terminal and run ```
sudo update-grub
``` and see if that fixes it.

---

### Post by Kim Foltz on 2009-12-03
> **presence1960 said:**
> from 9.10 open a terminal and run ```
sudo update-grub
``` and see if that fixes it.

I had ran the command before submitting the question and was puzzled when it didn't work. Tried running it again in response to your comment. It still doesn't change the Grub boot menu. In the messages the command generates it says "Found Ubuntu 9.04 on /dev/sda6". Some remnant is hanging around I don't know how to remove.

---

### Post by presence1960 on 2009-12-03
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Kim Foltz on 2009-12-04
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Hmm...
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #10 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb1b1b1b1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    32,772,599    32,772,537   7 HPFS/NTFS
/dev/sda2          32,772,600    88,984,034    56,211,435   7 HPFS/NTFS
/dev/sda3          88,984,035   490,223,474   401,239,440   f W95 Ext d (LBA)
/dev/sda5          88,984,098    89,176,814       192,717  83 Linux
/dev/sda6          89,176,878   108,615,464    19,438,587  83 Linux
/dev/sda7         108,615,528   112,519,259     3,903,732  82 Linux swap / Solaris
/dev/sda8         112,519,323   159,991,334    47,472,012  83 Linux
/dev/sda9         195,366,528   490,223,474   294,856,947   7 HPFS/NTFS
/dev/sda10        159,991,398   193,792,094    33,800,697  83 Linux
/dev/sda11        193,792,158   195,366,464     1,574,307  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="36E81885E8184591" LABEL="Drumline" TYPE="ntfs" 
/dev/sda2: UUID="461C94601C944CB5" LABEL="Soccer" TYPE="ntfs" 
/dev/sda5: UUID="6ef2b75b-6bfd-458a-9960-15de5a01a2e8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="1df76587-7ead-45bc-b1bd-62d5a413bd40" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="fe4d2baf-5e81-4f59-884f-974c4b457fa1" TYPE="swap" 
/dev/sda8: UUID="17d9ffd6-7f41-4d4d-8dac-f65344fcdd08" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="43A44A4A51843FCB" LABEL="Music" TYPE="ntfs" 
/dev/sda10: UUID="237b54a0-646a-4107-b55f-b6fb569dfd77" TYPE="ext4" 
/dev/sda11: UUID="7410d407-75b1-4392-92aa-09af10752361" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda10 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//Snooziebear3-4/Quicken on /media/quickendata type cifs (rw,mand)
gvfs-fuse-daemon on /home/kim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kim)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect


============================= sda5/grub/menu.lst: =============================

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
# kopt=root=UUID=1df76587-7ead-45bc-b1bd-62d5a413bd40 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6ef2b75b-6bfd-458a-9960-15de5a01a2e8

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		6ef2b75b-6bfd-458a-9960-15de5a01a2e8
kernel		/vmlinuz-2.6.28-16-generic root=UUID=1df76587-7ead-45bc-b1bd-62d5a413bd40 ro quiet splash 
initrd		/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		6ef2b75b-6bfd-458a-9960-15de5a01a2e8
kernel		/vmlinuz-2.6.28-16-generic root=UUID=1df76587-7ead-45bc-b1bd-62d5a413bd40 ro  single
initrd		/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, memtest86+
uuid		6ef2b75b-6bfd-458a-9960-15de5a01a2e8
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=================== sda5: Location of files loaded by Grub: ===================


  45.5GB: grub/menu.lst
  45.5GB: grub/stage2
  45.5GB: initrd.img-2.6.27-14-generic
  45.5GB: initrd.img-2.6.28-16-generic
  45.5GB: vmlinuz-2.6.28-16-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=1df76587-7ead-45bc-b1bd-62d5a413bd40 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=6ef2b75b-6bfd-458a-9960-15de5a01a2e8 /boot ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=17d9ffd6-7f41-4d4d-8dac-f65344fcdd08 /home ext3 relatime 0 2
# Entry for /dev/sda7 :
UUID=fe4d2baf-5e81-4f59-884f-974c4b457fa1 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda9 /media/ntfs ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda10 /media/ntfs-two ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/Soccer ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Drumline ntfs-3g defaults,locale=en_US.UTF-8 0 0

========================== sda10/boot/grub/grub.cfg: ==========================

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
set root=(hd0,10)
search --no-floppy --fs-uuid --set 237b54a0-646a-4107-b55f-b6fb569dfd77
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
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 237b54a0-646a-4107-b55f-b6fb569dfd77
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=237b54a0-646a-4107-b55f-b6fb569dfd77 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 237b54a0-646a-4107-b55f-b6fb569dfd77
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=237b54a0-646a-4107-b55f-b6fb569dfd77 ro single  splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 237b54a0-646a-4107-b55f-b6fb569dfd77
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=237b54a0-646a-4107-b55f-b6fb569dfd77 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 237b54a0-646a-4107-b55f-b6fb569dfd77
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=237b54a0-646a-4107-b55f-b6fb569dfd77 ro single  splash
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
menuentry "Microsoft Windows 2000 Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 36e81885e8184591
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6ef2b75b-6bfd-458a-9960-15de5a01a2e8
	linux /vmlinuz-2.6.28-16-generic root=UUID=1df76587-7ead-45bc-b1bd-62d5a413bd40 ro quiet splash
	initrd /initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6ef2b75b-6bfd-458a-9960-15de5a01a2e8
	linux /vmlinuz-2.6.28-16-generic root=UUID=1df76587-7ead-45bc-b1bd-62d5a413bd40 ro single
	initrd /initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6ef2b75b-6bfd-458a-9960-15de5a01a2e8
	linux /memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=237b54a0-646a-4107-b55f-b6fb569dfd77 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=7410d407-75b1-4392-92aa-09af10752361 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# mount quicken folder on Snoozie's computer
//Snooziebear3-4/Quicken  /media/quickendata  cifs  guest,rw,iocharset=utf8,filemode=0777,dirmode=0777 0 0

=================== sda10: Location of files loaded by Grub: ===================


  81.9GB: boot/grub/grub.cfg
  81.9GB: boot/initrd.img-2.6.31-14-generic
  81.9GB: boot/initrd.img-2.6.31-15-generic
  81.9GB: boot/vmlinuz-2.6.31-14-generic
  81.9GB: boot/vmlinuz-2.6.31-15-generic
  81.9GB: initrd.img
  81.9GB: initrd.img.old
  81.9GB: vmlinuz
  81.9GB: vmlinuz.old

---

### Post by presence1960 on 2009-12-04
There are no "remnants" of 9.04. It looks like you have root (/) on sda6 and /boot on sda5 which is a 9.04 install. If you don't want 9.04 then remove sda5 & sda6 from gparted and then run from terminal ```
sudo update-grub
```

If you want 9.04 and it won't boot from GRUB 2 then we'll try to work on that. To sum it up you have both 9.04 & 9.10 installed.

---

### Post by Kim Foltz on 2009-12-08
> **presence1960 said:**
> There are no "remnants" of 9.04. It looks like you have root (/) on sda6 and /boot on sda5 which is a 9.04 install. If you don't want 9.04 then remove sda5 & sda6 from gparted and then run from terminal ```
sudo update-grub
```

If you want 9.04 and it won't boot from GRUB 2 then we'll try to work on that. To sum it up you have both 9.04 & 9.10 installed.

The selection never worked on the boot menu so I assumed it was a remnant. When I went looking there was a 99 mb partition with the previous, 9.04, version on it. Deleted it and ran update-grub and everything is correct now. Thanks for the help.

---

### Post by presence1960 on 2009-12-08
> **Kim Foltz said:**
> The selection never worked on the boot menu so I assumed it was a remnant. When I went looking there was a 99 mb partition with the previous, 9.04, version on it. Deleted it and ran update-grub and everything is correct now. Thanks for the help.

glad you got it sorted out. Enjoy Ubuntu.

---

