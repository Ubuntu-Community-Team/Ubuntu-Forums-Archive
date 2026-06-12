---
title: "Grub 2 help"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by Micano on 2010-06-16
Hello!

I wrote here a few months back, because of a problem I had with grub ([http://ubuntuforums.org/showthread.php?t=1423998](http://ubuntuforums.org/showthread.php?t=1423998)). I  don't know how, but grub had been installed in every partition. Anyways,  I got fast help, and the problem got solved. But when updating ubuntu, I  ran into a little problem.

And the other thing is that I want a theme/background on my grub menu,  and when I check on forums and such, I hear about the file named  05_debian_theme. However I don't even have that file. Also, I want to remove some stuff on my boot menu. 

I have 
Linux 32 generic pae
Linux 32 generic pae safe mod
Linux 32 generic
Linux 32 generic safe mode
Memtest
Another memtest
Windows vista (don't even have that)
Windows 7

And why doesn't 05_debian_theme exist? The files I have in my grub.d folder are:

00_header
10_linux
11_windows.save
11_Windows.save
11_Windows.save.1
20_memtest 86+
30_os-prober
40_custom
README

```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-23-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-22-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-15-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-15-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Please help. Thanks!

---

### Post by Micano on 2010-06-18
bump

---

### Post by darkod on 2010-06-18
Why do you have menu.lst reported and grub2 when running update-grub?

That sounds like you started a procedure to upgrade from grub1 to grub2 but didn't finish it. Maybe that's why 05_debian doesn't exist yet.

In your first grub menu, do you have entry called like Chainloading to Grub2?

---

### Post by Micano on 2010-06-18
> **darkod said:**
> Why do you have menu.lst reported and grub2 when running update-grub?

That sounds like you started a procedure to upgrade from grub1 to grub2 but didn't finish it. Maybe that's why 05_debian doesn't exist yet.


Yeah if you check my first post that I linked, some crazy stuff happend when I updated from 9.10 to 10.04. 

>  In your first grub menu, do you have entry called like Chainloading to Grub2?

You mean when I boot up? If so, I don't have that option.

---

### Post by darkod on 2010-06-18
Boot ubuntu and check the version of grub installed with:

sudo grub-install -v

---

### Post by Micano on 2010-06-18
grub-install (GNU GRUB 0.97)

---

### Post by darkod on 2010-06-18
That's grub1. You have a mix of grub1 and grub2. Did you have a clean install of 9.10 before upgrading to 10.04, or that was also upgrade from 9.04?

If you did upgrade 9.04 -> 9.10, did you also upgrade grub1 -> grub2 or you are dragging grub1 with you all this time?

---

### Post by Micano on 2010-06-18
I had a clean install of 9.10. Then I upgraded to 10.04 in march, so it was a beta.

For some reason, grub 2 was installed in sda1 and sda2. And Grub1 was installed in my linux partition. I got help from meifra to be able to boot windows 7 again, but that would mean that I boot with grub1, however grub2 is installed somewhere, but not being used?

---

### Post by darkod on 2010-06-18
I have no idea how grub1 ended up on your linux partition. Yes, you made win7 bootable again but never removed grub1. No one even picked it up and commented on it, it seems.

I'm not sure if we can remove it now, without messing up the boot process. That is my worry. We could try though.

---

### Post by Micano on 2010-06-18
Yeah it's really weird. But if the boot process gets messed up, is there anyway that could be fixed? Or does everything have to be reinstalled?

---

### Post by darkod on 2010-06-18
You shouldn't need to reinstall everything. Lets see more details. Run the boot info script again like in your previous thread, and post the current results to see them. I still think this can only be upgraded grub1 -> grub2.

---

### Post by Micano on 2010-06-18
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 596619582 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 596493334 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 596627558 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,715,903    30,713,856  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,715,904   343,290,936   312,575,033   7 HPFS/NTFS
/dev/sda3         343,292,985   595,786,589   252,493,605   f W95 Ext d (LBA)
/dev/sda5         343,293,048   595,777,216   252,484,169   7 HPFS/NTFS
/dev/sda4         595,786,590   625,137,344    29,350,755  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        D0DAAFB9DAAF9A6C                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        6d1bba2b-6872-4846-9823-9dc8dc061d90   ext4                                     
/dev/sda5        5B8601CA50A3FA07                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda4/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6d1bba2b-6872-4846-9823-9dc8dc061d90

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic-pae
uuid		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic-pae
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic-pae (recovery mode)
uuid		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic-pae

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic-pae
uuid		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic-pae
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic-pae (recovery mode)
uuid		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic-pae

title		Ubuntu 10.04 LTS, kernel 2.6.32-15-generic-pae
uuid		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-15-generic-pae
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-15-generic-pae (recovery mode)
uuid		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro  single
initrd		/boot/initrd.img-2.6.32-15-generic-pae

title		Ubuntu 10.04 LTS, kernel 2.6.32-15-generic
uuid		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-15-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-15-generic (recovery mode)
uuid		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro  single
initrd		/boot/initrd.img-2.6.32-15-generic

title		Chainload into GRUB 2
root		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry "Ubuntu, with Linux 2.6.32-15-generic-pae" {
        recordfail
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
	linux	/boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-15-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-15-generic-pae (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
	echo	Loading Linux 2.6.32-15-generic-pae ...
	linux	/boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-15-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-15-generic" {
        recordfail
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
	linux	/boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-15-generic
}
menuentry "Ubuntu, with Linux 2.6.32-15-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
	echo	Loading Linux 2.6.32-15-generic ...
	linux	/boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 3c98-ac5d
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d0daafb9daaf9a6c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/OS ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/DATA ntfs-3g defaults,locale=en_US.UTF-8 0 0
/mnt/2048mb.swap none swap sw 0 0

=================== sda4: Location of files loaded by Grub: ===================


 305.4GB: boot/grub/core.img
 305.6GB: boot/grub/grub.cfg
 313.0GB: boot/grub/menu.lst
 305.4GB: boot/grub/stage2
 316.1GB: boot/initrd.img-2.6.32-15-generic
 316.1GB: boot/initrd.img-2.6.32-15-generic-pae
 316.1GB: boot/initrd.img-2.6.32-22-generic-pae
 316.1GB: boot/initrd.img-2.6.32-23-generic-pae
 317.5GB: boot/vmlinuz-2.6.32-15-generic
 317.6GB: boot/vmlinuz-2.6.32-15-generic-pae
 315.9GB: boot/vmlinuz-2.6.32-22-generic-pae
 315.2GB: boot/vmlinuz-2.6.32-23-generic-pae
 316.1GB: initrd.img
 316.1GB: initrd.img.old
 315.2GB: vmlinuz
 315.9GB: vmlinuz.old

```

---

### Post by darkod on 2010-06-18
title        Chainload into GRUB 2
root        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/grub/core.img

This is the entry in grub1 menu.lst which is usually there in the middle of the process upgrading from grub1 to grub2.

We could try and see what the upgrade command does, hopefully it will work out OK. Maybe because you upgraded to the development version of Lucid you had grub1 added then, I don't know.

That's why you shouldn't really upgrade to development versions, not for your main system.

In terminal try:

sudo upgrade-from-grub-legacy

If there is any problem booting, you can always boot the ubuntu cd in live mode.

---

### Post by Micano on 2010-06-18
sudo: upgrade-from-grub-legacy: command not found

---

### Post by darkod on 2010-06-18
You could try just removing the grub1 package, called grub. Since you also have grub2 and all its config files, it should keep on booting. But I have never tried it. And I have never had a mix of grub1 and grub2 like you have.
I can't really guarantee anything. :)

---

### Post by Micano on 2010-06-18
I don't think anyone ever have had a mix :P. I actually considered doing that, and I'll try it out. But grub2 is not installed in linux, so how will it keep on booting?

---

### Post by darkod on 2010-06-18
How do you mean it's not installed? Look in your results file, you have Grub2 in the MBR of the disk, and also on sda4 you have the grub2 boot files /boot/grub/grub.cfg and /boot/grub/core.img.

But you also have /boot/grub/menu.lst which has no place there. And somehow grub1 on the boot sector of sda4.

I also saw from your other new thread that you have the folder /etc/grub.d.old which could exist only if you created it. It seems you were trying something.

I suggest not to try too many things until you get a better understanding. That's how these complications happen.

---

### Post by Micano on 2010-06-18
Yeah okay. What I mean is, since it was using grub1 too boot through the linux partition, will it use grub2 on some other sda where it is installed? I don't remember what I was doing, but it was probably something stupid when I realized that I couldn't boot into windows after updating

Okay I have GRand Unified Bootloader (legacy version), 

and I have GRand Unified Bootloader, version 2 (common files)

---

### Post by oldfred on 2010-06-18
I would totally uninstall grub & grub2 and then totally reinstall grub2.

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

Since you can boot you can run this from your install, just do not stop after the uninstall or you will not be able to boot.

---

### Post by darkod on 2010-06-18
The upgrade to 10.04 was a different issue. The window asking you where you want grub2 installed is offering all DISKS and all PARTITIONS. If you don't pay attention, or you are not aware of the difference, and mark all of them, it will install grub2 to the boot sectors on all partitions.
In such case, and because of the specific way windows boots, you will not be able to boot windows with grub2 installer onto its partition boot sector. But that is sorted out with the testdisk procedure you did, and removed grub2 from the windows partition.

But all of the above NEVER installs grub1. So how did it end on your computer since you had a clean install of Karmic which also uses grub2. When did grub1 come into play, that's what we can't figure out.

You were not able to boot windows because of different reason.

---

### Post by darkod on 2010-06-18
> **oldfred said:**
> I would totally uninstall grub & grub2 and then totally reinstall grub2.

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

Since you can boot you can run this from your install, just do not stop after the uninstall or you will not be able to boot.

This is what we needed, more experienced help. :) Thanks.

Just a note, you need sudo in front of all these commands. Or to save yourself from typing sudo all the time, just do

sudo -i

before you start executing them. But BE CAREFUL what commands you execute while in sudo -i.

---

### Post by Micano on 2010-06-18
Configuring grub-pc 
The following Linux command line was extracted from /etc/default/grub or  &#9474; 
 &#9474; the `kopt' parameter in GRUB Legacy's menu.lst.  Please verify that it    &#9474; 
 &#9474; is correct, and modify it if necessary.

Anything I need to do or just press ok? Just wanna be 100% sure on everything I do

---

### Post by darkod on 2010-06-18
I can't see any question, what do you need to verify?

Don't be too afraid, you are the one seeing the screen, we can't. :)

---

### Post by Micano on 2010-06-18
Hehe I can press ok, or add some command if needed. I guess I just have to press ok. Just a bit paranoid now since I don't want to mess everything up :P

---

### Post by darkod on 2010-06-18
> **Micano said:**
> Hehe I can press ok, or add some command if needed. I guess I just have to press ok. Just a bit paranoid now since I don't want to mess everything up :P

That's how you learn. If you don't want to mess anything up, don't install new OSs. :)
Fire the OK...

---

### Post by Micano on 2010-06-18
Okay the "ok" button has been fired! 

Now I have to choose where to install grub.

/dev/sda  (320072 MB, ST9320423AS)
/dev/sda1 (15725 MB)
/dev/sda2 (160038 MB)
/dev/sda3 (0 MB)
/dev/sda4 (15027 MB)
/dev/sda5 (129271 MB)

---

### Post by oldfred on 2010-06-18
Quick answer  - sda

Drive are sda, sdb etc and partitions are sda1, sda2, sdb1 etc (with the numbers. You only want to install grub to a drive sda (or sdb if you have one). Installing grub to a partiiton can corrupt windows if it is a windows partition but can only be installed to a partition if you have another boot loader in a multiboot system.

---

### Post by Micano on 2010-06-18
&#9474; You chose not to install GRUB to any devices.  If you continue, the boot  &#9474; 
 &#9474; loader may not be properly configured, and when your computer next        &#9474; 
 &#9474; starts up it will use whatever was previously in the boot sector.  If     &#9474; 
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474; 
 &#9474; unable to load modules or handle the current configuration file. 

This happend when I pressed sda

---

### Post by oldfred on 2010-06-18
If you did not check sda or somehow it did not recognize it you can reinstall from a liveCD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)


Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by Micano on 2010-06-18
This is what I got from fdisk -l:


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b3496e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15356928   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1912       21369   156287516+   7  HPFS/NTFS
/dev/sda3           21370       37086   126246802+   f  W95 Ext'd (LBA)
/dev/sda4           37087       38913    14675377+  83  Linux
/dev/sda5           21370       37086   126242084+   7  HPFS/NTFS

```

---

### Post by oldfred on 2010-06-18
Your only linux partition is sda4 so you want to install to that instead of sda5 in the instrutions. 

You also so not have a swap?

---

### Post by Micano on 2010-06-18
Ah nvm. This is going to take some time, since I don't have a cd. I need to get going to another place, and bring my laptop. But I guess I have to power off and boot from a CD later anyways? 

I used to have a swap before the upgrade to 10.04

---

### Post by oldfred on 2010-06-18
The real answer is does it boot?

---

### Post by Micano on 2010-06-18
Aaand the answer is *drum rolls* no. Mabe I should just reinstall linux, will that work?

---

### Post by darkod on 2010-06-18
If you haven't rebooted it, you might be able to add grub2 now. Did you reboot it?

---

### Post by darkod on 2010-06-18
It's too late now, but for the future: When a message is asking you to select something and you don't have mouse pointer (in text mode), you need to use up/down usually to highlight the item you want to select, press Space bar to select it, and only then hit Enter or OK or Next.

Just hitting Enter is not selecting the item but it is only continuing the process. That's why it said you didn't select any device for grub2, by pressing Enter it just continued even though you had /dev/sda highlighted.

---

### Post by Micano on 2010-06-18
Oh god no! Seriously? Haha anyways, it's too late now :P. So what now? Should I try to reinstall grub using a CD or just reinstall ubuntu maybe? Doesn't matter, anything that fixes this

---

### Post by darkod on 2010-06-18
> **Micano said:**
> Oh god no! Seriously? Haha anyways, it's too late now :P. So what now? Should I try to reinstall grub using a CD or just reinstall ubuntu maybe? Doesn't matter, anything that fixes this

Lets figure out where you are at the moment. You installed grub2 (packages grub-pc and grub-common) as per oldfred's instructions right? The only glitch is that when it asked you where to install grub2, it continued with nothing selected. Right?

---

### Post by Micano on 2010-06-18
Yeah, I am currently booted on a CD. I checked Grub version and it is now 1.98

---

### Post by darkod on 2010-06-18
OK, since your ubuntu is on sda4 lets try to go inside with chroot and install it on the MBR. You have to mount it, because it can't work in live mode. Open terminal and execute one by one:

sudo -i
mount /dev/sda4 /mnt
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
grub-install /dev/sda (this should install it to the MBR)
update-grub (just in case)

Restart without the cd and see if that sorted it out. If it didn't, you know how to use live mode. :)

---

### Post by Micano on 2010-06-18
grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
no path or device is specified
Try ´/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option ´modules' explicitly.

---

### Post by darkod on 2010-06-18
The /boot/grub folder should have been created with the earlier set of commands. If you try to list it with:

ls /mnt/boot/grub

what does it say?

---

### Post by Micano on 2010-06-18
It brings up a lot of files with .mod and .img

---

### Post by darkod on 2010-06-18
Can it find:

ls /boot/grub/grub.cfg
ls /boot/grub/core.img

---

### Post by Micano on 2010-06-18
It can't find it

---

### Post by darkod on 2010-06-18
OK, they aren't created yet.

Lets split it in few steps.

1. Mount the root partition and confirm if grub-pc is installed:

sudo -i
mount /dev/sda4 /mnt
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt

grub-install -v && aptitude show|grub-pc -2

That should show grub version 1.98 and that grub-pc is installed. If yes, continue with:

grub-mkconfig

That should successfully create grub2 config files. If yes, continue with installing to the mbr:

grub-install --root-directory=/mnt/ /dev/sda
update-grub

If that is done successfully exit the chroot and unmount with:

exit
umount /mnt/sys (the command is umount, it's not a typo)
umount /mnt/dev
umount /mnt/proc

Restart.

---

### Post by Micano on 2010-06-18
grub-install (GNU GRUB 1.98-lubuntu6)
grub-pc: command not found

---

### Post by darkod on 2010-06-18
> **Micano said:**
> grub-install (GNU GRUB 1.98-lubuntu6)
grub-pc: command not found

Did you type the command exactly as it is, all of it? Or as two separate commands:

grub-install -v && aptitude show|grub-pc -2

or

grub-install -v
aptitude show|grub-pc -2

---

### Post by Micano on 2010-06-18
Exactly as you wrote. Tried both though

---

### Post by darkod on 2010-06-18
It seems grub-pc and maybe grub-common are not installed. They should have been if you did all the commands oldfred's post had.

Try now:

apt-get install grub-pc grub-common

It might not work though.

---

### Post by Micano on 2010-06-18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc is already the newest version.
grub-common is already the newest version.
grub-common set to manually installed.
The following packages were automatically installed and are no longer required:
  python-alsaaudio libfreebob0 libfont-freetype-perl
  linux-backports-modules-nouveau-lucid-generic libdesktop-agnostic0
  wine-gecko xchat-common kdebase-runtime-data-common hplip-cups
  nvidia-185-libvdpau fortunes-min libdesktop-agnostic-cfg-gconf
  nvidia-185-kernel-source linux-backports-modules-nouveau-2.6.32-15-generic
  libopenjpeg2 python-sqlalchemy libknotificationitem1 libass3
  kde-icons-oxygen fortune-mod libexiv2-5 odbcinst virtuosoconverter libawn0
  kcm-phonon-xine liblzma0 ttf-lyx unixodbc sdparm libx264-67 librecode0
  libdesktop-agnostic-vfs-gio python-urwid kdebase-runtime-bin-kde4
  libawn-extras0 libcelt0 libdbusmenu-qt1 odbcinst1debian1
  libdesktop-agnostic-fdo-glib libffado1 libxml++2.6-2 libqt4-phonon
  khelpcenter4 sqlite3 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by Micano on 2010-06-18
However I don\t have anything again a reinstall of ubuntu, if I can later install grub and dual boot windows 7 again. I just don't want any files to disappear on my hard drives cause I havent backed them up.

---

### Post by darkod on 2010-06-18
OK, if you have them installed continue with the grub-mkconfig command from previous post.

---

### Post by darkod on 2010-06-18
Since you are in chroot now and trying to make this work, see if those commands help.

Then depending what happens, you can simply backup anything you want using the live mode, all your partitions should be in Places.

---

### Post by Micano on 2010-06-18
This is what I get when I start my computer. Everything you said worked fine though.
 
GNU GRUB version  1.98-1ubuntu6
 
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

---

### Post by darkod on 2010-06-18
Because we've done quite a few changes, please post the script results again.

While I'm going through them you can copy the data you need onto external hdd if you have one at hand.

---

### Post by Micano on 2010-06-18
> **darkod said:**
> Because we've done quite a few changes, please post the script results again.
 
While I'm going through them you can copy the data you need onto external hdd if you have one at hand.
 
When I boot from CD, it doesn't find my usb external hdd

---

### Post by darkod on 2010-06-18
> **Micano said:**
> When I boot from CD, it doesn't find my usb external hdd

That's almost impossible. Live mode doesn't have any problems reading usb sticks and hdds.

How about the script results?

---

### Post by Micano on 2010-06-18
The results are comming. Im starting ubuntu from CD again. But how will I be able to copy the data? Maybe Ive missunderstood what live mode is :P

---

### Post by darkod on 2010-06-18
Oce the desktop of live mode loads, go in Places and you will see all partitions there. Live mode doesn't know what they are, so it will just say 100GB filesystem, 75GB filesystem, etc.
Just click on it, and it will mount and open. You can browse and see all files there. So you can simply copy anything you want.

---

### Post by Micano on 2010-06-18
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 596619582 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 596493334 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 596627558 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    30,715,903    30,713,856   c W95 FAT32 (LBA)
/dev/sda2          30,715,904   343,290,936   312,575,033   7 HPFS/NTFS
/dev/sda3         343,292,985   595,786,589   252,493,605   f W95 Ext d (LBA)
/dev/sda5         343,293,048   595,777,216   252,484,169   7 HPFS/NTFS
/dev/sda4         595,786,590   625,137,344    29,350,755  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        D0DAAFB9DAAF9A6C                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        6d1bba2b-6872-4846-9823-9dc8dc061d90   ext4                                     
/dev/sda5        5B8601CA50A3FA07                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-15-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux    /boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-15-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-15-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    echo    'Loading Linux 2.6.32-15-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-15-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux    /boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    echo    'Loading Linux 2.6.32-15-generic ...'
    linux    /boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set d0daafb9daaf9a6c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/OS ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/DATA ntfs-3g defaults,locale=en_US.UTF-8 0 0
/mnt/2048mb.swap none swap sw 0 0

=================== sda4: Location of files loaded by Grub: ===================


 315.2GB: boot/grub/core.img
 315.3GB: boot/grub/grub.cfg
 316.1GB: boot/initrd.img-2.6.32-15-generic
 316.1GB: boot/initrd.img-2.6.32-15-generic-pae
 316.1GB: boot/initrd.img-2.6.32-22-generic-pae
 316.1GB: boot/initrd.img-2.6.32-23-generic-pae
 317.5GB: boot/vmlinuz-2.6.32-15-generic
 317.6GB: boot/vmlinuz-2.6.32-15-generic-pae
 315.9GB: boot/vmlinuz-2.6.32-22-generic-pae
 315.2GB: boot/vmlinuz-2.6.32-23-generic-pae
 316.1GB: initrd.img
 316.1GB: initrd.img.old
 315.2GB: vmlinuz
 315.9GB: vmlinuz.old

```

---

### Post by Micano on 2010-06-18
Yeah it doesnt detect my usb external hdd drive though when i insert it

---

### Post by darkod on 2010-06-18
It actually looks very good, as far as I can tell. Just grub2 on the MBR is looking at the wrong place.

You already rebooted in live mode again right? So the chroot commands we did are gone. That's what we need, the command session to be gone, so if you restarted even better.

In terminal do (type EXACTLY):

sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart and check.

---

### Post by Micano on 2010-06-18
Thanks, it works perfectly. 

I can boot into Linux again. 

Gonna try windows when I get back. I really appreciate your help! If you wouldn't mind helping me with another thing, do you know how to remove different options from the grub menu?

For instance, I have three different linux versions and memtest and windows vista (which I don't even have), that I would like removed.

Thanks again for helping me and having the patience to endure my noobiness :).

---

### Post by darkod on 2010-06-18
We will sort out the boot menu later, no problem. The main thing is it's working.

The vista in the menu is your recovery partition. Grub2 detects boot files and tries to guess what OS they are from. The recovery partition has boot files resembling vista, that's why it says vista. It can be win7 recovery partition, doesn't matter.

Have in mind that you won't be able to boot/start the recovery partition right now because you have grub2 installed on the partition boot sector (check the top of the results file). You will need to use the testdisk procedure on /dev/sda1 if you want to remove grub2 from there:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, that's partition #1 on disk /dev/sda.

Win7 should work fine as it is.

---

### Post by Micano on 2010-06-18
Yeah windows 7 works. 

My hard drive is actually divided into 2 partitions from the start. Then I have another for Linux. So one of the partitions doesn't have any OS, just different files. However I suddenly found an ASUS recovery partition on my Windows 7, which I have never seen before.

---

### Post by darkod on 2010-06-18
That's it. It doesn't show in windows in Computer, unlike linux which shows all.

For the grub2 menu. After every change of the grub2 config files, you need to run:

sudo update-grub

to create updated grub.cfg file. So I don't have to write it all the time, you know to run it after any change you make.

To disable memtest showing:

sudo chmod -x /etc/grub.d/20_memtest86+

To enable it again, the same command only with +x.

The ubuntu kernels shown usually have normal and recovery mode entries. And then also you have different kernels, 2.6.32-22, 2.6.32-21, etc. It is recommended to keep the recovery mode entries, in case you need to log into a text based system for repair. It is also recommended to keep at least one older kernel together with the newest one.

Linux works that way that if one updated kernel starts giving you trouble, the older one might work just fine and you can use it to boot the system.

But if you have 3 or more kernels shown, you can remove the oldest ones. You remove kernels in Synaptic, just type linux-image in the search box and remove the kernel you want. Be careful not to remove all of them, there will be nothing to boot. The main kernel file is linux-image-2.6.3x-xx.
Just click on the kernel you want to remove and select Mark for Complete Removal. You need to run the update-grub also after that.

That's it in short. More for grub2 basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Micano on 2010-06-18
Thank you so much! Both you darkod and oldfred!

---

