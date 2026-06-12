---
title: "Broken OS selection in GRUB (extensive details inside)"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Dirty_habiT on 2010-05-10
**History**
I have installed these OS's in this order:

1 - Vista
2 - Ubuntu Server 9.04
3 - Ubuntu Desk 10.04
4 - BT4

I recently upgraded my most often used OS (#3) to 10.04 version and it updated GRUB to GRUB2 as part of the dist-upgrade.

I have a feeling that I wasn't careful enough when installing BT4 or I made a mistake in the partitioning. I had plenty of space that was free waiting to be used by some other os and I designated some of that space for BT4.

**The Issue**
When I got it all installed (off of a USB live boot) I rebooted and noticed it was back to grub one. The Vista install and the Ubuntu Server install both work still... but the recently updated (to Grub2) Ubuntu Desk install now hangs immediately after selecting it and pressing enter in Grub. I can mount the partition within BT4 just fine and see that all my data is still there, it just won't boot.

**What I've tried**
Using BT4 to install Grub2. (no luck)
Installing Grub1.5 back after finding Grub2 didn't work. (no luck)

**My plan**
When I get home from work today I'm going to take the "quiet" option off of the boot command in Grub for that Ubuntu OS and see if there's any error it's dumping before it hangs.
Hope that someone has had this issue before and can just tell me a straight forward way of resolving this issue. I'd prefer to use GRUB2 as my boot loader.

**Cliff Notes**
Had other OS's installed
Updated to newest Ubuntu (installed GRUB2 as the new bootloader)
Used some spare disk to install BT4
New Ubuntu that used Grub2 is now the only OS that won't boot

Any help is greatly appreciated, and I will post any information that anyone may need to help me get this resolved.

---

### Post by Dirty_habiT on 2010-05-10
I will also post the information of "bootinfo" when I get home.

---

### Post by Dirty_habiT on 2010-05-10
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 1.96 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80d2cc92

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   170,846,207   167,772,160   7 HPFS/NTFS
/dev/sda3         170,851,275   488,392,064   317,540,790   5 Extended
/dev/sda5         170,851,338   209,905,289    39,053,952  83 Linux
/dev/sda6         209,905,353   229,440,329    19,534,977  82 Linux swap / Solaris
/dev/sda7         229,440,393   237,440,699     8,000,307  82 Linux swap / Solaris
/dev/sda8         237,440,763   435,907,709   198,466,947  83 Linux
/dev/sda9         435,907,773   486,126,899    50,219,127  83 Linux
/dev/sda10        486,126,963   488,392,064     2,265,102  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4A8E7E8E8E7E7275                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda10       7f0c73b1-1a91-4623-ad5a-ba8b0a25e354   swap                                     
/dev/sda2        9E5085AB50858AAB                       ntfs       Main Disk                     
/dev/sda5        3702d06f-8da3-44ea-bb74-0d8dc564334b   ext4                                     
/dev/sda6        bf9513f5-60bf-4ca6-8d38-3d6b40e28621   swap                                     
/dev/sda7        dc70729a-1a3c-4121-bdc9-e28a9f645479   swap                                     
/dev/sda8        13580644-47b3-41cd-a257-6711f852c912   ext4                                     
/dev/sda9        c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext3       (rw,relatime,errors=remount-ro)


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
default		4

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
# kopt=root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3702d06f-8da3-44ea-bb74-0d8dc564334b

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
savedefault=true

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-server
uuid		3702d06f-8da3-44ea-bb74-0d8dc564334b
kernel		/boot/vmlinuz-2.6.28-14-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode)
uuid		3702d06f-8da3-44ea-bb74-0d8dc564334b
kernel		/boot/vmlinuz-2.6.28-14-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro  single
initrd		/boot/initrd.img-2.6.28-14-server

#title		Ubuntu 9.04, kernel 2.6.28-11-server
#uuid		3702d06f-8da3-44ea-bb74-0d8dc564334b
#kernel		/boot/vmlinuz-2.6.28-11-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-server
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
#uuid		3702d06f-8da3-44ea-bb74-0d8dc564334b
#kernel		/boot/vmlinuz-2.6.28-11-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro  single
#initrd		/boot/initrd.img-2.6.28-11-server

