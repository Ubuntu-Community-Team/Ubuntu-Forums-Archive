---
title: "Dual Boot Not Working, All I see is Grub"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by JeremyWorst on 2011-04-17
I installed a 2nd HD on an HP Pavilion 750c that already had Windows XP on the 1st HD, then installed Ubuntu 10.10 LTS on the 2nd HD. Everything went well, I got a boot screen where I could choose multiple OSs, Windows still booted and so did Ubuntu. But following the 1st time Ubuntu's Update Manager ran, there is no longer a boot screen, just 'grub>'. The 1st HD does have two partitions, one containing recovery info and the other containing the actual boot partition, not sure if that's a factor or not.

I'm no grub expert and I'm stuck. I can still boot from the Ubuntu Live CD to troubleshoot. 

Any ideas or suggestions? Thanks!

---

### Post by Dutch70 on 2011-04-17
I'm not sure why it would boot the first time, and then not boot after you update it, other than a kernel update messing it up. If you can see an older kernel, try logging into it. If not, then do the following.

Lets have a look at your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags.

---

### Post by JeremyWorst on 2011-04-18
Here it is:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       9764426 sectors.. But according to the info from the 
                       partition table , it has 9767456 sectors.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     9,767,519     9,767,457  12 Compaq diagnostics
/dev/sda2    *      9,767,520   156,340,799   146,573,280   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.1 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders, total 117304992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   112,422,911   112,420,864  83 Linux
/dev/sdb2         112,424,958   117,303,295     4,878,338   5 Extended
/dev/sdb5         112,424,960   117,303,295     4,878,336  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01F9-4949                              vfat       HP_RECOVERY                   
/dev/sda2        C47C325D7C324B06                       ntfs       HP_PAVILION                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        20e5ac65-c37b-4278-8dff-dafe38369863   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a81b886f-c173-4fd6-844e-6e74d5a99268   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/BOOT.INI: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows Whistler Personal" /fastdetect /NoExecute=OptIn


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=20e5ac65-c37b-4278-8dff-dafe38369863 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=20e5ac65-c37b-4278-8dff-dafe38369863 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=20e5ac65-c37b-4278-8dff-dafe38369863 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=20e5ac65-c37b-4278-8dff-dafe38369863 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 01f9-4949
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows Whistler Personal (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c47c325d7c324b06
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=20e5ac65-c37b-4278-8dff-dafe38369863 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a81b886f-c173-4fd6-844e-6e74d5a99268 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  53.8GB: boot/grub/grub.cfg
  17.3GB: boot/initrd.img-2.6.32-21-generic
  17.3GB: boot/initrd.img-2.6.32-30-generic
  17.3GB: boot/vmlinuz-2.6.32-21-generic
  17.3GB: boot/vmlinuz-2.6.32-30-generic
  17.3GB: initrd.img
  17.3GB: initrd.img.old
  17.3GB: vmlinuz
  17.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  98 87 0f 08 a0 81 42 0a  |..............B.|
00000040  09 50 75 29 2f 34 52 a4  a8 7b 9f 84 45 54 4a d4  |.Pu)/4R..{..ETJ.|
00000050  52 bc 90 e2 48 d2 c0 a1  9f 02 e3 a8 f5 40 0b e0  |R...H........@..|
00000060  0a 02 85 c6 92 a6 a0 00  0d 75 80 87 54 82 1d 40  |.........u..T..@|
00000070  a3 02 29 47 01 97 87 b1  d3 7b 50 79 2d 0f ff a7  |..)G.....{Py-...|
00000080  1c 27 47 45 9e cb 18 58  98 87 10 08 ea 9c db a6  |.'GE...X........|
00000090  69 59 06 00 1d 3a 9d c1  34 39 e4 a1 bb 08 2c 06  |iY...:..49....,.|
000000a0  bd 8a f7 80 0d 4a 3c 16  db a4 f6 d7 59 12 db 09  |.....J<.....Y...|
000000b0  91 d4 01 c0 03 f8 e0 11  b7 bd 96 67 9c ea b1 0b  |...........g....|
000000c0  14 51 c7 24 08 98 10 03  5c 38 4d e1 b6 0c f9 b7  |.Q.$....\8M.....|
000000d0  61 63 a9 14 1e 03 00 00  98 87 11 08 ce 98 6d 5d  |ac............m]|
000000e0  92 04 da 79 c3 09 24 b9  07 06 cf a4 b6 eb 5e 97  |...y..$.......^.|
000000f0  3e 78 93 62 44 a1 e1 8a  d4 2c bd fc dd 45 09 11  |>x.bD....,...E..|
00000100  ae a4 0a 10 87 f1 ca ac  99 ac ea be f5 b2 d1 04  |................|
00000110  d5 02 f4 8c 04 9a d0 07  68 e9 f8 8d 62 81 fa b5  |........h...b...|
00000120  a4 17 7e 98 b6 0b 07 8a  98 87 12 08 da 1d bb 8d  |..~.............|
00000130  a5 50 39 c3 96 0f e3 12  2e e1 e5 28 ed 18 3c c0  |.P9........(..<.|
00000140  d6 71 97 8f 09 fe 03 f4  e9 98 c2 25 5d cc a4 d2  |.q.........%]...|
00000150  46 02 fc 18 2b 0d ea 1a  a4 80 6b 91 a9 84 29 7f  |F...+.....k...).|
00000160  11 fe 33 36 18 25 c5 a4  1b 00 00 00 00 00 f6 37  |..36.%.........7|
00000170  02 9a 63 f2 61 80 00 00  98 87 13 08 ab 91 94 4e  |..c.a..........N|
00000180  15 2b 9d c1 73 f8 35 52  78 6c ae 9b 76 90 00 13  |.+..s.5Rxl..v...|
00000190  92 74 8d 3c 0d 50 c0 00  b2 a5 da 8a a1 0e 70 73  |.t.<.P........ps|
000001a0  9c f7 3f 88 58 00 b9 2f  a8 a9 e1 df 65 23 f3 25  |..?.X../....e#.%|
000001b0  80 00 00 00 01 12 1e c0  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 4a 00 00 00  |...........pJ...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Dutch70 on 2011-04-18
Well done! 

