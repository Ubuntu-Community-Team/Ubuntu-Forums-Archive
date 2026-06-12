---
title: "GRUB is borked after last update (7 Sept, 2010)"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by Robynsveil on 2010-09-07
Whilst I've been using Ubuntu for years now, I don't really do much at the command-line, basically because I don't *have* to (which, to me is the beauty of this OS!). However, the last update via update manager has rendered my dual-boot with Vista on an Asus laptop non-functioning (at least Linux).
What happens is this: after the BIOS splash screen, it says starting GRUB and then, instead of a menu of current and recent Linux versions and the Vista option at the bottom (white text against colour background) it now just shows one line of the menu in magenta... the rest of the menu is black, but the arrow keys will show the other options. Hitting ENTER does nothing: the text line is replaced with a blinking underline which goes back to the text in magenta again when i hit ESC.
I can't seem to ESC or SHIFT to GRUB's command-line prompt at all.

I've boot to the LiveCD and ran a boot_info_script in bash: here is what that revealed:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

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
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812  17 Hidden HPFS/NTFS
/dev/sda2    *     20,484,096   333,053,951   312,569,856   7 HPFS/NTFS
/dev/sda3         333,059,580   625,137,344   292,077,765   5 Extended
/dev/sda5         333,059,643   344,770,964    11,711,322  82 Linux swap / Solaris
/dev/sda6         344,771,028   625,137,344   280,366,317  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ae4049e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        193D96895E8865AE                       ntfs                                     
/dev/sda2        AE6CA6DC6CA69F19                       ntfs       VistaOS                       
/dev/sda5        0909184d-1894-4c5b-87f9-649c778c34cd   swap                                     
/dev/sda6        668b736c-f109-46d4-8848-cd12ada02acf   ext3                                     
/dev/sdb1        CD3F-62CA                              vfat       STORE N GO                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/STORE N GO        vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


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
timeout		25

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
# kopt=root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=668b736c-f109-46d4-8848-cd12ada02acf

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

title		Chainload into GRUB 2
root		668b736c-f109-46d4-8848-cd12ada02acf
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Debian GNU/Linux, kernel 2.6.28-16-generic
root		668b736c-f109-46d4-8848-cd12ada02acf
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro quiet splash
initrd		/boot/initrd.img-2.6.28-16-generic

title		Debian GNU/Linux, kernel 2.6.28-16-generic (recovery mode)
root		668b736c-f109-46d4-8848-cd12ada02acf
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Debian GNU/Linux, kernel 2.6.28-15-generic
root		668b736c-f109-46d4-8848-cd12ada02acf
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro quiet splash
initrd		/boot/initrd.img-2.6.28-15-generic

