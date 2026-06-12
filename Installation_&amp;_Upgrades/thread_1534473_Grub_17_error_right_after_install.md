---
title: "Grub 17 error right after install"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by parakeets11 on 2010-07-19
Well, its been a while since I last used Linux, and I'm just getting back into the swing of things.  I wanted to Dual Boot Linux with Windows 7 so I installed it on my second HDD.  The installation went through and I restarted my computer.  Thing was, the Grub menu didn't even show, it just went straight into Windows.  I restarted again and went into my BIOS boot menu and told it to boot from my Linux drive.  When it started to load the grub menu, I got Error 17.  I don't understand why it would do that, help please?

---

### Post by wilee-nilee on 2010-07-19
> **parakeets11 said:**
> Well, its been a while since I last used Linux, and I'm just getting back into the swing of things.  I wanted to Dual Boot Linux with Windows 7 so I installed it on my second HDD.  The installation went through and I restarted my computer.  Thing was, the Grub menu didn't even show, it just went straight into Windows.  I restarted again and went into my BIOS boot menu and told it to boot from my Linux drive.  When it started to load the grub menu, I got Error 17.  I don't understand why it would do that, help please?

Post the bootscript in my signature in code tags as described.

---

### Post by parakeets11 on 2010-07-19
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
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
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   390,719,487   390,512,640   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   371,093,503   371,091,456  83 Linux
/dev/sdb2         371,095,550   390,719,487    19,623,938   5 Extended
/dev/sdb5         371,095,552   390,719,487    19,623,936  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7EFC8ADCFC8A8DD9                       ntfs       System Reserved               
/dev/sda2        CE9C90689C904CB9                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        98cd9d27-96e0-4196-b901-fdaad7a4fd7f   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        df27c315-991a-4987-a45b-1889b0854a52   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        141654C81654AC8C                       ntfs       Large Drive - Movies          
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 98cd9d27-96e0-4196-b901-fdaad7a4fd7f
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 98cd9d27-96e0-4196-b901-fdaad7a4fd7f
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 98cd9d27-96e0-4196-b901-fdaad7a4fd7f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=98cd9d27-96e0-4196-b901-fdaad7a4fd7f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 98cd9d27-96e0-4196-b901-fdaad7a4fd7f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=98cd9d27-96e0-4196-b901-fdaad7a4fd7f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 98cd9d27-96e0-4196-b901-fdaad7a4fd7f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 98cd9d27-96e0-4196-b901-fdaad7a4fd7f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7efc8adcfc8a8dd9
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
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=df27c315-991a-4987-a45b-1889b0854a52 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 144.0GB: boot/grub/core.img
 116.2GB: boot/grub/grub.cfg
 144.0GB: boot/initrd.img-2.6.32-21-generic
 144.0GB: boot/vmlinuz-2.6.32-21-generic
 144.0GB: initrd.img
 144.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  f8 f1 13 01 af 1f 2e d2  8d d8 20 03 39 96 e4 a8  |.......... .9...|
