---
title: "Cloned Disk, Grub Broken (?)"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by ZER01NE1NE on 2010-06-02
Hi all,

I recently bought a new hard drive because I'm afraid my old one is going to wear out soon, as it's 5 years old. I used Clonezilla to copy the old one to the new one, but when I tried to boot from the new one, instead of booting properly it takes me to the grub boot menu. I can't boot into Ubuntu anymore. What do I do? Is Grub looking at the wrong disk? Please help.

~ Kyle

---

### Post by arrange on 2010-06-02
Is it an external or internal disk?
Could you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by darkod on 2010-06-02
Are you trying to test with both hdds connected? The cloning probably kept the same UUIDs for the partitions which are unique in the system. Two hdds with same partition UUIDs will probably confuse grub.

---

### Post by ZER01NE1NE on 2010-06-02
This is an internal 500GB hard drive, it's a different model than the old one, could that have something to do with it?

I ran that script, here's my results.txt file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdf and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

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

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdf2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdf3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sda2         104,856,255   150,994,934    46,138,680  83 Linux
/dev/sda3         150,994,935   390,716,864   239,721,930   5 Extended
/dev/sda5         150,994,998   182,450,204    31,455,207  83 Linux
/dev/sda6         182,450,268   203,415,029    20,964,762  83 Linux
/dev/sda7         203,415,093   205,519,544     2,104,452  83 Linux
/dev/sda8         205,519,608   209,712,509     4,192,902  82 Linux swap / Solaris
/dev/sda9         209,712,573   390,716,864   181,004,292   b W95 FAT32


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sdf2         104,856,255   150,994,934    46,138,680  83 Linux
/dev/sdf3         150,994,935   390,716,864   239,721,930   5 Extended
/dev/sdf5         150,994,998   182,450,204    31,455,207  83 Linux
/dev/sdf6         182,450,268   203,415,029    20,964,762  83 Linux
/dev/sdf7         203,415,093   205,519,544     2,104,452  83 Linux
/dev/sdf8         205,519,608   209,712,509     4,192,902  82 Linux swap / Solaris
/dev/sdf9         209,712,573   390,716,864   181,004,292   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F004203604200268                       ntfs       Windows                       
/dev/sda2        bc4da346-233a-479d-a88f-3df4aacc9a1f   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        763d8a10-8906-41a9-9461-d384fe14231c   ext3                                     
/dev/sda6        6d8520e4-1df9-44ad-be05-a44dc87fd63c   ext3                                     
/dev/sda7        c2dcbc49-de16-4286-9a81-837e268ab4f9   ext3                                     
/dev/sda8        af265325-0e06-48cc-91af-4e5fa8c2506a   swap                                     
/dev/sda9        7584a6e7-f000-417e-b4a1-3af03d16b906   ext3       Home                          
/dev/sda         ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ               ddf_raid_member                               
/dev/sdf1        F004203604200268                       ntfs       Windows                       
/dev/sdf2        bc4da346-233a-479d-a88f-3df4aacc9a1f   ext3                                     
/dev/sdf3: PTTYPE="dos" 
/dev/sdf5        763d8a10-8906-41a9-9461-d384fe14231c   ext3                                     
/dev/sdf6        6d8520e4-1df9-44ad-be05-a44dc87fd63c   ext3                                     
/dev/sdf7        c2dcbc49-de16-4286-9a81-837e268ab4f9   ext3                                     
/dev/sdf8        af265325-0e06-48cc-91af-4e5fa8c2506a   swap                                     
/dev/sdf9        7584a6e7-f000-417e-b4a1-3af03d16b906   ext3       Home                          
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro)
/dev/sda7        /tmp                     ext3       (rw)
/dev/sda9        /home                    ext3       (rw)
/dev/sda5        /usr                     ext3       (rw)
/dev/sda6        /var                     ext3       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 763d8a10-8906-41a9-9461-d384fe14231c
if loadfont /share/grub/unicode.pf2 ; then
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	echo	'Loading Linux 2.6.31-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f004203604200268
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=7584a6e7-f000-417e-b4a1-3af03d16b906 /home           ext3    defaults        0       2
# /tmp was on /dev/sda7 during installation
UUID=c2dcbc49-de16-4286-9a81-837e268ab4f9 /tmp            ext3    defaults        0       2
# /usr was on /dev/sda5 during installation
UUID=763d8a10-8906-41a9-9461-d384fe14231c /usr            ext3    defaults        0       2
# /var was on /dev/sda6 during installation
UUID=6d8520e4-1df9-44ad-be05-a44dc87fd63c /var            ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=af265325-0e06-48cc-91af-4e5fa8c2506a none            swap    sw              0       0

# Mount the second hard drive to /home/kyle/Videos
#UUID=fabce297-7674-49bc-9bd5-4ae3a3c7f714 /mnt/video	  ext3	  defaults 	  0	  2
#/mnt/video /home/kyle/Videos				  auto	  defaults,bind	  0	  0

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  64.8GB: boot/grub/core.img
  64.7GB: boot/grub/grub.cfg
  64.7GB: boot/initrd.img-2.6.31-21-generic-pae
  64.8GB: boot/initrd.img-2.6.32-22-generic-pae
  64.7GB: boot/vmlinuz-2.6.31-21-generic-pae
  64.7GB: boot/vmlinuz-2.6.32-22-generic-pae
  64.8GB: initrd.img
  64.7GB: initrd.img.old
  64.7GB: vmlinuz
  64.7GB: vmlinuz.old

