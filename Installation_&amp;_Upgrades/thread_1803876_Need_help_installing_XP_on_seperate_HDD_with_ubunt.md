---
title: "Need help installing XP on seperate HDD with ubuntu"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by Clorox on 2011-07-14
Hey Every,
Alright I have a 500GB harddisk that is dedicated to Ubuntu, I just recently installed two old Harddisks one 30 and one 160. I wanna install XP on the 160 and dual boot between Ubuntu and XP. I tried installing XP to the 160 through my XP CD but it says "this disk does not contain a Windows compatible partition." So after that I went into Ubuntu and used Disc Utility to make it into a NTFS partition. That still didn't work and got the same error on my disc, I also unplugged my SATA 500HDD so I could see if that worked, and it didnt. The 160HDD is completly empty and nothing is installed on it. Does ubuntu have something to do with this? How my drives are setup in the hardware? :confused:

Thanks a lot in advanced (I also hope I posted in the right area)

---

### Post by tommcd on 2011-07-14
Unplug all hard drives except for the 160GB drive that you want to install XP on. Set that hard drive to be the first hard drive in the computer's BIOS. Set the BIOS to boot from the cdrom drive as the first boot device with the hard drive as the second boot device.
When you boot the XP CD you can delete any partitions that are on the 160GB drive. Then use the XP CD to create NTFS partitions and install XP there.
Then hook up the hard drive that has Ubuntu on it. Set it to be the first hard drive in the computer's BIOS. Then when you boot up Ubuntu run:
```
sudo update-grub
``` in the terminal and it should add XP to your grub menu so you can boot XP.

You could also just leave the XP hard drive as the first hard drive in the BIOS. Then boot from the Ubuntu live CD and install grub2 to the MBR of the XP CD to dual boot both XP and Ubuntu. See this: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by Clorox on 2011-07-14
That worked! Thanks a lot! but now im running into an error when I try and boot into windows. 

> Error: invaild signature 
No such device (or something.)
Press any key to continue.

From what ive been reading its like GRUB2 can't see my harddrive? If you have any idea's so I can also get over this hurdle thanks.


*continues googleing*

---

### Post by jramshu on 2011-07-14
That error looks like a hdd disabled in bios.

---

