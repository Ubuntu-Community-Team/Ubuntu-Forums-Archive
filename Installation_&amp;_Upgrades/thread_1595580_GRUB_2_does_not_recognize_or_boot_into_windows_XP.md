---
title: "GRUB 2 does not recognize or boot into windows XP"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by thinhdu on 2010-10-13
Can someone please help me on this issue as i can't boot up my win XP after installing Ubuntu 10.10.

I decided to replace my Vista partition with Ubuntu 10.10 so i redo my partitions and split the current Vista partition to a swap and root partition and install Ubuntu 10.10

Everything went well and i got Ubuntu up and running. However, i realize that GRUB 2 didn't recognize my existing windows partition.
I double-check on grub.cfg and see that the default os_prober didn't recognize my XP partition either. 

After search on the internet for a while, i found many similar issue where most are fix when manually adding the entry yourself so i decided to add an entry 11_XP under /ect/grub.d/ for windows XP and confirm that the new entry are added to the update grub.cfg file before restarting

```
### BEGIN /etc/grub.d/11_XP ###
menuentry "Windows XP" {
set root=(hd0,5)
insmod chain
drivemap -s (hd0) 
chainloader +1
}
### END /etc/grub.d/11_XP ###
```

I also check to make sure i have the correct partition:

```
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb030b030

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       20887   167766145    f  W95 Ext'd (LBA)
/dev/sda3           20888       33942   104857600    7  HPFS/NTFS
/dev/sda4           33942       48642   118077440    7  HPFS/NTFS
/dev/sda5   *           2        7833    62910508+   7  HPFS/NTFS
/dev/sda6            7834        8456     5000192   82  Linux swap / Solaris
/dev/sda7            8456       20887    99854336   83  Linux
```

However, when i restart my machine and select Win XP entry that i just created but nothing happen. I'm basically stuck at the blinking screen and Win XP is not booted up.

Here is the result when i run the boot info script. 

