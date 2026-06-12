---
title: "grub dead wiki did not resolve"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2010-05-24
/dev/sda1   *          63    35166284    17583111    7  HPFS/NTFS
/dev/sda2        35166285    80228609    22531162+  83  Linux
/dev/sda3        80228671   234440703    77106016+   5  Extended
/dev/sda5        80228673    88421759     4096543+  82  Linux swap / Solaris
/dev/sda6        88421823   203096104    57337141    b  W95 FAT32
/dev/sda7       203098112   233031679    14966784   83  Linux
/dev/sda8       233033728   234440703      703488   82  Linux swap / Solaris

  sudo mount /dev/sda2 /mnt
  sudo grub-install --recheck --root-directory=/mnt /dev/sda


reboot

get following shell
gnu grub 1.98-1ubuntu5
min bash
grub>ls
(hd0) (hd0,8)...


how should I go about repair...
sda1 = xp
sda2= ubuntu 8.10
sda7= ubuntu 10.04

---

### Post by presence1960 on 2010-05-24
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by pjmlmas on 2010-05-24
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    35,166,284    35,166,222   7 HPFS/NTFS
/dev/sda2          35,166,285    80,228,609    45,062,325  83 Linux
/dev/sda3          80,228,671   234,440,703   154,212,033   5 Extended
/dev/sda5          80,228,673    88,421,759     8,193,087  82 Linux swap / Solaris
/dev/sda6          88,421,823   203,096,104   114,674,282   b W95 FAT32
/dev/sda7         203,098,112   233,031,679    29,933,568  83 Linux
/dev/sda8         233,033,728   234,440,703     1,406,976  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6A9F652C4B15AFC6                       ntfs                                     
/dev/sda2        73367600-be5b-47de-8922-3de3bd9daad9   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e9747b07-707d-4d1f-9ecd-b4306371a42d   swap                                     
/dev/sda6        49B1-A5FB                              vfat       f                             
/dev/sda7        b7837b32-ef57-491a-ae29-085632aa6452   ext4                                     
/dev/sda8        c81b9567-ab66-471c-ad0f-ce257280d6bb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=73367600-be5b-47de-8922-3de3bd9daad9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=73367600-be5b-47de-8922-3de3bd9daad9

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		73367600-be5b-47de-8922-3de3bd9daad9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=73367600-be5b-47de-8922-3de3bd9daad9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		73367600-be5b-47de-8922-3de3bd9daad9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=73367600-be5b-47de-8922-3de3bd9daad9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		73367600-be5b-47de-8922-3de3bd9daad9
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
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=73367600-be5b-47de-8922-3de3bd9daad9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e9747b07-707d-4d1f-9ecd-b4306371a42d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  34.8GB: boot/grub/core.img
  35.5GB: boot/grub/menu.lst
  35.5GB: boot/grub/stage2
  35.5GB: boot/initrd.img-2.6.27-7-generic
  35.5GB: boot/vmlinuz-2.6.27-7-generic
  35.5GB: initrd.img.old
  35.5GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set b7837b32-ef57-491a-ae29-085632aa6452
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set b7837b32-ef57-491a-ae29-085632aa6452
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b7837b32-ef57-491a-ae29-085632aa6452
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b7837b32-ef57-491a-ae29-085632aa6452 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b7837b32-ef57-491a-ae29-085632aa6452
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b7837b32-ef57-491a-ae29-085632aa6452 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b7837b32-ef57-491a-ae29-085632aa6452
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b7837b32-ef57-491a-ae29-085632aa6452 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b7837b32-ef57-491a-ae29-085632aa6452
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b7837b32-ef57-491a-ae29-085632aa6452 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b7837b32-ef57-491a-ae29-085632aa6452
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b7837b32-ef57-491a-ae29-085632aa6452
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6a9f652c4b15afc6
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 73367600-be5b-47de-8922-3de3bd9daad9
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=73367600-be5b-47de-8922-3de3bd9daad9 ro quiet splash
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 73367600-be5b-47de-8922-3de3bd9daad9
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=73367600-be5b-47de-8922-3de3bd9daad9 ro single
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 73367600-be5b-47de-8922-3de3bd9daad9
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=b7837b32-ef57-491a-ae29-085632aa6452 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c81b9567-ab66-471c-ad0f-ce257280d6bb none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 117.0GB: boot/grub/core.img
 115.0GB: boot/grub/grub.cfg
 117.1GB: boot/initrd.img-2.6.32-21-generic
 117.1GB: boot/initrd.img-2.6.32-22-generic
 117.1GB: boot/vmlinuz-2.6.32-21-generic
 117.1GB: boot/vmlinuz-2.6.32-22-generic
 117.1GB: initrd.img
 117.1GB: initrd.img.old
 117.1GB: vmlinuz
 117.1GB: vmlinuz.old

---

### Post by presence1960 on 2010-05-24
Boot from the 10.04 Live CD. Choose try ubuntu without any changes. When the desktop loads open a terminal & run ```
sudo mount /dev/sda7 /mnt
```

next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

After process is completed reboot without the Live CD and boot into 10.04. Open a terminal and run ```
sudo update-grub
```

---

