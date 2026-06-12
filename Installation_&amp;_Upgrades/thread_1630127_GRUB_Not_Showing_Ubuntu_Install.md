---
title: "GRUB Not Showing Ubuntu Install"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by -nat- on 2010-11-24
I have both 8.10 and 10.10 installed on my hard drive, but whenever I boot the GRUB (I believe it is GRUB Legacy not GRUB2) only shows 8.10. Is there any way to get it to see my newly-installed 10.10?

---

### Post by Quackers on 2010-11-24
From within the booted up system have you run sudo update-grub in a terminal? Is the other system picked up then?

---

### Post by robert shearer on 2010-11-24
> **-nat- said:**
> I have both 8.10 and 10.10 installed on my hard drive, but whenever I boot the GRUB (I believe it is GRUB Legacy not GRUB2) only shows 8.10. Is there any way to get it to see my newly-installed 10.10?

Strange, unless you installed 8.10 **after** 10.10 then you should have Grub2 and all should be sweet.
Legacy grub AFAIK does not support Ext 4 so won't see your 10.10 install.


Here is the Grub documentation page...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You might want to scroll down to "Reinstalling Grub2 from the live cd" and check that.
Post if you have Questions. :)

---

### Post by wilee-nilee on 2010-11-24
Could be a number of reasons, post the running of the bootscript in my signature. Post it in code tags by clicking on the # in the reply panel. Paste all the text from the generated file between the code tags.

Quackers or I can help you better and others if we see what's up much better.;)

---

### Post by -nat- on 2010-11-24
> **Quackers said:**
> From within the booted up system have you run sudo update-grub in a terminal? Is the other system picked up then?

Tried that, didn't work. Tried updating to Grub2, but it still doesn't see the install (it's defenatly there though)

---

### Post by Quackers on 2010-11-24
We need the output of the boot script as willee-nillee suggests in post #4 please :-)

---

### Post by -nat- on 2010-11-24
> **wilee-nilee said:**
> Could be a number of reasons, post the running of the bootscript in my signature. Post it in code tags by clicking on the # in the reply panel. Paste all the text from the generated file between the code tags.

Quackers or I can help you better and others if we see what's up much better.;)

Here you go: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 
    330341876 of the same hard drive for the stage2 file. A stage2 file is at 
    this location on /dev/sda. Stage2 looks on partition #3 for 
    /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 397531580 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 445324415 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2             409,640   308,512,259   308,102,620  af HFS
/dev/sda3    *    308,512,260   432,453,734   123,941,475  83 Linux
/dev/sda4         432,453,735   577,327,904   144,874,170  83 Linux


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   308,512,259   308,102,620 HFS+
/dev/sda3     308,512,260   432,453,734   123,941,475 Linux or Data
/dev/sda4     432,453,735   577,327,904   144,874,170 Linux or Data
/dev/sda5     577,327,905   583,175,564     5,847,660 Linux Swap

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2012 MB, 2012217344 bytes
255 heads, 63 sectors/track, 244 cylinders, total 3930112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006834e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     3,919,859     3,919,797   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3F3C-1AF6                              vfat       EFI                           
/dev/sda2                                               hfsplus                                  
/dev/sda3        5df09047-425f-40e3-88a6-a9e4bfd5f7dc   ext3                                     
/dev/sda4        12a501fb-046f-4c57-8bb9-ea8d450e8d82   ext4                                     
/dev/sda5        290869d8-c447-4336-9e1c-152a5fe38b62   swap                                     
/dev/sdb1        4C4F-9AC8                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash vga=773

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

title		Chainload into GRUB 2
root		(hd0,2)
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 8.10, kernel 2.6.27-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc ro single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 8.10, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt3)'
search --no-floppy --fs-uuid --set 5df09047-425f-40e3-88a6-a9e4bfd5f7dc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt3)'
search --no-floppy --fs-uuid --set 5df09047-425f-40e3-88a6-a9e4bfd5f7dc
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.27-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 5df09047-425f-40e3-88a6-a9e4bfd5f7dc
	linux	/boot/vmlinuz-2.6.27-15-generic root=UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.27-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 5df09047-425f-40e3-88a6-a9e4bfd5f7dc
	echo	'Loading Linux 2.6.27-15-generic ...'
	linux	/boot/vmlinuz-2.6.27-15-generic root=UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.27-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 5df09047-425f-40e3-88a6-a9e4bfd5f7dc
	linux	/boot/vmlinuz-2.6.24-16-generic root=UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 5df09047-425f-40e3-88a6-a9e4bfd5f7dc
	echo	'Loading Linux 2.6.24-16-generic ...'
	linux	/boot/vmlinuz-2.6.24-16-generic root=UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
	insmod part_gpt
	insmod hfsplus
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 882cca128b467f03
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 882cca128b467f03 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
	insmod part_gpt
	insmod hfsplus
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 882cca128b467f03
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 882cca128b467f03 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda3/etc/fstab: ===============================

