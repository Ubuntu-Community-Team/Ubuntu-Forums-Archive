---
title: "Problems with grub2: no way to update the boot menu"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by Rehdon on 2010-06-25
Hi all,
I upgraded my main box to Ubuntu 10.04 and everything runs fine, except for a problem with grub: I can't modify the boot menu in any way, I'm stuck with what grub2 thought was the optimal setup at installation time (and it got it wrong, btw). The current boot menu lists:

- my older 9.10 install in sdb2 (one kernel)
- legacy windows XP install on sda1
- my even older 9.04 install in sdb1 (two kernel versions)
- my new install in sdb3, with only one kernel (the one coming with the distro CD)

I tried anything I could think of to modify this menu:

- modify the /etc grub config file then running sudo update-grub
- using a specific app (system manager? don't remember its name)
- upgrading to the latest kernel
- removing and reinstalling grub

to no avail: the menu is still there in the above form, and I have to manually select the 10.04 (old) kernel by hand every time I reboot.

Any idea about what I should do? Thx in advance.

Rehdon

---

### Post by kalistona on 2010-06-25
i do not understand : sdb means usbkey or another disk
legacy means linux before grub 2 in XP ?
so i do not understand if it is a problem or if you want re-install properly all that; from a command line ?

---

### Post by Rehdon on 2010-06-25
Nope, sdb is short for /dev/sdb, i.e. my second hard disk drive. "Legacy" means that Windows is just sitting there unused because I only use Ubuntu Linux now. I properly reinstalled grub following an Ubuntu howto using the command line.

Rehdon

---

### Post by mikewhatever on 2010-06-25
Why do you want to modify the menu in the first place? Don't you want to boot all those OSs you have installed? In case not, why have them installed? Why do you have to chose the old kernel for 10.04? What's wrong with the new one?

---

### Post by Rehdon on 2010-06-25
> **mikewhatever said:**
> Why do you want to modify the menu in the first place? Don't you want to boot all those OSs you have installed? In case not, why have them installed? Why do you have to chose the old kernel for 10.04? What's wrong with the new one?

In short:

- I want the most recent 10.04 kernel to be booted as default;
- as the automatic kernel upgrade doesn't work, at least I'd like to be able to manually config the boot order and add the last kernel(s): atm the upgraded kernels aren't accessible;
- of course I want to be able to boot all the other OSs on my drives, but only if necessary: it doesn't make sense that 9.10 be the default boot option, as grub seems to have decided for me.

Hope it's clearer now :)

Rehdon

---

### Post by wilee-nilee on 2010-06-25
Post the boot script in my sig in code tags we may see some anomalies there.

---

### Post by Rehdon on 2010-06-25
There you go: 

```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

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
    Operating System:  
    Boot files/dirs:   

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
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 400.1 GB, 400088457216 byte
255 testine, 63 settori/tracce, 48641 cilindri, totale 781422768 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,964,824    20,964,762   7 HPFS/NTFS
/dev/sda2          20,964,825   100,968,524    80,003,700   7 HPFS/NTFS
/dev/sda3         100,968,586   781,417,664   680,449,079   5 Extended
/dev/sda5         100,968,588   102,960,584     1,991,997  82 Linux swap / Solaris
/dev/sda6         102,960,648   161,549,639    58,588,992  83 Linux
/dev/sda7         161,549,703   781,417,664   619,867,962  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 250.1 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri, totale 488397168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    16,000,739    16,000,677  83 Linux
/dev/sdb2          16,000,740    32,001,479    16,000,740  83 Linux
/dev/sdb3          32,001,480    48,002,219    16,000,740  83 Linux
/dev/sdb4          48,002,220   488,392,064   440,389,845   5 Extended
/dev/sdb5          48,002,283    96,823,754    48,821,472  83 Linux
/dev/sdb6          96,823,818   488,392,064   391,568,247  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DE103A62103A4237                       ntfs                                     
/dev/sda2        CC70960F7095FFFE                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        8399da30-10b6-4731-beb0-9291bfbc9019   swap                                     
/dev/sda6        8a5cd3ba-8a56-4308-bd71-27bbb47e3e18   ext3       backup                        
/dev/sda7        bb224ba1-eeb9-4be1-9e2a-a116ca1a11bd   ext3       multimedia                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4debf91d-418d-40a1-9a0d-38c5f27e1fac   ext3                                     
/dev/sdb2        46d0bda3-c9b4-4c86-8035-cfe80fcf4447   ext3                                     
/dev/sdb3        3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68   ext3                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        3ac97593-dbca-4240-a8c4-f48668281f47   ext3                                     
/dev/sdb6        8ca353e8-44aa-4057-8f70-98a0237888fe   ext3       store                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext3       (rw,errors=remount-ro)
/dev/sda6        /media/backup            ext3       (rw)
/dev/sdb5        /home                    ext3       (rw)
/dev/sda7        /media/multimedia        ext3       (rw)
/dev/sda2        /media/win-store         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /media/store             ext3       (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=4debf91d-418d-40a1-9a0d-38c5f27e1fac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4debf91d-418d-40a1-9a0d-38c5f27e1fac

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
# howmany=4

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		4debf91d-418d-40a1-9a0d-38c5f27e1fac
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=4debf91d-418d-40a1-9a0d-38c5f27e1fac ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		4debf91d-418d-40a1-9a0d-38c5f27e1fac
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=4debf91d-418d-40a1-9a0d-38c5f27e1fac ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, memtest86+
uuid		4debf91d-418d-40a1-9a0d-38c5f27e1fac
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4f8838e6-c0d9-4161-b8a9-21fca9483e98 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4f8838e6-c0d9-4161-b8a9-21fca9483e98 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=4f8838e6-c0d9-4161-b8a9-21fca9483e98 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-20-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=4f8838e6-c0d9-4161-b8a9-21fca9483e98 ro single 
initrd		/boot/initrd.img-2.6.24-20-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 8.10, kernel 2.6.27-12-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=48d9e95c-60c1-4dae-a20c-b0b25f6f025c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=48d9e95c-60c1-4dae-a20c-b0b25f6f025c ro single 
initrd		/boot/initrd.img-2.6.27-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=48d9e95c-60c1-4dae-a20c-b0b25f6f025c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=48d9e95c-60c1-4dae-a20c-b0b25f6f025c ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=48d9e95c-60c1-4dae-a20c-b0b25f6f025c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=48d9e95c-60c1-4dae-a20c-b0b25f6f025c ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=48d9e95c-60c1-4dae-a20c-b0b25f6f025c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=48d9e95c-60c1-4dae-a20c-b0b25f6f025c ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb3)
root		(hd1,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb1 :
UUID=4debf91d-418d-40a1-9a0d-38c5f27e1fac	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb5 :
UUID=3ac97593-dbca-4240-a8c4-f48668281f47	/home	ext3	relatime	0	2
#Entry for /dev/sda6 :
UUID=8a5cd3ba-8a56-4308-bd71-27bbb47e3e18	/media/backup	ext3	relatime	0	2
#Entry for /dev/sda7 :
UUID=bb224ba1-eeb9-4be1-9e2a-a116ca1a11bd	/media/multimedia	ext3	relatime	0	2
#Entry for /dev/sdb6 :
UUID=8ca353e8-44aa-4057-8f70-98a0237888fe	/media/store	ext3	relatime	0	2
#Entry for /dev/sda5 :
UUID=8399da30-10b6-4731-beb0-9291bfbc9019	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



=================== sdb1: Location of files loaded by Grub: ===================


   4.7GB: boot/grub/menu.lst
   4.7GB: boot/grub/stage2
   5.2GB: boot/initrd.img-2.6.28-16-generic
   1.7GB: boot/vmlinuz-2.6.28-16-generic
   5.2GB: initrd.img
   1.7GB: vmlinuz

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set 46d0bda3-c9b4-4c86-8035-cfe80fcf4447
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
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 46d0bda3-c9b4-4c86-8035-cfe80fcf4447
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=46d0bda3-c9b4-4c86-8035-cfe80fcf4447 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 46d0bda3-c9b4-4c86-8035-cfe80fcf4447
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=46d0bda3-c9b4-4c86-8035-cfe80fcf4447 ro single 
	initrd	/boot/initrd.img-2.6.31-21-generic
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set de103a62103a4237
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 4debf91d-418d-40a1-9a0d-38c5f27e1fac
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=4debf91d-418d-40a1-9a0d-38c5f27e1fac ro quiet splash vga=773
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 4debf91d-418d-40a1-9a0d-38c5f27e1fac
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=4debf91d-418d-40a1-9a0d-38c5f27e1fac ro single
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 4debf91d-418d-40a1-9a0d-38c5f27e1fac
	linux /boot/memtest86+.bin 
}
menuentry "'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, con Linux 2.6.32-21-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=46d0bda3-c9b4-4c86-8035-cfe80fcf4447 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=3ac97593-dbca-4240-a8c4-f48668281f47 /home           ext3    defaults        0       2
# /media/backup was on /dev/sda6 during installation
UUID=8a5cd3ba-8a56-4308-bd71-27bbb47e3e18 /media/backup   ext3    defaults        0       2
# /media/multimedia was on /dev/sda7 during installation
UUID=bb224ba1-eeb9-4be1-9e2a-a116ca1a11bd /media/multimedia ext3    defaults        0       2
# /media/store was on /dev/sdb6 during installation
UUID=8ca353e8-44aa-4057-8f70-98a0237888fe /media/store    ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8399da30-10b6-4731-beb0-9291bfbc9019 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


=================== sdb2: Location of files loaded by Grub: ===================


   9.4GB: boot/grub/core.img
   9.5GB: boot/grub/grub.cfg
   9.6GB: boot/initrd.img-2.6.31-21-generic
   8.9GB: boot/vmlinuz-2.6.31-21-generic
   9.6GB: initrd.img
   8.9GB: vmlinuz

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
set locale_dir=($root)/boot/grub/locale
set lang=it
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
menuentry 'Ubuntu, con Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
	echo	'Caricamento Linux 2.6.32-22-generic...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68 ro single 
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
	echo	'Caricamento Linux 2.6.32-21-generic...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68 ro single 
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set de103a62103a4237
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 4debf91d-418d-40a1-9a0d-38c5f27e1fac
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=4debf91d-418d-40a1-9a0d-38c5f27e1fac ro quiet splash vga=773
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 4debf91d-418d-40a1-9a0d-38c5f27e1fac
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=4debf91d-418d-40a1-9a0d-38c5f27e1fac ro single
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 4debf91d-418d-40a1-9a0d-38c5f27e1fac
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 46d0bda3-c9b4-4c86-8035-cfe80fcf4447
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=46d0bda3-c9b4-4c86-8035-cfe80fcf4447 ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 46d0bda3-c9b4-4c86-8035-cfe80fcf4447
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=46d0bda3-c9b4-4c86-8035-cfe80fcf4447 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=3dbd6e07-4c43-4b4f-9dfa-50d123b2ed68 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=3ac97593-dbca-4240-a8c4-f48668281f47 /home           ext3    defaults        0       2
# /media/backup was on /dev/sda6 during installation
UUID=8a5cd3ba-8a56-4308-bd71-27bbb47e3e18 /media/backup   ext3    defaults        0       2
# /media/multimedia was on /dev/sda7 during installation
UUID=bb224ba1-eeb9-4be1-9e2a-a116ca1a11bd /media/multimedia ext3    defaults        0       2
# /media/store was on /dev/sdb6 during installation
UUID=8ca353e8-44aa-4057-8f70-98a0237888fe /media/store    ext3    defaults        0       2
# /media/win-store was on /dev/sda2 during installation
UUID=CC70960F7095FFFE /media/win-store ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /windows was on /dev/sda1 during installation
UUID=DE103A62103A4237 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=8399da30-10b6-4731-beb0-9291bfbc9019 none            swap    sw              0       0


=================== sdb3: Location of files loaded by Grub: ===================


  18.0GB: boot/grub/core.img
  18.1GB: boot/grub/grub.cfg
  17.2GB: boot/initrd.img-2.6.32-21-generic
  18.1GB: boot/initrd.img-2.6.32-22-generic
  18.0GB: boot/vmlinuz-2.6.32-21-generic
  18.1GB: boot/vmlinuz-2.6.32-22-generic
  18.1GB: initrd.img
  17.2GB: initrd.img.old
  18.1GB: vmlinuz
  18.0GB: vmlinuz.old

```

---

### Post by darkod on 2010-06-25
It seems you are booting the 9.10 grub2, which of course considers the 9.10 as main OS and has it at the top of the list.
Boot your 10.04 and just do:

sudo grub-install /dev/sdb

As far as the order of the other OSs, if you really want to change the order, just open in 10.04 the /boot/grub/grub.cfg and copy the entries in the order you want them into /etc/grub.d/40_custom

After that is done disable os-prober with:

sudo chmod -x /etc/grub.d/30_os-prober

Update the grub.cfg with

sudo update-grub

That should sort it out. But with os-prober disabled it will not auto detect new OSs (how often you add a new one), and I'm not sure about new kernels when they are added.

---

### Post by wilee-nilee on 2010-06-25
B

---

### Post by Rehdon on 2010-06-25
> **darkod said:**
> That should sort it out. But with os-prober disabled it will not auto detect new OSs (how often you add a new one), and I'm not sure about new kernels when they are added.

Thanks a lot. I noticed how grub is installed in sdb as well only now, could that be the real problem here? some sort of conflict between different grub installs? if yes, how do you remove grub from a boot sector?

Ty again for your advice, will follow it and see what happens.

Rehdon

---

### Post by darkod on 2010-06-25
> **Rehdon said:**
> Thanks a lot. I noticed how grub is installed in sdb as well only now, could that be the real problem here? some sort of conflict between different grub installs? if yes, how do you remove grub from a boot sector?

Ty again for your advice, will follow it and see what happens.

Rehdon

I'm not sure I follow. If you mean about grub2 on the MBR of sdb, it should be there because your ubuntus are on sdb too. Grub2 boots fastest when it's on the same disk as ubuntu.
But the issue seems to be that the grub2 on sdb is from 9.10, not 10.04. So the general layout which is:
ubuntu
other OSs (including other linux and ubuntu)

becomes:
9.10
other OSs

When you install grub2 from 10.04 to sdb it will be:
10.04
other OSs

---

### Post by mikewhatever on 2010-06-25
Rehdon, you can set the default booting entry by editing the /etc/default/grub. The line which is of interest is this one: 'GRUB_DEFAULT=0'. You'll need to change it to GRUB_DEFAULT="menu entry", where ''menu entry' is the exact menu entry for 10.04 from /boot/grub/grub.cfg. For example, in my case, the menu entry would be "Ubuntu, Linux 2.6.31-22-generic" (see the full text below).
```
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)

```

As for the newer kernels not showing, can you post the full output of **sudo update-grub**.

---

### Post by Rehdon on 2010-06-25
> **darkod said:**
> I'm not sure I follow. If you mean about grub2 on the MBR of sdb, it should be there because your ubuntus are on sdb too. Grub2 boots fastest when it's on the same disk as ubuntu.

I assumed that grub(2) would install on the MBR of the first hard drive, which is why I never thought of doing a sudo grub-install /dev/sdb.

@mikewhatever: here it is:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 9.04 (9.04) on /dev/sdb1
Found Ubuntu 9.10 (9.10) on /dev/sdb2
done
```

Rehdon

---

### Post by darkod on 2010-06-25
Are you happy with the menu now? :)

---

### Post by Rehdon on 2010-06-26
> **darkod said:**
> Are you happy with the menu now? :)

I followed your instructions, and that did it! thanks a lot :D

Actually installing grub on sdb was enough to fix the boot menu.

Rehdon

---

