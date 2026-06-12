---
title: "Loss of windows 7 after installing upgrades"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by Canime on 2011-03-22
I installed ubuntu about a month ago. I upgraded for the first time today using the upgrade manager that downloaded the 315 some MB's of upgrades. After re-booting the windows 7 option was missing from the boot menu. How can I get it back, and what could have happened?

---

### Post by mastablasta on 2011-03-22
do you have Ubuntu maybe installed through wubi?
 
Please post the output of this script that will tell us how the computer is actually booting:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
Instructions are found on the website.

---

### Post by Canime on 2011-03-22
> **mastablasta said:**
> do you have Ubuntu maybe installed through wubi?
 
Please post the output of this script that will tell us how the computer is actually booting:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
Instructions are found on the website.

No, I haven't installed it on wubi, its a dual partition (actually a tri partition, with the outer two sectors belonging to the windows installation, that I installed first, the middle sector belonging to Ubuntu that I installed second. I didn't do ANYTHING to it, just ran the update manager, and as you can see below, windows 7, exists still. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2007. But according to the info from fdisk, 
                       sda5 starts at sector 178532352.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

```

How can I get it back as a grub menu option?

---

### Post by wilee-nilee on 2011-03-22
Post all the text from the script.

---

### Post by Canime on 2011-03-22
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2007. But according to the info from fdisk, 
                       sda5 starts at sector 178532352.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    82,829,311    82,827,264   7 HPFS/NTFS
/dev/sda2          82,831,358   312,573,943   229,742,586   5 Extended
/dev/sda5         178,532,352   312,573,943   134,041,592   7 HPFS/NTFS
/dev/sda6          82,831,360   178,530,303    95,698,944  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,953,520,127 1,953,520,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56DA91DFDA91BBA5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ECCE5604CE55C80A                       ntfs       Local Disk                    
/dev/sda6        66fab157-b85e-49d4-bf56-f9c884218006   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9A80F6E580F6C733                       ntfs       Expansion Drive               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
[operating systems]
C:\grldr="openSUSE 11.0 installer (LOCAL)"

=========================== sda6/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 66fab157-b85e-49d4-bf56-f9c884218006
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 66fab157-b85e-49d4-bf56-f9c884218006
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 66fab157-b85e-49d4-bf56-f9c884218006
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=66fab157-b85e-49d4-bf56-f9c884218006 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 66fab157-b85e-49d4-bf56-f9c884218006
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=66fab157-b85e-49d4-bf56-f9c884218006 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 66fab157-b85e-49d4-bf56-f9c884218006
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=66fab157-b85e-49d4-bf56-f9c884218006 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 66fab157-b85e-49d4-bf56-f9c884218006
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=66fab157-b85e-49d4-bf56-f9c884218006 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 66fab157-b85e-49d4-bf56-f9c884218006
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 66fab157-b85e-49d4-bf56-f9c884218006
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=66fab157-b85e-49d4-bf56-f9c884218006 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/mnt/512Mb.swap none swap sw 0 0


=================== sda6: Location of files loaded by Grub: ===================


  55.4GB: boot/grub/core.img
  57.6GB: boot/grub/grub.cfg
  46.5GB: boot/initrd.img-2.6.35-22-generic
  46.0GB: boot/initrd.img-2.6.35-28-generic
  55.4GB: boot/vmlinuz-2.6.35-22-generic
  55.5GB: boot/vmlinuz-2.6.35-28-generic
  46.0GB: initrd.img
  46.5GB: initrd.img.old
  55.5GB: vmlinuz
  55.4GB: vmlinuz.old
```

Here, you can see that sda1, with windows 7 is still boot, however no menu option on startup.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    82,829,311    82,827,264   7 HPFS/NTFS
/dev/sda2          82,831,358   312,573,943   229,742,586   5 Extended
/dev/sda5         178,532,352   312,573,943   134,041,592   7 HPFS/NTFS
/dev/sda6          82,831,360   178,530,303    95,698,944  83 Linux
```

I am really scared I can't get this menu option back btw. I really DON'T want to re-install windows 7 or Ubuntu. I have that plan as a back-up, but there is no way in the world I will I resort to re-installing either.

---

### Post by Quackers on 2011-03-22
Have you run ```
sudo update-grub
``` in a terminal?

If that does not find a Windows entry, please go to synaptic package manager and in the search box enter "os-prober". It will then apear in the main window. Is it showing as installed (with a green box on its left)? If not, please install it and then run sudo update-grub again.

---

### Post by Canime on 2011-03-22
> **Quackers said:**
> Have you run ```
sudo update-grub
``` in a terminal?

If that does not find a Windows entry, please go to synaptic package manager and in the search box enter "os-prober". It will then apear in the main window. Is it showing as installed (with a green box on its left)? If not, please install it and then run sudo update-grub again.

SOLVED. That worked well. 

On first run of sudo update-grub, this was found,```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin

```

After installing os-prober, it found:
```
/dev/sda1:Windows 7 (loader):Windows:chain

```

After running sudo-update grub again, it generated,
```
[sudo] password for iain: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```

On restart all of my stuff was there and all the changes from start-up manager had taken affect :). By the way, start-up manager doesn't give any options to change boot configuration of the OS, only which operating system you want as default, display sizes and timeout.

Thanks!!!

---

### Post by Quackers on 2011-03-22
Glad it worked. I don't know why os-prober wasn't there to start with - it should have been. However, it has happened before occasionally.
What boot configuration do you want to change?

---

### Post by Canime on 2011-03-22
I wanted the plymouth program to have a different color to purple, that was the only thing.

---

### Post by Quackers on 2011-03-22
Some details in the thread below, though I haven't delved into it
[http://ubuntuforums.org/showthread.php?t=1492277](http://ubuntuforums.org/showthread.php?t=1492277)

And more here
[http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html](http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html)

---

