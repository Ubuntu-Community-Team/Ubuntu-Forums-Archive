---
title: "grub2 does not see partions"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by edogd on 2010-05-20
Hi all,

I just did a fresh install of LucidLynx 10.04 on to a new 2Tb SATA drive (/dev/sdc1=(hd2,0).  I have 2 other drives with windows XP and Karmic respectively (sda1=(hd0,1) and sdb1=(hd1,1) that are IDE drives.

I can boot into Lucid just fine.  But when I try to boot into the WinXP drive I get:

No such device
invalid signature

from grub2.

Now I went into the grub2 command line and did an ls and found that it listed all the partitions for /dev/sdc but did not list the partitions for /dev/sda and /dev/sdb, hence the reason for the "No such device" error when trying to boot to WinXP.  So basically grub2 cannot see the partitions on sda and sdb.

Now I tried the Grub Super boot disk and I have no problems booting into any drive or partition.  And when I do an ls in GSB disk, I can see all the drives and all the partitions.  Both the Grub Super disk and the grub that came with Lucid are version 1.98.

Also, I have tried installing the grub to the MBR for /dev/sda to avoid problems with the GPT of the 2TB drive.  During installation of Lucid, I did tell the installer to put grub on sdc.  I am not sure if that messed things up or what? 

How can I get grub to see all the partitions?
Any thoughts?

---

### Post by darkod on 2010-05-20
After installing grub2 to /dev/sda too, does the same thing happen when you try booting from /dev/sda?

Also, because you are trying to boot XP it seems there is entry in the grub boot menu for XP. But if it was never able to see that disk, how did it know there is XP there?

Use these instructions and post the content of your results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by tommcd on 2010-05-20
> **edogd said:**
> 
How can I get grub to see all the partitions?
Any thoughts?
Grub2 should be installed to the MBR of whatever hard drive you have listed as the *first boot device* in the computer's BIOS.

Since you did a clean install of Lucid, did you try simply running: 
```
sudo update-grub
```
from the terminal? This command will build a new /boot/grub/grub.cfg file that hopefully will allow you to boot Windows and Karmic.
Besides using the boot-info script that Darkod mentioned, post the contents of /boot/grub/grub.cfg after running: "sudo update-grub".

And welcome to the Ubuntu forums!

---

### Post by edogd on 2010-05-20
Thanks for the quick replies.

I have run the following commands

```

% sudo grub-mkdevicemap
% sudo grub-install /dev/sda
Installation finished. No error reported.
% sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP (loader) on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sda2
Found Ubuntu 9.10 (9.10) on /dev/sdb1
done
```

grub is seeing all the drives and partitions.  It's just that when grub boots is stops seeing the  partitions on sda and sdb.


Below is the output of my RESULTS.txt generated from ```
sudo ./boot_info_script055.sh 
```


>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks at sector 222582800 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

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
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   140,649,074   140,649,012   7 HPFS/NTFS
/dev/sda2         140,649,075   335,935,214   195,286,140   7 HPFS/NTFS
/dev/sda3         335,935,215   390,716,864    54,781,650   f W95 Ext d (LBA)
/dev/sda5         335,951,280   370,233,989    34,282,710   7 HPFS/NTFS
/dev/sda6         370,234,053   390,716,864    20,482,812   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,316   156,296,384     6,458,069   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1           2,048   976,562,175   976,560,128 Linux or Data
/dev/sdc2     976,562,176 1,953,124,351   976,562,176 Linux or Data
/dev/sdc3   3,891,027,968 3,907,028,991    16,001,024 Linux Swap
/dev/sdc4   1,953,124,352 3,891,027,967 1,937,903,616 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D474A26974A24DD4                       ntfs       WinXP                         
/dev/sda2        76D8030CD802C9F7                       ntfs       WinXPOld                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        01C4B5966CB8F8C0                       ntfs       Data                          
/dev/sda6        4183-E279                              vfat       WIN98                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        74291798-2166-45d6-8f58-0165e84ec52d   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        7da710e1-6328-44ef-b116-3bb143a01496   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        a2f9575c-c894-49c9-8f66-bd5870b71d2e   ext4                                     
/dev/sdc2        01de3024-f06d-48e9-a13f-c3ad22d7e7ad   ext4                                     
/dev/sdc3        a8f20fc8-728c-4569-b16d-0bb41cefd22c   swap                                     
/dev/sdc4        0b111c95-af39-4993-aaf6-bea3d2069333   ext4                                     
/dev/sdc: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc4        /export                  ext4       (rw)
/dev/sdc2        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Old Microsoft Windows XP Professional" /fastdetect


================================ sda2/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

c:\linux.bin="Linux" 

c:\stage1="Linux2" 


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
default		1	

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	2	

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows NT/2000/XP (loader)
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Microsoft Windows XP Professional
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Debian Kernels:
root


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
# kopt=root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=74291798-2166-45d6-8f58-0165e84ec52d

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

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		74291798-2166-45d6-8f58-0165e84ec52d
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		74291798-2166-45d6-8f58-0165e84ec52d
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		74291798-2166-45d6-8f58-0165e84ec52d
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		74291798-2166-45d6-8f58-0165e84ec52d
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		74291798-2166-45d6-8f58-0165e84ec52d
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		74291798-2166-45d6-8f58-0165e84ec52d
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, memtest86+
uuid		74291798-2166-45d6-8f58-0165e84ec52d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1



=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=74291798-2166-45d6-8f58-0165e84ec52d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=7da710e1-6328-44ef-b116-3bb143a01496 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /win_data ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  31.7GB: boot/grub/menu.lst
  31.6GB: boot/grub/stage2
  32.0GB: boot/initrd.img-2.6.31-17-generic
  31.6GB: boot/initrd.img-2.6.31-20-generic
  31.6GB: boot/initrd.img-2.6.31-21-generic
  32.0GB: boot/vmlinuz-2.6.31-17-generic
  31.5GB: boot/vmlinuz-2.6.31-20-generic
  31.5GB: boot/vmlinuz-2.6.31-21-generic
  31.6GB: initrd.img
  31.6GB: initrd.img.old
  31.5GB: vmlinuz
  31.5GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a2f9575c-c894-49c9-8f66-bd5870b71d2e
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a2f9575c-c894-49c9-8f66-bd5870b71d2e
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
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set a2f9575c-c894-49c9-8f66-bd5870b71d2e
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a2f9575c-c894-49c9-8f66-bd5870b71d2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set a2f9575c-c894-49c9-8f66-bd5870b71d2e
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a2f9575c-c894-49c9-8f66-bd5870b71d2e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set a2f9575c-c894-49c9-8f66-bd5870b71d2e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a2f9575c-c894-49c9-8f66-bd5870b71d2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set a2f9575c-c894-49c9-8f66-bd5870b71d2e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a2f9575c-c894-49c9-8f66-bd5870b71d2e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set a2f9575c-c894-49c9-8f66-bd5870b71d2e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set a2f9575c-c894-49c9-8f66-bd5870b71d2e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d474a26974a24dd4
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 76d8030cd802c9f7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 74291798-2166-45d6-8f58-0165e84ec52d
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 74291798-2166-45d6-8f58-0165e84ec52d
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 74291798-2166-45d6-8f58-0165e84ec52d
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 74291798-2166-45d6-8f58-0165e84ec52d
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 74291798-2166-45d6-8f58-0165e84ec52d
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 74291798-2166-45d6-8f58-0165e84ec52d
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=74291798-2166-45d6-8f58-0165e84ec52d ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 74291798-2166-45d6-8f58-0165e84ec52d
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=a2f9575c-c894-49c9-8f66-bd5870b71d2e /               ext4    errors=remount-ro 0       1
# /export was on /dev/sdc4 during installation
UUID=0b111c95-af39-4993-aaf6-bea3d2069333 /export         ext4    defaults        0       2
/dev/sdc2       /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=7da710e1-6328-44ef-b116-3bb143a01496 none            swap    sw              0       0
# swap was on /dev/sdc3 during installation
UUID=a8f20fc8-728c-4569-b16d-0bb41cefd22c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 113.9GB: boot/grub/core.img
 113.9GB: boot/grub/grub.cfg
 113.9GB: boot/initrd.img-2.6.32-21-generic
 114.0GB: boot/initrd.img-2.6.32-22-generic
 113.9GB: boot/vmlinuz-2.6.32-21-generic
  58.5GB: boot/vmlinuz-2.6.32-22-generic
 114.0GB: initrd.img
 113.9GB: initrd.img.old
  58.5GB: vmlinuz
 113.9GB: vmlinuz.old
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo1/sda6: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

---

### Post by oldfred on 2010-05-20
the boot script or grub2 do not always report drives correctly. Your grub entry in sda that says same drive does not mean same drive. I have same error on my system.

I thought with gpt partitioning you needed a BIOS_boot partition, but you are able to boot. Does both sda and sdc allow you to boot?

I would try as you boot edit out the search line in the windows entry. Sometimes that has caused problems. Sometimes mixed IDE and SATA have cause drive order issues also. You may want to check /boot/grub/device.map. I also saw one user who got it to work by changing drive number (which seemed wrong) from hd0 to hd1 or hd2.

You entries look ok to me, maybe someone else will see something.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by edogd on 2010-05-21
The odd thing is that when I use the Grub Super boot disk all hard disks and all partitions are recognized.

Why would the grub that comes with Lucid not be able to see the same things?


What do you mean by a BIOS_boot partition?  Do I need to make a special partition and mount it to /boot?  I am not familiar with this.

TIA

---

### Post by darkod on 2010-05-21
Your 10.04 is on /dev/sdc but the grub2 that is there is not working:

=> Grub 2 is installed in the MBR of /dev/sdc and looks at sector  222582800 
    of the same hard drive for core.img, but core.img can not be found  at this 
    location.

Also, to make things more confusing, your 2TB disk, sdc, is using a GPT partition table, not DOS.

But your older disks are with DOS partition table.

If you can make the system boot from the 2TB disk (sometimes it wouldn't let you when you have mix of IDE and SATA disks), then I would try reinstalling grub2 to /dev/sdc. Also, if you can boot into ubuntu, try this fix first for mixed GPT/DOS disks. This fix was needed for grub2 in 9.10, not sure if it's also needed for grub2 in 10.04:
[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)

Then reinstall grub2 to /dev/sdc. Again, if you can boot your ubuntu, you only need to do:

sudo grub-install /dev/sdc

If you can't, the commands are different but we'll discuss that later if needed. 

For the XP no such disk error, you might need to do this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by edogd on 2010-05-22
darkod you solved it!

You comment about the mixed drives was the key 
> If you can make the system boot from the 2TB disk (sometimes it wouldn't let you when you have mix of IDE and SATA disks), then I would try reinstalling grub2 to /dev/sdc. Also, if you can boot into ubuntu, try this fix first for mixed GPT/DOS disks. This fix was needed for grub2 in 9.10, not sure if it's also needed for grub2 in 10.04:
[http://ubuntuforums.org/showpost.php...0&postcount=14](http://ubuntuforums.org/showpost.php...0&postcount=14)


I added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!  
I can now see all the partitions on my IDE drives and boot from them too!!!!!


Actually, before I did that I wiped the 2TB SATA drive and started again.  This time I booted to the live Ubuntu CD and used Gparted to partition the disk.  I made small 8MB partition in the beginning of the disk along with my other larger partitions.  With the partitions in place I set the "grub_boot" flag on the small partition to allow grub place its core.img file in a fixed location not have to deal with blocklists.  But all that still did not work.  Oddly the boot_info_script055.sh script still tells me that the core.img can not be found.

" => Grub 2 is installed in the MBR of /dev/sdc and looks at sector 34 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.
"
I am pretty sure that the core.img got written to the grub_boot partition, because when I ran grub-install /dev/sdc this time it did not give me a warning about blocklists.  Maybe the script needs to be modified some how.

Nevertheless, only your suggestion solved it!

Why oh why is this part_msdos module not loaded up by default?  I am sure I am not the only person in the world with mixed MRB and GPT disks using grub2.

---

### Post by darkod on 2010-05-22
> **edogd said:**
> darkod you solved it!



Actually someone else solved it, I just gave you the link. :)
Glad it works now, enjoy it.

---

