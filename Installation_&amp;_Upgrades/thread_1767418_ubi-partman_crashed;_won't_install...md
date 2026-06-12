---
title: "ubi-partman crashed; won't install.."
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by lmn. on 2011-05-25
Hi,

this morning I installed warsow, happily playing for 30 mins or so until ubuntu locks up.
you know the drill, restart, busybox blahblahblahh.. your install is broken and there isn't much you can do about it.

so yeh now that I try to reinstall, theres an error by the name of  'ubi-partman failed to load /crashed with error/exit level 10' and the  install process doesn't show a progress bar and appears not to be  installing at all..?

tried with cd & usb, and with 2 different copies of the ISO, same problem

windows sucks, please help me get back into ubuntu! 

cheers.

---

### Post by lmn. on 2011-05-25
any ideas?
booting into recovery mode just takes me to busybox..

remembering an error as something like;
file modified in /init/... try -bootargs

probably doesn't help

---

### Post by lmn. on 2011-05-28
figured my best option was to ditch 11.04 & to try 11.10

..installed fine, but the boot option doesn't show in grub. super grub disk or rescuetux don't change anything

any help/known solutions much appreciated, thanks..

---

### Post by Hedgehog1 on 2011-05-28
We need to get a look at your install to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by lmn. on 2011-05-28
thanks hedge, will report back in 10 :D

---

