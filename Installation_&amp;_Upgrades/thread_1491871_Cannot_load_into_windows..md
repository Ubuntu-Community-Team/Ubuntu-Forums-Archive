---
title: "Cannot load into windows."
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by powerchess on 2010-05-24
While I was looking for solutions to prevent my 10.04 from overheating, I decided to try and upgrade my grub(I had upgraded from 9.04 twice to 10.04 so did not have grub2). Anyway, the 'upgrade' prevented me from being able to boot windows(there was some error). It would just get stuck with the annoying flashing _ at the top right corner.

So to fix that I tried to use the windows repair CD. Which prevented my Ubuntu from loading AND did not fix my windows loading problem.. So, now to be able to use my 10.04, I installed 9.04, which gave me a grub and I used that to get into my beloved 10.04. 

All I need now is a way to start windows! I want to avoid the CD at all costs if possible.

---

### Post by arrange on 2010-05-24
Please provide the output from [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/"). (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").).

---

### Post by powerchess on 2010-05-24
Thanks for your reply, this was the output. 

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 341796544 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 341796544 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 342540672 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 342468816 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   304,239,419   273,437,500   7 HPFS/NTFS
/dev/sda4         304,255,035   488,392,064   184,137,030   5 Extended
/dev/sda5         480,022,263   488,392,064     8,369,802  82 Linux swap / Solaris
/dev/sda6         323,774,136   480,022,199   156,248,064  83 Linux
/dev/sda7         304,255,161   323,774,009    19,518,849  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        82721BA4721B9BCB                       ntfs       RECOVERY                      
/dev/sda3        46161DA2161D9451                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        a01a2279-f57f-4c4f-9562-143ed8ee01cb   swap                                     
/dev/sda6        dadfc1d8-a4b3-4351-9e00-d349f3648998   ext3                                     
/dev/sda7        fae7d87f-583b-4c57-b0a0-2ceeb9776719   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=chaitanya)


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
# kopt=root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dadfc1d8-a4b3-4351-9e00-d349f3648998

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro quiet splash
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro quiet splash
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
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
search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
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
search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro   quiet splash acpi.power_nocheck
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro   quiet splash acpi.power_nocheck
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro   quiet splash acpi.power_nocheck
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	echo	'Loading Linux 2.6.28-11-generic ...'
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 82721ba4721b9bcb
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
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a01a2279-f57f-4c4f-9562-143ed8ee01cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 175.3GB: boot/grub/core.img
 175.0GB: boot/grub/grub.cfg
 174.9GB: boot/grub/menu.lst
 175.3GB: boot/grub/stage2
 174.9GB: boot/initrd.img-2.6.32-22-generic
 174.9GB: boot/vmlinuz-2.6.32-22-generic
 174.9GB: initrd.img
 174.9GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fae7d87f-583b-4c57-b0a0-2ceeb9776719

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		fae7d87f-583b-4c57-b0a0-2ceeb9776719
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		fae7d87f-583b-4c57-b0a0-2ceeb9776719
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		fae7d87f-583b-4c57-b0a0-2ceeb9776719
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single 
initrd		/boot/initrd.img-2.6.32-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 10.04 LTS, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


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
UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a01a2279-f57f-4c4f-9562-143ed8ee01cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 165.2GB: boot/grub/menu.lst
 165.2GB: boot/grub/stage2
 165.1GB: boot/initrd.img-2.6.28-11-generic
 165.1GB: boot/vmlinuz-2.6.28-11-generic
 165.1GB: initrd.img
 165.1GB: vmlinuz

---

### Post by arrange on 2010-05-24
IMO what you need to do is to repair the boot sector on */dev/sda2* (Grub2 resides there now and must be eliminated :))

This can be done via *fixboot* (not *fixmbr*) or *testdisk*. You can find more info at
[http://ubuntuforums.org/showthread.php?t=1490480](http://ubuntuforums.org/showthread.php?t=1490480)

If you need more help, just ask :)

---

### Post by powerchess on 2010-05-24
Is there a way to do this from within ubuntu? I do not want to try and fix using the windows CD, it takes painfully long to load that disc. (~30 minutes)

---

### Post by darkod on 2010-05-24
> **arrange said:**
> IMO what you need to do is to repair the boot sector on */dev/sda2* (Grub2 resides there now and must be eliminated :))

This can be done via *fixboot* (not *fixmbr*) or *testdisk*. You can find more info at
[http://ubuntuforums.org/showthread.php?t=1490480](http://ubuntuforums.org/showthread.php?t=1490480)

If you need more help, just ask :)

Exactly, this was your issue why windows was not booting. It's best to use the testdisk procedure mentioned.

But after you used the windows disc and it overwrote grub2, you didn't have to install 9.04 just to get access to 10.04.

Once you are done removing grub2 from /dev/sda2, use the 10.04 cd in live mode to reinstall grub2 to the MBR:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

After that check if it's working, and you can remove the 9.04 if the only purpose was to reach 10.04.

