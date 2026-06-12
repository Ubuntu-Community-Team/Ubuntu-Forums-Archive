---
title: "Unable to boot 10.4,  getting grub rescue"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by kgorton on 2010-07-10
as previously directed to by drs305 I have done the following.  
```

Boot from a recent LiveCD and mount sda6 on /mnt:
Code:
sudo mount /dev/sda6 /mnt
Then install grub to the MBR, and place the files in sda6 with the following command. Note that you do not designate the partition in the command, which will ensure Grub2 is installed in the MBR. The configuration files will be placed in /boot/grub of sda6 since that is the partition that is mounted:
Code:
sudo grub-install --root-directory=/mnt /dev/sda
```

and I still have an issue,  when I boot it shows me

```

Error: file not found
grub rescue>

```

I am wondering if I have a corrupt file in my /boot directory on sda6 at this point.  please assist.   Thanks


Here is a copy of my results from bootinfo script.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 102674792 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   102,687,479       289,170  83 Linux
/dev/sda3         102,687,480 1,953,520,064 1,850,832,585   5 Extended
/dev/sda5         102,687,543   395,648,819   292,961,277  83 Linux
/dev/sda6         395,648,883   424,951,379    29,302,497  83 Linux
/dev/sda7         976,960,908 1,953,520,064   976,559,157  83 Linux
/dev/sda8         957,425,868   976,960,844    19,534,977  82 Linux swap / Solaris
/dev/sda9         424,951,443   620,269,649   195,318,207  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1                                              squashfs                                 
/dev/loop2                                              squashfs                                 
/dev/sda1        C664997964996D45                       ntfs                                     
/dev/sda2        97262b9f-67ed-4870-b79d-a8301bc535e0   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e2516c08-9ddf-4a1f-8f8e-b5d19e7e2247   reiserfs                                 
/dev/sda6        48570eb2-26f9-4a15-a6e7-25bfcaac83e5   ext4                                     
/dev/sda7        198a592f-370e-4c62-a17e-f61b565e28f9   reiserfs                                 
/dev/sda8        b8ddbab1-10cb-4779-8dbb-15a550c5be1e   swap                                     
/dev/sda9        72b72833-030a-414f-8bc4-ceaac1fc44b8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /lib/unionfs/usr         squashfs   (rw)
/dev/loop1       /lib/unionfs/firmware    squashfs   (rw)
/dev/loop2       /lib/unionfs/modules     squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

============================= sda2/grub/menu.lst: =============================

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
# kopt=root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=97262b9f-67ed-4870-b79d-a8301bc535e0

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-9-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-9-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/memtest86+.bin
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


=================== sda2: Location of files loaded by Grub: ===================


  52.5GB: grub/menu.lst
  52.5GB: grub/stage2
  52.4GB: initrd.img-2.6.27-7-generic
  52.4GB: initrd.img-2.6.27-9-generic
  52.4GB: vmlinuz-2.6.27-7-generic
  52.4GB: vmlinuz-2.6.27-9-generic

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
search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
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
search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-19-generic ...'
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c664997964996d45
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=72b72833-030a-414f-8bc4-ceaac1fc44b8 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=b8ddbab1-10cb-4779-8dbb-15a550c5be1e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda7	/media/storage	reiserfs	defaults,rw,nosuid,nodev	0	0

