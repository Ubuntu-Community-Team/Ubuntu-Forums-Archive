---
title: "grub2 error: no such disk; sda=karmic=gpt; sdb=win7=mbr"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by frafu on 2009-12-06
Hi,

I have two disks on my computer:
- sda (a WD disk) is partitioned using gpt and contains karmic 
- sdb (a Samsung disk) is partitioned using mbr and contains Windows 7 Home Premium Edition 32 bit

Both systems start properly when their disks is the first in the disk boot sequence in BIOS.

Here is how I performed the installation:
- I set the Samsung disk as the first to boot and installed BCD and Windows 7 on partition 3 and 4 of the disk. (Windows refused to install on a gpt disk.)
- Afterwards, I set the WD disk as the first disk in bios and installed karmic on it.

grub.cfg contains menuentries for Windows 7, but when I try to choose it from the grub2 menu list, it tells me "no such disk". I have searched the forums and googled for a solution without success. 

Does anybody know the reason for the problem and tell me a fix for it?


I would also accept a boot manager as a work around to install on the WD disk as sda under the condition (for accessibility reasons: I cannot use a hardware keyboard ) that the boot manager supports the mouse to choose the operating system. In grub2 I use the trick of specifying the system into which to boot next with grub-set-default before restarting. 


Many thanks in advanced for any help.

Francesco

---

### Post by presence1960 on 2009-12-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by louieb on 2009-12-06
The script should tell something. 

