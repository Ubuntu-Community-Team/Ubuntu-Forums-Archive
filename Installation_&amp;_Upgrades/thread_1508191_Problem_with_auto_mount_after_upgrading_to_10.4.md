---
title: "Problem with auto mount after upgrading to 10.4"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by Exus on 2010-06-12
I upgraded to 10.4 and installed Grub on a wrong drive. This means that i have it on the right drive (the one with Ubuntu) and in the wrong one (the one use for data). I have no problems with booting to Ubuntu or Windows. I can even access the files from the data drive (called Storage) after the systems boots.
The thing is that i can't auto mount it anymore (with /etc/fstab) and i don't know how to remove grub from the drive, because i can't find where the boot files are.
When booting Ubuntu, a message appears saying that there has been an error when trying to mount the drive, i press 'S', to skip the mounting and it goes to the desktop with no problems after that.
I only want to be able to auto mount it, even if i can't remove it.



This is the info from Boot Info Script:

```
 

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 275327 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 275327 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   136,825,604   136,825,542  83 Linux
/dev/sda2         136,825,605   156,360,644    19,535,040   5 Extended
/dev/sda5         136,825,668   156,360,644    19,534,977  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   321,492,779   321,492,717   7 HPFS/NTFS
/dev/sdb2         321,492,780   976,768,064   655,275,285   5 Extended
/dev/sdb5         321,492,843   976,768,064   655,275,222   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        980d87a0-97b3-4304-9986-7e1038d6a17c   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        14fcd19d-4477-4e71-8dc6-e9fd408652b6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0DF9526E213C090A                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        445CEE055CEDF19A                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 980d87a0-97b3-4304-9986-7e1038d6a17c
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 980d87a0-97b3-4304-9986-7e1038d6a17c
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 980d87a0-97b3-4304-9986-7e1038d6a17c
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=980d87a0-97b3-4304-9986-7e1038d6a17c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 980d87a0-97b3-4304-9986-7e1038d6a17c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=980d87a0-97b3-4304-9986-7e1038d6a17c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 980d87a0-97b3-4304-9986-7e1038d6a17c
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=980d87a0-97b3-4304-9986-7e1038d6a17c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 980d87a0-97b3-4304-9986-7e1038d6a17c
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=980d87a0-97b3-4304-9986-7e1038d6a17c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 980d87a0-97b3-4304-9986-7e1038d6a17c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 980d87a0-97b3-4304-9986-7e1038d6a17c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0df9526e213c090a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry “Windows Seven" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 20606A47606A23AE 
	drivemap -s (hd0) (hd1)
	chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=980d87a0-97b3-4304-9986-7e1038d6a17c /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda3 during installation
#UUID=C846-A3BE  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb5 during installation
UUID=14fcd19d-4477-4e71-8dc6-e9fd408652b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda5 /media/blackhole ntfs-3g quiet,defaults,rw 0 0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   3.1GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.31-22-generic
   1.5GB: boot/initrd.img-2.6.32-22-generic
   2.1GB: boot/vmlinuz-2.6.31-22-generic
   1.9GB: boot/vmlinuz-2.6.32-22-generic
   1.5GB: initrd.img
   1.5GB: initrd.img.old
   1.9GB: vmlinuz
   2.1GB: vmlinuz.old

```

SO... any ideas?

---

### Post by darkod on 2010-06-12
=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=980d87a0-97b3-4304-9986-7e1038d6a17c /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda3 during installation
#UUID=C846-A3BE  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb5 during installation
UUID=14fcd19d-4477-4e71-8dc6-e9fd408652b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

[COLOR=Red]/dev/sda5[/COLOR] /media/blackhole ntfs-3g quiet,defaults,rw 0 0

As you can see at the top of the results file, in the partitions section, it seems your disks somehow switched names. Your windows disk is now /dev/sdb.

And don't refer to your storage partition as drive, it's confusing. Drive is a Hard Disk Drive, your storage partition is only a partition on /dev/sdb.

In /etc/fstab change the /dev/sda5 to /dev/sdb5 and it should be OK. Because you are using the device name in fstab, and not UUID, the disks switching their device names made the entry wrong. It needs to be edited.

---

### Post by Exus on 2010-06-12
It worked!! Thx!

---

