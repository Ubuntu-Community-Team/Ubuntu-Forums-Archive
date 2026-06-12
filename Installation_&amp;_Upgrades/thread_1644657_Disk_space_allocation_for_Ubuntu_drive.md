---
title: "Disk space allocation for Ubuntu drive"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by savramesh on 2010-12-13
i was using vista in my laptop, recently installed ubuntu in another drive partition which is 69 GB. but during ubuntu installation i gave only 16GB to ubuntu from this drive. 

i guess the remaining 69 GB - 16 GB = 53 GB is unused space now..

now how can i allocate all 69GB in that drive to ubuntu ?

---

### Post by Quackers on 2010-12-13
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively a screenshot of your Gparted screen would help

---

### Post by savramesh on 2010-12-13
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    20,561,919    20,480,000   7 HPFS/NTFS
/dev/sda3    *     20,561,920   166,682,287   146,120,368   7 HPFS/NTFS
/dev/sda4         166,682,624   312,578,047   145,895,424   f W95 Ext d (LBA)
/dev/sda5         166,684,672   312,578,047   145,893,376   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       357a00b9-ef26-4824-8a4e-73e83c4beb38   ext4                                     
/dev/sda1        07D7-0615                              vfat       DellUtility                   
/dev/sda2        AAB6D921B6D8EEB7                       ntfs       Local Disk                    
/dev/sda3        768A075D8A07196F                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        52C4AF3AC4AF1F6B                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda5/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 52c4af3ac4af1f6b
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 52c4af3ac4af1f6b
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 52c4af3ac4af1f6b
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 52c4af3ac4af1f6b
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 768a075d8a07196f
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

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


   4.6GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
   1.6GB: boot/initrd.img-2.6.35-23-generic
   9.6GB: boot/vmlinuz-2.6.35-22-generic
   9.6GB: boot/vmlinuz-2.6.35-23-generic
   1.6GB: initrd.img
   1.5GB: initrd.img.old
   9.6GB: vmlinuz
   9.6GB: vmlinuz.old
```

---

### Post by Quackers on 2010-12-13
As your installation is a wubi installation and as I know very little about wubi I shall leave this for more experience wubi users to answer. I'm sure somebody will be along soon :-)

---

### Post by bcbc on 2010-12-13
You could allocate all that space, but... really if you want the whole partition dedicated to Ubuntu, you should install direct to it.

with Wubi the defauly max 'virtual disk' is about 30GB. You can increase that or add additional virtual disks, in theory, but that's not a typical use of Wubi.

The best way to use up that space that I can think of is to store your data on the host ntfs partition (it's mounted under /host). You could even link e.g. your Pictures folder to a folder under /host, and that way get around the virtual disk constraints without constantly moving data around.

Personally I would just install Ubuntu into that complete partition.

PS here's my standard Wubi Warning: do not update packages grub-pc and grub-common. They are known to break Wubi Ubuntu or (in your specific situation) prompt you to overwrite the windows bootloader in the disk MBR which prevents any OS from booting.

---

### Post by savramesh on 2010-12-13
Hi bcbc.

Thanks, that would be fine.. i will have my backups inside host folder and utilize that space..

---