Looks like grub is installed to the wrong hdd. Boot up the live cd/usb and run the following commands. 
```
sudo mount /dev/sdb1 /mnt
```
Then...
```
sudo grub-install --root-directory=/mnt /dev/sdb
```
Reboot & log in to Ubuntu and run...
```
sudo update-grub
```
Reboot again to make sure everything is showing up correctly.

Here is the [[COLOR="RoyalBlue"]Link[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by JeremyWorst on 2011-04-19
It still is not working, I still only get the 'grub' prompt. If it helps, here's the new boot info:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       9764426 sectors.. But according to the info from the 
                       partition table , it has 9767456 sectors.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     9,767,519     9,767,457  12 Compaq diagnostics
/dev/sda2    *      9,767,520   156,340,799   146,573,280   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.1 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders, total 117304992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   112,422,911   112,420,864  83 Linux
/dev/sdb2         112,424,958   117,303,295     4,878,338   5 Extended
/dev/sdb5         112,424,960   117,303,295     4,878,336  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01F9-4949                              vfat       HP_RECOVERY                   
/dev/sda2        C47C325D7C324B06                       ntfs       HP_PAVILION                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        20e5ac65-c37b-4278-8dff-dafe38369863   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a81b886f-c173-4fd6-844e-6e74d5a99268   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/BOOT.INI: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows Whistler Personal" /fastdetect /NoExecute=OptIn


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=20e5ac65-c37b-4278-8dff-dafe38369863 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=20e5ac65-c37b-4278-8dff-dafe38369863 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=20e5ac65-c37b-4278-8dff-dafe38369863 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=20e5ac65-c37b-4278-8dff-dafe38369863 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 20e5ac65-c37b-4278-8dff-dafe38369863
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 01f9-4949
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows Whistler Personal (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c47c325d7c324b06
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=20e5ac65-c37b-4278-8dff-dafe38369863 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a81b886f-c173-4fd6-844e-6e74d5a99268 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  53.8GB: boot/grub/grub.cfg
  17.3GB: boot/initrd.img-2.6.32-21-generic
  17.3GB: boot/initrd.img-2.6.32-30-generic
  17.3GB: boot/vmlinuz-2.6.32-21-generic
  17.3GB: boot/vmlinuz-2.6.32-30-generic
  17.3GB: initrd.img
  17.3GB: initrd.img.old
  17.3GB: vmlinuz
  17.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  98 87 0f 08 a0 81 42 0a  |..............B.|
00000040  09 50 75 29 2f 34 52 a4  a8 7b 9f 84 45 54 4a d4  |.Pu)/4R..{..ETJ.|
00000050  52 bc 90 e2 48 d2 c0 a1  9f 02 e3 a8 f5 40 0b e0  |R...H........@..|
00000060  0a 02 85 c6 92 a6 a0 00  0d 75 80 87 54 82 1d 40  |.........u..T..@|
00000070  a3 02 29 47 01 97 87 b1  d3 7b 50 79 2d 0f ff a7  |..)G.....{Py-...|
00000080  1c 27 47 45 9e cb 18 58  98 87 10 08 ea 9c db a6  |.'GE...X........|
00000090  69 59 06 00 1d 3a 9d c1  34 39 e4 a1 bb 08 2c 06  |iY...:..49....,.|
000000a0  bd 8a f7 80 0d 4a 3c 16  db a4 f6 d7 59 12 db 09  |.....J<.....Y...|
000000b0  91 d4 01 c0 03 f8 e0 11  b7 bd 96 67 9c ea b1 0b  |...........g....|
000000c0  14 51 c7 24 08 98 10 03  5c 38 4d e1 b6 0c f9 b7  |.Q.$....\8M.....|
000000d0  61 63 a9 14 1e 03 00 00  98 87 11 08 ce 98 6d 5d  |ac............m]|
000000e0  92 04 da 79 c3 09 24 b9  07 06 cf a4 b6 eb 5e 97  |...y..$.......^.|
000000f0  3e 78 93 62 44 a1 e1 8a  d4 2c bd fc dd 45 09 11  |>x.bD....,...E..|
00000100  ae a4 0a 10 87 f1 ca ac  99 ac ea be f5 b2 d1 04  |................|
00000110  d5 02 f4 8c 04 9a d0 07  68 e9 f8 8d 62 81 fa b5  |........h...b...|
00000120  a4 17 7e 98 b6 0b 07 8a  98 87 12 08 da 1d bb 8d  |..~.............|
00000130  a5 50 39 c3 96 0f e3 12  2e e1 e5 28 ed 18 3c c0  |.P9........(..<.|
00000140  d6 71 97 8f 09 fe 03 f4  e9 98 c2 25 5d cc a4 d2  |.q.........%]...|
00000150  46 02 fc 18 2b 0d ea 1a  a4 80 6b 91 a9 84 29 7f  |F...+.....k...).|
00000160  11 fe 33 36 18 25 c5 a4  1b 00 00 00 00 00 f6 37  |..36.%.........7|
00000170  02 9a 63 f2 61 80 00 00  98 87 13 08 ab 91 94 4e  |..c.a..........N|
00000180  15 2b 9d c1 73 f8 35 52  78 6c ae 9b 76 90 00 13  |.+..s.5Rxl..v...|
00000190  92 74 8d 3c 0d 50 c0 00  b2 a5 da 8a a1 0e 70 73  |.t.<.P........ps|
000001a0  9c f7 3f 88 58 00 b9 2f  a8 a9 e1 df 65 23 f3 25  |..?.X../....e#.%|
000001b0  80 00 00 00 01 12 1e c0  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 4a 00 00 00  |...........pJ...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Dutch70 on 2011-04-19
Well, I'm not sure what would be causing it. Hopefully one of these links will help.
Mainly the 2nd one. 
[[COLOR="RoyalBlue"]http://www.linuxforums.org/forum/newbie/139419-i-am-stuck-grub-cant-boot-vista-anymore.html[/COLOR]]("http://www.linuxforums.org/forum/newbie/139419-i-am-stuck-grub-cant-boot-vista-anymore.html")
[[COLOR="RoyalBlue"]http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html[/COLOR]]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html")

I can't seem to find very much on the subject with google, but I've seen that same issue on here a few times lately.

---

### Post by wilee-nilee on 2011-04-19
The sdb hd needs to be read first check the bios.

---

### Post by Dutch70 on 2011-04-20
> **wilee-nilee said:**
> The sdb hd needs to be read first check the bios.

Haa, very good point. :P

---

### Post by JeremyWorst on 2011-04-21
Thanks for all the help. I ended up taking a highly technical, very sophisticated approach. I did a complete re-install of Ubuntu. ^^ This was a new install anyway, so nothing lost but my precious time. Everything worked after the install, including dual boot. I did a few re-boots between Windows and Ubuntu before I allowed Update Manager to apply any updates. Following updates everything is still fine. I think maybe something had happened during the previous updates that caused a problem. 

Anyway my apologies if I offended anybody by taking the easy way out and skipped an opportunity to learn a little about Grub.

---

### Post by Dutch70 on 2011-04-21
I'm sure no one is offended, hate that you had to reinstall, but sometimes it's the easiest way to get back in business. That's one reason having a separate /home partition is such a great thing. You can reinstall without losing your data or even your settings.

Anyway, glad you got it working.

Don't forget to mark the thread [Solved] with "Thread Tools" at the top of the page.

---

