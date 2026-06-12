---
title: "Unable to boot using GRUB"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by kulturloseramerikaner on 2011-01-21
OK, here's a rundown of what happened.

I have my system set up with 4 HDD's, each with its own OS. There is Win XP for legacy stuff I still need on sda, Ubuntu 10.04 for everyday stuff on sdb, another drive that wouldn't boot (sdc) because the loader for PC-BSD and GRUB 2 don't play well together, and Win 7 for games on sdd.

About 10 days ago, I was on in Win 7 when it kicked up an error stating that there was a failure detected in the hard disk drive. A bit of checking confirmed that is was sdb, the drive containing Ubuntu and of course, GRUB. I wasn't able to reboot to Ubuntu and loading Win 7 worked sometimes but it took forever to get to the selection screen. I booted up with System Recovery Disk was not able to read the disk with the recovery tools there. The disk was shot.

I got a new drive from Newegg and just got everything put back together a couple days ago. The install went fine, but when I restarted to apply the kernel update, it went right to Win 7 instead, bypassing GRUB all together. I restarted with a livecd of PCLinuxOS in the cd drive and installed that to sdc to try it out. Restarted to apply kernel and video driver updates. Same deal, went straight back to Win 7 on sdd. I can boot anything if I start with the SuperGRUB 1.30 disk in the CD drive, but for some reason it just won't see the install on the hard disk. I had everything running fine before the disk failure; even had a customized selection screen with a nice background and the older kernels and memtest option removed. As I recall, I was having this problem when I first upgraded to 10.04 from 8.04 a year ago, and I can't recall what I did to fix it. What would my next step be please?
Thanks.

---

### Post by presence1960 on 2011-01-21
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by kulturloseramerikaner on 2011-01-21
From what I can tell it seems to be looking now to sdc for the grub legacy file (PCLOS still uses that???) but I can't see why it would behave the same way before and after installing PCLOS.
In any event, thanks for the help.

All right, here goes:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Testdisk is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  PCLinuxOS release 2010 
                       (PCLinuxOS) for i586 Kernel 2.6.33.7-pclos6.bfs on a 
                       4-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   952,999,935   952,997,888  83 Linux
/dev/sdb2         953,001,982   976,773,119    23,771,138   5 Extended
/dev/sdb5         953,001,984   976,773,119    23,771,136  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
16 heads, 63 sectors/track, 310019 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    25,189,919    25,189,857  83 Linux
/dev/sdc2          25,189,920   312,499,151   287,309,232   5 Extended
/dev/sdc5          25,189,983    33,380,927     8,190,945  82 Linux swap / Solaris
/dev/sdc6          33,380,991   312,499,151   279,118,161  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdd2             206,848 1,250,260,991 1,250,054,144   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        10A49415A493FF80                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0fa354a9-8ebe-4b1d-832f-349cde6c78b1   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        59bded55-3a0b-40c5-a9e3-a06ba1c37326   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        09258edb-5b6a-4bdb-b628-17aa021c616d   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        e7c21b6d-4d24-4c13-90e7-1826a1202cd3   swap                                     
/dev/sdc6        70f0d89d-976f-481b-b5a0-2b518a1b9af0   ext4                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        80B6E60EB6E6050E                       ntfs       System Reserved               
/dev/sdd2        4E2EE8432EE82625                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


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
search --no-floppy --fs-uuid --set 0fa354a9-8ebe-4b1d-832f-349cde6c78b1
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
search --no-floppy --fs-uuid --set 0fa354a9-8ebe-4b1d-832f-349cde6c78b1
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0fa354a9-8ebe-4b1d-832f-349cde6c78b1
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=0fa354a9-8ebe-4b1d-832f-349cde6c78b1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0fa354a9-8ebe-4b1d-832f-349cde6c78b1
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=0fa354a9-8ebe-4b1d-832f-349cde6c78b1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0fa354a9-8ebe-4b1d-832f-349cde6c78b1
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0fa354a9-8ebe-4b1d-832f-349cde6c78b1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0fa354a9-8ebe-4b1d-832f-349cde6c78b1
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0fa354a9-8ebe-4b1d-832f-349cde6c78b1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0fa354a9-8ebe-4b1d-832f-349cde6c78b1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0fa354a9-8ebe-4b1d-832f-349cde6c78b1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 10a49415a493ff80
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "linux (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 09258edb-5b6a-4bdb-b628-17aa021c616d
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=09258edb-5b6a-4bdb-b628-17aa021c616d resume=UUID=59bded55-3a0b-40c5-a9e3-a06ba1c37326 splash=silent vga=788
	initrd (hd2,0)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 09258edb-5b6a-4bdb-b628-17aa021c616d
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=09258edb-5b6a-4bdb-b628-17aa021c616d resume=UUID=59bded55-3a0b-40c5-a9e3-a06ba1c37326
	initrd (hd2,0)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 09258edb-5b6a-4bdb-b628-17aa021c616d
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=09258edb-5b6a-4bdb-b628-17aa021c616d failsafe
	initrd (hd2,0)/boot/initrd.img
}
menuentry "Windows 7 (loader) (on /dev/sdd1)" {
	insmod ntfs
	set root='(hd3,1)'
	search --no-floppy --fs-uuid --set 80b6e60eb6e6050e
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
UUID=0fa354a9-8ebe-4b1d-832f-349cde6c78b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=59bded55-3a0b-40c5-a9e3-a06ba1c37326 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 197.7GB: boot/grub/core.img
 197.7GB: boot/grub/grub.cfg
 197.7GB: boot/initrd.img-2.6.32-24-generic
 197.7GB: boot/initrd.img-2.6.32-27-generic
 197.8GB: boot/vmlinuz-2.6.32-24-generic
 197.8GB: boot/vmlinuz-2.6.32-27-generic
 197.7GB: initrd.img
 197.7GB: initrd.img.old
 197.8GB: vmlinuz
 197.8GB: vmlinuz.old

=========================== sdc1/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd2,0)/boot/gfxmenu
default 0