but 1st Easy to try - can't hurt
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
More here [IDBS GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html") 

Just wondering why you went with a gpt partition table for the one drive? Is this an Apple computer? - maybe something got confused with the mix of partition table types.

---

### Post by frafu on 2009-12-07
> **louieb said:**
> The script should tell something. 

but 1st Easy to try - can't hurt
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Unfortunately, it did not help.  

> 
Just wondering why you went with a gpt partition table for the one drive? Is this an Apple computer? - maybe something got confused with the mix of partition table types.

I chose gpt because it is an harddisk of 1TB and I wanted to create a lot of partitions. In the meantime I think that it was an error and that I should have used mbr and work with logical partitions inside an extended partition. 

Does anybody know whether I can install grub2 into the PBR of a logical partition of an mbr disk and chainload to it? I already did it with primary partitions if I remember correctly, but what about logical partitions? 

> **presence1960 said:**
> Let's get a better look at your setup & boot process. ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop.

Here is the RESULTS.txt file:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks at sector 
    148873488 of the same hard drive for core.img, core.img is at this 
    location on /dev/sdb and looks on partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda10 and 
                       looks at sector 576906228 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #10 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34     2,104,514     2,104,481 System/Boot Partition
/dev/sda2       2,104,515   102,607,154   100,502,640 Linux (usually)
/dev/sda3     102,607,155   143,572,904    40,965,750 Linux (usually)
/dev/sda4     143,572,905   145,613,159     2,040,255 Linux (usually)
/dev/sda5     145,613,160   248,011,469   102,398,310 Linux (usually)
/dev/sda6     248,011,470   350,409,779   102,398,310 Linux (usually)
/dev/sda7     350,409,780   366,796,079    16,386,300 Linux Swap
/dev/sda8     366,796,080   469,194,389   102,398,310 Linux (usually)
/dev/sda9     469,194,390   571,592,699   102,398,310 Linux (usually)
/dev/sda10    571,592,700   592,075,574    20,482,875 Linux (usually)
/dev/sda11    592,075,575 1,953,520,064 1,361,444,490 Linux (usually)

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a0229

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         133,114,590 1,346,359,454 1,213,244,865  83 Linux
/dev/sdb2       1,346,359,455 1,465,144,064   118,784,610   5 Extended
/dev/sdb5       1,346,359,518 1,448,757,764   102,398,247  83 Linux
/dev/sdb6       1,448,757,828 1,465,144,064    16,386,237  82 Linux swap / Solaris
/dev/sdb3    *         16,065       257,039       240,975   7 HPFS/NTFS
/dev/sdb4             257,040   133,114,589   132,857,550   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="DC8AE05F8AE037A2" TYPE="ntfs" 
/dev/sda2: UUID="2EE0EB96E0EB6297" TYPE="ntfs" 
/dev/sda3: UUID="2A84F2A384F27125" TYPE="ntfs" 
/dev/sda4: UUID="3E8CFC728CFC2655" TYPE="ntfs" 
/dev/sda5: UUID="1c114653-9dbb-4b5a-9d74-39855008c2a4" TYPE="ext4" 
/dev/sda6: LABEL="UbuntuDesktop2" UUID="b1bbc26e-67d9-4a66-b3b0-d97966a77bf3" TYPE="ext4" 
/dev/sda7: UUID="ce2b5194-227c-4dce-83cd-0d44808c3319" TYPE="swap" 
/dev/sda8: LABEL="OS3" UUID="a83e4ada-1a4e-483d-9f5d-69d40fe832bf" TYPE="ext4" 
/dev/sda9: LABEL="OS4" UUID="5eca49d0-7e5d-4aa3-b2a2-5961d5af0594" TYPE="ext4" 
/dev/sda10: UUID="d5f31439-b364-49f6-ae59-dd4929efc825" TYPE="ext4" 
/dev/sda11: LABEL="Data" UUID="2f3606e1-11c2-47b7-8c23-f50862cf2e8f" TYPE="ext4" 
/dev/sdb1: LABEL="Whale" UUID="4c4f302a-fd8f-4bc8-b315-7dd33a65be06" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="288DF7F50ECF4523" TYPE="ntfs" 
/dev/sdb4: UUID="AA0C3F160C3EDD4F" TYPE="ntfs" 
/dev/sdb5: LABEL="UbuntuDesktop3" UUID="f98f306e-0a83-4766-8cca-24a1f0305792" TYPE="ext4" 
/dev/sdb6: UUID="82df7478-ef3d-4418-88f2-a3ac77a2b82d" TYPE="swap" 

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
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 1c114653-9dbb-4b5a-9d74-39855008c2a4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1920x1200
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
  set timeout=5
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
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1c114653-9dbb-4b5a-9d74-39855008c2a4
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=1c114653-9dbb-4b5a-9d74-39855008c2a4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1c114653-9dbb-4b5a-9d74-39855008c2a4
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=1c114653-9dbb-4b5a-9d74-39855008c2a4 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1c114653-9dbb-4b5a-9d74-39855008c2a4
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=1c114653-9dbb-4b5a-9d74-39855008c2a4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1c114653-9dbb-4b5a-9d74-39855008c2a4
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=1c114653-9dbb-4b5a-9d74-39855008c2a4 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "UbuntuDesktop3,  chainload to sdb5" {
	saved_entry=0
	save_env saved_entry
	insmod ext2
	set root=(hd1,5)
	chainloader +1
}
menuentry "UbuntuDesktop3,  chainload to sdb5 by uuid" {
	saved_entry=0
	save_env saved_entry
	insmod ext2
	set root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4
	chainloader +1
}
menuentry "Windows 7,  chainload to loader on sdb3" {
	saved_entry=0
	save_env saved_entry
	insmod ntfs
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 288df7f50ecf4523
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb3)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd1,4)
	search --no-floppy --fs-uuid --set 288df7f50ecf4523
	chainloader +1
}

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
#
#
# 1TB WDC WD10EADS-00M /dev/sda5
UUID=1c114653-9dbb-4b5a-9d74-39855008c2a4 /               ext4    errors=remount-ro 0       1
#
# 1TB WDC WD10EADS-00M /dev/sda7
UUID=ce2b5194-227c-4dce-83cd-0d44808c3319 none            swap    sw              0       0
#
#
# 1TB WDC WD10EADS-00M /dev/sda8
UUID=a83e4ada-1a4e-483d-9f5d-69d40fe832bf /media/OS3 ext4    relatime,errors=remount-ro 0       1
#
# 1TB WDC WD10EADS-00M /dev/sda11
UUID=2f3606e1-11c2-47b7-8c23-f50862cf2e8f	/media/Data	ext4	defaults,relatime	0	2
#
#
#
# 750GB Samsung /dev/sdb1
UUID=4c4f302a-fd8f-4bc8-b315-7dd33a65be06	/media/Whale	ext4	defaults,relatime	0	2
#
# 750GB Samsung /dev/sdb5
UUID=f98f306e-0a83-4766-8cca-24a1f0305792 /media/UbuntuDesktop3 ext4    relatime,errors=remount-ro 0       1
#
# swap was on /dev/sdb6 during installation
#UUID=82df7478-ef3d-4418-88f2-a3ac77a2b82d none            swap    sw              0       0
#
#
#
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  74.5GB: boot/grub/grub.cfg
  74.5GB: boot/initrd.img-2.6.31-15-generic
  74.5GB: boot/initrd.img-2.6.31-16-generic
  74.5GB: boot/vmlinuz-2.6.31-15-generic
  74.5GB: boot/vmlinuz-2.6.31-16-generic
  74.5GB: initrd.img
  74.5GB: initrd.img.old
  74.5GB: vmlinuz
  74.5GB: vmlinuz.old