### Post by oldfred on 2011-07-14
Post this so we can see where everything is installed:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Clorox on 2011-07-14
Here are my results ```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sdc.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048   952,987,647   952,985,600  83 Linux
/dev/sdd2         952,989,694   976,773,119    23,783,426   5 Extended
/dev/sdd5         952,989,696   976,773,119    23,783,424  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sdc1        74B003FCB003C418                       ntfs       
/dev/sdd1        513e55f7-5b84-4df6-93f2-baed404873fc   ext4       
/dev/sdd5        6f52d6e5-ec1d-4cc5-b7dc-1acb8013200e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/ARMPXOEM          iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=1
default=signature(9d360)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
signature(9d360)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
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
search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=513e55f7-5b84-4df6-93f2-baed404873fc ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=513e55f7-5b84-4df6-93f2-baed404873fc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=513e55f7-5b84-4df6-93f2-baed404873fc ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=513e55f7-5b84-4df6-93f2-baed404873fc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=513e55f7-5b84-4df6-93f2-baed404873fc ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=513e55f7-5b84-4df6-93f2-baed404873fc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 513e55f7-5b84-4df6-93f2-baed404873fc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 74B003FCB003C418
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=513e55f7-5b84-4df6-93f2-baed404873fc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6f52d6e5-ec1d-4cc5-b7dc-1acb8013200e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 156.134025574 = 167.647633408  boot/grub/core.img                             1
 136.971576691 = 147.072110592  boot/grub/grub.cfg                             1
   0.390537262 = 0.419336192    boot/initrd.img-2.6.32-28-generic              2
 244.396717072 = 262.418976768  boot/initrd.img-2.6.32-31-generic              2
 137.217239380 = 147.335888896  boot/initrd.img-2.6.32-32-generic              1
 156.132625580 = 167.646130176  boot/vmlinuz-2.6.32-28-generic                 1
 156.143428802 = 167.657730048  boot/vmlinuz-2.6.32-31-generic                 1
 137.053577423 = 147.160158208  boot/vmlinuz-2.6.32-32-generic                 1
 137.217239380 = 147.335888896  initrd.img                                     1
 244.396717072 = 262.418976768  initrd.img.old                                 2
 137.053577423 = 147.160158208  vmlinuz                                        1
 156.143428802 = 167.657730048  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdd2

00000000  f9 ac 9c ff fb ad 9e ff  fc ae 9e ff fd af 9f ff  |................|
00000010  fe b0 a0 ff ff b0 a0 ff  ff 96 80 ff e4 b3 a8 ff  |................|
00000020  d8 e0 e1 ff c3 c3 c3 ff  99 99 99 fb 9c 9c 9c 22  |..............."|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  c6 c6 c8 bf bc c0 c2 ff  8f 3e 39 ff aa 50 4a ff  |.........>9..PJ.|
00000060  b0 5f 5a ff b3 61 59 ff  b1 55 4b ff 96 14 06 ff  |._Z..aY..UK.....|
00000070  98 0d 00 ff 86 15 03 ff  3b 76 20 ff 0b cd 35 ff  |........;v ...5.|
00000080  02 dc 3a ff 00 d8 40 ff  00 d5 3f ff 03 c6 43 ff  |..:...@...?...C.|
00000090  39 84 2e ff 77 59 1c ff  a3 3a 0e ff da 4d 33 ff  |9...wY...:...M3.|
000000a0  e8 a3 94 ff c8 b7 b2 ff  e8 ec ed ff cb 98 8e ff  |................|
000000b0  f7 b0 a3 ff f3 ae a1 ff  f8 b1 a3 ff fb b3 a5 ff  |................|
000000c0  fc b4 a6 ff fe b6 a6 ff  ff b6 a7 ff ff b6 a8 ff  |................|
000000d0  ff b8 a9 ff ff b9 aa ff  ff a2 8d ff e5 af a3 ff  |................|
000000e0  da e1 e2 ff c8 c8 c8 ff  99 99 99 fe 9b 9b 9b 49  |...............I|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000110  cd ce cf 9b c3 c8 cb ff  98 4d 48 ff a8 4e 48 ff  |.........MH..NH.|
00000120  b6 6a 62 ff b9 6b 63 ff  ab 44 3a ff 96 0c 00 ff  |.jb..kc..D:.....|
00000130  9d 10 00 ff a3 12 00 ff  9d 14 00 ff 78 39 0e ff  |............x9..|
00000140  46 79 21 ff 1d b1 34 ff  07 c7 43 ff 02 ca 48 ff  |Fy!...4...C...H.|
00000150  00 ce 4e ff 15 ba 4d ff  38 a7 45 ff 51 a9 58 ff  |..N...M.8.E.Q.X.|
00000160  8c b8 85 ff a2 af 8c ff  d2 dc c9 ff 92 9a 9d ff  |................|
00000170  e5 a9 99 ff fd bd ae ff  fc bd ad ff fb bd ad ff  |................|
00000180  ff c1 b0 ff ff c2 b0 ff  ff c3 b1 ff ff c4 b2 ff  |................|
00000190  ff c4 b2 ff ff c6 b4 ff  ff b4 9c ff e8 af 9c ff  |................|
000001a0  db e0 e2 ff cd cd cd ff  9a 9a 9a ff 9b 9b 9b 73  |...............s|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 6a 01 00 00  |............j...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sda sdb 


```

---

### Post by oldfred on 2011-07-14
Did you plug in some drives and unplug them. The 160GB drive is showing as sdc, but windows want to be the first drive or sda?

> ================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=1
default=signature(9d360)disk(0)[COLOR=Red]rdisk(0)[/COLOR]partition(1)\WINDOWS
[operating systems]
signature(9d360)disk(0)[COLOR=Red]rdisk(0[/COLOR])partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect


If the 160 is always going to be sdc then you have to change boot.ini to be the correct drive number or rdisk(2).

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.


How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

---