title linux
kernel (hd2,0)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=09258edb-5b6a-4bdb-b628-17aa021c616d  resume=UUID=59bded55-3a0b-40c5-a9e3-a06ba1c37326 splash=silent vga=788
initrd (hd2,0)/boot/initrd.img

title linux-nonfb
kernel (hd2,0)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=09258edb-5b6a-4bdb-b628-17aa021c616d  resume=UUID=59bded55-3a0b-40c5-a9e3-a06ba1c37326
initrd (hd2,0)/boot/initrd.img

title failsafe
kernel (hd2,0)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=09258edb-5b6a-4bdb-b628-17aa021c616d  failsafe
initrd (hd2,0)/boot/initrd.img

title Windoze Ex Pee
root (hd0,0)
makeactive
chainloader +1

title windows 7
root (hd3,0)
map (0x83) (0x80)
map (0x80) (0x83)
makeactive
chainloader +1

=============================== sdc1/etc/fstab: ===============================

# Entry for /dev/sdc1 :
UUID=09258edb-5b6a-4bdb-b628-17aa021c616d / ext4 defaults 1 1
# Entry for /dev/sdc6 :
UUID=70f0d89d-976f-481b-b5a0-2b518a1b9af0 /home ext4 defaults 1 2
none /proc proc defaults 0 0
# Entry for /dev/sdb5 :
UUID=59bded55-3a0b-40c5-a9e3-a06ba1c37326 swap swap defaults 0 0
# Entry for /dev/sdc5 :
UUID=e7c21b6d-4d24-4c13-90e7-1826a1202cd3 swap swap defaults 0 0