=========================== sda8/boot/grub/menu.lst: ===========================

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
default		saved
# default		8

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=84ad03ed-4b5a-40ff-b159-8253b3bc4434 ro

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=84ad03ed-4b5a-40ff-b159-8253b3bc4434 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=84ad03ed-4b5a-40ff-b159-8253b3bc4434 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry was added by frafu
title		CleanUbuntu, switch to menu.lst on (hd1,3)
savedefault     0
configfile	(hd1,3)/boot/grub/menu.lst

# This entry was added by frafu
title		UbuntuDesktop2, Chainload into GRUB 2 on (hd1,0)
savedefault     0
uuid		ad6aa7d5-a6cf-4a4e-af29-e92f88d6fba1
kernel		/boot/grub/core.img

# This entry was added by frafu
title		UbuntuDesktop3, Chainload into GRUB 2 on (hd1,2)
savedefault     0
uuid		860bda22-91e6-494d-8de0-c353f3d2fa61
kernel		/boot/grub/core.img

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Edition familiale sur (hd0,0)
root		(hd0,0)
savedefault	0
makeactive
chainloader	+1

# This entry was added by frafu
#title		UbuntuDesktop3, switch to menu.lst on (hd1,2)
#savedefault     0
#configfile	(hd1,2)/boot/grub/menu.lst




=========================== sda8/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set a83e4ada-1a4e-483d-9f5d-69d40fe832bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1920x1200
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
  set timeout=5
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
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set c203aa9e-22a6-4661-9119-b1d79698a6e4
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set c203aa9e-22a6-4661-9119-b1d79698a6e4
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set c203aa9e-22a6-4661-9119-b1d79698a6e4
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set c203aa9e-22a6-4661-9119-b1d79698a6e4
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro single 
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "UbuntuDesktop2, chainload to sdb1" {
	saved_entry=0
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	chainloader +1
}

