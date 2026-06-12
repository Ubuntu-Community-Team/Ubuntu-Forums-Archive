---
title: "Dual boot problems after adding 10.04"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by justgrant2009 on 2010-08-16
Ok, so i have windows vista on my system as well as kubuntu and ubuntu hardy heron.  I kinda pulled a rookie move and installed yet another partition with ubuntu 10.04 instead of updating the other one, with the intent of just deleting the older partition to completely start fresh with 10.04.  Unfortunately after that, Windows won't boot anymore.  In the grub menu, i still select the windows loader, and when it loads, it asks me to "fix" windows.  It takes a while to fix it, then says to reboot.  I do, and it goes right back to asking me to fix it. 
Any help? if there is anything you need me to list out for you, just ask.  

Thanks in advance.

---

### Post by oldfred on 2010-08-16
What kind of 'fix' does it want to run. chkdsk?

I have several Ubuntu root partitions of 20-25GB so I keep my last install, current install and one for testing next install. But I keep all data in a separate /data partition.

To see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by justgrant2009 on 2010-08-17
When I boot the windows partition, it just pulls up a windows menu thing asking me how i want to repair it, I asked it to do an auto repair and it took a while, then asked me to reboot saying that after reboot it should have been fine, but it took me right back to that same menu.

Here is the Results.txt


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

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

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   523,576,471   520,502,424   7 HPFS/NTFS
/dev/sda3         608,464,896   625,141,759    16,676,864  17 Hidden HPFS/NTFS
/dev/sda4         523,577,342   608,461,874    84,884,533   5 Extended
/dev/sda5         606,710,853   608,461,874     1,751,022  82 Linux swap / Solaris
/dev/sda6         563,447,871   568,331,504     4,883,634  83 Linux
/dev/sda7         568,331,568   568,684,934       353,367  82 Linux swap / Solaris
/dev/sda8         568,684,998   606,710,789    38,025,792  83 Linux
/dev/sda9         523,577,344   561,694,719    38,117,376  83 Linux
/dev/sda10        561,696,768   563,447,807     1,751,040  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       b901f965-3c3e-488d-8181-83ff21afd5a1   swap                                     
/dev/sda1        DA1C4F001C4ED763                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        BA4C7E6B4C7E21F5                       ntfs       SQ004732V03                   
/dev/sda3        4484A48084A475D8                       ntfs       HDDRECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        149040d8-85ea-44b5-8fd7-62f5357bff6f   swap                                     
/dev/sda6        4254e082-e6b3-4c4d-aec3-09fd3375adfc   ext3                                     
/dev/sda7        b11c5087-afeb-41fe-907a-9f97564fc79e   swap                                     
/dev/sda8        4254e082-e6b3-4c4d-aec3-09fd3375adfc   ext3                                     
/dev/sda9        9eb61add-0547-4b83-997e-87c8e1919027   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,errors=remount-ro)


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
# kopt=root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4254e082-e6b3-4c4d-aec3-09fd3375adfc

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		4254e082-e6b3-4c4d-aec3-09fd3375adfc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4254e082-e6b3-4c4d-aec3-09fd3375adfc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		4254e082-e6b3-4c4d-aec3-09fd3375adfc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Kubuntu (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5958468a-6dc6-4c5f-b06e-af0b5ca13206 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5958468a-6dc6-4c5f-b06e-af0b5ca13206 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=b11c5087-afeb-41fe-907a-9f97564fc79e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 290.8GB: boot/grub/menu.lst
 289.2GB: boot/grub/stage2
 289.2GB: boot/initrd.img-2.6.28-11-generic
 288.6GB: boot/vmlinuz-2.6.28-11-generic
 289.2GB: initrd.img
 288.6GB: vmlinuz

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
# kopt=root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4254e082-e6b3-4c4d-aec3-09fd3375adfc

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




title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		4254e082-e6b3-4c4d-aec3-09fd3375adfc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4254e082-e6b3-4c4d-aec3-09fd3375adfc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		4254e082-e6b3-4c4d-aec3-09fd3375adfc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Kubuntu (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5958468a-6dc6-4c5f-b06e-af0b5ca13206 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5958468a-6dc6-4c5f-b06e-af0b5ca13206 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=b11c5087-afeb-41fe-907a-9f97564fc79e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 293.1GB: boot/grub/menu.lst
 291.8GB: boot/grub/stage2
 291.9GB: boot/initrd.img-2.6.28-11-generic
 293.7GB: boot/initrd.img-2.6.28-15-generic
 291.3GB: boot/vmlinuz-2.6.28-11-generic
 293.1GB: boot/vmlinuz-2.6.28-15-generic
 293.7GB: initrd.img
 291.9GB: initrd.img.old
 293.1GB: vmlinuz
 291.3GB: vmlinuz.old

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 9eb61add-0547-4b83-997e-87c8e1919027
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 9eb61add-0547-4b83-997e-87c8e1919027
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
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 9eb61add-0547-4b83-997e-87c8e1919027
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=9eb61add-0547-4b83-997e-87c8e1919027 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 9eb61add-0547-4b83-997e-87c8e1919027
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=9eb61add-0547-4b83-997e-87c8e1919027 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 9eb61add-0547-4b83-997e-87c8e1919027
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9eb61add-0547-4b83-997e-87c8e1919027 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 9eb61add-0547-4b83-997e-87c8e1919027
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9eb61add-0547-4b83-997e-87c8e1919027 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 9eb61add-0547-4b83-997e-87c8e1919027
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 9eb61add-0547-4b83-997e-87c8e1919027
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set ba4c7e6b4c7e21f5
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4484a48084a475d8
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4254e082-e6b3-4c4d-aec3-09fd3375adfc
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4254e082-e6b3-4c4d-aec3-09fd3375adfc
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4254e082-e6b3-4c4d-aec3-09fd3375adfc
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 4254e082-e6b3-4c4d-aec3-09fd3375adfc
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 4254e082-e6b3-4c4d-aec3-09fd3375adfc
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=4254e082-e6b3-4c4d-aec3-09fd3375adfc ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 4254e082-e6b3-4c4d-aec3-09fd3375adfc
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=9eb61add-0547-4b83-997e-87c8e1919027 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=b901f965-3c3e-488d-8181-83ff21afd5a1 none            swap    sw              0       0

=================== sda9: Location of files loaded by Grub: ===================


 270.3GB: boot/grub/core.img
 278.9GB: boot/grub/grub.cfg
 270.6GB: boot/initrd.img-2.6.32-21-generic
 271.6GB: boot/initrd.img-2.6.32-24-generic
 270.6GB: boot/vmlinuz-2.6.32-21-generic
 270.9GB: boot/vmlinuz-2.6.32-24-generic
 271.6GB: initrd.img
 270.6GB: initrd.img.old
 270.9GB: vmlinuz
 270.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ae 36 90 d5 be 10 63 24  fd fe 4c 3d 52 f6 c0 e5  |.6....c$..L=R...|
00000010  1e a1 bd b7 f5 7a 84 20  69 20 96 67 10 dd 29 64  |.....z. i .g..)d|
00000020  19 d6 1e bc 8d 4a 88 16  72 7b 19 cd fb ba 3f 7a  |.....J..r{....?z|
00000030  5a 6a f5 63 bc 2c 9c 77  de 88 47 6c d1 2b eb d3  |Zj.c.,.w..Gl.+..|
00000040  77 7d f1 92 7c 11 8a 63  59 64 16 ff b6 e8 83 22  |w}..|..cYd....."|
00000050  9e 09 44 ac d2 4f 29 56  89 00 ca 36 99 5e b9 30  |..D..O)V...6.^.0|
00000060  21 98 45 d3 45 54 e6 2d  ea c0 fa e4 83 b9 a8 85  |!.E.ET.-........|
00000070  75 a8 41 0d 23 48 7b 74  20 3f a7 24 e5 40 50 db  |u.A.#H{t ?.$.@P.|
00000080  fd 34 e8 35 9f a5 05 4c  89 c0 82 3f 22 fe 09 21  |.4.5...L...?"..!|
00000090  b2 06 41 23 50 d7 05 d0  74 89 b8 40 10 c0 e1 8b  |..A#P...t..@....|
000000a0  93 2f 50 0c ba e7 df 67  f6 4f 0b e5 de 69 5b 36  |./P....g.O...i[6|
000000b0  c6 67 42 bb 72 79 aa 0f  65 c1 79 66 5d 8b b7 88  |.gB.ry..e.yf]...|
000000c0  e3 fd 79 d9 db 66 9f d1  15 38 b7 b5 e9 2b f5 70  |..y..f...8...+.p|
000000d0  75 f3 29 45 42 81 24 24  65 b2 59 57 17 32 c4 f2  |u.)EB.$$e.YW.2..|
000000e0  80 af c8 c3 0f 79 88 68  1a 2d 46 ed 35 d4 83 53  |.....y.h.-F.5..S|
000000f0  8d 8c 9f 3b 43 62 65 4c  db 17 13 7d 93 a0 c2 78  |...;CbeL...}...x|
00000100  12 80 00 00 30 5d 08 00  01 03 00 9c 5f 00 00 00  |....0]......_...|
00000110  00 af 01 21 4f fe ff ff  91 83 45 8c 36 6e 50 91  |...!O.....E.6nP.|
00000120  32 24 cb 38 63 8c 97 71  c7 42 b3 6d 52 86 6d ad  |2$.8c..q.B.mR.m.|
00000130  45 66 81 5b 4a fa 9a fc  d3 1b ef 51 71 2c 79 50  |Ef.[J......Qq,yP|
00000140  f9 e9 ae 6e a2 e0 13 78  65 9f 6b fb 24 ea 7e 93  |...n...xe.k.$.~.|
00000150  78 5f df 2b 46 31 2c 98  06 89 29 df 72 32 69 2c  |x_.+F1,...).r2i,|
00000160  f4 74 82 fd 51 df 46 52  10 2f d9 c4 87 29 f8 5d  |.t..Q.FR./...).]|
00000170  95 5b b5 99 db 0d 87 89  33 44 b9 42 3f 5e fe 6f  |.[......3D.B?^.o|
00000180  25 63 d1 d1 2f 54 75 18  f0 72 f8 e6 dd df 2d 00  |%c../Tu..r....-.|
00000190  5c 4c 71 f8 12 79 fe 2a  4a 80 13 d4 c0 b1 27 83  |\Lq..y.*J.....'.|
000001a0  9d d6 bb 8f 38 c8 05 82  4c 12 4e 3b 49 04 80 e7  |....8...L.N;I...|
000001b0  1f 6b 4b 1a b8 bc f8 57  15 b6 69 77 6d 0d 00 fe  |.kK....W..iwm...|
000001c0  ff ff 82 fe ff ff 47 84  f4 04 ee b7 1a 00 00 fe  |......G.........|
000001d0  ff ff 05 fe ff ff 02 60  60 02 f1 84 4a 00 00 00  |.......``...J...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-08-17
The windows auto repair often has to be run 3 times for it to repair everything.

I see you added a windows boot in the old install but do not see one in the new install.

Did your run this in the new install?

sudo update-grub

---

### Post by justgrant2009 on 2010-08-17
No i havn't run that command, should I?

---

### Post by justgrant2009 on 2010-08-17
Ok, I just ran that command, I'm about to see if I reboot to windows if it works yet.  Cross your fingers.

OK! it worked, I found out that actually, somehow my boot menu titles got mixed up.  I was trying to select the boot menu item labled windows loader, but when i selected windows recovery loader, it loaded windows like normal... :-/ soooo, i don't really know how that happened, but at least its working again.  

Thanks fred

---

### Post by oldfred on 2010-08-17
We have seen a lot of the mis labeling of recovery & actual installs. The workaround is not exactly easy but you copy your entries into 40_custom and fix the titles ( or remove the recovery) and turn off os prober to prevent it from running on updates and giving duplicate entries.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

I added this to turn off prober :
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

