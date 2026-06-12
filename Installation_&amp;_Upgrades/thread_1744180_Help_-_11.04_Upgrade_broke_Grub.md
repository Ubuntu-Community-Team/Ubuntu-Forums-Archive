---
title: "Help - 11.04 Upgrade broke Grub"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by eakergd on 2011-04-30
I am working from a live cd now - upgraded last night and I can no longer boot. I have seen other tutorials for fixing this from a live cd, but I have 2 HDDs with Vista on sda (I only use it for gaming - don't look down your nose at me :-) ) and ubuntu on sdb. I haven't seen any instructions on how to fix grub with this configuration. Sda2 is my boot partition, since the original HDD has a hidden partition for reinstalling Vista (sda1).

Could someone please tell me how to fix grub from a live cd with this configuration? I don't want to lose my Vista partition, and I really need the files on my Ubuntu Home partition, so a wipe and reinstall at this point is not an option. Below is the output of my fdisk -l command.  Thanks in advance.

Gary


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12289693+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1531       20987   156284928    7  HPFS/NTFS
/dev/sda3           20987       38914   143994880    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5           20987       38914   143993856    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00019497

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29273   235126784   83  Linux
/dev/sdb2           29273       30402     9069569    5  Extended
/dev/sdb5           29273       30402     9069568   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by dino99 on 2011-04-30
what do you mean "broke" grub ? 

If you mean it dont boot when you select ubuntu boot line, then it might be due to wrong uuid

from a terminal: sudo blkid
will give you the uuids

only edit the grub boot line and change the wrong uuid by the good one, then ctrl+x to boot

If its not the case, then you need to reinstall grub from livecd

---

### Post by Quackers on 2011-04-30
Which hard drive is set to boot first in your bios?

---

### Post by eakergd on 2011-04-30
Sorry I wasn't more specific. What I mean by "broke grub" is that I get no grub menu. When I boot from my hdd, I get a black screen with a blinking cursor in the top left - no grub menu - nothing.

I realize I probably need to reinstall grub from the live cd. I need help with that, please. I have seen tutorials, but they say to mount certain partitions if you have a separate boot partition. Does my windows partition which is set as my boot partition fall into that category?

Do I need to chroot with this configuration? Which partitions do I need to mount?

---

### Post by eakergd on 2011-04-30
> **Quackers said:**
> Which hard drive is set to boot first in your bios?

sda2 is set as my boot partition -- that is where Vista resides.

---

### Post by ajgreeny on 2011-04-30
Click on the boot-info-script entry in my signature and follow all the instructions there to copy the RESULTS.txt file back here.

I am sure that I, or someone else will be able to help you get grub back.

---

### Post by eakergd on 2011-04-30
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,579,449    24,579,387  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     24,580,096   337,149,951   312,569,856   7 HPFS/NTFS
/dev/sda3         337,149,952   625,139,711   287,989,760   f W95 Ext d (LBA)
/dev/sda5         337,152,000   625,139,711   287,987,712   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   470,255,615   470,253,568  83 Linux
/dev/sdb2         470,257,662   488,396,799    18,139,138   5 Extended
/dev/sdb5         470,257,664   488,396,799    18,139,136  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D476-EF15                              vfat       RECOVERY                      
/dev/sda2        009A8AAE9A8A9FB0                       ntfs       Vista64                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4EE2C7F3E2C7DCF9                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        75c04589-cbd2-419b-b184-a716feb69d78   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        5511e5ed-5e8d-4383-bd0e-9e35cee5f157   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/stage2

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=75c04589-cbd2-419b-b184-a716feb69d78 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5511e5ed-5e8d-4383-bd0e-9e35cee5f157 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  79.6GB: boot/grub/core.img
  62.6GB: boot/grub/grub.cfg
  11.2GB: boot/initrd.img-2.6.32-25-generic
  11.0GB: boot/initrd.img-2.6.35-28-generic
  11.8GB: boot/initrd.img-2.6.38-8-generic
  17.8GB: boot/initrd.img-2.6.38-8-generic-pae
  79.8GB: boot/vmlinuz-2.6.32-25-generic
  85.9GB: boot/vmlinuz-2.6.35-28-generic
 139.3GB: boot/vmlinuz-2.6.38-8-generic
 139.4GB: boot/vmlinuz-2.6.38-8-generic-pae
  17.8GB: initrd.img
  11.8GB: initrd.img.old
 139.4GB: vmlinuz
 139.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 38 5b 44 09  |............8[D.|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  89 52 00 00 48 0b 00 00  25 05 00 11 93 52 00 00  |.R..H...%....R..|
00000010  2a 0e 00 00 01 00 04 00  00 00 00 00 44 08 1f 00  |*...........D...|
00000020  10 01 01 10 b9 1b 00 00  3a 0b 00 00 10 01 01 10  |........:.......|
00000030  a2 52 00 00 48 0b 00 00  25 05 00 11 a7 52 00 00  |.R..H...%....R..|
00000040  2a 0e 00 00 01 00 04 00  00 00 00 00 44 08 21 00  |*...........D.!.|
00000050  10 01 01 10 bf 52 00 00  3a 0b 00 00 10 01 01 10  |.....R..:.......|
00000060  41 1b 00 00 48 0b 00 00  25 05 00 11 c4 52 00 00  |A...H...%....R..|
00000070  2a 0e 00 00 01 00 04 00  00 00 00 00 44 08 23 00  |*...........D.#.|
00000080  10 01 01 10 75 19 00 00  3a 0b 00 00 10 01 01 10  |....u...:.......|
00000090  7a 19 00 00 48 0b 00 00  25 05 00 11 d0 52 00 00  |z...H...%....R..|
000000a0  2a 0e 00 00 01 00 03 00  00 00 00 00 44 08 24 00  |*...........D.$.|
000000b0  10 01 02 10 e6 52 00 00  e5 37 00 00 25 05 00 11  |.....R...7..%...|
000000c0  f8 52 00 00 2a 0e 00 00  01 00 04 00 00 00 00 00  |.R..*...........|
000000d0  44 08 26 00 10 01 01 10  c3 11 00 00 3a 0b 00 00  |D.&.........:...|
000000e0  10 01 01 10 01 53 00 00  48 0b 00 00 25 05 00 11  |.....S..H...%...|
000000f0  06 53 00 00 2a 0e 00 00  01 00 04 00 00 00 00 00  |.S..*...........|
00000100  44 08 28 00 10 01 01 10  7c 17 00 00 3a 0b 00 00  |D.(.....|...:...|
00000110  10 01 01 10 16 53 00 00  48 0b 00 00 25 05 00 11  |.....S..H...%...|
00000120  1b 53 00 00 2a 0e 00 00  01 00 04 00 00 00 00 00  |.S..*...........|
00000130  44 08 2a 00 10 01 01 10  20 0e 00 00 3a 0b 00 00  |D.*..... ...:...|
00000140  10 01 03 10 2c 53 00 00  48 0b 00 00 25 05 00 11  |....,S..H...%...|
00000150  36 53 00 00 2a 0e 00 00  01 00 04 00 00 00 00 00  |6S..*...........|
00000160  44 08 2c 00 10 01 01 10  51 1a 00 00 3a 0b 00 00  |D.,.....Q...:...|
00000170  10 01 01 10 83 1a 00 00  48 0b 00 00 25 05 00 11  |........H...%...|
00000180  47 53 00 00 2a 0e 00 00  01 00 04 00 00 00 00 00  |GS..*...........|
00000190  44 08 2e 00 10 01 01 10  51 1a 00 00 3a 0b 00 00  |D.......Q...:...|
000001a0  10 01 01 10 63 53 00 00  48 0b 00 00 25 05 00 11  |....cS..H...%...|
000001b0  68 53 00 00 2a 0e 00 00  01 00 04 00 00 00 00 fe  |hS..*...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 14 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by eakergd on 2011-04-30
Bump - anyone?

---

### Post by Quackers on 2011-04-30
You didn't answer my previous question. Which hard drive (not partition) is set to boot first in your bios?

The file in red below needs to be removed from the Windows root.
```

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #1 for (,msdos1)/boot/grub.
=> No boot loader is installed in the MBR of /dev/sdb

sda1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Vista: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /bootmgr /boot/bcd [COLOR="Red"]/boot/grub/core.img[/COLOR]
```

You can then boot from a live cd/usb and run the following commands to re-install grub2
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
PLEASE NOTE that the above is only good if the first boot device in your bios is /dev/sda (which is the 320GB drive).

---

### Post by eakergd on 2011-04-30
OK, I've been using linux for 2 years now and this is the one stupid thing that continues to drive me nuts. I don't understand the relationship of how linux sees my physical drives - just when I think I have it figured out, something like this comes up to let me know that I don't.

I have 2 drives in the system. Drive hdd0 is the drive that the computer boots off of. On that drive are three partitions. In the first partition is hidden, and is set up as a rescue partition for reloading windows. The second partition is set as the boot partition, and that is the partition that Vista resides on. The third partition is segmented off as a place to store data.

On my second drive - hdd1, which the linux sees as sdb, there are three linux partitions.

So I go into the windows root directory, which I think is the one that appears in nautilis as a separate drive called vista 64. When I am in it, the location bar in nautilis reads /media/Vista64. There is a folder called "boot", but there is no folder underneath it called "grub" and I cannot find a file called "core.img".

If I back up in the nautilis location bar to just "/", there is also a folder called "boot", and under that there is a folder called "grub", but still no "core.img".

So where am I supposed to look to remove this "core.img"?

P.S. I lgrew very dissatisfied with windows and I really like linux, but this is freakin' frustrating. I upgraded windows from 3.0 to XP and never had this crazy problem. Somebody in the linux world needs to get it together if they ever want linux to go mainstream on the desktop. It's hard to tell all my buddies how great it is when (what should be) a simple upgrade breaks my system.

OK, I'm done ranting. Please help?

Thanks.

---

### Post by eakergd on 2011-04-30
Here is what happened when I went ahead and tried the grub re-install:


ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=mnt /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for mnt/boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$

---

### Post by Quackers on 2011-04-30
In your Windows root there should be just one folder called boot. This folder should have a load of Language folders and a BCD file and a BCD.log file and a few others. Do you have more than one folder called boot?
If not, in that folder called boot, is there another one called boot as well?

---

### Post by eakergd on 2011-04-30
That is the folder I went into. It had the BCD log files, but there was no grub folder to be found there. It had all the language folders, too - so that is probably the one I should have been in. Is it possible that the installer deleted the grub folder? I seem to remember a year ago when I switched to 10.04 I had a similar problem and I had to switch back to the old version of grub to get everything working.

---

### Post by Quackers on 2011-04-30
So where was it then? Or is it a secret?

---

### Post by eakergd on 2011-04-30
I never found it -- still can't find it. I think the aliens took it.

---

### Post by eakergd on 2011-04-30
OK, I found that grub folder with the .img files. It is on my partition that has the ubuntu install -- sdb, not sure which partition, though. Looks like my root folder though -- bin, mnt, home folders are all there.

---

### Post by Quackers on 2011-04-30
NO!!! Leave that one!
The file you want to delete is on sda1 not Ubuntu - as stated earlier.

---

### Post by eakergd on 2011-04-30
OK -- but how do I get to sda1 if it is a hidden partition? It doesn't show up in nautilis.

---

### Post by Quackers on 2011-04-30
It isn't hidden from Linux. It shows up on the boot script. Does it show in gparted? I'm not absolutely sure though, how to get to it. 
No matter, that can be fixed later with a Windows repair/installation disc. Do you have one?
The sbin probe error may be because core.img is in the wrong place.
You will need to purge then re-install grub following the CHROOT section of the guide below. The partition to mount is /dev/sdb1 and the place to install grub is /dev/sda
As you don't have a separate Ubuntu /boot partition you don't need to mount it.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by eakergd on 2011-04-30
OK - grub is fixed. Thank you. 

New problem - now it boots to the UBUNTU splash screen and hangs.

So I entered recovery mode and followed the prompts - before I did that, it at least showed the word ubuntu. Now I just get a purple screen and nothing.

Thanks for your help so far.

---

### Post by mabloom on 2011-05-01
I have a similar problem on a system with a virgin /dev/sda containing a windows instalation and a /dev/sdb that had contained a Linux Ubuntu 10.10 installation.

My posting on the problem is at: [[COLOR="DarkRed"]_update sets root device in /dev/sdb1's grub.cfg to open hd0,msdos2 to look for grub modules_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10746956&postcount=1")

Updating a self contained /dev/sdb should not change the config files on sdb to think the root is on /dev/sda2! (especially when /dev/sda2 is a pure untouched Windows system that knows nothing of Linux! (sda1 being an ASUS Windows recovery partition))

Even after correcting that, there are other problems that prevent bringing the system up, which I haven't traced down yet, but this is a configuration type that I think the Ubuntu developers should be testing, and obviously have not been.

---

### Post by Quackers on 2011-05-01
mabloom please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

