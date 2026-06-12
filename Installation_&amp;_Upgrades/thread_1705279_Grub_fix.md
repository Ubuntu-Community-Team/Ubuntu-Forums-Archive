---
title: "Grub fix?"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by wgw on 2011-03-12
I'm trying to fix my grub installation and tidy up my hard disk after an upgrade. 

I upgraded to Lucid, updated to grub2, and converted my windows partition into a ubuntu partition. 

Now I realize that my legacy grub is the only grub running. Grub2 isn't firing. 

The legacy grub is on sda6 under boot_ and grub2 is on sda8 under boot.

> $ grub-probe -t device /boot/grub
/dev/sda8
$ grub-probe -t device /boot_/grub
/dev/sda6

I thought all I had to do was to change the boot would be to: sudo grub-install /dev/sd8

But the doc says I shouldn't put it on a particular partition:

>       If the user attempts to run the command with a specific partition (example: sudo grub-install /dev/sda6 ) a warning will be issued. Specifying a partition is not recommended due to the use of blocklists, which the developers consider unreliable. An option is provided on how to override this recommendation if the user still wishes to do so.

But it looks like it is already on a partition, sda6. At any rate, I would prefer to first chainload grub2. Tried that,with this entry to menu.lst, but got a file error. 
> 
title        Chainload into GRUB 2
uuid        1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
kernel        /boot/grub/core.img

??? 

What is the best way to untangle my grubs?

Thanks for any suggestions...

(attaching complete grub information)

---

### Post by wilee-nilee on 2011-03-12
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a what is where picture of the whole thang.

---

### Post by wgw on 2011-03-12
Already attached that (Results.txt) in my first post...

(Thanks!)

---

### Post by wilee-nilee on 2011-03-12
Sorry about that I should have looked,lets share it with everybody eh.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    42,797,159    42,797,097  83 Linux
/dev/sda2         147,283,920   156,295,439     9,011,520  12 Compaq diagnostics
/dev/sda3          42,797,160   147,283,919   104,486,760   5 Extended
/dev/sda5          42,797,223    46,974,059     4,176,837  82 Linux swap / Solaris
/dev/sda6          46,974,123    58,010,714    11,036,592  83 Linux
/dev/sda7         100,679,418   147,283,919    46,604,502  83 Linux
/dev/sda8          58,010,778   100,679,354    42,668,577  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        290885aa-f307-4a49-86e0-c313d24c53c8   ext3                                     
/dev/sda2        083C-C531                              vfat       SERVICEV001                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        6b754661-dc0f-4867-8845-812a94e3333a   swap                                     
/dev/sda6        6b1185d5-39cf-4baa-9b31-8fbd30d8ad32   ext3                                     
/dev/sda7        2c5acbe7-4c7d-4257-8691-bda22ef074ab   ext3                                     
/dev/sda8        1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext3       (rw,errors=remount-ro)
/dev/sda6        /boot_                   ext3       (rw)
/dev/sda7        /home                    ext3       (rw)
/dev/sda1        /data2                   ext3       (rw)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=0
default=C:\
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\ = "PC-DOS"

============================= sda6/grub/menu.lst: =============================

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
# timeout		10

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=splash quiet

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.32-25-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro splash quiet 
initrd		/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.32-25-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro  single
initrd		/initrd.img-2.6.32-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.32-24-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro splash quiet 
initrd		/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.32-24-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro  single
initrd		/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.31-22-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro splash quiet 
initrd		/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.31-22-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro  single
initrd		/initrd.img-2.6.31-22-generic

title		Ubuntu 10.04.1 LTS, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Chainload into GRUB 2
uuid        1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
kernel        /boot/grub/core.img






