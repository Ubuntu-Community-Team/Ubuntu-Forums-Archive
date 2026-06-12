---
title: "Triboot question win7,unbuntu, bt4"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by bpalyshka on 2010-02-09
I recently installed the new version of backtrack to my HDD to my laptop.  I used wubi (bad idea i know) to install the os.

I currently run windows 7 and ubuntu fine dual booted through grub. But when i installed BT4 I've been getting problems.  I cannot boot into ubuntu now.  Here is what i have managed to figure out so far.

grub looks like this

Menu.lst



title           Back Track 4
uuid            1c7d5f03-3418-4437-aad4-ce60f0d6bf7e
kernel          /boot/vmlinuz-2.6.30.9 root=UUID=1c7d5f03-3418-4437-aad4-ce60f0$
initrd          /boot/initrd.img-2.6.30.9
quiet

title           Back Track 4(recovery mode)
uuid            1c7d5f03-3418-4437-aad4-ce60f0d6bf7e
kernel          /boot/vmlinuz-2.6.30.9 root=UUID=1c7d5f03-3418-4437-aad4-ce60f0$
initrd          /boot/initrd.img-2.6.30.9

title           Memtest86+
uuid            1c7d5f03-3418-4437-aad4-ce60f0d6bf7e
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.


title           Ubuntu, Linux 2.6.31-17-generic (on /dev/sda5)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=50a5ecab-a2f5-47e7-9a$
initrd          /boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.

title           Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=50a5ecab-a2f5-47e7-9a$
initrd          /boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title           Ubuntu, Linux 2.6.31-14-generic (on /dev/sda5)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=50a5ecab-a2f5-47e7-9a$
initrd          /boot/initrd.img-2.6.31-14-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.


title           Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda5)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=50a5ecab-a2f5-47e7-9a$
initrd          /boot/initrd.img-2.6.31-14-generic
savedefault
boot
===========================================================

I had to change the (hd0,4) to 5 to point it at the partition, upon doing so i get a boot error idk id have to reboot to look grub spit out a error of 17 i think idk again id have to try again.

So here is my question: When i had my laptop dual booted it had grub rockin and rollin. when i use wubi during the backtrack install did it over write grub? do i have 2 versions?  When using 2 linux distros can they share a swap or do i need 2?  Can someone point me in the write direction.

Only reason i installed 2 versions of linux is to toy around without installing all the apps to my ubuntu os. independent of each other. "why didn't you use virtual box or vm ware?"  I like grub and independent work stations plus i dig the persistance mode and a clean install my dvdrom is not working well.

thanks and if you need more info let me know ill post it. thanks

B3nJi

---

### Post by dstew on 2010-02-09
Do your UUID's really have a '$' at the end?

---

### Post by oldfred on 2010-02-09
Old grub counts partitions starting at 0 where grub2 starts at 1.
         _____OLD      GRUB2
sda1  (hd0,0)  (hd0,1)
sda2  (hd0,1)  (hd0,2)

to see your entire boot configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by bpalyshka on 2010-02-09
> **oldfred said:**
> Old grub counts partitions starting at 0 where grub2 starts at 1.
         _____OLD      GRUB2
sda1  (hd0,0)  (hd0,1)
sda2  (hd0,1)  (hd0,2)

to see your entire boot configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