================================ sdf1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdf2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 763d8a10-8906-41a9-9461-d384fe14231c
if loadfont /share/grub/unicode.pf2 ; then
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	echo	'Loading Linux 2.6.31-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bc4da346-233a-479d-a88f-3df4aacc9a1f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f004203604200268
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdf2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=7584a6e7-f000-417e-b4a1-3af03d16b906 /home           ext3    defaults        0       2
# /tmp was on /dev/sda7 during installation
UUID=c2dcbc49-de16-4286-9a81-837e268ab4f9 /tmp            ext3    defaults        0       2
# /usr was on /dev/sda5 during installation
UUID=763d8a10-8906-41a9-9461-d384fe14231c /usr            ext3    defaults        0       2
# /var was on /dev/sda6 during installation
UUID=6d8520e4-1df9-44ad-be05-a44dc87fd63c /var            ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=af265325-0e06-48cc-91af-4e5fa8c2506a none            swap    sw              0       0

# Mount the second hard drive to /home/kyle/Videos
#UUID=fabce297-7674-49bc-9bd5-4ae3a3c7f714 /mnt/video	  ext3	  defaults 	  0	  2
#/mnt/video /home/kyle/Videos				  auto	  defaults,bind	  0	  0

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdf2: Location of files loaded by Grub: ===================


  64.7GB: boot/grub/grub.cfg
  64.7GB: boot/grub/stage2
  64.7GB: boot/initrd.img-2.6.31-21-generic-pae
  64.8GB: boot/initrd.img-2.6.32-22-generic-pae
  64.7GB: boot/vmlinuz-2.6.31-21-generic-pae
  64.7GB: boot/vmlinuz-2.6.32-22-generic-pae
  64.8GB: initrd.img
  64.7GB: initrd.img.old
  64.7GB: vmlinuz
  64.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

/dev/sda is the original 186GB internal hard drive, and /dev/sdf is the cloned 500GB internal hard drive.

I just noticed that the original has GRUB 2, and the clone has GRUB 0.97. Did Clonezilla do this perhaps? Is there some way I can use GRUB 2?

---

### Post by darkod on 2010-06-02
You are also missing the /boot/grub/core.img file in the cloned disk. Did you maybe use old version of clonezilla? The current one supports grub2 according to their website but not sure when that was introduced.

Also, take your original disk out, you have UUID conflict like this. Even if the cloned disk doesn't boot correctly, take the original disk out and we can sort out the booting from live mode.

Not sure what went wrong and why grub2 is not restored properly. Unless clonezilla is old version as already mentioned.

Also, your original disk has raid metadata on it that was never properly removed. Not sure if that can interfere with clonezilla and the backup.

---

### Post by ZER01NE1NE on 2010-06-02
The version I have is 1.2.2, the latest is 1.2.5. Does 1.2.2 not support GRUB 2? I'm gonna download Clonezilla 1.2.5 and start over I guess.

---

### Post by ZER01NE1NE on 2010-06-02
OK, I've got a new problem. I downloaded Clonezilla 1.2.5, and successfully cloned the disk, and Grub works and everything, but now it gives me all kinds of error messages about reading the disk, and when I try to start the X server it says "No protocol specified" or something like that. Is there some configuration file I need to edit? All the UUID's and stuff are the same so I don't see what the problem is.

---

### Post by ZER01NE1NE on 2010-06-03
Help anyone?

---

### Post by wkulecz on 2010-06-10
I've never used "clonezilla" and never had any success that wasn't more trouble than it was worth with "partimage".

But I've had great success cloning Linux systems with rsync (lets you easily change partition sizes) and then re-installing grub from a live CD.

Grub2 throws up a lot of obsticals, especially for multiboot systems.

If you are not multibooting, you need to boot the live cd after swapping drives, open a root terminal, mount the cloned drive and follow these instructions to re-install grub2:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


But before you run  grub-install you have to fix the UUID issues in 10.04 and grub.

Use blkid to find your new UUIDs and then edit /boot/grub/grub.cfg and /boot/grub/load.cfg files (ignore the do not edit warnings as these are what grub-install will use at this point) to replace all the instances of your old UUID with the new. Also you must change the UUIDs in /root/etc on the cloned drive.

Then run grub-install as described the article I've linked and after you reboot, run sudo grub-update and you should be back in business.

For multiboot systems, grub2 is a travesty -- good luck!.

IMHO UUID mount is a cure worse than the disease who's fundamental cause if pretending that IDE, SCSI, and SATA drives are the same, when they physically clearly are not! Combined with the dynamic drive assigment disaster awaits as soon as you move things around at all.  This is almost as malicious and windows "activation".

---

### Post by ZER01NE1NE on 2010-06-10
OK, here's the thing, GRUB works now, and multiboot still works, but when it gets to the Linux kernel it spazzes out because it doesn't like the new hard drive for some reason, but all the UUID's and stuff are the same, I don't understand... Any idea what's wrong with Linux?

---

