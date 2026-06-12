---
title: "Grub won't load after 10.10 upgrade."
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by markprovan on 2010-09-27
I had installed Ubuntu 10.04 within Windows 7 and everything work perfect until this morning. When I turned my laptop on I was told that Grub could'nt find the storage device and was presented with a grub command line.

I am posting from the Live CD.

Any suggestions?

---

### Post by Rubi1200 on 2010-09-27
Yes, 
post the results of the bootscript linked at the bottom of my post.

And welcome to the forums :-)

---

### Post by gpaccola on 2010-09-29
Had the same problem here, im copying the RESULT.txt below, im very thankful for any help u can provide.

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065   976,768,064   976,752,000   f W95 Ext d (LBA)
/dev/sdc5              16,128   976,768,064   976,751,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1c675268-46b9-4508-a9cb-439434b09d69   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f43d5f2c-7d6d-4c30-bf08-2e387b27517d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BC8CCE458CCDF9C2                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc5        94C4494CC4493232                       ntfs       3                             
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/1c675268-46b9-4508-a9cb-439434b09d69 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
set locale_dir=($root)/boot/grub/locale
set lang=pt
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
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=1c675268-46b9-4508-a9cb-439434b09d69 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    echo    'Loading Linux 2.6.35-19-generic ...'
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=1c675268-46b9-4508-a9cb-439434b09d69 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1c675268-46b9-4508-a9cb-439434b09d69 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1c675268-46b9-4508-a9cb-439434b09d69 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1c675268-46b9-4508-a9cb-439434b09d69 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1c675268-46b9-4508-a9cb-439434b09d69 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1c675268-46b9-4508-a9cb-439434b09d69
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set bc8cce458ccdf9c2
    drivemap -s (hd0) ${root}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1c675268-46b9-4508-a9cb-439434b09d69 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f43d5f2c-7d6d-4c30-bf08-2e387b27517d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  73.1GB: boot/grub/core.img
  47.3GB: boot/grub/grub.cfg
  73.1GB: boot/initrd.img-2.6.32-21-generic
  73.5GB: boot/initrd.img-2.6.32-24-generic
    .7GB: boot/initrd.img-2.6.35-19-generic
  73.1GB: boot/vmlinuz-2.6.32-21-generic
  73.5GB: boot/vmlinuz-2.6.32-24-generic
  73.2GB: boot/vmlinuz-2.6.35-19-generic
    .7GB: initrd.img
  73.2GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  93 ae 7b f7 c3 25 a6 34  7b 0c 43 a3 ac 8f 4e 76  |..{..%.4{.C...Nv|
00000010  5a 3c 51 f4 95 50 e0 5b  7c 09 7d 5e a0 44 1e e8  |Z<Q..P.[|.}^.D..|
00000020  3c b6 2b 5b 30 0d a6 b6  d5 87 03 9a 18 ff 2f f5  |<.+[0........./.|
00000030  e9 2a 7d e4 d4 29 81 54  9c 1e 4a 9a 25 30 2f 30  |.*}..).T..J.%0/0|
00000040  89 5a 1b 44 a6 8c 9e 2c  0c b3 d7 cf 9d df dc 6f  |.Z.D...,.......o|
00000050  2e 4c 34 b4 ce 1a 35 bf  53 2b 15 31 93 3e a9 32  |.L4...5.S+.1.>.2|
00000060  33 16 83 da eb 3b 2c 33  ea 65 c6 30 8d e5 d9 b8  |3....;,3.e.0....|
00000070  04 6a 94 f6 d6 23 34 4a  c9 de 56 b4 f0 65 04 53  |.j...#4J..V..e.S|
00000080  dc aa f8 4d 1a 4c ed cc  60 d4 20 97 a7 78 5a b7  |...M.L..`. ..xZ.|
00000090  39 13 b9 38 d7 3e fd 4f  07 a8 e7 7f 77 5a ef 26  |9..8.>.O....wZ.&|
000000a0  2d 04 d5 b6 df 34 3c bb  28 42 5d a9 05 18 8d 65  |-....4<.(B]....e|
000000b0  1c 78 c7 9e 9e c9 b5 6f  e4 fa 5f b9 8b 52 89 b0  |.x.....o.._..R..|
000000c0  73 85 7c 3c 88 2d ce 5d  2b c6 db af 0f bd 2a 72  |s.|<.-.]+.....*r|
000000d0  da dd d4 76 85 4f c2 76  af 7b ab 94 e7 14 bb 79  |...v.O.v.{.....y|
000000e0  64 db 9c 5b 7c b7 57 17  cd 72 c0 c1 3c 53 32 e0  |d..[|.W..r..<S2.|
000000f0  af 09 9f fc 67 17 b3 0b  57 31 84 1d 9e 6d 47 fb  |....g...W1...mG.|
00000100  e8 04 2d a6 bd f8 88 32  a8 34 91 2b 98 73 e6 23  |..-....2.4.+.s.#|
00000110  6d 59 1a 22 52 36 a6 82  0a 9b bc 11 d0 c3 3f 86  |mY."R6........?.|
00000120  86 33 5e 93 75 93 4e 1e  58 0e 28 ec 65 19 17 6b  |.3^.u.N.X.(.e..k|
00000130  a6 6b 86 75 ef ed 55 bd  4e 2a 20 99 70 f1 42 81  |.k.u..U.N* .p.B.|
00000140  2a f2 76 42 ed c3 d3 5b  3b 64 0e 3d fd 3c e0 5f  |*.vB...[;d.=.<._|
00000150  64 6b de 32 5a 50 de 45  c7 47 68 c4 f5 0d c2 5b  |dk.2ZP.E.Gh....[|
00000160  83 86 5f 64 cb 45 27 0b  be f8 e8 74 65 8f 84 63  |.._d.E'....te..c|
00000170  7e de 7f 37 09 0d bf 14  02 63 9e 9e 82 fc 7e e2  |~..7.....c....~.|
00000180  fc 18 72 e3 a7 d1 32 4e  ae b6 f2 99 92 03 2c 28  |..r...2N......,(|
00000190  9c 8c c9 be 8e 5e 7a de  37 2d b1 1f 65 0a a3 8a  |.....^z.7-..e...|
000001a0  df b8 b7 87 b4 2c 13 53  a8 80 13 6e bd 75 ea 75  |.....,.S...n.u.u|
000001b0  12 45 70 cc d3 8a 3b 48  4a 22 15 07 26 4f 00 fe  |.Ep...;HJ"..&O..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



---

### Post by psusi on 2010-09-29
Your subject says you upgraded to 10.10, but the body of your post says you were running 10.04 and then suddenly this happened.  Which is it?  Did you upgrade to 10.10 or not?  It looks like you did upgrade to 10.10.  Did this happen immediately after the upgrade, or did it work for a while, and then fail today?  What EXACTLY does grub say when you try to boot?

---

### Post by strange_cathect on 2010-10-15
There is definitely a serious problem that is in the upgrade process. It affects people who have two hard drives. 

I am having this problem after an upgrade to 10.10 from 10.04. (This also happened to me when I upgraded to 10.04).

After completing the upgrade, and rebooting, I get the error message: 

> error: the symbol 'grub_xputs' not found.
grub rescue>

---