### Post by lmn. on 2011-05-28
ok here they are;

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 1e566b75-bec8-45dc-b678-e2f3b9e0a53a root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 82204bb3-2f46-4f99-8d43-f60ce199b690 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 2129360 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu oneiric (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sdc5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     2,541,109     2,539,062   b W95 FAT32
/dev/sda2           2,541,566     7,829,503     5,287,938   5 Extended
/dev/sda5           2,541,568     4,509,695     1,968,128  83 Linux
/dev/sda6           4,511,744     4,814,847       303,104  82 Linux swap / Solaris
/dev/sda7           4,816,896     7,829,503     3,012,608  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848 1,945,137,151 1,944,930,304   7 NTFS / exFAT / HPFS
/dev/sdb3       1,945,139,198 1,953,523,711     8,384,514   5 Extended
/dev/sdb5       1,945,139,200 1,953,523,711     8,384,512  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,053,692,260 1,053,690,213  83 Linux
/dev/sdc2       1,053,693,950 1,250,263,039   196,569,090   5 Extended
/dev/sdc5       1,053,693,952 1,241,876,479   188,182,528  83 Linux
/dev/sdc6       1,241,878,528 1,250,263,039     8,384,512  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2EFC-15F8                              vfat       
/dev/sda5        d187d52b-2610-48d2-a6c5-0e8ec59c5d2a   ext4       
/dev/sda6        193ec78f-b50c-4c35-8227-3c478ed542d9   swap       
/dev/sda7        508dafd5-7916-47e9-9b21-ff91aa03b146   ext4       
/dev/sdb1        5C687770687747B2                       ntfs       System Reserved
/dev/sdb2        3E9851269850DE49                       ntfs       
/dev/sdb5        258ddd33-4e7d-4226-934a-2e2c9a1c601d   swap       
/dev/sdc1        34dac116-ab16-4f02-a107-4b8682cbdd86   ext4       ||
/dev/sdc5        1e566b75-bec8-45dc-b678-e2f3b9e0a53a   ext4       
/dev/sdc6        79cef149-a708-47af-ab00-08c17777cc88   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda5        /media/d187d52b-2610-48d2-a6c5-0e8ec59c5d2a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/508dafd5-7916-47e9-9b21-ff91aa03b146 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sda1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry6 
menu label Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry7 
menu label Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- 
 
label ubnentry8 
menu label Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- 
 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
menuentry 'Ubuntu, with Linux 2.6.39-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio

    linux    /boot/vmlinuz-2.6.39-3-generic root=/dev/sdc5 ro   splash quiet vt.handoff=7
    initrd    /boot/initrd.img-2.6.39-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio

    echo    'Loading Linux 2.6.39-3-generic ...'
    linux    /boot/vmlinuz-2.6.39-3-generic root=/dev/sdc5 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.39-3-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {

    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {

    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d187d52b-2610-48d2-a6c5-0e8ec59c5d2a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=508dafd5-7916-47e9-9b21-ff91aa03b146 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=193ec78f-b50c-4c35-8227-3c478ed542d9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.322246552 = 1.419751424    boot/grub/core.img                             1
   1.399417877 = 1.502613504    boot/grub/grub.cfg                             1
   1.303558350 = 1.399685120    boot/initrd.img-2.6.39-3-generic               3
   1.809974670 = 1.943445504    boot/vmlinuz-2.6.39-3-generic                  1
   1.303558350 = 1.399685120    initrd.img                                     3
   1.809974670 = 1.943445504    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  97 85 a8 04 44 99 ab f9  19 7d 2b 94 e3 32 1c 7f  |....D....}+..2..|
00000010  59 be f2 39 77 5a f5 3a  cf b9 73 fd 60 d5 03 69  |Y..9wZ.:..s.`..i|
00000020  9c da b3 e3 66 4b cd 85  9a d7 0b ed 35 2b 9c ff  |....fK......5+..|
00000030  56 9e 15 91 35 45 d6 28  06 04 42 33 91 44 a6 ae  |V...5E.(..B3.D..|
00000040  5f 69 7d 22 90 e2 48 7b  4c 4c e7 88 24 16 42 45  |_i}"..H{LL..$.BE|
00000050  cc c8 26 6a c7 d5 d0 1a  fb c1 0a 6d 25 ab 52 b6  |..&j.......m%.R.|
00000060  1f d8 98 12 75 c7 fa c0  fb d0 3e b3 c6 f6 5b 1b  |....u.....>...[.|
00000070  cd 13 5b c8 66 cd 31 95  99 0b 2d 35 88 d7 61 8d  |..[.f.1...-5..a.|
00000080  76 a6 b5 09 31 ac 06 69  dc 47 d6 68 53 5a a3 fd  |v...1..i.G.hSZ..|
00000090  67 1d 51 19 63 80 46 5e  94 d6 15 5f 60 11 a9 33  |g.Q.c.F^..._`..3|
000000a0  da e2 d6 d9 dc bd a6 16  f3 c4 0d 11 cf 6c 11 ea  |.............l..|
000000b0  8b 45 e3 b8 98 60 28 44  68 70 5a a9 a2 1f 7b d4  |.E...`(DhpZ...{.|
000000c0  16 a7 60 11 da b8 8b 6c  68 6c 0c 12 a9 45 29 7c  |..`....lhl...E)||
000000d0  45 6d f1 73 17 61 3f 2c  42 7e 59 14 42 e3 0f f2  |Em.s.a?,B~Y.B...|
000000e0  d4 d1 8b b0 fd 8b 72 4c  c4 e2 05 d4 78 52 c4 55  |......rL....xR.U|
000000f0  a8 47 8c 8f c5 e8 2f 2c  46 1b 7e f1 78 55 5d 22  |.G..../,F.~.xU]"|
00000100  51 8c af aa 0e 51 1b 83  64 31 ca b8 c5 68 ef 2f  |Q....Q..d1...h./|
00000110  de a6 66 6e 49 64 f3 18  2d 6c 83 c5 28 ff 16 67  |..fnId..-l..(..g|
00000120  0b 2d 65 c6 42 91 39 c2  58 59 ce 97 08 8d 45 8a  |.-e.B.9.XY....E.|
00000130  bd 7d 15 32 6a 09 fa 42  4b 48 de 8e 5a 25 24 52  |.}.2j..BKH..Z%$R|
00000140  6a 65 4c 9e 7a c5 fa 5b  82 7e dc 12 4b a9 48 48  |jeL.z..[.~..K.HH|
00000150  02 36 a0 09 5b a9 e4 99  ca b9 8a 76 c7 12 17 25  |.6..[......v...%|
00000160  7d 43 fe f6 54 8d 03 ca  18 2e 45 7b 76 09 8e ff  |}C..T.....E{v...|
00000170  92 a3 34 fe a3 72 83 5a  f1 b6 75 78 c6 a6 e2 ea  |..4..r.Z..ux....|
00000180  bf 14 e5 c5 d2 7e ca 32  73 ae 89 50 32 5f 64 cc  |.....~.2s..P2_d.|
00000190  33 3e c8 52 f4 97 97 a2  fc 5f 2a 53 89 9b b3 10  |3>.R....._*S....|
000001a0  4d 1a d1 a0 3a 63 89 2d  45 de 5d 8a fa 6f e9 d1  |M...:c.-E.]..o..|
000001b0  ea fe 99 b9 70 81 68 1e  3d 0d c9 c7 a6 5e 00 34  |....p.h.=....^.4|
000001c0  17 9e 83 b6 5e 18 02 00  00 00 00 08 1e 00 00 b6  |....^...........|
000001d0  5f 18 05 b5 4a 2b 02 08  1e 00 00 a8 04 00 00 00  |_...J+..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb3

00000000  98 a9 fe 40 0f ad 0f 4d  d8 73 79 1c a6 91 a0 d8  |...@...M.sy.....|
00000010  dd 0c c3 ae e9 d1 0f ef  3c cd d7 fe f9 c5 74 da  |........<.....t.|
00000020  27 c3 0f 10 ea 8e 49 d4  2d 26 b1 8c 6e 7b 98 67  |'.....I.-&..n{.g|
00000030  41 18 1e 9b 88 c6 7d ba  d7 61 37 c1 e9 d6 e1 6d  |A.....}..a7....m|
00000040  cd ed 8c 2a 06 58 a5 b9  98 a8 fc 0f 5a d6 d3 be  |...*.X......Z...|
00000050  1b f8 62 d6 c9 e3 fe d2  d6 c1 4e 5e 75 b3 11 c4  |..b.......N^u...|
00000060  0f d0 83 8a 89 55 8f 71  6a ef 6d ce 1f 4f f8 75  |.....U.qj.m..O.u|
00000070  60 8e 5e 59 74 86 8a 39  0a c8 cf a8 86 65 f4 24  |`.^Yt..9.....e.$|
00000080  0f e9 9a 5b ad 37 e1 ee  96 5a 2b e7 bb 9e 40 d8  |...[.7...Z+...@.|
00000090  2b 65 6a ce 31 ea 18 95  af 49 f0 f7 80 3f 79 fd  |+ej.1....I...?y.|
000000a0  b3 a7 44 b2 c5 6d 1f 49  c2 19 a5 39 fb e9 21 5e  |..D..m.I...9..!^|
000000b0  4f b0 18 15 bb 71 a1 79  fa 14 f7 ed 6b a8 5c c2  |O....q.y....k.\.|
000000c0  89 89 85 e6 a6 a4 42 48  e4 e0 81 9f 6a c5 e2 20  |......BH....j.. |
000000d0  9e e3 50 9b 47 9c f8 77  c3 df 0d f5 4b 53 fd 9a  |..P.G..w....KS..|
000000e0  ba e5 cc f8 c8 44 d3 a6  40 07 72 c4 82 bf ad 6f  |.....D..@.r....o|
000000f0  e9 df 08 6c 6e d8 9f ed  53 6f 19 19 55 9b 0a e7  |...ln...So..U...|
00000100  3d b6 b0 06 b4 24 be d2  2c 60 b5 b4 d3 75 7d 81  |=....$..,`...u}.|
00000110  7e 64 31 dc 22 4b 1b 01  cf ce c0 29 cd 4d a8 78  |~d1."K.....).M.x|
00000120  b3 4f 99 26 b9 9b 55 d6  64 bb 97 19 ba 4b b4 95  |.O.&..U.d....K..|
00000130  d4 0f e1 05 b0 14 7f bb  59 bc 44 be c9 af b1 5b  |........Y.D....[|
00000140  b6 5a f0 97 c1 cf 0f 8b  80 b7 36 f2 ea 6a 1b 0e  |.Z........6..j..|
00000150  b1 c6 63 54 1e a4 9e 0f  d2 ba bd 3b c0 9e 0f d2  |..cT.......;....|
00000160  b5 54 bc 3e 10 b1 92 da  3f dd cd bf 4d 9a 6c b1  |.T.>....?...M.l.|
00000170  fb b8 da 70 0f 5e c6 bc  33 59 f1 bd c3 5e 4d 06  |...p.^..3Y...^M.|
00000180  93 ad 6b 28 ce ff 00 24  4d 19 98 39 f5 24 1c 83  |..k(...$M..9.$..|
00000190  f4 cd 5b f1 17 8d 3e 23  c3 a6 96 bb f1 9d c7 87  |..[...>#........|
000001a0  e2 78 42 08 a4 5d d3 c8  98 fe 08 c0 ca 83 ea 6b  |.xB..].........k|
000001b0  2a 8a bc 9a f7 8a 84 69  a5 b1 ef 57 71 f8 00 fe  |*......i...Wq...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 7f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```thanks again :D

---

### Post by Hedgehog1 on 2011-05-28
It appears you were trying to have 1 disk per OS at one time, but then made the XP and Windows7 disks dual boot as well:

```
/dev/sda1    *          2,048     2,541,109     2,539,062   b W95 FAT32
/dev/sda2           2,541,566     7,829,503     5,287,938   5 Extended
/dev/sda5           2,541,568     4,509,695     1,968,128  83 Linux
**[COLOR="red"]/dev/sda6           4,511,744     4,814,847       303,104  82 Linux swap / Solaris[/COLOR]**
/dev/sda7           4,816,896     7,829,503     3,012,608  83 Linux


/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848 1,945,137,151 1,944,930,304   7 NTFS / exFAT / HPFS
/dev/sdb3       1,945,139,198 1,953,523,711     8,384,514   5 Extended
**[COLOR="red"]/dev/sdb5       1,945,139,200 1,953,523,711     8,384,512  82 Linux swap / Solaris[/COLOR]**


dev/sdc1               2,048 1,053,692,260 1,053,690,213  83 Linux
/dev/sdc2       1,053,693,950 1,250,263,039   196,569,090   5 Extended
/dev/sdc5       1,053,693,952 1,241,876,479   188,182,528  83 Linux
[COLOR="Red"]**/dev/sdc6       1,241,878,528 1,250,263,039     8,384,512  82 Linux swap / Solaris**[/COLOR]

```

The three different swap partitions indicate at least three different install attempts of Linux.

What is the desired install you really want to have on this PC?

***The Hedge***

:KS

---

### Post by lmn. on 2011-05-28
Yerh i've been fiddling around with trying to get cs:s working on ubuntu, failed & installed win7.. then ubuntu stopped working and was forced back into windows allowing for multiple failed attempts of ubuntu reinstalls.

I would like windows 7 on my main hd, as cs:s prefers 7200rpm; Ubuntu on my secondary hd

is there any way to remove the broken installs? I would still like to keep all my files..

cheers dude :D

---

### Post by Hedgehog1 on 2011-05-28
I think that cleaning things up (and not loading the ***very-pre-alpha*** 11.10 this time!) is your best plan of attack.

Moving Win7 to the 640 gig 7200 RPM drive from the 1tb 5400 rpm drive is doable; but it requires planning and restraint to be successful.

To do this, you will have to:

1) Resize your C: drive/partiton to a size small enough to fit on the 640 gig drive. This is done using the Windows Disk Manager.

2) Do you have any data you need to retrieve from the 640 gig drive?
If so, copy those files to the new, smaller 'C:' partitons OR to an external hard drive.

3) Using CLONEZILLA, copy the 1st two partitions of the 1tb drive as the first two partitions of the 640 gig drive. This will now give you two identical Win7 installs on both drives.

4) Swap the SATA connectoer of the two drives so you boot from the 640 gig drive instead of the 1tb one.


This will leave you with a 640 gig boot drive with 2 Windows partitions - the 100 meg boot partition and the larger WIN7 data partition.

Once you are booting from the 640 gig drive, you can clean and reshape the 1TB drive as a bulk-shared-storage and an Ubuntu install.

Does this make sense do far?

---

### Post by lmn. on 2011-05-28
I'm having severe ubuntu withdrawal symptoms, hence the 11.10 attempt. lol.

the tb is 7200 and the 640 is 5400, all my files are on the 640 formatted as ext4 meaning i can't access them without a successful ubuntu reinstall.

sounds like a potentially system damaging process? is there an easier way??

if i moved windows over to the 640 using the clonexilla method you mentioned, do you think an install on the freshly formatted tb would run smoothly? it seems it is only ubi-partman causing the problem.. would it be possible to patch this file and recreate the usb disk??

If i could be sure that moving/wiping windows and installing ubuntu onto the formatted drive would work, I would do it, but i think the partman error would happen again so the install process would skip formatting options & jump straight to a failed install.

Ideally, I would be able to upgrade/reinstall the current 11.04 on the 640 hd and simply carry on using it.. would rather not swap the contents over and risk losing everything..

I'll be on a faster connection in a week or so, when I'll redownload the ISO and hopefully it'l decide to work. other than that, do you think it would be possible to patch the partman problem?

thanks :D

---

### Post by Hedgehog1 on 2011-05-28
OK - I did not realize the current drive WIN7 was on is the destination drive.  So you do not have to move the WIN7 OS.  Gotcha.

To copy your documents and data from the Ubuntu partitions to the Windows partition, you can use this: **_[ext2-ext3-ext4-filesystem-from-windows]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-filesystem-from-windows-7/")_**

Once you have your data safely in the Windows partition, then we can look at a clean-up and clean install of Ubuntu for you.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-28
With your data safely copied onto your Windows partition; you can then do a complete clean install (with a disk partition map wipe) on the 640 gig drive this way:

Please begin your Ubuntu clean-install by using gparted and do this:

(Your Drive is likely /dev/sdb, not the /dev/sda these screen shots were taken from):

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]

**Then begin creating 3 partitions for '/' (root) '/home' & Swap:**

[IMG]http://img853.imageshack.us/img853/503/mbrpariondemo04.png[/IMG]

**Make your root partition 20-30 gigs**

[IMG]http://img7.imageshack.us/img7/2554/mbrpariondemo05.png[/IMG]

**Make your '/home' partition all the rest of the disk space except that you need for swap (swap = RAM size + 10%)**

[IMG]http://img851.imageshack.us/img851/2815/mbrpariondemo06.png[/IMG]

**Next your swap partition:**

[IMG]http://img132.imageshack.us/img132/8353/mbrpariondemo07.png[/IMG]

**Press the 'check mark' button to make the changes real:**

[IMG]http://img402.imageshack.us/img402/5460/mbrpariondemo08.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-28
**gparted will ask this:**

[IMG]http://img826.imageshack.us/img826/7826/mbrpariondemo09.png[/IMG]

**Then it updates your partitions:**

[IMG]http://img101.imageshack.us/img101/5706/mbrpariondemo10.png[/IMG]

**You can see a list of the changes made once the work is done:**

[IMG]http://img862.imageshack.us/img862/7135/mbrpariondemo11.png[/IMG]

**And a view of what the partitions look like after the update:**

[IMG]http://img600.imageshack.us/img600/4516/mbrpariondemo12.png[/IMG]

**Same layout, but as seen using the Disk Utility:**

[IMG]http://img825.imageshack.us/img825/2018/mbrpariondemo13.png[/IMG]

**Now when you re-install, select this method:**

[IMG]http://img51.imageshack.us/img51/337/mbrpariondemo15.png[/IMG]

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.

**And tell the install to use the three partitions this way (Your Drive is likely /dev/sdb, not the /dev/sdc this screen shot was taken from):**

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]


***The Hedge***

---

### Post by lmn. on 2011-05-28
thanks mate, looking into it now :D

*the ext reader for windows tool is a real treat, should help me fix it for sure!! thanks again pal.

---

### Post by lemonchicken on 2011-05-29
found that program to become unresponsive after a few gb's of transfer,
Now using puppy linux to copy them over and can confirm 100% satisfaction.

will report back in 1 week after I've returned from my travels, wiped my hd and attempted to reinstall Natty..

---

### Post by ssmewing on 2012-01-08
I am a newby to Linix anything. I am also trying to dual boot and had this same error. What I believe happened to me at least is my drive had 2 partions and when trying to install ubuntu it needed to create 3 more partions. Max I found is 4. This is what I think caused the error 10.
 
I went through the steps using Gpart to create as given in this trhead and that worked for the most part. I had to create a VD to get around the 4 partition  issue. The problem that I still have though is I did not get the boot option installed through this route.
 
I have given up for now. I will wait until HD are back on the market and reasonable. Then I will add one for Ubuntu only. 
 
I went through all this in an effort to get the add-on by BlueCop for Amazon Prime videos and its way of db creation.

---