=================== sdc1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/menu.lst
   3.5GB: boot/grub/stage2
   2.2GB: boot/vmlinuz
   2.2GB: boot/vmlinuz-2.6.33.7-pclos6.bfs
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  89 3c 62 cb 73 ac c8 76  bb 42 5f c1 78 ae 54 1b  |.<b.s..v.B_.x.T.|
00000010  e6 62 16 2e 8e 4a d3 01  d9 b8 b6 e6 2c 0a 85 da  |.b...J......,...|
00000020  96 13 72 26 12 12 e6 64  3d 57 21 33 9c ca 37 37  |..r&...d=W!3..77|
00000030  ca d1 22 56 29 df 48 9a  bc 15 de d4 6b 74 91 c5  |.."V).H.....kt..|
00000040  5d 68 f7 2b d9 ed 09 96  6c 2b 20 51 9d ed e1 b3  |]h.+....l+ Q....|
00000050  a9 f7 35 26 63 65 5c cd  1d 6e ba 86 fd 81 66 04  |..5&ce\..n....f.|
00000060  66 bc bf b3 db 5a d3 4f  8a b5 77 54 8b a9 27 c5  |f....Z.O..wT..'.|
00000070  2b 49 e4 ff fb e2 40 00  00 0a 37 68 d6 d3 38 7b  |+I....@...7h..8{|
00000080  68 d5 ed 1a da 67 0f 6d  1c dd a3 5b 4c e5 ed a3  |h....g.m...[L...|
00000090  b5 34 6b 29 ac bd b4 14  44 58 92 4a 49 c2 40 1e  |.4k)....DX.JI.@.|
000000a0  00 69 a2 a1 1a 07 97 50  68 78 29 41 49 77 5a f1  |.i.....Phx)AIwZ.|
000000b0  82 51 5f d5 14 a0 6c d4  8a 32 9a ce 5b 3a 5e 16  |.Q_...l..2..[:^.|
000000c0  a4 e2 83 75 1b 15 2c 06  da be ce 3c 22 01 62 71  |...u..,....<".bq|
000000d0  c8 8b f6 b9 cb 7c e2 3d  8f 03 76 52 c8 94 fc 92  |.....|.=..vR....|
000000e0  95 52 48 68 e9 65 80 d1  60 3e e1 31 17 74 39 57  |.RHh.e..`>.1.t9W|
000000f0  0f 05 f1 ef 84 be cf 02  03 39 42 42 31 59 1d b9  |.........9BB1Y..|
00000100  27 51 b0 ab 11 9a 69 9e  29 26 7e 87 ba 3f 6e d8  |'Q....i.)&~..?n.|
00000110  a4 70 3f 49 c8 5f b6 d9  76 b1 94 8f 43 95 73 44  |.p?I._..v...C.sD|
00000120  72 3d 12 8f 15 71 15 ea  33 0a cf 11 8b 2c ae 39  |r=...q..3....,.9|
00000130  5d 26 df 42 8e af 62 83  ec ad 75 24 7c cc de c7  |]&.B..b...u$|...|
00000140  57 b1 3c 57 ef d8 a3 ee  b0 5f 55 b6 57 b1 76 fb  |W.<W....._U.W.v.|
00000150  c1 8d b9 de e6 f4 83 88  52 52 f5 a6 69 25 a9 1a  |........RR..i%..|
00000160  24 4d c0 ac 2b 62 bb c5  23 e3 39 6d 8d ff ff ff  |$M..+b..#.9m....|
00000170  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 0f  |................|
000001c0  ff ff 82 0f ff ff 3f 00  00 00 e1 fb 7c 00 00 0f  |......?.....|...|
000001d0  ff ff 05 0f ff ff 20 fc  7c 00 90 01 a3 10 00 00  |...... .|.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh

```

---

### Post by drs305 on 2011-01-21
It appears you have the appropriate Grub2 files on sdb1 but Grub2 is not installed on any mbr. 

The easiest way to fix this is to boot the LiveCD, open a terminal and run the following commands:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

```
Note in the second command you are not including the partition number.

After running the above, reboot without the CD. Make sure BIOS points first to the sdb (Ubuntu) drive.

It should boot to the Grub2 menu, and your Windows entries should be included. After booting, just to ensure it's picked up all the OSs, run:
```
sudo update-grub
```

If for some reason Grub2 is not fully installed we may need to reinstall it from the LiveCD, but try the above first.

---

### Post by kulturloseramerikaner on 2011-01-21
Got it! :) 

Thank you guys.

---

### Post by kulturloseramerikaner on 2011-01-21
Well, now I'm using the wiki [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide]("here") to try to get everything at least back where it was. It worked a couple weeks ago, but now it's giving me this:

hirnrissigermann@HAL:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 but it is not going to be installed
             Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32asound2 but it is not going to be installed
             Depends: lib32bz2-1.0 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed
             Depends: lib32v4l-0 but it is not going to be installed
E: Broken packages

I tried to install each individually, and have had no luck. I just want to get my system as close as possible to the state it was in 2 weeks ago before the drive failure; where I should I go from here?

---

### Post by Rubi1200 on 2011-01-22
Hi,
glad you got the booting issues sorted out.

For the packages, try this:

```
sudo apt-get install -f

sudo dpkg --configure -a
```

---