If the 9.04 installer resized your 10.04 partition I hope there is no corruption on it or something.

---

### Post by darkod on 2010-05-24
> **powerchess said:**
> Is there a way to do this from within ubuntu? I do not want to try and fix using the windows CD, it takes painfully long to load that disc. (~30 minutes)

Yes, run testdisk from ubuntu. Install it first:

sudo apt-get install testdisk
sudo testdisk

After that use these instructions on partition #2 on disk /dev/sda:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by arrange on 2010-05-24
Yes, *testdisk*. That will use a sector backup to repair it. See
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by powerchess on 2010-05-24
The thing is that I do not think I ever fixed my windows problem. I was never able to log into windows. 
Can someone tell me how to do a fixboot? 
Also, I do not have a 10.04 live CD or spare CD's to do that, is it possible to use my 9.04 CD?

---

### Post by powerchess on 2010-05-24
Sorry, I didnt read the latest posts before posting. Ill try testdisk and let you know. Thanks

---

### Post by darkod on 2010-05-24
> **powerchess said:**
> Sorry, I didnt read the latest posts before posting. Ill try testdisk and let you know. Thanks

You should be able to use testdisk from ubuntu, but you can't use a 9.04 cd to reinstall grub2. It comes with grub1.

---

### Post by powerchess on 2010-05-24
I tried testdisk and it didnt help. 
I am not interested in upgrading to grub2, I want to stay with grub.

---

### Post by darkod on 2010-05-24
> **powerchess said:**
> I tried testdisk and it didnt help. 
I am not interested in upgrading to grub2, I want to stay with grub.

Are you sure you ran the procedure correctly?

Run the boot info script again so we can see the results. And this time please post them inside CODE tags for easier reading. With the text selected just hit the # button in the toolbar above when creating the post.

---

### Post by powerchess on 2010-05-24
I forgot to add, there was no option to "BackupBS" in the testdisk

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 341796544 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 341796544 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 342540672 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 342468816 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   304,239,419   273,437,500   7 HPFS/NTFS
/dev/sda4         304,255,035   488,392,064   184,137,030   5 Extended
/dev/sda5         480,022,263   488,392,064     8,369,802  82 Linux swap / Solaris
/dev/sda6         323,774,136   480,022,199   156,248,064  83 Linux
/dev/sda7         304,255,161   323,774,009    19,518,849  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        82721BA4721B9BCB                       ntfs       RECOVERY                      
/dev/sda3        46161DA2161D9451                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        a01a2279-f57f-4c4f-9562-143ed8ee01cb   swap                                     
/dev/sda6        dadfc1d8-a4b3-4351-9e00-d349f3648998   ext3                                     
/dev/sda7        fae7d87f-583b-4c57-b0a0-2ceeb9776719   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


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
# kopt=root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dadfc1d8-a4b3-4351-9e00-d349f3648998

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro quiet splash
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro quiet splash
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		dadfc1d8-a4b3-4351-9e00-d349f3648998
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
search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
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
search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro   quiet splash acpi.power_nocheck
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro   quiet splash acpi.power_nocheck
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro   quiet splash acpi.power_nocheck
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	echo	'Loading Linux 2.6.28-11-generic ...'
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set dadfc1d8-a4b3-4351-9e00-d349f3648998
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 82721ba4721b9bcb
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
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a01a2279-f57f-4c4f-9562-143ed8ee01cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 175.3GB: boot/grub/core.img
 175.0GB: boot/grub/grub.cfg
 174.9GB: boot/grub/menu.lst
 175.3GB: boot/grub/stage2
 174.9GB: boot/initrd.img-2.6.32-22-generic
 174.9GB: boot/vmlinuz-2.6.32-22-generic
 174.9GB: initrd.img
 174.9GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fae7d87f-583b-4c57-b0a0-2ceeb9776719

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

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		fae7d87f-583b-4c57-b0a0-2ceeb9776719
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		fae7d87f-583b-4c57-b0a0-2ceeb9776719
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		fae7d87f-583b-4c57-b0a0-2ceeb9776719
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		fae7d87f-583b-4c57-b0a0-2ceeb9776719
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		fae7d87f-583b-4c57-b0a0-2ceeb9776719
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=dadfc1d8-a4b3-4351-9e00-d349f3648998 ro single 
initrd		/boot/initrd.img-2.6.32-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 10.04 LTS, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


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
UUID=fae7d87f-583b-4c57-b0a0-2ceeb9776719 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a01a2279-f57f-4c4f-9562-143ed8ee01cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 165.2GB: boot/grub/menu.lst
 165.2GB: boot/grub/stage2
 165.1GB: boot/initrd.img-2.6.28-11-generic
 165.2GB: boot/initrd.img-2.6.28-18-generic
 165.1GB: boot/vmlinuz-2.6.28-11-generic
 165.2GB: boot/vmlinuz-2.6.28-18-generic
 165.2GB: initrd.img
 165.1GB: initrd.img.old
 165.2GB: vmlinuz
 165.1GB: vmlinuz.old
