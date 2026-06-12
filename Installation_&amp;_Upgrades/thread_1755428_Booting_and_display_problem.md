---
title: "Booting and display problem"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by kafunit on 2011-05-11
I have updated the latest Ubuntu 11.04 from 10.10. on 32-bit machine

currently i am facing two problem with 11.04

1) after the login screen as soon as the desktop window opens after few minutes the task-bar and the side panel display gets distorted.
for preview i have attached picture.

2) after upgrading from 10.10 to 11.04 during boot-up there is no option regarding the boot-up option, it just boots up with Ubuntu and i am not able to use windows 7

one more problem i am facing is that i am not able to install 11.04 on my laptop which is 64-bit machine
after the booting up from the live-CD( ubuntu-64Bit), as soon as i select the language menu the screen goes off blank and there is no display but laptop is still running.

kindly please revert on this as soon as possible

---

### Post by Hedgehog1 on 2011-05-11
> **kafunit said:**
> 2) after upgrading from 10.10 to 11.04 during boot-up there is no option regarding the boot-up option, it just boots up with Ubuntu and i am not able to use windows 7

kafunit,

On this PC, please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

This will give us enough information to help you boot into Windows 7 as well.

***The Hedge***

:KS

---

### Post by kafunit on 2011-05-12
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 9fo.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for cbh.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046    35,160,063    35,158,018   5 Extended
/dev/sda5               2,048    33,327,103    33,325,056  83 Linux
/dev/sda6          33,329,152    35,160,063     1,830,912  82 Linux swap / Solaris
/dev/sda2          40,962,048   156,301,311   115,339,264   7 HPFS/NTFS
/dev/sda3          35,160,064    40,962,047     5,801,984  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   204,802,047   204,595,200   7 HPFS/NTFS
/dev/sdb3         204,802,048   368,642,047   163,840,000   7 HPFS/NTFS
/dev/sdb4         368,642,048   488,394,751   119,752,704   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        586EA31D5377CBCE                       ntfs                                     
/dev/sda3        823f68b3-e44d-439d-850e-f599758c0a7b   swap                                     
/dev/sda5        79437bb5-e6b8-4a67-bcca-091ead342e8b   ext4                                     
/dev/sda6        962b70f0-5c85-4f46-8fe0-80cd1a0b2307   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D8186E37186E1532                       ntfs       System Reserved               
/dev/sdb2        8CD477ABD47795E4                       ntfs                                     
/dev/sdb3        B260730A6072D517                       ntfs       MEDIA FILES                   
/dev/sdb4        9C5C7D0A5C7CE086                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 79437bb5-e6b8-4a67-bcca-091ead342e8b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 79437bb5-e6b8-4a67-bcca-091ead342e8b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 79437bb5-e6b8-4a67-bcca-091ead342e8b
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=79437bb5-e6b8-4a67-bcca-091ead342e8b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 79437bb5-e6b8-4a67-bcca-091ead342e8b
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=79437bb5-e6b8-4a67-bcca-091ead342e8b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 79437bb5-e6b8-4a67-bcca-091ead342e8b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 79437bb5-e6b8-4a67-bcca-091ead342e8b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root D8186E37186E1532
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=79437bb5-e6b8-4a67-bcca-091ead342e8b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=962b70f0-5c85-4f46-8fe0-80cd1a0b2307 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.38-8-generic
   2.4GB: boot/vmlinuz-2.6.38-8-generic
   1.7GB: initrd.img
   2.4GB: vmlinuz

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  31 54 7e 55 f0 c8 84 29  ab 8a 3b 13 61 5f 85 bc  |1T~U...)..;.a_..|
00000010  e2 f4 b0 29 c9 5a bd 59  68 68 4b 7f e8 e6 3e 51  |...).Z.YhhK...>Q|
00000020  fe b5 9c 2d 56 2a ca 71  12 4f 8a 33 61 30 59 41  |...-V*.q.O.3a0YA|
00000030  ab 2a 62 d1 83 1c c9 32  9b cb a2 05 0e 62 aa 92  |.*b....2.....b..|
00000040  b8 09 ad e4 fa 27 a2 39  da a1 8f 87 99 0c 85 24  |.....'.9.......$|
00000050  e4 53 af 05 a8 7b bb f4  d9 f1 e2 c2 a5 f6 6b 16  |.S...{........k.|
00000060  4c d1 43 81 dc 72 07 a1  65 f1 7e c9 75 1e 6e 09  |L.C..r..e.~.u.n.|
00000070  4a 25 4b f3 14 8e ce ac  a1 74 0a ce 7d b5 bd 7a  |J%K......t..}..z|
00000080  87 7c e1 e1 22 45 aa 81  6a 8a 99 2f fa 9b cf 19  |.|.."E..j../....|
00000090  de 3a a7 56 40 20 98 d4  0e e2 a6 1d ae cb a9 e4  |.:.V@ ..........|
000000a0  f3 ba 31 18 a9 d3 32 28  50 5d b8 50 20 5c 96 51  |..1...2(P].P \.Q|
000000b0  2d e0 78 3e 85 ed 61 fc  3b 4f 1f 06 d6 b8 43 80  |-.x>..a.;O....C.|
000000c0  64 df ad a3 90 03 36 b5  13 8e 43 1f 00 0d da 03  |d.....6...C.....|
000000d0  76 42 3a 80 9c b7 9f 81  ad 64 82 67 8b d3 30 93  |vB:......d.g..0.|
000000e0  20 94 8f a5 c1 22 ab 91  a0 cb 3a 1d 23 87 fc b8  | ...."....:.#...|
000000f0  29 59 fb 0b e6 bd c4 89  bc 30 5d 3d a0 59 95 f4  |)Y.......0]=.Y..|
00000100  07 da 78 24 e3 9c 89 7a  d1 6c c7 7d f0 76 6e d3  |..x$...z.l.}.vn.|
00000110  5b 48 58 46 78 b0 fe 20  76 d8 77 c0 91 a6 c6 de  |[HXFx.. v.w.....|
00000120  e0 55 42 3d ac 97 34 4e  25 6d c7 43 24 af e7 f6  |.UB=..4N%m.C$...|
00000130  5f 8d 8c f0 e3 3d e7 c4  21 4f 72 65 a6 c5 0a 0e  |_....=..!Ore....|
00000140  5a 9f 19 63 56 f5 73 cd  f6 8b 14 9f fe 71 16 35  |Z..cV.s......q.5|
00000150  3f 79 45 2b 9d 20 53 f2  63 86 d2 dc 3f 9d 61 45  |?yE+. S.c...?.aE|
00000160  28 85 ab f1 f6 36 df 02  33 c2 f8 39 99 c6 30 60  |(....6..3..9..0`|
00000170  f0 ca eb 2b 82 07 47 32  ba 25 ed ed 18 91 0a 6c  |...+..G2.%.....l|
00000180  43 e3 1d 41 37 14 8e 6e  7d 78 4f 09 7e ec 1f 7a  |C..A7..n}xO.~..z|
00000190  c5 05 ad be 1c 21 b0 c6  8f 87 8a 2d e6 bf 7b a5  |.....!.....-..{.|
000001a0  2e d4 00 a5 43 bb cb 8d  3b ca e9 64 56 8d b6 f8  |....C...;..dV...|
000001b0  98 8e 78 dc 6b 17 20 1f  f7 96 de 4c 79 5d 00 20  |..x.k. ....Ly]. |
000001c0  21 00 83 fe ff ff 02 00  00 00 00 80 fc 01 00 fe  |!...............|
000001d0  ff ff 05 fe ff ff 02 80  fc 01 00 f8 1b 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Hedgehog1 on 2011-05-12
If you have not already done so, please download the ISO and make a LiveCD/LiveUSB of Ubuntu 11.04.

Boot from the LiveCD/LiveUSB, select 'TRY' and then do these step to reload grub in the proper partition:


```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Then you can reboot and you should get the grub menu again, and be presented with Windows 7 as a boot option.

***The Hedge***

:KS

p.s. **If you have a mix of IDE and SATA hard drives, and the above commands do not fix the reboot**, you may need to reverse the device letters to match the possible reversing of the 80 and 500 gig drives at boot time.

The reversed commands would be:

```
sudo mount /dev/sdb5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sdb
```

---