menuentry "CleanUbuntu, chainload to sdb4" {
	saved_entry=0
	save_env saved_entry
	insmod ext2
	set root=(hd1,4)
	chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0


# 1TB WDC WD10EADS-00M /dev/sda8
UUID=a83e4ada-1a4e-483d-9f5d-69d40fe832bf /               ext4    relatime,errors=remount-ro 0       1

# 1TB WDC WD10EADS-00M /dev/sda7
UUID=ce2b5194-227c-4dce-83cd-0d44808c3319 none            swap    sw              0       0
#
# 1TB WDC WD10EADS-00M /dev/sda11
UUID=2f3606e1-11c2-47b7-8c23-f50862cf2e8f	/media/Data	ext4	defaults,relatime	0	2


# 750GB Samsung /dev/sdb1
# UUID=ad6aa7d5-a6cf-4a4e-af29-e92f88d6fba1	/media/UbuntuDesktop2	ext4	defaults,relatime	0	2

# 750GB Samsung /dev/sdb2
# UUID=52529fbc-21fa-4ead-916e-6eba9447fb95	/media/Whale	ext3	defaults,relatime	0	2

# 750GB Samsung /dev/sdb4
# UUID=ba314244-619f-461d-ae7c-270776120b43	/media/CleanUbuntu	ext3	defaults,relatime	0	2



# /dev/sda1 i.e. partition with Windows XP
# /dev/sda1	/media/XP	ntfs-3g defaults,ro,locale=en_US.utf8 0 0

# /dev/sda2
# UUID=84ad03ed-4b5a-40ff-b159-8253b3bc4434	/media/UbuntuDesktop	ext3	defaults,relatime	0	2

# /dev/sda3
# UUID=21b787b7-c0c7-41b8-bf3a-0b704228f6f2	/media/Data	ext4	defaults,relatime	0	2

# /dev/sda4
# UUID=b2ecc8b1-a99e-4876-92ea-5ce31e2c9d6c none            swap    sw              0       0


#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0



=================== sda8: Location of files loaded by Grub: ===================


 187.7GB: boot/grub/grub.cfg
 187.7GB: boot/grub/menu.lst
 187.7GB: boot/grub/stage2
 187.7GB: boot/initrd.img-2.6.31-14-generic
 187.7GB: boot/initrd.img-2.6.31-15-generic
 187.7GB: boot/vmlinuz-2.6.31-14-generic
 187.7GB: boot/vmlinuz-2.6.31-15-generic
 187.7GB: initrd.img
 187.7GB: initrd.img.old
 187.7GB: vmlinuz
 187.7GB: vmlinuz.old

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
search --no-floppy --fs-uuid --set d5f31439-b364-49f6-ae59-dd4929efc825
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
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set d5f31439-b364-49f6-ae59-dd4929efc825
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d5f31439-b364-49f6-ae59-dd4929efc825 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set d5f31439-b364-49f6-ae59-dd4929efc825
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d5f31439-b364-49f6-ae59-dd4929efc825 ro single 
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
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1c114653-9dbb-4b5a-9d74-39855008c2a4
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=1c114653-9dbb-4b5a-9d74-39855008c2a4 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1c114653-9dbb-4b5a-9d74-39855008c2a4
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=1c114653-9dbb-4b5a-9d74-39855008c2a4 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1c114653-9dbb-4b5a-9d74-39855008c2a4
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=1c114653-9dbb-4b5a-9d74-39855008c2a4 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1c114653-9dbb-4b5a-9d74-39855008c2a4
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=1c114653-9dbb-4b5a-9d74-39855008c2a4 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set a83e4ada-1a4e-483d-9f5d-69d40fe832bf
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set a83e4ada-1a4e-483d-9f5d-69d40fe832bf
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set a83e4ada-1a4e-483d-9f5d-69d40fe832bf
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set a83e4ada-1a4e-483d-9f5d-69d40fe832bf
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Windows 7 (loader) (on /dev/sdb3)" {
	insmod ntfs
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 288df7f50ecf4523
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set f98f306e-0a83-4766-8cca-24a1f0305792
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set f98f306e-0a83-4766-8cca-24a1f0305792
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set f98f306e-0a83-4766-8cca-24a1f0305792
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set f98f306e-0a83-4766-8cca-24a1f0305792
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
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
UUID=d5f31439-b364-49f6-ae59-dd4929efc825 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ce2b5194-227c-4dce-83cd-0d44808c3319 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=82df7478-ef3d-4418-88f2-a3ac77a2b82d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


 292.6GB: boot/grub/grub.cfg
 292.6GB: boot/initrd.img-2.6.31-14-generic
 292.6GB: boot/vmlinuz-2.6.31-14-generic
 292.6GB: initrd.img
 292.6GB: vmlinuz

=========================== sdb5/boot/grub/menu.lst: ===========================

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
default		saved
# default		8

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=84ad03ed-4b5a-40ff-b159-8253b3bc4434 ro

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=84ad03ed-4b5a-40ff-b159-8253b3bc4434 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=84ad03ed-4b5a-40ff-b159-8253b3bc4434 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry was added by frafu
title		CleanUbuntu, switch to menu.lst on (hd1,3)
savedefault     0
configfile	(hd1,3)/boot/grub/menu.lst

# This entry was added by frafu
title		UbuntuDesktop2, Chainload into GRUB 2 on (hd1,0)
savedefault     0
uuid		ad6aa7d5-a6cf-4a4e-af29-e92f88d6fba1
kernel		/boot/grub/core.img

# This entry was added by frafu
title		UbuntuDesktop3, Chainload into GRUB 2 on (hd1,2)
savedefault     0
uuid		860bda22-91e6-494d-8de0-c353f3d2fa61
kernel		/boot/grub/core.img

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Edition familiale sur (hd0,0)
root		(hd0,0)
savedefault	0
makeactive
chainloader	+1

# This entry was added by frafu
#title		UbuntuDesktop3, switch to menu.lst on (hd1,2)
#savedefault     0
#configfile	(hd1,2)/boot/grub/menu.lst




=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set a83e4ada-1a4e-483d-9f5d-69d40fe832bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1920x1200
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
  set timeout=5
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
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set c203aa9e-22a6-4661-9119-b1d79698a6e4
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set c203aa9e-22a6-4661-9119-b1d79698a6e4
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set c203aa9e-22a6-4661-9119-b1d79698a6e4
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set c203aa9e-22a6-4661-9119-b1d79698a6e4
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c203aa9e-22a6-4661-9119-b1d79698a6e4 ro single 
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "UbuntuDesktop2, chainload to sdb1" {
	saved_entry=0
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	chainloader +1
}

menuentry "CleanUbuntu, chainload to sdb4" {
	saved_entry=0
	save_env saved_entry
	insmod ext2
	set root=(hd1,4)
	chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0


# 1TB WDC WD10EADS-00M /dev/sda8
UUID=a83e4ada-1a4e-483d-9f5d-69d40fe832bf /               ext4    relatime,errors=remount-ro 0       1

# 1TB WDC WD10EADS-00M /dev/sda7
UUID=ce2b5194-227c-4dce-83cd-0d44808c3319 none            swap    sw              0       0
#
# 1TB WDC WD10EADS-00M /dev/sda11
UUID=2f3606e1-11c2-47b7-8c23-f50862cf2e8f	/media/Data	ext4	defaults,relatime	0	2


# 750GB Samsung /dev/sdb1
# UUID=ad6aa7d5-a6cf-4a4e-af29-e92f88d6fba1	/media/UbuntuDesktop2	ext4	defaults,relatime	0	2

# 750GB Samsung /dev/sdb2
# UUID=52529fbc-21fa-4ead-916e-6eba9447fb95	/media/Whale	ext3	defaults,relatime	0	2

# 750GB Samsung /dev/sdb4
# UUID=ba314244-619f-461d-ae7c-270776120b43	/media/CleanUbuntu	ext3	defaults,relatime	0	2



# /dev/sda1 i.e. partition with Windows XP
# /dev/sda1	/media/XP	ntfs-3g defaults,ro,locale=en_US.utf8 0 0

# /dev/sda2
# UUID=84ad03ed-4b5a-40ff-b159-8253b3bc4434	/media/UbuntuDesktop	ext3	defaults,relatime	0	2

# /dev/sda3
# UUID=21b787b7-c0c7-41b8-bf3a-0b704228f6f2	/media/Data	ext4	defaults,relatime	0	2

# /dev/sda4
# UUID=b2ecc8b1-a99e-4876-92ea-5ce31e2c9d6c none            swap    sw              0       0


#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0



=================== sdb5: Location of files loaded by Grub: ===================


 689.3GB: boot/grub/grub.cfg
 689.3GB: boot/grub/menu.lst
 689.3GB: boot/grub/stage2
 689.3GB: boot/initrd.img-2.6.31-14-generic
 689.3GB: boot/initrd.img-2.6.31-15-generic
 689.3GB: boot/vmlinuz-2.6.31-14-generic
 689.3GB: boot/vmlinuz-2.6.31-15-generic
 689.3GB: initrd.img
 689.3GB: initrd.img.old
 689.3GB: vmlinuz
 689.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde 
```

For the moment, the relevant partitions with a system are sda5 with karmic and sdb3 and sdb4 with windows. 

In the meantime, I wonder whether grub2 does not have problems with disks of different partition types, or even with gpt partitions. For example, I just tried to install karmic into another free gpt partition by using the livecd and by specifying that it should install grub2 into sda10 instead of sda. The result: grub2 did not work any longer and I had to manually reinstall it into sda by using the chroot method from the livecd.

Maybe that I should change the harddisk back to mbr as long as I can afford removing the files that it contains.

Cheers 

Francesco

---

### Post by darkod on 2009-12-07
There is grub2 on sda10 as the results show. But depending what you wanted to achieve, BIOS can't call it on sda10. You should have some other bootloader on the MBR (Master Boot Record), don't know how it would be called on GPT drives, and then call the sda10 grub2 from there.
That's why if you are planning to use grub2 you should always put it on /dev/sda (MBR of the device) and not a particular partition like /dev/sda10.
Presence has much more experience with this so we'll have to wait for his post too.

PS. You said the relevant is sda5 with Ubuntu 9.10 but you also have 9.10 on sda8 and sdb5. Did you plan to have so many installs on purpose?

---

### Post by presence1960 on 2009-12-07
I am not sure if GRUB 2 will work with gpt partition table. But either way I would clean up those partitions. You have three 9.10 installs on two disks?

I would try reinstalling GRUB 2 from the live CD. See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"). Remember your root partition is sda5 and you want to install GRUB to sda. If that does not work you may have to consider getting rid of gpt.

As far as using many partitions you can create an extended partition. Once created you cab create as many logical partitions inside the extended as you wish. The only limitation being how much space you allocate for the extended partition. Linux, unlike Windows boots from a logical partition.

---

### Post by louieb on 2009-12-07
> **frafu said:**
> 
Does anybody know whether I can install grub2 into the PBR of a logical partition of an mbr disk and chainload to it? I already did it with primary partitions if I remember correctly, but what about logical partitions? 

GRUB2 will install to the boot sector of a logical partition. and you can chain load to it. I had to use the grub-setup command with --force option.
[IDBS GRUB 1.97]("http://members.iinet.net/%7Eherman546/p20.html") 

```

============================= Boot Info Summary: 

 Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.

``````

============================= sda3/grub/menu.lst:
#...
title  Test Linux chainload on (hd0,5)    
       savedefault     
       root (hd0,5)  
       chainloader +1
# ...

``````

sda6: _________________________________

    File system:       ext4
    Boot sector type:  Grub1.97
    Boot sector info:  Grub1.97 is installed in the boot sector of sda6 and 
                       looks at sector 38190672 on boot drive #1 for core.img 
                       and on partition #6 for /boot/grub.
    Mounting failed:
mount: unknown filesystem type 'ext4'

```Just a note about the mount failed: Ran the script from my Hardy install. Hardy do not have support for ext4. And its to big of a pain in the butt to add it.

GRUB2 has some neat setup scripts might look at Hermans site.

---

### Post by frafu on 2009-12-07
Hi,

> **darkod said:**
> 
That's why if you are planning to use grub2 you should always put it on /dev/sda (MBR of the device) and not a particular partition like /dev/sda10.
Presence has much more experience with this so we'll have to wait for his post too.

The reason to put it into sda10 is to chainload to it from grub2 installed in sda. This way, each installation remains independent from the others, as far as I understand it.

> **darkod said:**
> 
PS. You said the relevant is sda5 with Ubuntu 9.10 but you also have 9.10 on sda8 and sdb5. Did you plan to have so many installs on purpose?

Yes, I like to use a main installation with all my custom configurations, a backup installation to rsync from, a clean installation,...

> **presence1960 said:**
> I am not sure if GRUB 2 will work with gpt partition table. <snip> If that does not work you may have to consider getting rid of gpt.

As far as using many partitions you can create an extended partition. Once created you cab create as many logical partitions inside the extended as you wish. The only limitation being how much space you allocate for the extended partition. Linux, unlike Windows boots from a logical partition.

The more prudent way probably is to go back to the mbr partition system and use logical partitions, especially since louieb showed that it is possible to chainload to logical partitions. I have started backing up the data from the gpt disk...

> **louieb said:**
> GRUB2 will install to the boot sector of a logical partition. and you can chain load to it. 

Thanks for telling me that it works and for your example about chainloading from grub in sda to grub2 in sda6. 

Finally, it turns out that it was not a good idea to choose the gpt partition scheme. Thanks to you all: the original problem might not have been solved, but in the end, I will have what I wanted with gpt by using mbr on both disks.

Cheers 

Francesco

---

### Post by darkod on 2009-12-07
At the end of the day, it's your choice. I can understand having different installs but chainloading grub2 to grub2? You're not achieving anything with that, you can boot them all from a single grub2 on the MBR. And if you are afraid that grub2 will brake somehow, then the chainloading won't work neither. You still need your first grub2 to be functional to chainload to the other grub2.

---

### Post by oldfred on 2009-12-07
I know Darko is not a fan of chainbooting but my Karmic grub.cfg is way too long. I know I can customize it and will do so but I still like chainbooting. I also chainbooted into Karmic alpha when I first installed it and it was in a logical partition. It still complains about blocklist being BAD but works. They say it may not in the future, but my understand is the windows boot is a blocklist style boot.

GPT is going to be the future as MBR has a hard max of 2TB. Larger drives cannot use MBR or end up with some kluge to work. Some of the newest windows support GPT but only as data partitions and will only boot from a EFI system. Grub legacy was modified to at least recognize GPT so a not to destroy them. Grub2 supposed will boot from GPT by useing the MBR partition that GPT has but then also requires a BIOS boot partition.

info on BIOS boot partition and why Blocklists are bad[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
Search to about 2/3 down for grub2 & GPT info
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by frafu on 2009-12-07
> **darkod said:**
> At the end of the day, it's your choice. I can understand having different installs but chainloading grub2 to grub2? You're not achieving anything with that, you can boot them all from a single grub2 on the MBR. And if you are afraid that grub2 will brake somehow, then the chainloading won't work neither. You still need your first grub2 to be functional to chainload to the other grub2.

The main reason for using chainloading is that I cannot use a keyboard during startup to choose what installation to boot. Consequently, my grub2 on sda (that is from the first installation) is configured to use the saved value as default menuentry. Consequently, if I want to boot into another installation, I use the grub-set-default command to indicate to grub2 to use that other installation as default. So the computer automatically boots in the other installation. However ,as the menuentry of that other installation has commands to reset the saved value to the installation using grub2 in sda, on the next reboot, it will again automatically reboot into the first installation. 

A better way, about how to change the installation to boot from without using a keyboard would be greatly appreciated. I would be able to use the pointer to choose what installation to boot from if grub would support it.

Cheers 

Francesco

---

