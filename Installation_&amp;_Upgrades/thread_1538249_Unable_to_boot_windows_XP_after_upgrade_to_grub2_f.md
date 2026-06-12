---
title: "Unable to boot windows XP after upgrade to grub2 from grub"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by mahongquan on 2010-07-24
yestoday,after I upgrade,unable to boot windows xp.
if I use grub ,windows xp can boot up.but now I want to use grub2,does anyone help me?
boot info script's results.txt is at below.
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /boot.ini /ntldr /NTDETECT.COM 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32, Non Bootable
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       144,584       144,522   6 FAT16
/dev/sda2             144,585     4,353,614     4,209,030   b W95 FAT32
/dev/sda3           4,353,615   156,280,319   151,926,705   f W95 Ext d (LBA)
/dev/sda5           4,353,678    35,069,894    30,716,217   7 HPFS/NTFS
/dev/sda6          35,069,958    55,552,769    20,482,812  83 Linux
/dev/sda7          66,830,463    96,518,519    29,688,057   b W95 FAT32
/dev/sda8          96,518,583   156,280,319    59,761,737   7 HPFS/NTFS
/dev/sda9          55,552,833    65,705,849    10,153,017  83 Linux
/dev/sda10         65,705,913    66,830,399     1,124,487  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       50bf5f79-db50-40d5-b73a-5f6d2e84d828   swap                                     
/dev/sda1        07D7-040A                              vfat       DELL                          
/dev/sda2        07D7-040A                              vfat       DRIVERS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        047C4B5C7C4B479E                       ntfs       winxp                         
/dev/sda6        34a71c51-3319-42ee-bbed-0cc4f5fd518c   ext3                                     
/dev/sda7        2450-129D                              vfat       DOC                           
/dev/sda8        BC847FC3847F7F28                       ntfs       bak                           
/dev/sda9        717b6b28-bba2-48a7-adee-e235d284a397   ext4       myhome                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda9        /home                    ext4       (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

#
# Sample boot menu configuration file
#

# Boot automatically after 30 secs.
timeout 6

# By default, boot the first entry.
default 4

# Fallback to the second entry.
#fallback 1
# 0000000000000000000000
title  dos
                        map --mem (hd0,0)/boot/bootdisk.img (fd0)
			map --hook
			chainloader (fd0)+1
			rootnoverify (fd0)
			map --floppies=1
			boot
#1111111111111111111111111
title  dos_ntfs
			map --mem (hd0,0)/boot/ntfs.img (fd0)
			map --hook
			chainloader (fd0)+1
			rootnoverify (fd0)
			map --floppies=1
			boot

#2222222222222222222222222
itle gentoo
root (hd0,4)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
#33333333333333333333333333333333333
title gentoo
root (hd0,4)
kernel          /boot/vmlinuz root=/dev/hda5
#4444444444444444444444444444444
title ubuntu2.6.15-26-686
root (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda10 ro 
initrd		/boot/initrd.img-2.6.15-26-686
#555555555555555555555555555555555
title sda2
root (hd1,0)
kernel          /vmlinuz-2.6.12-10-686 root=/dev/sda2 ro 
initrd		/initrd.img-2.6.12-10-686

================================ sda1/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\ = "dos_dell"

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2

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
default         4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		8

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
# kopt=root=UUID=34a71c51-3319-42ee-bbed-0cc4f5fd518c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=34a71c51-3319-42ee-bbed-0cc4f5fd518c

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		34a71c51-3319-42ee-bbed-0cc4f5fd518c
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=34a71c51-3319-42ee-bbed-0cc4f5fd518c ro quiet splash
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		34a71c51-3319-42ee-bbed-0cc4f5fd518c
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=34a71c51-3319-42ee-bbed-0cc4f5fd518c ro single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		34a71c51-3319-42ee-bbed-0cc4f5fd518c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		3_Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		4_Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 34a71c51-3319-42ee-bbed-0cc4f5fd518c
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 34a71c51-3319-42ee-bbed-0cc4f5fd518c
set locale_dir=($root)/boot/grub/locale
set lang=zh
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=8
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu&#65292;Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 34a71c51-3319-42ee-bbed-0cc4f5fd518c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=34a71c51-3319-42ee-bbed-0cc4f5fd518c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu&#65292;Linux 2.6.32-24-generic (&#24674;&#22797;&#27169;&#24335;)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 34a71c51-3319-42ee-bbed-0cc4f5fd518c
	echo	'&#36733;&#20837; Linux ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=34a71c51-3319-42ee-bbed-0cc4f5fd518c ro single 
	echo	'&#36733;&#20837;&#24341;&#23548;&#34394;&#25311;&#30913;&#30424; ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 34a71c51-3319-42ee-bbed-0cc4f5fd518c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 34a71c51-3319-42ee-bbed-0cc4f5fd518c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d7-040a
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=34a71c51-3319-42ee-bbed-0cc4f5fd518c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=07D7-040A  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
#UUID=07D7-040A  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
#UUID=047C4B5C7C4B479E /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
#UUID=2450-129D  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
#UUID=BC847FC3847F7F28 /media/sda8     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda9
/dev/sda10  none            swap    sw              0       0
/dev/sda9 /home               ext4  
#/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sda6: Location of files loaded by Grub: ===================


  21.2GB: boot/grub/core.img
  21.2GB: boot/grub/grub.cfg
  21.2GB: boot/grub/menu.lst
  21.2GB: boot/grub/stage2
  21.5GB: boot/initrd.img-2.6.32-24-generic
  21.2GB: boot/vmlinuz-2.6.32-24-generic
  21.5GB: initrd.img
  21.2GB: vmlinuz

---

### Post by oldfred on 2010-07-25
You have grub2 installed to the MBR. What does boot?

Windows and/or the osprober may have trouble with your windows in sda1 as it also has grub installed.

  /boot/grub/menu.lst is in your windows partition. Delete the entire /boot folder.

Your sda1 is labeled Dell and the boot.ini in says it wants to boot sda3, but sda3 is now your extended partition. Is sda1 your windows or was it sda3 which is now gone?

multi(0)disk(0)rdisk(0)partition([COLOR=Red]3[/COLOR])\WINDOWS="Micro  soft Windows XP Professional" /noexecute=optin /fastdetect

---

