---
title: "Can't install bootloader on my SSD"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by mbarnes2013 on 2011-02-01
Ok So I haven't been able to find a solution to this so I thought I'd ask.

I have a custom computer and it has 3 hard drives.

a 750 GB HDD
a 1TB HDD
and a 30 GB SSD

originally I had the 750 as my primary HDD but got the SSD.
Since I'm a C S major I decided to put linux on part of the 1TB HDD I got.

The problem.

I am trying to get the grub bootloader onto the SDD(where my primary windows install is) so I can choose when I boot without having to call the boot menu. During install of Ubuntu I had to install the bootloader on the 750Gb HDD because It could not detect my SSD.

Does anyone know how to fix this? I just want to be able to choose what OS to boot to when I boot to my primary (SSD) drive. But It can't be seen by the live cd or Ubuntu itself.

---

### Post by mbarnes2013 on 2011-02-01
If I could do it with the Windows Bootloader instead of Grub that might be easier If anyone could walk me through it.

---

### Post by wilee-nilee on 2011-02-01
> **mbarnes2013 said:**
> If I could do it with the Windows Bootloader instead of Grub that might be easier If anyone could walk me through it.

You want grub on the same HD as its installed in. It helps if you actually name the windows OS and all your setups, but even easier is running the bootscript in my signature. Post the text from the generated file in code tags. To get code tags open a reply click on the** #** in the reply panel and paste the text in between. The script will identify what is where and what they are.

The only way you can use the windows bootloader to boot Ubuntu or any Linux is with easybcd, I'm not sure that is the best solution though. Very little of the forum members use easybcd, and so the help is very sparse, I can't help you there.

---

### Post by mbarnes2013 on 2011-02-01
Sounds good ill do that as soon as I get out of class.

---

### Post by wilee-nilee on 2011-02-01
> **mbarnes2013 said:**
> Sounds good ill do that as soon as I get out of class.

I will be gone in a hour or so to my classes, so others will probably help you.

---

### Post by mbarnes2013 on 2011-02-01
Ok, Heres the result of the Boot Script, Only problem I can see is its still not showing my SDD. Its got my two HDD's and my two Externals, but no dice on the Solid State.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 851732632 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,465,145,343 1,464,938,496   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,949,218,815 1,949,216,768  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1               2,048 1,953,515,519 1,953,513,472   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5AC88613C885EE17                       ntfs       System Reserved               
/dev/sda2        36F287AFF2877243                       ntfs       Old HDD                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b8ce262d-e45c-4273-ba8c-84787449d49a   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        B0747382747349DC                       ntfs       FreeAgent Drive               
/dev/sdd: PTTYPE="dos" 
/dev/sde1        80F05B48F05B4396                       ntfs       My Book 3.0                   
/dev/sde: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sde1        /media/My Book 3.0       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b8ce262d-e45c-4273-ba8c-84787449d49a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b8ce262d-e45c-4273-ba8c-84787449d49a
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set b8ce262d-e45c-4273-ba8c-84787449d49a
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b8ce262d-e45c-4273-ba8c-84787449d49a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set b8ce262d-e45c-4273-ba8c-84787449d49a
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b8ce262d-e45c-4273-ba8c-84787449d49a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set b8ce262d-e45c-4273-ba8c-84787449d49a
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=b8ce262d-e45c-4273-ba8c-84787449d49a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set b8ce262d-e45c-4273-ba8c-84787449d49a
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=b8ce262d-e45c-4273-ba8c-84787449d49a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set b8ce262d-e45c-4273-ba8c-84787449d49a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set b8ce262d-e45c-4273-ba8c-84787449d49a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5ac88613c885ee17
	chainloader +1
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b8ce262d-e45c-4273-ba8c-84787449d49a /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/core.img
 560.6GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.32-28-generic
   1.6GB: boot/initrd.img-2.6.35-25-generic
  77.5GB: boot/vmlinuz-2.6.32-28-generic
  77.5GB: boot/vmlinuz-2.6.35-25-generic
   1.6GB: initrd.img
   1.2GB: initrd.img.old
  77.5GB: vmlinuz
  77.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by mbarnes2013 on 2011-02-01
Does anyone know if there are any known issues with Linux and Solid state drives?

---

