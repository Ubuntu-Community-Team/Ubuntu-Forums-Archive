---
title: "Dell Utility Partition"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by AZinOH on 2011-01-22
My dual-boot of Vista/10.04 is working great...so good in fact, it's scary. Since I did the clean install on this Dell Inspiron 530, only one thing is as yet unsolved. Grub2 never saw the Dell Utility Partition. I know it's still there-GParted can see it just fine right where it's supposed to be at /dev/sda1  fat16  all 54.88mb of it. This hasn't been a concern so far but it would be if ever I need it so...is there an easy way to get Grub2 to recognize it? Thanks for any assistance.

---

### Post by Quackers on 2011-01-22
That sounds like a partition for tools of some kind. As such it won't be a bootable partition, so grub won't see it.

---

### Post by presence1960 on 2011-01-22
On some Dells you access the utility partition by depressing the key which brings up the menu for a one time boot device selection. It will give you options such as hard disk, CD/DVD drive, USB, network & Utility partition.

Refer to your documentation to see which key brings up the popup Boot device menu.

---

### Post by AZinOH on 2011-01-22
> **Quackers said:**
> That sounds like a partition for tools of some kind. As such it won't be a bootable partition, so grub won't see it.

Maybe...but my other Dell which was updated (not a clean install) from 8.04 to 10.04 has a listing in Grub for its own Dell Utility Partition so I was making a guess that they should be the same. Perhaps I was wrong.

---

### Post by Quackers on 2011-01-22
Does that partition hold a recovery image as well?
If you post the output of the boot script something may show up.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by AZinOH on 2011-01-22
Yes, the other machine has a recovery image in the Dell Utility Partition.


Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

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
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    21,084,159    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,084,160   842,553,335   821,469,176   7 HPFS/NTFS
/dev/sda4         842,553,342   976,768,064   134,214,723   5 Extended
/dev/sda5         971,209,638   976,768,064     5,558,427  82 Linux swap / Solaris
/dev/sda6         842,553,344   971,208,703   128,655,360  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-041D                              vfat       DellUtility                   
/dev/sda2        9CECDCF3ECDCC8A2                       ntfs       RECOVERY                      
/dev/sda3        AC64DF5964DF253C                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        1d59c11e-e52b-434a-a2d0-07ec2f2b453f   swap                                     
/dev/sda6        38986b09-3b01-4243-8d83-ec82ce7bc524   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=38986b09-3b01-4243-8d83-ec82ce7bc524 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 38986b09-3b01-4243-8d83-ec82ce7bc524
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ac64df5964df253c
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 478.7GB: boot/grub/core.img
 446.2GB: boot/grub/grub.cfg
 479.0GB: boot/initrd.img-2.6.32-24-generic
 479.3GB: boot/initrd.img-2.6.32-25-generic
 479.1GB: boot/initrd.img-2.6.32-26-generic
 434.3GB: boot/initrd.img-2.6.32-27-generic
 479.2GB: boot/initrd.img-2.6.32-28-generic
 478.9GB: boot/vmlinuz-2.6.32-24-generic
 479.0GB: boot/vmlinuz-2.6.32-25-generic
 479.0GB: boot/vmlinuz-2.6.32-26-generic
 479.2GB: boot/vmlinuz-2.6.32-27-generic
 479.2GB: boot/vmlinuz-2.6.32-28-generic
 479.2GB: initrd.img
 434.3GB: initrd.img.old
 479.2GB: vmlinuz
 479.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  63 de c1 5f 0d 56 8c 17  82 37 22 41 2d d1 e4 9d  |c.._.V...7"A-...|