ran the .sh script tho i really didnt have a chance to look at the results yet since i have to go into work tonight.

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa47e93ac

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   221,241,880   221,035,033   7 HPFS/NTFS
/dev/sda3         221,247,180   390,716,864   169,469,685   5 Extended
/dev/sda5         304,206,903   387,086,174    82,879,272  83 Linux
/dev/sda6         387,086,238   390,716,864     3,630,627  82 Linux swap / Solaris
/dev/sda7         221,247,306   300,704,669    79,457,364  83 Linux
/dev/sda8         300,704,733   304,206,839     3,502,107  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3E420D23420CE20F                       ntfs       System Reserved               
/dev/sda2        5A2E12C02E12955B                       ntfs                                     
/dev/sda5        50a5ecab-a2f5-47e7-9a79-fd5c148da3a2   ext4                                     
/dev/sda6        7da03c9d-e19c-4ac5-9a4f-3398ce3a3e49   swap                                     
/dev/sda7        1c7d5f03-3418-4437-aad4-ce60f0d6bf7e   ext3                                     
/dev/sda8                                               swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)


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
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 50a5ecab-a2f5-47e7-9a79-fd5c148da3a2
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 50a5ecab-a2f5-47e7-9a79-fd5c148da3a2
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=50a5ecab-a2f5-47e7-9a79-fd5c148da3a2 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 50a5ecab-a2f5-47e7-9a79-fd5c148da3a2
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=50a5ecab-a2f5-47e7-9a79-fd5c148da3a2 ro single  splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 50a5ecab-a2f5-47e7-9a79-fd5c148da3a2
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=50a5ecab-a2f5-47e7-9a79-fd5c148da3a2 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 50a5ecab-a2f5-47e7-9a79-fd5c148da3a2
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=50a5ecab-a2f5-47e7-9a79-fd5c148da3a2 ro single  splash
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 3e420d23420ce20f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=50a5ecab-a2f5-47e7-9a79-fd5c148da3a2 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=7da03c9d-e19c-4ac5-9a4f-3398ce3a3e49 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/System\040Reserved ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 159.6GB: boot/grub/core.img
 157.0GB: boot/grub/grub.cfg
 156.3GB: boot/initrd.img-2.6.31-14-generic
 156.7GB: boot/initrd.img-2.6.31-17-generic
 156.3GB: boot/vmlinuz-2.6.31-14-generic
 156.4GB: boot/vmlinuz-2.6.31-17-generic
 156.7GB: initrd.img
 156.3GB: initrd.img.old
 156.4GB: vmlinuz
 156.3GB: vmlinuz.old

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
#      password --md5 lets not post hash =)
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
# kopt=root=UUID=1c7d5f03-3418-4437-aad4-ce60f0d6bf7e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1c7d5f03-3418-4437-aad4-ce60f0d6bf7e

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
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

splashimage=1c7d5f03-3418-4437-aad4-ce60f0d6bf7e/boot/grub/splash.xpm.gz

title		Back Track 4
uuid		1c7d5f03-3418-4437-aad4-ce60f0d6bf7e
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=1c7d5f03-3418-4437-aad4-ce60f0d6bf7e ro quiet splash 
initrd		/boot/initrd.img-2.6.30.9
quiet

title		Back Track 4(recovery mode)
uuid		1c7d5f03-3418-4437-aad4-ce60f0d6bf7e
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=1c7d5f03-3418-4437-aad4-ce60f0d6bf7e ro  single
initrd		/boot/initrd.img-2.6.30.9

title		Memtest86+
uuid		1c7d5f03-3418-4437-aad4-ce60f0d6bf7e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, Linux 2.6.31-17-generic (on /dev/sda5)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=50a5ecab-a2f5-47e7-9a79-fd5c148da3a2 ro splash quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=50a5ecab-a2f5-47e7-9a79-fd5c148da3a2 ro single splash 
initrd		/boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, Linux 2.6.31-14-generic (on /dev/sda5)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=50a5ecab-a2f5-47e7-9a79-fd5c148da3a2 ro splash quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda5)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=50a5ecab-a2f5-47e7-9a79-fd5c148da3a2 ro single splash 
initrd		/boot/initrd.img-2.6.31-14-generic
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=1c7d5f03-3418-4437-aad4-ce60f0d6bf7e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=00c36d5a-43af-4c6f-8ec8-caf873eb5565 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

hda 

```

---

### Post by bpalyshka on 2010-02-10
> **dstew said:**
> Do your UUID's really have a '$' at the end?

no

---

### Post by oldfred on 2010-02-10
I do not know why you were not able to boot with old grub when you had (hd0,4)? The change to 0,5 is wrong as that is only for grub2. It may just be easiest to reinstall grub2 and boot thru ubuntu. It should find the bt install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once booted into ubuntu
sudo update-grub

should find the BT install.

---

### Post by bpalyshka on 2010-02-12
> **oldfred said:**
> I do not know why you were not able to boot with old grub when you had (hd0,4)? The change to 0,5 is wrong as that is only for grub2. It may just be easiest to reinstall grub2 and boot thru ubuntu. It should find the bt install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once booted into ubuntu
sudo update-grub

should find the BT install.


super thank you for helping me reconfigure my grub. i followed the directions booted from cd and reinstalled grub booted back into ubuntu (yes!) and ran the update for grub command and volia super easy to do thanks for the help really appreciate it.  I edited my menu.lst file for ascetic value. flawless thanks again

---