title		Ubuntu 9.04, memtest86+
uuid		3702d06f-8da3-44ea-bb74-0d8dc564334b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=279e1f64-04ba-4fbb-94b9-ca6ed01cb00b /home           ext4    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=bf9513f5-60bf-4ca6-8d38-3d6b40e28621 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  87.5GB: boot/grub/menu.lst
  87.7GB: boot/grub/stage2
  88.3GB: boot/initrd.img-2.6.28-11-server
  89.2GB: boot/initrd.img-2.6.28-14-server
  87.9GB: boot/vmlinuz-2.6.28-11-server
  88.9GB: boot/vmlinuz-2.6.28-14-server
  89.2GB: initrd.img
  88.3GB: initrd.img.old
  88.9GB: vmlinuz
  87.9GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 13580644-47b3-41cd-a257-6711f852c912
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 13580644-47b3-41cd-a257-6711f852c912
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13580644-47b3-41cd-a257-6711f852c912
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13580644-47b3-41cd-a257-6711f852c912 ro splash vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13580644-47b3-41cd-a257-6711f852c912
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13580644-47b3-41cd-a257-6711f852c912 ro single splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13580644-47b3-41cd-a257-6711f852c912
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13580644-47b3-41cd-a257-6711f852c912
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 9e5085ab50858aab
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-server (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3702d06f-8da3-44ea-bb74-0d8dc564334b
	linux /boot/vmlinuz-2.6.28-14-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-server
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3702d06f-8da3-44ea-bb74-0d8dc564334b
	linux /boot/vmlinuz-2.6.28-14-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro single
	initrd /boot/initrd.img-2.6.28-14-server
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3702d06f-8da3-44ea-bb74-0d8dc564334b
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=13580644-47b3-41cd-a257-6711f852c912 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bf9513f5-60bf-4ca6-8d38-3d6b40e28621 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=dc70729a-1a3c-4121-bdc9-e28a9f645479 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 121.7GB: boot/grub/core.img
 122.1GB: boot/grub/grub.cfg
 144.2GB: boot/initrd.img-2.6.32-21-generic
 136.1GB: boot/vmlinuz-2.6.32-21-generic
 144.2GB: initrd.img
 136.1GB: vmlinuz

=========================== sda9/boot/grub/menu.lst: ===========================

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
default         0

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
# kopt=root=UUID=c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8

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
# defoptions=vga=0x317

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

splashimage=c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8/boot/grub/splash.xpm.gz

title		Debian GNU/Linux, kernel 2.6.30.9
root		c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8 ro vga=0x317
initrd		/boot/initrd.img-2.6.30.9

title		Debian GNU/Linux, kernel 2.6.30.9 (recovery mode)
root		c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8 ro single
initrd		/boot/initrd.img-2.6.30.9

title		Debian GNU/Linux, kernel memtest86+
root		c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-14-server (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro single 
initrd		/boot/initrd.img-2.6.28-14-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=13580644-47b3-41cd-a257-6711f852c912 ro splash vga=795 quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=13580644-47b3-41cd-a257-6711f852c912 ro single splash vga=795 
initrd		/boot/initrd.img-2.6.32-21-generic
savedefault
boot


=========================== sda9/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,9)
if font (hd0,9)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.30.9" {
	linux	(hd0,9)/boot/vmlinuz-2.6.30.9 root=UUID=c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8 ro quiet splash 
	initrd	(hd0,9)/boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu, linux 2.6.30.9 (single-user mode)" {
	linux	(hd0,9)/boot/vmlinuz-2.6.30.9 root=UUID=c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8 ro single
	initrd	(hd0,9)/boot/initrd.img-2.6.30.9
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	(hd0,9)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista/Longhorn (loader) (on /dev/sda2)" {
	set root=(hd0,2)
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-server (on /dev/sda5)" {
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.28-14-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-server
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode) (on /dev/sda5)" {
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.28-14-server root=UUID=3702d06f-8da3-44ea-bb74-0d8dc564334b ro single
	initrd /boot/initrd.img-2.6.28-14-server
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda5)" {
	set root=(hd0,5)
	linux /boot/memtest86+.bin 
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda8)" {
	set root=(hd0,8)
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=13580644-47b3-41cd-a257-6711f852c912 ro splash vga=795 quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda8)" {
	set root=(hd0,8)
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=13580644-47b3-41cd-a257-6711f852c912 ro single splash vga=795
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=c0fdcd45-c81f-46db-ac22-e32f8e3a2bd8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=7f0c73b1-1a91-4623-ad5a-ba8b0a25e354 none            swap    sw              0       0

=================== sda9: Location of files loaded by Grub: ===================


 240.3GB: boot/grub/core.img
 240.2GB: boot/grub/grub.cfg
 240.3GB: boot/grub/menu.lst
 240.3GB: boot/initrd.img-2.6.30.9
 240.3GB: boot/vmlinuz-2.6.30.9
 240.3GB: initrd.img
 240.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hda 

```

Also, removing the "quiet" from the boot options for 10.04 ubuntu didn't do anything, it still froze right after saying "running boot commands" or something along those lines.

---

### Post by oldfred on 2010-05-10
Script says grub is 1.96, Ubuntu 10.04 is now grub 1.98 with lots of improvements. I would reinstall grub2 from the 10.04 install and use it to boot. It should find your other installs without any issue.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Dirty_habiT on 2010-05-12
That is helpful and I will try it, but I'm wondering if it will work from my 10.04 live disk.  Someone in the IRC chat on freenode suggested that I boot into rescue mode that would allow me to mount and boot into w/e partition I wanted... so I'd be able to boot into my old linux partition and once there, reinstall grub2.

I will try what you've suggested but I'd be really happy if I could do it w/ the newest live disk instead of downloading one of the other older versions and then burning it.

---

### Post by oldfred on 2010-05-12
If your current grub boots you can manually edit the grub lines to boot or you can use your 10.04 liveCD to reinstall grub2 for your 10.04 Ubuntu.

[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

Install from LiveCD:
Find linux partition  should be sda8 for you:
sudo fdisk -l
sudo mkdir /mnt/sda8
sudo mount /dev/sda8 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