title		Debian GNU/Linux, kernel 2.6.28-15-generic (recovery mode)
root		668b736c-f109-46d4-8848-cd12ada02acf
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
root		668b736c-f109-46d4-8848-cd12ada02acf
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root		668b736c-f109-46d4-8848-cd12ada02acf
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
root		668b736c-f109-46d4-8848-cd12ada02acf
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=30
set root=(hd0,6)
search --fs-uuid --set 668b736c-f109-46d4-8848-cd12ada02acf
if font /usr/share/grub/ascii.pff ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set root=(hd0,6)
search --fs-uuid --set 668b736c-f109-46d4-8848-cd12ada02acf
insmod tga
if background_image /usr/share/images/grub/Charlotte118.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,6)
search --fs-uuid --set 668b736c-f109-46d4-8848-cd12ada02acf
menuentry "Ubuntu, linux 2.6.28-19-generic" {
	linux	/boot/vmlinuz-2.6.28-19-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro vga=792 splash #GRUB_DISABLE_LINUX_UUID=true quiet splash
	initrd	/boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu, linux 2.6.28-19-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-19-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro single vga=792 splash #GRUB_DISABLE_LINUX_UUID=true
	initrd	/boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu, linux 2.6.28-18-generic" {
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro vga=792 splash #GRUB_DISABLE_LINUX_UUID=true quiet splash
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-18-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro single vga=792 splash #GRUB_DISABLE_LINUX_UUID=true
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-17-generic" {
	linux	/boot/vmlinuz-2.6.28-17-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro vga=792 splash #GRUB_DISABLE_LINUX_UUID=true quiet splash
	initrd	/boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, linux 2.6.28-17-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-17-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro single vga=792 splash #GRUB_DISABLE_LINUX_UUID=true
	initrd	/boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, linux 2.6.28-16-generic" {
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro vga=792 splash #GRUB_DISABLE_LINUX_UUID=true quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-16-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro single vga=792 splash #GRUB_DISABLE_LINUX_UUID=true
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic" {
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro vga=792 splash #GRUB_DISABLE_LINUX_UUID=true quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro single vga=792 splash #GRUB_DISABLE_LINUX_UUID=true
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic" {
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro vga=792 splash #GRUB_DISABLE_LINUX_UUID=true quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=668b736c-f109-46d4-8848-cd12ada02acf ro single vga=792 splash #GRUB_DISABLE_LINUX_UUID=true
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	set root=(hd0,1)
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	set root=(hd0,2)
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=668b736c-f109-46d4-8848-cd12ada02acf / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=0909184d-1894-4c5b-87f9-649c778c34cd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# for /dev/sda2
UUID=AE6CA6DC6CA69F19 /media/VistaOS ntfs-3g defaults,locale=en_AU.UTF-8 0 0

=================== sda6: Location of files loaded by Grub: ===================


 233.6GB: boot/grub/core.img
 234.1GB: boot/grub/grub.cfg
 233.6GB: boot/grub/menu.lst
 233.5GB: boot/initrd.img-2.6.28-11-generic
 233.6GB: boot/initrd.img-2.6.28-15-generic
 233.6GB: boot/initrd.img-2.6.28-16-generic
 233.6GB: boot/initrd.img-2.6.28-17-generic
 233.6GB: boot/initrd.img-2.6.28-18-generic
 234.1GB: boot/initrd.img-2.6.28-19-generic
 233.6GB: boot/vmlinuz-2.6.28-11-generic
 233.5GB: boot/vmlinuz-2.6.28-15-generic
 233.6GB: boot/vmlinuz-2.6.28-16-generic
 233.6GB: boot/vmlinuz-2.6.28-17-generic
 233.5GB: boot/vmlinuz-2.6.28-18-generic
 234.1GB: boot/vmlinuz-2.6.28-19-generic
 234.1GB: initrd.img
 233.6GB: initrd.img.old
 234.1GB: vmlinuz
 233.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3



=============================== StdErr Messages: ===============================

hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory

```

So, something is stuffed somewhere. No idea where to go from here. Might anyone have any clues what I've done wrong?

---

### Post by Robynsveil on 2010-09-08
Whilst waiting for someone to offer ideas, I've been doing a bit of fumbling around with Rescatux Rescapp: you know, that Debian-LIVE based GRUB fix thing. It actually managed to write a new GRUB for me, so now when I boot, voila: a menu list that looks like it *should* work.
However, selecting *anything from this GRUB menu gives me the error:

```
Error 11: Unrecognized device string
Press any key to continue...
```

So, I went back with my Super GRUB Disk and took GRUB off the MBR so that I could at least boot to Vista.
There wouldn't be some simple solution - or one that everyone but *me* is familiar with - to getting the device strings to be recognised? Or do I need to re-install 9.04? From what I've read, I'm not too keen to update to 10.04 at this point: seems like it has dramas 9.04 didn't.

---

### Post by ronparent on 2010-09-08
Reinstalling grub from a live cd is pretty straightforward. See this reference: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by Robynsveil on 2010-09-08
Thanks for your reply, Ron. ):P

I'm still using legacy GRUB, based on that boot_info_script RESULTS.TXT file. 1.9.8, I believe. 

I *was* able to get the menu back to looking as it should, but the menu doesn't do anything but produce those errors. Do I just try to re-install GRUB again, or is there somewhere else I should be looking?

Thanks to all who respond... this is completely baffling, not to mention a bit frustrating, too.

EDIT: Ooops, I was wrong... based on your article, I must be running GRUB2... I'll have a go at re-installing GRUB2 and get back to you.

---

### Post by wilee-nilee on 2010-09-08
I saw somebody post this so I think it's what your looking for with grub-legacy.
[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

---

### Post by andrewthomas on 2010-09-08
```
title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ root          
title        When you have verified GRUB 2 works, you can use this command to root  
title        complete the upgrade:  upgrade-from-grub-legacy root  
title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ root
```

you seem to be partially but not fully updated from grub to grub2
[https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

---

### Post by Robynsveil on 2010-09-08
I think I am *seriously* messing things up.

I've gone ahead and create a CD with Ubunto 9.10 on it, and using that followed the instructions to restore GRUB2. I followed the 1st lot of steps ([the easiest ones]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")) and it seemed to work, but when I rebooted, it dropped me at the GRUB command prompt.
```
GNU GRUB version 1.97~beta4
```

I tried a **cat /boot/grub/grub.cfg** but got a file not found error.
This is puzzling beyond words...

---

### Post by colorpurple21859 on 2010-09-08
try this
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

---

### Post by ronparent on 2010-09-08
Robynsveil - If by chance you used the command of the form: sudo grub-install --root-directory=/mnt/ /dev/sdX

If the / following the mount wasn't included, you might get the results you did!

---

### Post by Robynsveil on 2010-09-09
This is goiing from bad to worse.

I've gone ahead and did as suggested: did the [GRUB Rescue]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode") thing as per that link, and actually got IN.
Once.
Whereupon I immediately updated GRUB 2 as suggested with the update-from-grub-legacy command and now I'm getting the **Error 15: File not found** again at boot when selecting a menu item.  I feel I'm *so* close... :confused: ](*,)

BTW, the menu I *still* see says ```
Chainload into GRUB 2
``` up the top, so obviously it didn't really complete the process??

---

### Post by Robynsveil on 2010-09-09
Right, a bit of followup. I'm not going to mark this solved because I never did get a solution that worked properly to the whole GRUB issue. My take is that I'd sort-of set this to fail at some point because I didn't follow through with upgrading from GRUB legacy as I was meant to... I didn't realise at the time that it had not been completed.

What I *did* end up doing was: upgrading to Ubuntu 10.04. The upgrade went seamlessly, preserving all my settings and data and fixing some other, nagging problems I had with Jackalope, which didn't shut down my Asus laptop properly. Lynx does.

So I'm a happy camper, Ubuntu-ing merrily away again, confidence restored. :)

---