```
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,126   335,548,415   335,532,290   f W95 Ext d (LBA)
/dev/sda5    *         16,128   125,837,144   125,821,017   7 HPFS/NTFS
/dev/sda6         125,837,312   135,837,695    10,000,384  82 Linux swap / Solaris
/dev/sda7         135,839,744   335,548,415   199,708,672  83 Linux
/dev/sda3         335,550,464   545,265,663   209,715,200   7 HPFS/NTFS
/dev/sda4         545,265,664   781,420,543   236,154,880   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda3        5AF0C1DFF0C1C18D                       ntfs       XP Data Drive                 
/dev/sda4        68A8D5E3A8D5AFB4                       ntfs       Vista Data Drive              
/dev/sda5        26E434E7E434BABF                       ntfs       XP OS                         
/dev/sda6        d1940cd9-52c4-4680-bd72-33e8c8f4fddc   swap                                     
/dev/sda7        95381070-67c8-4ec6-a8f8-bafc50096de8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 95381070-67c8-4ec6-a8f8-bafc50096de8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 95381070-67c8-4ec6-a8f8-bafc50096de8
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 95381070-67c8-4ec6-a8f8-bafc50096de8
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=95381070-67c8-4ec6-a8f8-bafc50096de8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 95381070-67c8-4ec6-a8f8-bafc50096de8
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=95381070-67c8-4ec6-a8f8-bafc50096de8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_XP ###
menuentry "Windows XP" {
set root=(hd0,5)
insmod chain
drivemap -s (hd0) 
chainloader +1
}
### END /etc/grub.d/11_XP ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 95381070-67c8-4ec6-a8f8-bafc50096de8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 95381070-67c8-4ec6-a8f8-bafc50096de8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=95381070-67c8-4ec6-a8f8-bafc50096de8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d1940cd9-52c4-4680-bd72-33e8c8f4fddc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  91.1GB: boot/grub/core.img
  91.1GB: boot/grub/grub.cfg
  70.2GB: boot/initrd.img-2.6.35-22-generic-pae
  91.1GB: boot/vmlinuz-2.6.35-22-generic-pae
  70.2GB: initrd.img
  91.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  a8 6b 00 74 80 0a 66 98  17 6b 80 18 d6 70 80 01  |.k.t..f..k...p..|
00000010  81 35 4b 86 05 1b 8c 1d  8b 31 95 81 19 79 80 cd  |.5K......1...y..|
00000020  65 80 2e 0a 00 81 1a 75  85 06 2f 9a 1b 79 80 6e  |e......u../..y.n|
00000030  81 bf 81 52 64 ad 80 5a  61 80 4b 8b 25 59 9c 10  |...Rd..Za.K.%Y..|
00000040  2e c0 43 a8 61 00 7a c2  85 72 c2 78 20 c0 77 46  |..C.a.z..r.x .wF|
00000050  65 40 3b c1 53 65 00 6b  40 15 65 9b c0 45 c3 79  |e@;.Se.k@.e..E.y|
00000060  20 c2 28 41 7d 5f 01 c1  41 8a 72 40 46 53 c0 38  | .(A}_..A.r@FS.8|
00000070  79 00 66 40 01 aa 20 40  2e 75 c0 0a 75 c0 0c 75  |y.f@.. @.u..u..u|
00000080  c0 12 a0 75 00 71 00 42  44 83 61 c0 60 35 c1 08  |...u.q.BD.a.`5..|
00000090  79 c2 09 61 c0 50 c3 5c  61 00 68 5f 01 6e 40 8e  |y..a.P.\a.h_.n@.|
000000a0  74 c0 0c c1 68 31 ac 01  2c c0 30 c1 96 70 c0 73  |t...h1..,.0..p.s|
000000b0  6f c0 43 da 6c 40 0c 72  40 a5 c1 05 73 c0 02 c3  |o.C.l@.r@...s...|
000000c0  1a 56 6e c2 a9 43 76 74  42 05 20 c0 72 65 db 42  |.Vn..CvtB. .re.B|
000000d0  7a 41 29 69 40 2e 41 03  20 c0 01 c3 a5 aa 6d 40  |zA)i@.A. .....m@|
000000e0  22 6e 42 23 76 c0 44 20  c2 3a a8 72 00 6a 40 22  |"nB#v.D .:.r.j@"|
000000f0  6e c0 1e 65 c8 38 1f c1  2a c1 22 43 1e 41 8c 41  |n..e.8..*."C.A.A|
00000100  48 31 01 63 cb c0 1c cf  38 1a d0 38 31 01 43 26  |H1.c....8..81.C&|
00000110  c5 55 dc 31 01 41 4a c1  d4 45 04 00 40 b6 cd 46  |.U.1.AJ..E..@..F|
00000120  ed c5 34 6e c0 33 c1 e1  6c 40 42 c1 4b 47 11 c5  |..4n.3..l@B.KG..|
00000130  41 24 63 40 07 1f 01 31  40 4d 41 7b 6a f6 40 49  |A$c@...1@MA{j.@I|
00000140  63 c0 33 64 c0 00 41 f3  67 3c 00 f6 40 73 c1 83  |c.3d..A.g<..@s..|
00000150  41 45 4d 1d 31 01 3b 21  08 e1 04 42 e0 05 a3 63  |AEM.1.;!...B...c|
00000160  61 48 20 00 5a 47 e4 06  41 20 2e 41 6c 2c fa 4e  |aH .ZG..A .Al,.N|
00000170  65 d0 00 2d 00 70 a0 36  73 a0 05 a1 25 bd a1 0a  |e..-.p.6s...%...|
00000180  20 60 6d a1 11 21 11 e1  0e 50 e6 03 55 a3 0b 6e  | `m..!...P..U..n|
00000190  62 47 72 ea 77 4a 60 7e  72 75 e0 04 67 a0 2f 61  |bGr.wJ`~ru..g./a|
000001a0  20 32 a3 77 e1 12 69 eb  6a 32 63 3f fc a0 04 fc  | 2.w..i.j2c?....|
000001b0  a2 04 e1 38 e1 91 5f 61  7a 23 96 21 2e e3 80 01  |...8.._az#.!....|
000001c0  01 01 07 fe ff ff 02 00  00 00 59 e0 7f 07 00 fe  |..........Y.....|
000001d0  ff ff 05 fe ff ff 5b e0  7f 07 a7 98 98 00 00 00  |......[.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by kansasnoob on 2010-10-13
Would you please also post the output of:

```
sudo parted /dev/sda print
```

---

### Post by oldfred on 2010-10-13
Windows only boots thru a primary partition with windows installed. Also since that is how windows boots other installs move the boot loaders into the bootable partition. All your XP boot files in sda5 were in the Vista partition that you deleted. If XP was in a primary partition then it would be repairable with windows XP repair/install CD. If you reversed you data drive in sda3 as the OS and made sda5 the data directory it would be easy.

More info on how windows multi boots. Lots of detail but pictures show a lot.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I have links to old posts where meierfra (who wrote boot script) fixes XP from Ubuntu so it may be possible.

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Vista Win7 missing boot files meieifra
[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)
meierfra. - How to fix XP when the boot files are missing
How to fix Vista/Window 7 when the boot files are missing post4
[http://ubuntuforums.org/showthread.php?p=5726832](http://ubuntuforums.org/showthread.php?p=5726832)

---

### Post by thinhdu on 2010-10-14
Thanks so much for the information. 

This post helped me and XP is now booted up correctly

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