00000010  08 58 29 bb 38 6d 2e 65  8b dc 5e d9 84 08 a1 09  |.X).8m.e..^.....|
00000020  d1 54 f8 de 6f 45 20 56  83 82 40 e4 5b a2 3d 41  |.T..oE V..@.[.=A|
00000030  02 1f da 6a 60 25 a9 c8  2e df 16 ed 93 06 28 2c  |...j`%........(,|
00000040  ac b7 14 92 10 ea 28 53  ee 8b ec 54 6b 69 35 ac  |......(S...Tki5.|
00000050  79 7e 23 39 37 88 e0 a3  26 af 58 dc 93 47 ed cd  |y~#97...&.X..G..|
00000060  05 65 de c5 1e 6c 04 dd  72 48 30 e4 d1 16 83 d2  |.e...l..rH0.....|
00000070  a5 fc 17 53 b6 09 71 c8  34 bb aa a7 e3 41 47 62  |...S..q.4....AGb|
00000080  45 e8 56 c8 ac 51 ad 1e  f8 b2 32 45 32 47 7a dc  |E.V..Q....2E2Gz.|
00000090  e1 3d 03 74 9a a1 40 31  c5 98 26 13 fb 71 0b 30  |.=.t..@1..&..q.0|
000000a0  ab f8 68 b1 42 d7 d6 c5  b7 c7 7e ca 0d 71 d7 06  |..h.B.....~..q..|
000000b0  4e 49 a9 a8 24 27 92 2f  98 7d a8 71 5e aa 55 c6  |NI..$'./.}.q^.U.|
000000c0  3d af 89 7f 60 80 4c a7  85 56 0c 19 61 ed dc c7  |=...`.L..V..a...|
000000d0  7c a9 a0 78 b1 da 8c 24  23 7c 9f da 0a 5e 77 51  ||..x...$#|...^wQ|
000000e0  8b d4 4f f4 8e 4d 5a 45  97 ff de 48 0e ad eb 89  |..O..MZE...H....|
000000f0  a7 10 24 dc 80 03 36 93  fc 5e 4b cf 91 ed 9f 4c  |..$...6..^K....L|
00000100  5d 7c 73 d8 00 dc 76 c8  ea 2c f2 a9 c3 a8 c2 c9  |]|s...v..,......|
00000110  ab ef cd 6d d3 56 ec 7c  88 0c 25 b6 90 50 f1 26  |...m.V.|..%..P.&|
00000120  2d 4a 83 e0 72 fd 29 64  25 b0 6e b2 1c eb a7 5b  |-J..r.)d%.n....[|
00000130  a4 d5 d5 91 ba a6 cb 15  79 d4 05 f0 17 56 1a 43  |........y....V.C|
00000140  8c 62 ef ee 49 61 27 00  31 24 b5 97 32 cb 99 91  |.b..Ia'.1$..2...|
00000150  23 f0 6f 94 c2 f4 77 08  ab 4d 60 06 2d 64 7c ac  |#.o...w..M`.-d|.|
00000160  5f d8 af 91 52 08 d2 b7  93 1b 34 c2 c5 a0 2f f2  |_...R.....4.../.|
00000170  85 27 7a 28 e8 a7 f8 d9  f2 95 c6 13 77 64 29 23  |.'z(........wd)#|
00000180  a5 8f 1b 11 10 65 e6 f4  45 9b 4e cb 04 74 6e d1  |.....e..E.N..tn.|
00000190  67 fe 55 98 c9 0a ba 48  8f d1 94 3b cf 1b c0 af  |g.U....H...;....|
000001a0  40 8a 3c b1 7a ce c4 10  aa 13 58 c0 98 1d 10 ba  |@.<.z.....X.....|
000001b0  b3 f8 4b 8b dd e0 e5 66  b2 35 42 f2 2b c4 00 fe  |..K....f.5B.+...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 2b 01 00 00  |...........p+...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Sorry for the wait, had to boot using the LiveCD

---

### Post by oldfred on 2010-07-19
Error 17 is from old grub so you must be booting sda. But your new grub2 is in sdb. Change your boot order in BIOS to boot sdb. 
Since they are both 200GB you just have to switch. I have two identical 160GB drives and only can tell them apart in BIOS from which one boots which system.

---

### Post by parakeets11 on 2010-07-19
I switched them, but I'm getting the same error.

---

### Post by oldfred on 2010-07-19
Sorry misread. The grub2 is installed in the 1.5TB drive. Try booting that.

But I prefer to have grub on the same drive as the Ubuntu install. If it boots you should reinstall grub to sdb and set that to boot in BIOS.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by parakeets11 on 2010-07-20
Well, my BIOS was all like, > You can't boot from that drive because I don't want you to, derp derp derp
So, since it was a fresh install, I decided to install again, and behold, I noticed at the very end of the installation, under the advanced tab, it asks if you would like to install a boot loader, and on which drive.  So I did it.  I don't know what prompted the installer to install the boot loader onto a storage drive, but whatever, it works now.  Thanks for the help though.

---