proc                                       /proc          proc         defaults                    0  0  
UUID=5df09047-425f-40e3-88a6-a9e4bfd5f7dc  /              ext3         relatime,errors=remount-ro  0  1  
UUID=7397d6be-11d0-434a-becf-2390dacc7e42  /              ext3         relatime,errors=remount-ro  0  1  
UUID=1059d667-c8f6-4540-92fa-319e51823ab8  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,exec,utf8              0  0  
#/dev/sdb /media/sdcard

=================== sda3: Location of files loaded by Grub: ===================


 203.5GB: boot/grub/core.img
 203.5GB: boot/grub/grub.cfg
 165.6GB: boot/grub/menu.lst
 169.1GB: boot/initrd.img-2.6.24-16-generic
 169.1GB: boot/initrd.img-2.6.24-16-generic.bak
 165.9GB: boot/initrd.img-2.6.27-15-generic
 169.1GB: boot/vmlinuz-2.6.24-16-generic
 169.1GB: boot/vmlinuz-2.6.27-15-generic
 165.9GB: initrd.img
 169.1GB: initrd.img.old
 169.1GB: vmlinuz
 169.1GB: vmlinuz.old
```

If I can't get this working today, I'm just going to wipe both Ubuntu partitions and re-install 10.10, as I need to get back to doing important things on it asap. :)

---

### Post by Quackers on 2010-11-24
I'm not so good with grub legacy, but it appears that grub2 is installed in several partitions.
My suggestion would be to boot from a live cd and see if you can access everything you need to backup and back it up, then re-install 10.10.

See if willee-nillee has a more amenable suggestion first though :-)

---

### Post by wilee-nilee on 2010-11-24
> **Quackers said:**
> I'm not so good with grub legacy, but it appears that grub2 is installed in several partitions.
My suggestion would be to boot from a live cd and see if you can access everything you need to backup and back it up, then re-install 10.10.

See if willee-nillee has a more amenable suggestion first though :-)

I agree with the wipe and reinstall, it is convoluted to say the least, might be fixable but a reinstall would be much faster. You have a BSD, and GPT indication in sda1, and missing files from what I assume is sda4=10.10, and the sda3 which has both grub-legacy and grub2.

Sometimes it is just easier to wipe it, and install.

Do you need any OS besides 10.10 at this time?

---

### Post by -nat- on 2010-11-24
I backed everything important up as soon as the problems started, just incase. I don't need 8.10 anymore, only Mac OSX and Ubuntu 10.10. Time to get installing then I guess.

Thanks for all your help!

---

### Post by ajgreeny on 2010-11-24
You should be able to restore grub2 using the following page from these forums, but making sure you choose /dev/sda4 as the mount choice in the second command and then /dev/sda as the grub destination in the third command.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Your problem is that you chose to install grub to partitions, not to the disk so it is not seeing grub2 when booted.

I note that the boot-info-script could not mount sda4 for some reason, so just wonder if there is a problem with that partition.  However, give those commands a try and see if it is possible.  If not come back again.

---

### Post by wilee-nilee on 2010-11-24
> **ajgreeny said:**
> You should be able to restore grub2 using the following page from these forums, but making sure you choose /dev/sda4 as the mount choice in the second command and then /dev/sda as the grub destination in the third command.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Your problem is that you chose to install grub to partitions, not to the disk so it is not seeing grub2 when booted.

I note that the boot-info-script could not mount sda4 for some reason, so just wonder if there is a problem with that partition.  However, give those commands a try and see if it is possible.  If not come back again.

They would need the full purge grub in drs305's tutorial to begin with don't you think? Isn't a fresh install since they are backed up more prudent here, needing only 10.10 with the Mac set up.

---

### Post by Quackers on 2010-11-24
Also, are you using a EFI boot partition, for Mac?

---

### Post by -nat- on 2010-11-24
> **ajgreeny said:**
> You should be able to restore grub2 using the following page from these forums, but making sure you choose /dev/sda4 as the mount choice in the second command and then /dev/sda as the grub destination in the third command.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Your problem is that you chose to install grub to partitions, not to the disk so it is not seeing grub2 when booted.

I note that the boot-info-script could not mount sda4 for some reason, so just wonder if there is a problem with that partition.  However, give those commands a try and see if it is possible.  If not come back again.

Too late! :P
Already 50% throught the Ubuntu installation process.
Although I had tried re-installing grub a couple of times with no luck. I just looked at the Boot Info Script output, and noticed "Grub 0.97 is installed in the MBR of /dev/sda" - I think that may have been my problem, Grub was on the MBR when it shouldn't have been. Oh well, I had been planning on doing a clean install in a month or so anyway.

[EDIT] All seems to have gone well, the install completed fine and 10.10 is bootable :)

---

### Post by Quackers on 2010-11-24
Just out of interest did you use iatkos for mac?

---

### Post by -nat- on 2010-11-24
> **Quackers said:**
> Just out of interest did you use iatkos for mac?

Not entirely sure what that is, but looks to be hackintosh related? I'm on a MacBook, so have OSX installed by default.

---

### Post by Quackers on 2010-11-24
Hence the GUID partition table.

---