```

---

### Post by darkod on 2010-05-24
I don't know what happened, but grub2 is still on /dev/sda2:

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda2 [/COLOR]and 
                       looks at sector 341796544 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

Also, I am slightly confused whether /dev/sda2 or /dev/sda3 is your win partition with the boot files on it. It seems /dev/sda2 might be a recovery partition.

In that case, if win is on /dev/sda3, you don't have grub2 installed there which is good, but you also don't have the win boot files which is not good:

Boot files/dirs:   /Windows/System32/winload.exe

You should also have /bootmgr and /boot/bcd here.

You can add them using the win7 dvd. Also, first from ubuntu run Gparted and remove the boot flag from /dev/sda2, set it on /dev/sda3. Then run the repair of the win7 boot files, only the /fixboot, not /fixmbr.
There are instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you run the /fixmbr also, it will overwrite grub1 on your MBR which you don't want.

---

### Post by powerchess on 2010-05-24
Thank You so much! I am back into Windows! :)

All I need now is to remove 9.04 and merge the space into 10.04. Any Slick ways to do that?

---

### Post by powerchess on 2010-05-24
And, Do I need to do anything about the other remnants of Grub 2. sda1 etc? or are they not going to cause me any future problems?

---

### Post by darkod on 2010-05-24
> **powerchess said:**
> And, Do I need to do anything about the other remnants of Grub 2. sda1 etc? or are they not going to cause me any future problems?

Grub2 on a partition will give you trouble only if you call up that partition (the OS on it) with chainloading. Like windows.

sda1 seems to be some Dell utility partition. If you think you will ever need it, remove grub2 from there. Or remove it when you need it now that you know how.

You can leave grub2 on the ubuntu partitions, it doesn't interfere with ubuntu.

You said you wanted to stay with your grub1 but its config files are in 9.04. If you remove it, grub1 won't work and you won't be able to boot anything.

That's why I suggested reinstalling grub2 to the MBR of the disk, checking that it's working fine, and after that you can delete the 9.04 partition. But you said you don't have a 10.04 cd right now.

After that you could use Gparted but from a LIVE MODE to resize the 10.04 root partition to include the space created by deleting the 9.04 partition.

---

### Post by powerchess on 2010-05-24
If I could get the 10.04 CD delivered(or I could burn it), does it matter that I am using a 64-bit ubuntu and the CD that ubuntu delivers is 32 bit? or does it not matter for the GRUB

---

### Post by darkod on 2010-05-25
> **powerchess said:**
> If I could get the 10.04 CD delivered(or I could burn it), does it matter that I am using a 64-bit ubuntu and the CD that ubuntu delivers is 32 bit? or does it not matter for the GRUB

Not sure about that. The package might be different for different architecture. On the other hand, it might not be. :)

If you are downloading and burning it, then you can choose which image to download.

---

### Post by kansasnoob on 2010-05-25
If you can boot into 10.04 now using 9.04's grub you shouldn't need to use a live CD to hand boot control off to 10.04. Just boot into 10.04 and check the grub version by running:

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

Example:

> grub-install (GNU GRUB 1.98-1ubuntu6)
Package: grub
State: not installed
Package: grub-pc
State: installed
Package: grub-common
State: installed
Package: os-prober
State: installed

You can see there that the grub version is "1.98-1ubuntu6" which is grub 2, basically "0.9*" = legacy grub, and "1.9*" = grub 2. As far as packages are concerned:

grub = legacy grub
grub-pc = grub 2
grub-common is shared by both legacy grub and grub 2
os-prober is particularly necessary for the proper function of grub 2

So, if it looks like grub 2 is installed and in charge of boot you should be able to just:

```
sudo grub-install /dev/sda
```

But you have mixed legacy grub and grub 2 files/directories:

> sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 342540672 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/**[COLOR="Red"]menu.lst[/COLOR]** /boot/grub/**[COLOR="Red"]grub.cfg[/COLOR]** /etc/fstab 
                       /boot/grub/core.img

That will turn around and bite you eventually so I'd personally want to fix that. Which version of grub do you prefer?

I rather prefer grub 2, but it's up to you.

---

### Post by kansasnoob on 2010-05-25
> **darkod said:**
> Not sure about that. The package might be different for different architecture. On the other hand, it might not be. :)

If you are downloading and burning it, then you can choose which image to download.

There are different packages for 32 bit and 64 bit:

[http://packages.ubuntu.com/lucid/admin/grub-pc](http://packages.ubuntu.com/lucid/admin/grub-pc)

[http://packages.ubuntu.com/lucid/grub-common](http://packages.ubuntu.com/lucid/grub-common)

I wrote some notes that still need polishing so someone should be able to restore any version of grub using any Live CD:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

After I get that polished up a bit I'll submit it for HowTo status. It just makes sense to be able to depend on an OS's own package management.

---