=================== sda6: Location of files loaded by Grub: ===================


 204.1GB: boot/grub/core.img
 204.0GB: boot/grub/grub.cfg
 202.9GB: boot/grub/stage2
 215.8GB: boot/initrd.img-2.6.31-19-generic
 215.5GB: boot/initrd.img-2.6.31-20-generic
 204.7GB: boot/initrd.img-2.6.31-21-generic
 213.0GB: boot/initrd.img-2.6.31-22-generic
 215.0GB: boot/initrd.img-2.6.32-23-generic
 202.8GB: boot/vmlinuz-2.6.31-19-generic
 215.5GB: boot/vmlinuz-2.6.31-20-generic
 204.7GB: boot/vmlinuz-2.6.31-21-generic
 216.9GB: boot/vmlinuz-2.6.31-22-generic
 212.7GB: boot/vmlinuz-2.6.32-23-generic
 215.0GB: initrd.img
 213.0GB: initrd.img.old
 212.7GB: vmlinuz
 216.9GB: vmlinuz.old
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```

__________________

---

### Post by efflandt on 2010-07-10
What motherboard do you have?  Maybe your BIOS cannot cope with the new default partition alignment.  I had that problem (error: file not found) with an old HP a530n with Asus mobo from 2004.  So you might need to remove your sda6 and use **partman/alignment=cylinder** kernel boot parameter when booting install CD or iso on USB.

What was amusing when that happened is that from grub rescue I could **ls (hd0,2)** and **ls (hd0,2)/**, but **ls (hd0,2)/boot** just showed a happy face ascii character and **ls (hd0,2)/boot/grub** said file not found.

Note that there is a gap between where sda5 ends and sda6 begins.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems")

---

### Post by Rubi1200 on 2010-07-10
The above post by efflandt makes a good point, but I actually don't think that is the problem.

I think what we have here is a syntax error.

> sudo mount /dev/sda6 /mntThis looks okay.

> sudo grub-install --root-directory=/mnt /dev/sdaI think the problem is here. It is supposed to be, I am almost certain, this:

```
sudo grub-install --root-directory=/mnt**/** /dev/sda
```Notice the slash after mnt

See here for confirmation:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Try it again and see if it works and don't forget to run ```
sudo update-grub
``` once you have rebooted.

---

### Post by kgorton on 2010-07-10
efflandt, 
    I too see your point, yet do not agree this is the issue since when i first upgraded to 10.4 my PC was booting fine.  The issue only started occuring after the PC locked up in a suspend and I only had the option to turn it off directly.  (which is why i was thinking it could be corrupt files.  but i did run fsck on the drive and cleaned up a bunch of errors that occured. ) Although i will get back to you with the information still when I get home to doublecheck.

Rubi1200 - I will try the commands again with the extra '/'.

---

### Post by kgorton on 2010-07-10
I reran the commands and ran the update-grub still no luck having the same issue.   I am thinking that I am going to have to do a reformat.  possibly with the errors that were on the partition it is just ready nuke and pave.

her is another copy of my most recent results log  just in case it is any different after, although at quick glance i don't see any issues.

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 102674792 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   102,687,479       289,170  83 Linux
/dev/sda3         102,687,480 1,953,520,064 1,850,832,585   5 Extended
/dev/sda5         102,687,543   395,648,819   292,961,277  83 Linux
/dev/sda6         395,648,883   424,951,379    29,302,497  83 Linux
/dev/sda7         976,960,908 1,953,520,064   976,559,157  83 Linux
/dev/sda8         957,425,868   976,960,844    19,534,977  82 Linux swap / Solaris
/dev/sda9         424,951,443   620,269,649   195,318,207  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1                                              squashfs                                 
/dev/loop2                                              squashfs                                 
/dev/sda1        C664997964996D45                       ntfs                                     
/dev/sda2        97262b9f-67ed-4870-b79d-a8301bc535e0   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e2516c08-9ddf-4a1f-8f8e-b5d19e7e2247   reiserfs                                 
/dev/sda6        48570eb2-26f9-4a15-a6e7-25bfcaac83e5   ext4                                     
/dev/sda7        198a592f-370e-4c62-a17e-f61b565e28f9   reiserfs                                 
/dev/sda8        b8ddbab1-10cb-4779-8dbb-15a550c5be1e   swap                                     
/dev/sda9        72b72833-030a-414f-8bc4-ceaac1fc44b8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /lib/unionfs/usr         squashfs   (rw)
/dev/loop1       /lib/unionfs/firmware    squashfs   (rw)
/dev/loop2       /lib/unionfs/modules     squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

============================= sda2/grub/menu.lst: =============================

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
# kopt=root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=97262b9f-67ed-4870-b79d-a8301bc535e0

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-9-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-9-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/memtest86+.bin
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


=================== sda2: Location of files loaded by Grub: ===================


  52.5GB: grub/menu.lst
  52.5GB: grub/stage2
  52.4GB: initrd.img-2.6.27-7-generic
  52.4GB: initrd.img-2.6.27-9-generic
  52.4GB: vmlinuz-2.6.27-7-generic
  52.4GB: vmlinuz-2.6.27-9-generic

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
search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
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
search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-19-generic ...'
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c664997964996d45
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=72b72833-030a-414f-8bc4-ceaac1fc44b8 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=b8ddbab1-10cb-4779-8dbb-15a550c5be1e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda7	/media/storage	reiserfs	defaults,rw,nosuid,nodev	0	0

=================== sda6: Location of files loaded by Grub: ===================


 204.0GB: boot/grub/core.img
 204.0GB: boot/grub/grub.cfg
 202.9GB: boot/grub/stage2
 215.8GB: boot/initrd.img-2.6.31-19-generic
 215.5GB: boot/initrd.img-2.6.31-20-generic
 204.7GB: boot/initrd.img-2.6.31-21-generic
 213.0GB: boot/initrd.img-2.6.31-22-generic
 215.0GB: boot/initrd.img-2.6.32-23-generic
 202.8GB: boot/vmlinuz-2.6.31-19-generic
 215.5GB: boot/vmlinuz-2.6.31-20-generic
 204.7GB: boot/vmlinuz-2.6.31-21-generic
 216.9GB: boot/vmlinuz-2.6.31-22-generic
 212.7GB: boot/vmlinuz-2.6.32-23-generic
 215.0GB: initrd.img
 213.0GB: initrd.img.old
 212.7GB: vmlinuz
 216.9GB: vmlinuz.old
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```

---

### Post by drs305 on 2010-07-10
> **kgorton said:**
> ```

=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```

kgorton,

Do you have a RAID setup? Your RESULTS.txt looks completely normal except for the last entry. I know there have been issues with Grub 2 and RAID, and I know there were workarounds when a RAID setup was detected but not used.

I don't use RAID and so am pretty uninformed about it, but your problems may be due to a RAID setting (real or imagined by Grub) - even if you aren't using it. I've seen posts about this and how to remove it but couldn't find them with a quick search. 

Someone familiar with this problem may answer, you could check the Launchpad bug reports, or do a more in-depth Google search if you think this might have something to do with your inablility to boot.

---

### Post by kgorton on 2010-07-10
drs,

no I do not have raid setup.  I only have 1 single Terabyte Hard drive and i did not setup any raid on that.

---

### Post by drs305 on 2010-07-11
Since you are getting the mdadm message, something is going on whereby Grub2 may be looking for a RAID setup. 

As I mentioned, RAID is beyond my expertise but if:
a. I had time
b. had an unbootable system, and
c. wanted to experiment before accomplishing a full reinstall
this post [noparse](#18)[/noparse] may hold some promise:
[http://ubuntuforums.org/showthread.php?p=9237139#post9237139]("http://ubuntuforums.org/showthread.php?p=9237139#post9237139")
Installing *mdadm* and letting it run may help clear things up.

---

### Post by oldfred on 2010-07-11
If you do not have RAID but the BIOS has or had a raid setting it may have written data on the drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

I also see two sets of windows XP files in sda1. And This file in your grub
 202.9GB: boot/grub/stage2
That stage2 is from old grub legacy and we have seen issues with old grub interfering with grub2. If the raid setting fix does not solve it we may need to totally uninstall grub & grub2 and cleanly reinstall grub2.

---

### Post by Sticky_Bit on 2010-07-11
I had this issue after upgrading from 9.10 to 10.04 this morning. Let me refer you to this post.

[http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub)

The OP solution worked for me. You basically go through the install routine without wiping any data and just re-install grub. I have 2 hdd's One with Win 7 64bit and one with Ubuntu 10.04 64bit in a dual-boot and everything works fine now. I'm wrinting you this from my 10.04 install while it is updating 224 packages....:p

UPDATE: Windows 7 boot loader was hosed, but Ubuntu boots fine

---

### Post by alexshr on 2010-07-11
I am exactly not sure whether this will work for you or not, but I found it somewhere in internet, while I was searching for some other solutions. 

Anyway, here is the solution that I found.

If you just want to get your grub back, then you can simply use the Linux Live CD for the version of Linux you are using. 

Follow the installation instructions as usual, when you come to the stage to install grub. Install it and then simply abort the installation, that will install the grub into the desired partition and you'll still be able to login to the system.

Sorry I don't remember the url for the link.

---

### Post by kgorton on 2010-07-11
I tried checking to see if raid was on the drive, and ran the command and came up with

```

dmraid -E -r /dev/sda
no raid disks and with names: "/dev/sda"

```

The bios settings appear to be disabled.  I will double check.  But I am inclined to think i do need to completely reinstall GRUB2.  I know that grub is on sda2 this had not been an issue in the past but certainly i have no issue getting rid f it.  also sda1 the windows partition that was there is actually no longer there it is simply an NTFS partition with my old "DOCUMENTS and SETTINGS" folder, so everything else has been deleted,  just never cleaned up grub.  Those both were there from when I had ubuntu 8.10 with a dual boot.  but then I decieded to format and install.  I just had chosen at that point when I installed 9.4 to keep /boot as part of / instead of using the 100mb sdb2 partition.  All that to say at this point I have no issues cleaning those up (sda1, and sda2) and getting rid of them.  But how do I go about uninstalling and reinstalling GRUB2.  I have been looking for a solution like that since, as i stated earlier,  this was booting fine in ubuntu 10.4 until a system crash.  then it was no longet booting, even after checking/fixing the partition (through Gparted and e2fsck).

---

### Post by oldfred on 2010-07-11
Kansasnoob has combined the chroot into one line with &
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Once chrooted to uninstall grub & grub2 (grub-pc), change sda to sdb, sdc etc if grub wanted on MBR of different drive.

apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
# possibly this also
dpkg-reconfigure grub-pc

---

### Post by kgorton on 2010-07-20
I appologize for the super late response in this reply.   I have resolved the issue by chrooting into the correct drive and uninstalling and reinstalling grub.  must have been a corrup file somewhere in there.  Thanks All for your help.

---