=================== sda6: Location of files loaded by Grub: ===================


  26.6GB: grub/menu.lst
  26.6GB: grub/stage2
  24.5GB: initrd.img-2.6.17-10-generic.bak
  24.5GB: initrd.img-2.6.17-11-generic.bak
  24.4GB: initrd.img-2.6.31-22-generic
  24.4GB: initrd.img-2.6.32-24-generic
  24.5GB: initrd.img-2.6.32-25-generic
  24.5GB: vmlinuz-2.6.31-22-generic
  24.5GB: vmlinuz-2.6.32-24-generic
  24.5GB: vmlinuz-2.6.32-25-generic

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
search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
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
search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 083c-c531
	drivemap -s (hd0) ${root}
	chainloader +1
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda8 :
UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb	/	ext3	defaults,errors=remount-ro	0	1
#Entry for /dev/sda6 :
UUID=6b1185d5-39cf-4baa-9b31-8fbd30d8ad32	/boot_	ext3	defaults	0	2
#Entry for /dev/sda7 :
UUID=2c5acbe7-4c7d-4257-8691-bda22ef074ab	/home	ext3	defaults	0	2
#Entry for /dev/sda1 :
UUID=290885aa-f307-4a49-86e0-c313d24c53c8	/data2	ext3	defaults	0	1
#Entry for /dev/sda2 :
UUID=083C-C531	/media/sda2	vfat	defaults,utf8,umask=007,gid=46,noauto	0	1
#Entry for /dev/sda5 :
UUID=6b754661-dc0f-4867-8845-812a94e3333a	none	swap	sw	0	0
/dev/cdrom	/media/cdrom0	udf,iso9660	user,noauto	0	0



=================== sda8: Location of files loaded by Grub: ===================


  35.3GB: boot/grub/core.img
  45.4GB: boot/grub/grub.cfg
  35.3GB: boot/initrd.img-2.6.32-25-generic
  35.3GB: boot/initrd.img-2.6.32-26-generic
  35.4GB: boot/initrd.img-2.6.32-27-generic
  36.1GB: boot/initrd.img-2.6.32-28-generic
  38.3GB: boot/initrd.img-2.6.32-29-generic
  35.4GB: boot/vmlinuz-2.6.32-26-generic
  38.3GB: boot/vmlinuz-2.6.32-27-generic
  35.4GB: boot/vmlinuz-2.6.32-28-generic
  38.3GB: boot/vmlinuz-2.6.32-29-generic
  38.3GB: initrd.img
  36.1GB: initrd.img.old
  38.3GB: vmlinuz
  35.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

....


```

---

### Post by Hedgehog1 on 2011-03-12
fstab says **/boot_** is in sda6:

```
proc	/proc	proc	defaults	0	0
#Entry for /dev/sda8 :
UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb	/	ext3	defaults,errors=remount-ro	0	1
#Entry for /dev/**sda6** :
UUID=6b1185d5-39cf-4baa-9b31-8fbd30d8ad32	**/boot_**	ext3	defaults	0	2
```

But grub2 is really in /boot of **sda8**, right? 

```
sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   **/boot/grub/grub.cfg** /etc/fstab /boot/grub/core.img
```

So the fstab entry for **/boot_** is outdated.  The reference to **sda6** can be removed (commented out for now with a '#') from fstab.

Can the partition **sda6** be deleted if everything boots OK after the fstab change?  I think so...

***The Hedge***

:KS

---

### Post by debd on 2011-03-12
the purge and reinstalling of grub by drs305 has worked for me everytime my grub was messed up.
here is the thread link__  [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

the part - "purge and reinstall without chroot" is the method that solved most of the problems.

the generated grub.cfg should recognise which partition has the boot dir.

---

### Post by wgw on 2011-03-12
yup; that is correct. I have on sda6 the legacy grub, and it boots from there for a moment.

I can't delete that unless I point the boot to sda8. That is why I was chainloading sda8. 

But, my guess is I should bite the bullet and install on sd6: it is in fact set up as the boot partition and is designated as boot. 

I suppose I can overwrite it with grub-install....

---

### Post by Quackers on 2011-03-12
Use the chroot part of the guide by drs305, ignoring the boot partition and mounting sda8. You can then purge grub and grub2 and start again. That way the part of grub2 in the mbr of the drive will automatically know that the rest of its boot files are in sda8.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Hedgehog1 on 2011-03-12
> **Quackers said:**
> You can then purge grub and grub2 and start again. That way the part of grub2 in the mbr of the drive will automatically know that the rest of its boot files are in sda8.]

Well, I was **close.**  I didn't see the purge grub(s) and start again part.  This stuff gets tricky, ya know?

***The Hedge***

:KS

---

### Post by Quackers on 2011-03-12
> **Hedgehog1 said:**
> Well, I was **close.**  I didn't see the purge grub(s) and start again part.  This stuff gets tricky, ya know?

***The Hedge***

:KS

Lol, yes it does :-)
That's one reason why it's better to start again sometimes from the beginning. It undo's everything! Using drs305's guide gets rid of anything to do with grub legacy and grub2 that was connected to sda8 (in wgw's case) and gives a completely fresh start. Very useful :-)

---

### Post by wgw on 2011-03-12
Thanks for such prompt responses: I feel better about starting over again. Will follow the chroot scenario (erasing everything first). 

Thanks!

---