00000010  f5 e0 16 c1 9e fe 30 2e  3d 16 6e 3c ad 87 0d 14  |......0.=.n<....|
00000020  5b c2 c5 08 b2 a9 35 94  be 46 57 05 67 68 29 27  |[.....5..FW.gh)'|
00000030  63 ca d6 19 56 eb 3a ce  7a 57 bd 8f a6 71 3b 2b  |c...V.:.zW...q;+|
00000040  22 85 61 06 82 33 02 94  3a ae 3d a0 ff 53 2a db  |".a..3..:.=..S*.|
00000050  d8 80 38 a7 ee 1f d7 a3  4f d2 42 0a 5b d9 dd 17  |..8.....O.B.[...|
00000060  5a d9 0f 2f 24 c8 51 31  10 eb ad 2b 60 73 22 dd  |Z../$.Q1...+`s".|
00000070  86 49 4d 53 c1 c9 fd 0f  17 1f 94 a6 09 a7 54 01  |.IMS..........T.|
00000080  8a 9e 3e 22 40 45 22 91  9f e1 ef f3 29 64 67 ea  |..>"@E".....)dg.|
00000090  68 a6 d6 55 f8 13 b1 13  05 a4 21 b7 c8 6e f4 9a  |h..U......!..n..|
000000a0  bb 34 0e a4 05 e5 5e f9  3d 13 c2 f7 f2 4a 4b 41  |.4....^.=....JKA|
000000b0  73 fe 83 ee 7d 70 04 69  f6 44 01 66 73 ab 31 2d  |s...}p.i.D.fs.1-|
000000c0  f2 43 44 79 36 3b d5 35  82 dd 9a 87 c7 d0 e3 fa  |.CDy6;.5........|
000000d0  72 b0 28 f3 d9 4d 7c 4f  e3 5b 29 dd 48 a7 21 f2  |r.(..M|O.[).H.!.|
000000e0  37 ab db 47 6c 75 fb ec  e7 80 08 48 7d 14 04 70  |7..Glu.....H}..p|
000000f0  e4 49 9c 1f 58 be 48 fb  95 70 30 7a 77 3d 58 a4  |.I..X.H..p0zw=X.|
00000100  ad 8c e2 cc 8c 89 b2 c9  66 99 ae 69 67 e5 a0 e5  |........f..ig...|
00000110  1c d9 d0 6d b5 70 14 9b  3f 5e a3 71 08 60 3e 7f  |...m.p..?^.q.`>.|
00000120  3f 2a 16 e1 6d b0 97 b1  ac 9e d6 ac f8 66 c9 9f  |?*..m........f..|
00000130  7c eb 29 15 93 d9 c7 4b  e7 25 3a 54 85 17 3d 8e  ||.)....K.%:T..=.|
00000140  fc 77 27 13 28 9d bf 18  92 ec c3 ce d5 b8 5d 83  |.w'.(.........].|
00000150  17 43 37 65 20 4d 37 20  03 0c 92 d7 e6 6e fb a6  |.C7e M7 .....n..|
00000160  c3 8b a7 82 6f d5 e2 da  53 60 cb db 25 51 bb a4  |....o...S`..%Q..|
00000170  d5 f6 c5 d4 48 92 92 ba  74 a6 c6 ba 4a 36 2c 5d  |....H...t...J6,]|
00000180  3a 25 32 2b f8 95 8b a3  b5 9c 25 6f 7f a4 52 f2  |:%2+......%o..R.|
00000190  a3 d5 80 97 bc d9 17 89  e2 ce b7 db 60 1d 32 b9  |............`.2.|
000001a0  68 d0 22 d1 11 cb 18 43  df 56 25 33 18 56 cb 9d  |h."....C.V%3.V..|
000001b0  bf 70 73 15 cc 07 75 78  df a3 b9 12 5d e3 00 fe  |.ps...ux....]...|
000001c0  ff ff 82 fe ff ff a8 23  ab 07 9b d0 54 00 00 fe  |.......#....T...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 20 ab 07 00 00  |........... ....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by Quackers on 2011-01-22
Thanks.
sda1 doesn't have the normal boot files that most recovery partitions have, but it does have /COMMAND.COM, so I'm not sure whether grub would normally pick that up as a bootable partition or not.
As your sda3 partition is picked up as a Windows Recovery Loader, I presume you have Vista installed, as this seems to be the only version of Windows that grub labels wrongly.
Did you see presence1960's post (no 3) regarding accessing that partition?

---

### Post by AZinOH on 2011-01-22
>>Did you see presence1960's post (no 3) regarding accessing that partition?

No I have not seen that post. Will look for it. Thank you.

---

