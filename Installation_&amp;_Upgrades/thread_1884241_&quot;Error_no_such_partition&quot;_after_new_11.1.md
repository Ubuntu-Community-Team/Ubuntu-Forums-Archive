---
title: "&quot;Error: no such partition&quot; after new 11.10 install"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by qv0 on 2011-11-20
I am attempting to install Ubuntu 11.10 dual-boot with a pre-existing WinXP partition. Both are on the same physical disk. The Linux install is on a logical partition. 
 
The installation appears to succeed, but I receive the following after rebooting:
```

Error: no such partition.
grub rescue>

```
 
Restoring my MBR is not a problem (done it multiple times now), but that only allows me to boot back to WinXP. I've already read through a number of forum threads concerning the same error, but none have resolved the problem.
 
Can anyone tell me what I am doing wrong?
 
Oh, and I realize that multiple swap partitions are not needed. I created only one of them. The other appeared after running the Ubuntu install.
 
Following is output from boot_info_script:
```

                  Boot Info Script 0.60    from 17 May 2011
 
============================= Boot Info Summary: ===============================
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
sda1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr
sda2: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sda5: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
sda6: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda7: __________________________________________________________________________
    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda8: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  SYSLINUX 3.85 2010-02-20
    Boot sector info:   Syslinux looks at sector 1593904 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *          2,048   245,762,047   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda2         245,764,094   625,141,759   379,377,666   5 Extended
/dev/sda5         245,764,096   450,564,095   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda6         614,408,192   625,141,759    10,733,568  82 Linux swap / Solaris
/dev/sda7         450,566,144   610,213,887   159,647,744  83 Linux
/dev/sda8         610,215,936   614,406,143     4,190,208  82 Linux swap / Solaris
 
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1    *            137     3,842,047     3,841,911   b W95 FAT32
 
"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        BA9869439868FEEF                       ntfs       
/dev/sda5        51136EA21925F6BF                       ntfs       Data
/dev/sda6        316aa5fc-5882-4967-bd4d-a1fe880746e1   swap       
/dev/sda7        6b958270-401b-420d-bda0-e6d9a2301726   ext2       
/dev/sda8        dfc979fe-9fe2-4410-9a24-0fa6dec53720   swap       
/dev/sdb1        9854-6253                              vfat       PENDRIVE
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /mnt                     ext2       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
 
================================ sda1/boot.ini: ================================
--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------
=========================== sda7/boot/grub/grub.cfg: ===========================
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 6b958270-401b-420d-bda0-e6d9a2301726
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root 6b958270-401b-420d-bda0-e6d9a2301726
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 set gfxpayload=$linux_gfx_mode
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root 6b958270-401b-420d-bda0-e6d9a2301726
 linux /boot/vmlinuz-3.0.0-12-generic root=/dev/sda7 ro   quiet splash vt.handoff=7
 initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root 6b958270-401b-420d-bda0-e6d9a2301726
 echo 'Loading Linux 3.0.0-12-generic ...'
 linux /boot/vmlinuz-3.0.0-12-generic root=/dev/sda7 ro recovery nomodeset 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root 6b958270-401b-420d-bda0-e6d9a2301726
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root 6b958270-401b-420d-bda0-e6d9a2301726
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set=root BA9869439868FEEF
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
--------------------------------------------------------------------------------
=============================== sda7/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=6b958270-401b-420d-bda0-e6d9a2301726 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=316aa5fc-5882-4967-bd4d-a1fe880746e1 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=dfc979fe-9fe2-4410-9a24-0fa6dec53720 none            swap    sw              0       0
--------------------------------------------------------------------------------
=================== sda7: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               5
               =                boot/vmlinuz-3.0.0-12-generic                  3
               =                initrd.img                                     5
               =                vmlinuz                                        3
============================== sdb1/syslinux.cfg: ==============================
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
--------------------------------------------------------------------------------
================= sdb1: Location of files loaded by Syslinux: ==================
           GiB - GB             File                                 Fragment(s)
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1
============== sdb1: Version of COM32(R) files used by Syslinux: ===============
 menu.c32                           :  COM32R module (v3.xx)
======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on sda2
00000000  86 e3 5b de 24 fb c5 1f  6a 64 dd 19 58 55 71 16  |..[.$...jd..XUq.|
00000010  30 33 17 2b 42 de c6 e5  9f b3 86 87 99 0c 3f fc  |03.+B.........?.|
00000020  b2 8a 5f 4e 1b 46 1a 51  5b 53 ff 02 0c bc 61 fc  |.._N.F.Q[S....a.|
00000030  3e 6c a2 84 bd 1b e2 a6  70 0f 50 82 77 d6 b2 a3  |>l......p.P.w...|
00000040  49 d8 06 70 48 8e 09 d3  ab 32 c8 a9 55 de 48 41  |I..pH....2..U.HA|
00000050  6b 3b e1 ca 2d 51 72 cb  68 b2 70 d0 df 8a 64 c3  |k;..-Qr.h.p...d.|
00000060  8f 0f b9 84 c0 5f 88 5f  c1 d7 62 17 93 92 ff a7  |....._._..b.....|
00000070  fd 77 fb b0 3d 63 65 a4  3c 96 f3 c5 e6 21 84 c3  |.w..=ce.<....!..|
00000080  45 a1 8c 8f 57 88 87 5d  a3 70 26 95 5d d2 7b 7c  |E...W..].p&.].{||
00000090  ed b6 5c 23 77 54 58 6e  4c 03 cd 8b 61 53 df a1  |..\#wTXnL...aS..|
000000a0  73 d7 33 7e cc 4a d7 6d  af df 7e 27 4d 36 9e 65  |s.3~.J.m..~'M6.e|
000000b0  4e 8a 0d 35 1b 11 ff c7  d4 5b a6 ee 2f 1b 9b 29  |N..5.....[../..)|
000000c0  58 9e 84 b3 0a f0 90 69  de f8 5e 4d b2 47 62 6a  |X......i..^M.Gbj|
000000d0  36 26 34 16 7f cb a9 86  96 a6 d5 47 dd 49 db 78  |6&4........G.I.x|
000000e0  82 68 a4 33 29 b7 64 b1  d8 fb e9 b9 bf 9f ef c1  |.h.3).d.........|
000000f0  32 fb f9 a6 f3 d7 fa 00  d7 36 66 4e 81 1b 7b 76  |2........6fN..{v|
00000100  a3 7f 57 64 73 00 9f a8  ed 10 5e 2f de 51 e3 c4  |..Wds.....^/.Q..|
00000110  b5 ff b7 b3 f9 f9 9d 43  46 fc b1 b0 83 51 94 f0  |.......CF....Q..|
00000120  76 00 8f 3c 88 ac 20 3a  32 54 7e 14 f5 32 16 b5  |v..<.. :2T~..2..|
00000130  6d e1 3b af 44 7d 58 2d  53 3a 7c a0 d3 8b bb 49  |m.;.D}X-S:|....I|
00000140  db 26 3c f0 c9 c8 d1 7f  ec f9 db 2d 6d 32 c5 73  |.&<........-m2.s|
00000150  15 78 fe 51 0a c4 c4 35  d9 70 9d d4 ff 3d f0 da  |.x.Q...5.p...=..|
00000160  0f df f2 55 f3 97 cb 42  35 a5 df 9d be 68 06 c7  |...U...B5....h..|
00000170  4a a7 4a 13 ed bf 13 1b  cd ec c5 7b 18 94 5f 41  |J.J........{.._A|
00000180  33 de 4a 5f 08 2c 45 df  49 e9 b6 d4 c4 8f 36 2e  |3.J_.,E.I.....6.|
00000190  9f 43 44 54 85 5c 99 49  bd be 53 36 6d 38 2b 53  |.CDT.\.I..S6m8+S|
000001a0  c8 ba 67 ef b4 38 f9 37  6c cb 68 f0 88 2e ad 83  |..g..8.7l.h.....|
000001b0  94 a3 4b 41 15 1d 39 eb  8d 9b ff d8 67 a7 00 1b  |..KA..9.....g...|
000001c0  da ff 07 51 c3 ff 02 00  00 00 00 00 35 0c 00 fe  |...Q........5...|
000001d0  ff ff 05 fe ff ff 02 08  f9 15 00 d0 a3 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
 
=============================== StdErr Messages: ===============================
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by fantab on 2011-11-20
> **qv0 said:**
> I am attempting to install Ubuntu 11.10 dual-boot with a pre-existing WinXP partition. Both are on the same physical disk. The Linux install is on a logical partition. 
 
The installation appears to succeed, but I receive the following after rebooting:
[CODE]
[B]Error: no such partition.
grub rescue>[/B]

Re-Install Ubuntu and use "**Something Else**" option to install Ubuntu to manually select your partitions and this way Ubuntu won't create an additional SWAP.  INSTALL GRUB to **/dev/sda** only.

Also, is there any particular reason you've formatted Linux partitions using ext2. If possible use ext4. Not that it matters much but ext4 is the latest version of the ext-filesystem. 

Is Windows vista/7 actually on /dev/sda5, which is Logical Partition? If that is so you may have issues booting it. Windows is not friendly with Logical Partitions when booting from. You should consider a Primary Partition to boot any Windows. It is all right if its a DATA partition though.

---

### Post by qv0 on 2011-11-21
> **fantab said:**
> Re-Install Ubuntu and use "**Something Else**" option to install Ubuntu to manually select your partitions and this way Ubuntu won't create an additional SWAP. INSTALL GRUB to **/dev/sda** only.
 
Also, is there any particular reason you've formatted Linux partitions using ext2. If possible use ext4. Not that it matters much but ext4 is the latest version of the ext-filesystem. 
 
Is Windows vista/7 actually on /dev/sda5, which is Logical Partition? If that is so you may have issues booting it. Windows is not friendly with Logical Partitions when booting from. You should consider a Primary Partition to boot any Windows. It is all right if its a DATA partition though.
 
 
I used the **Something Else** option on the last couple attempts, and you're probably correct that one of the other options (on a previous attempt) decided to be helpful and create a new swap for me.
 
As to where grub is installed, I thought it was installed on /dev/sda.  Do you see anything that indicates otherwise?
 
I started with ext4, then tried ext3 and finally ext2 on the possibility that grub was having trouble with the newer file systems.  As you might guess, that made no difference.
 
The system isn't running Win7/Vista, it's running WinXP that happens to be on /dev/sda1.  /dev/sda5 is an NTFS formatted non-bootable data partition.  No clue why it's suddenly being labelled as Win7/Vista...

---

### Post by qv0 on 2011-11-21
> **qv0 said:**
> I used the **Something Else** option on the last couple attempts, and you're probably correct that one of the other options (on a previous attempt) decided to be helpful and create a new swap for me.
 
As to where grub is installed, I thought it was installed on /dev/sda. Do you see anything that indicates otherwise?
 
I started with ext4, then tried ext3 and finally ext2 on the possibility that grub was having trouble with the newer file systems. As you might guess, that made no difference.
 
The system isn't running Win7/Vista, it's running WinXP that happens to be on /dev/sda1. /dev/sda5 is an NTFS formatted non-bootable data partition. No clue why it's suddenly being labelled as Win7/Vista...
 
 
I reinstalled with the **Something Else** option again, making sure it was installing grub to /dev/sda.  Same error after reboot.
 
```

                  Boot Info Script 0.60    from 17 May 2011

============================= Boot Info Summary: ===============================
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
sda1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr
sda2: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sda5: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
sda6: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda7: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda8: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  SYSLINUX 3.85 2010-02-20
    Boot sector info:   Syslinux looks at sector 1593904 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *          2,048   245,762,047   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda2         245,764,094   625,141,759   379,377,666   5 Extended
/dev/sda5         245,764,096   450,564,095   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda6         614,408,192   625,141,759    10,733,568  82 Linux swap / Solaris
/dev/sda7         450,566,144   610,213,887   159,647,744  83 Linux
/dev/sda8         610,215,936   614,406,143     4,190,208  82 Linux swap / Solaris

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1    *            137     3,842,047     3,841,911   b W95 FAT32

"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        BA9869439868FEEF                       ntfs       
/dev/sda5        51136EA21925F6BF                       ntfs       Data
/dev/sda6        316aa5fc-5882-4967-bd4d-a1fe880746e1   swap       
/dev/sda7        ba28fd7a-441d-44f6-ad4a-17f1bc32c275   ext4       
/dev/sda8        dfc979fe-9fe2-4410-9a24-0fa6dec53720   swap       
/dev/sdb1        9854-6253                              vfat       PENDRIVE
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /mnt                     ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

================================ sda1/boot.ini: ================================
--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------
=========================== sda7/boot/grub/grub.cfg: ===========================
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 set gfxpayload=$linux_gfx_mode
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux /boot/vmlinuz-3.0.0-12-generic root=UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 ro   quiet splash vt.handoff=7
 initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 echo 'Loading Linux 3.0.0-12-generic ...'
 linux /boot/vmlinuz-3.0.0-12-generic root=UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 ro recovery nomodeset 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set=root BA9869439868FEEF
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
--------------------------------------------------------------------------------
=============================== sda7/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=316aa5fc-5882-4967-bd4d-a1fe880746e1 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=dfc979fe-9fe2-4410-9a24-0fa6dec53720 none            swap    sw              0       0
--------------------------------------------------------------------------------
=================== sda7: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1
============================== sdb1/syslinux.cfg: ==============================
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
--------------------------------------------------------------------------------
================= sdb1: Location of files loaded by Syslinux: ==================
           GiB - GB             File                                 Fragment(s)
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1
============== sdb1: Version of COM32(R) files used by Syslinux: ===============
 menu.c32                           :  COM32R module (v3.xx)
======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on sda2
00000000  86 e3 5b de 24 fb c5 1f  6a 64 dd 19 58 55 71 16  |..[.$...jd..XUq.|
00000010  30 33 17 2b 42 de c6 e5  9f b3 86 87 99 0c 3f fc  |03.+B.........?.|
00000020  b2 8a 5f 4e 1b 46 1a 51  5b 53 ff 02 0c bc 61 fc  |.._N.F.Q[S....a.|
00000030  3e 6c a2 84 bd 1b e2 a6  70 0f 50 82 77 d6 b2 a3  |>l......p.P.w...|
00000040  49 d8 06 70 48 8e 09 d3  ab 32 c8 a9 55 de 48 41  |I..pH....2..U.HA|
00000050  6b 3b e1 ca 2d 51 72 cb  68 b2 70 d0 df 8a 64 c3  |k;..-Qr.h.p...d.|
00000060  8f 0f b9 84 c0 5f 88 5f  c1 d7 62 17 93 92 ff a7  |....._._..b.....|
00000070  fd 77 fb b0 3d 63 65 a4  3c 96 f3 c5 e6 21 84 c3  |.w..=ce.<....!..|
00000080  45 a1 8c 8f 57 88 87 5d  a3 70 26 95 5d d2 7b 7c  |E...W..].p&.].{||
00000090  ed b6 5c 23 77 54 58 6e  4c 03 cd 8b 61 53 df a1  |..\#wTXnL...aS..|
000000a0  73 d7 33 7e cc 4a d7 6d  af df 7e 27 4d 36 9e 65  |s.3~.J.m..~'M6.e|
000000b0  4e 8a 0d 35 1b 11 ff c7  d4 5b a6 ee 2f 1b 9b 29  |N..5.....[../..)|
000000c0  58 9e 84 b3 0a f0 90 69  de f8 5e 4d b2 47 62 6a  |X......i..^M.Gbj|
000000d0  36 26 34 16 7f cb a9 86  96 a6 d5 47 dd 49 db 78  |6&4........G.I.x|
000000e0  82 68 a4 33 29 b7 64 b1  d8 fb e9 b9 bf 9f ef c1  |.h.3).d.........|
000000f0  32 fb f9 a6 f3 d7 fa 00  d7 36 66 4e 81 1b 7b 76  |2........6fN..{v|
00000100  a3 7f 57 64 73 00 9f a8  ed 10 5e 2f de 51 e3 c4  |..Wds.....^/.Q..|
00000110  b5 ff b7 b3 f9 f9 9d 43  46 fc b1 b0 83 51 94 f0  |.......CF....Q..|
00000120  76 00 8f 3c 88 ac 20 3a  32 54 7e 14 f5 32 16 b5  |v..<.. :2T~..2..|
00000130  6d e1 3b af 44 7d 58 2d  53 3a 7c a0 d3 8b bb 49  |m.;.D}X-S:|....I|
00000140  db 26 3c f0 c9 c8 d1 7f  ec f9 db 2d 6d 32 c5 73  |.&<........-m2.s|
00000150  15 78 fe 51 0a c4 c4 35  d9 70 9d d4 ff 3d f0 da  |.x.Q...5.p...=..|
00000160  0f df f2 55 f3 97 cb 42  35 a5 df 9d be 68 06 c7  |...U...B5....h..|
00000170  4a a7 4a 13 ed bf 13 1b  cd ec c5 7b 18 94 5f 41  |J.J........{.._A|
00000180  33 de 4a 5f 08 2c 45 df  49 e9 b6 d4 c4 8f 36 2e  |3.J_.,E.I.....6.|
00000190  9f 43 44 54 85 5c 99 49  bd be 53 36 6d 38 2b 53  |.CDT.\.I..S6m8+S|
000001a0  c8 ba 67 ef b4 38 f9 37  6c cb 68 f0 88 2e ad 83  |..g..8.7l.h.....|
000001b0  94 a3 4b 41 15 1d 39 eb  8d 9b ff d8 67 a7 00 1b  |..KA..9.....g...|
000001c0  da ff 07 51 c3 ff 02 00  00 00 00 00 35 0c 00 fe  |...Q........5...|
000001d0  ff ff 05 fe ff ff 02 08  f9 15 00 d0 a3 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=============================== StdErr Messages: ===============================
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by fantab on 2011-11-21
> **qv0 said:**
> I reinstalled with the **Something Else** option again, making sure it was installing grub to /dev/sda.  Same error after reboot.

As far as I can see, you have installed Ubuntu correctly. 


[LIST=1]
[*] Did you change the BIOS in anyway to use your LiveUSB (I think you are using LiveUSB)?
[*] If you have then have you changed it back to boot from your hard disk?
[/LIST]
 
If the above questions do not apply to you then:
Please read this information [**GRUB RESCUE**]("http://ubuntuforums.org/showthread.php?t=1594052") and try to recover GRUB.

Keep the forum posted.

---

### Post by larrypg on 2011-11-21
hello,

Do you have both a wubi install (inside of windows) and a regular install? Noticed this...Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

---

### Post by qv0 on 2011-11-21
> **fantab said:**
> As far as I can see, you have installed Ubuntu correctly. 


[LIST=1]
[*] Did you change the BIOS in anyway to use your LiveUSB (I think you are using LiveUSB)?
[*] If you have then have you changed it back to boot from your hard disk?
[/LIST]
 
If the above questions do not apply to you then:
Please read this information [**GRUB RESCUE**]("http://ubuntuforums.org/showthread.php?t=1594052") and try to recover GRUB.

Keep the forum posted.

Correct, I installed from a LiveUSB image.  No recent changes to the BIOS.  It is configured to boot from USB as a first choice, but there is no USB device connected when I reboot and end up on a grub rescue command line.  An MBR that points to WinXP works fine, so I hadn't paid much attention to BIOS or the boot sequence.

I've tried the normal set of GRUB RESCUE commands but noticed that it's "insmod linux" at the link you provided.  The instructions I had followed specified "insmod normal", resulting in an unknown file system response (this is when I tried reverting to ext2).

Going to try it with "insmod linux" shortly.  Warning - I am new to Grub Rescue.  Not even sure it existed last time I had problems with Grub...

---

### Post by qv0 on 2011-11-21
> **larrypg said:**
> hello,

Do you have both a wubi install (inside of windows) and a regular install? Noticed this...Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr


Wish I had a good explanation for that.  I do not run wubi.  In fact, I've never run any Linux install from this particular laptop until now.

Could LILO have deposited those wubi boot files?  I used LILO to restore the MBR several times    (sudo lilo -M /dev/sda mbr) and that's roughly when those files appeared.

:confused:

---

### Post by Rubi1200 on 2011-11-21
Boot from the LiveCD/USB and run the following commands:

```
sudo apt-get update
sudo apt-get install gawk
```When completed, download and run the boot info script again and post the results as before.

By the way, installing lilo could not have installed those Wubi files; they are the remnants of an old, uninstalled Wubi install.

> Wish I had a good explanation for that.  I do not run wubi.  In fact,  I've never run any Linux install from this particular laptop until now.
Is it possible someone else installed and uninstalled Wubi on the laptop?

---

### Post by qv0 on 2011-11-21
[QUOTE=Rubi1200;11477340]Boot from the LiveCD/USB and run the following commands:
 
```
sudo apt-get update
sudo apt-get install gawk
```
 
 
Sorry about gawk. Got lazy after the eighth or ninth install. :oops:
 
Results with gawk installed:
```

                  Boot Info Script 0.60    from 17 May 2011
 
============================= Boot Info Summary: ===============================
 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
sda1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr
sda2: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sda5: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
sda6: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda7: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda8: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  SYSLINUX 3.85 2010-02-20
    Boot sector info:   Syslinux looks at sector 1593904 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *          2,048   245,762,047   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda2         245,764,094   625,141,759   379,377,666   5 Extended
/dev/sda5         245,764,096   450,564,095   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda6         614,408,192   625,141,759    10,733,568  82 Linux swap / Solaris
/dev/sda7         450,566,144   610,213,887   159,647,744  83 Linux
/dev/sda8         610,215,936   614,406,143     4,190,208  82 Linux swap / Solaris
 
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1    *            137     3,842,047     3,841,911   b W95 FAT32
 
"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        BA9869439868FEEF                       ntfs       
/dev/sda5        51136EA21925F6BF                       ntfs       Data
/dev/sda6        316aa5fc-5882-4967-bd4d-a1fe880746e1   swap       
/dev/sda7        ba28fd7a-441d-44f6-ad4a-17f1bc32c275   ext4       
/dev/sda8        dfc979fe-9fe2-4410-9a24-0fa6dec53720   swap       
/dev/sdb1        9854-6253                              vfat       PENDRIVE
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /mnt                     ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
 
================================ sda1/boot.ini: ================================
--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------
=========================== sda7/boot/grub/grub.cfg: ===========================
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 set gfxpayload=$linux_gfx_mode
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux /boot/vmlinuz-3.0.0-12-generic root=UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 ro   quiet splash vt.handoff=7
 initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 echo 'Loading Linux 3.0.0-12-generic ...'
 linux /boot/vmlinuz-3.0.0-12-generic root=UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 ro recovery nomodeset 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set=root BA9869439868FEEF
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
--------------------------------------------------------------------------------
=============================== sda7/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=316aa5fc-5882-4967-bd4d-a1fe880746e1 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=dfc979fe-9fe2-4410-9a24-0fa6dec53720 none            swap    sw              0       0
--------------------------------------------------------------------------------
=================== sda7: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
 263.077674866 = 282.477502464  boot/grub/core.img                             1
 263.077690125 = 282.477518848  boot/grub/grub.cfg                             1
 216.226554871 = 232.171495424  boot/initrd.img-3.0.0-12-generic               2
 255.015121460 = 273.820401664  boot/vmlinuz-3.0.0-12-generic                  1
 216.226554871 = 232.171495424  initrd.img                                     2
 255.015121460 = 273.820401664  vmlinuz                                        1
============================== sdb1/syslinux.cfg: ==============================
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
--------------------------------------------------------------------------------
================= sdb1: Location of files loaded by Syslinux: ==================
           GiB - GB             File                                 Fragment(s)
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1
============== sdb1: Version of COM32(R) files used by Syslinux: ===============
 menu.c32                           :  COM32R module (v3.xx)
======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on sda2
00000000  86 e3 5b de 24 fb c5 1f  6a 64 dd 19 58 55 71 16  |..[.$...jd..XUq.|
00000010  30 33 17 2b 42 de c6 e5  9f b3 86 87 99 0c 3f fc  |03.+B.........?.|
00000020  b2 8a 5f 4e 1b 46 1a 51  5b 53 ff 02 0c bc 61 fc  |.._N.F.Q[S....a.|
00000030  3e 6c a2 84 bd 1b e2 a6  70 0f 50 82 77 d6 b2 a3  |>l......p.P.w...|
00000040  49 d8 06 70 48 8e 09 d3  ab 32 c8 a9 55 de 48 41  |I..pH....2..U.HA|
00000050  6b 3b e1 ca 2d 51 72 cb  68 b2 70 d0 df 8a 64 c3  |k;..-Qr.h.p...d.|
00000060  8f 0f b9 84 c0 5f 88 5f  c1 d7 62 17 93 92 ff a7  |....._._..b.....|
00000070  fd 77 fb b0 3d 63 65 a4  3c 96 f3 c5 e6 21 84 c3  |.w..=ce.<....!..|
00000080  45 a1 8c 8f 57 88 87 5d  a3 70 26 95 5d d2 7b 7c  |E...W..].p&.].{||
00000090  ed b6 5c 23 77 54 58 6e  4c 03 cd 8b 61 53 df a1  |..\#wTXnL...aS..|
000000a0  73 d7 33 7e cc 4a d7 6d  af df 7e 27 4d 36 9e 65  |s.3~.J.m..~'M6.e|
000000b0  4e 8a 0d 35 1b 11 ff c7  d4 5b a6 ee 2f 1b 9b 29  |N..5.....[../..)|
000000c0  58 9e 84 b3 0a f0 90 69  de f8 5e 4d b2 47 62 6a  |X......i..^M.Gbj|
000000d0  36 26 34 16 7f cb a9 86  96 a6 d5 47 dd 49 db 78  |6&4........G.I.x|
000000e0  82 68 a4 33 29 b7 64 b1  d8 fb e9 b9 bf 9f ef c1  |.h.3).d.........|
000000f0  32 fb f9 a6 f3 d7 fa 00  d7 36 66 4e 81 1b 7b 76  |2........6fN..{v|
00000100  a3 7f 57 64 73 00 9f a8  ed 10 5e 2f de 51 e3 c4  |..Wds.....^/.Q..|
00000110  b5 ff b7 b3 f9 f9 9d 43  46 fc b1 b0 83 51 94 f0  |.......CF....Q..|
00000120  76 00 8f 3c 88 ac 20 3a  32 54 7e 14 f5 32 16 b5  |v..<.. :2T~..2..|
00000130  6d e1 3b af 44 7d 58 2d  53 3a 7c a0 d3 8b bb 49  |m.;.D}X-S:|....I|
00000140  db 26 3c f0 c9 c8 d1 7f  ec f9 db 2d 6d 32 c5 73  |.&<........-m2.s|
00000150  15 78 fe 51 0a c4 c4 35  d9 70 9d d4 ff 3d f0 da  |.x.Q...5.p...=..|
00000160  0f df f2 55 f3 97 cb 42  35 a5 df 9d be 68 06 c7  |...U...B5....h..|
00000170  4a a7 4a 13 ed bf 13 1b  cd ec c5 7b 18 94 5f 41  |J.J........{.._A|
00000180  33 de 4a 5f 08 2c 45 df  49 e9 b6 d4 c4 8f 36 2e  |3.J_.,E.I.....6.|
00000190  9f 43 44 54 85 5c 99 49  bd be 53 36 6d 38 2b 53  |.CDT.\.I..S6m8+S|
000001a0  c8 ba 67 ef b4 38 f9 37  6c cb 68 f0 88 2e ad 83  |..g..8.7l.h.....|
000001b0  94 a3 4b 41 15 1d 39 eb  8d 9b ff d8 67 a7 00 1b  |..KA..9.....g...|
000001c0  da ff 07 51 c3 ff 02 00  00 00 00 00 35 0c 00 fe  |...Q........5...|
000001d0  ff ff 05 fe ff ff 02 08  f9 15 00 d0 a3 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by qv0 on 2011-11-21
> **fantab said:**
> Please read this information [**GRUB RESCUE**]("http://ubuntuforums.org/showthread.php?t=1594052") and try to recover GRUB.
 
Keep the forum posted.
 
 
I've been playing around with grub rescue and am consistently running into the following error from "ls (hd0,6)":
```
error: no such partition.
```
 
Also, the output of plain "ls" is:
 
```
 
(hd0) (hd0,msdos5) (hd0,msdos1)

```
 
 
I'm assuming that (hd0,msdos1) is my WinXP NTFS file system, and (hd0,msdos5) is the other NTFS file system. Shouldn't I expect the Linux file systems to show up here as well?
 
And the partition table looks fine when I view it after booting from a USB image...

---

### Post by Quackers on 2011-11-21
Somehow you have lost grub from the MBR of /dev/sda and it has been replaced by Lilo.
I would suggest re-installing grub as a first measure at this stage.
Please boot from the Ubuntu live cd/usb and select "try Ubuntu" then when the desktop loads open up a terminal and run these two commands, one at a time, pressing enter after each line.
```
sudo mount /dev/sda7 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
``` This should report no errors and should put grub back in the MBR of the drive.
See if it boots after that. Other measures may still need to be taken.
If it won't boot please install gawk again and re-run the boot script.

It does look like there has been a wubi installation at some time.

By the way is this on an older pc?

---

### Post by qv0 on 2011-11-21
> **Quackers said:**
> Somehow you have lost grub from the MBR of /dev/sda and it has been replaced by Lilo.
I would suggest re-installing grub as a first measure at this stage.
...
By the way is this on an older pc?
 
 
The last boot_info_script output showed LILO because I had used LILO to restore the MBR in order to boot back to Windows.
 
I manually installed grub anyway as you suggested (in case the installer was doing something strange), but am getting the same error on boot. boot_info_script output reflecting this state is below.
 
It is an older system - Dell Inspiron 9300
 
```

                  Boot Info Script 0.60    from 17 May 2011
 
============================= Boot Info Summary: ===============================
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
sda1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr
sda2: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sda5: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
sda6: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda7: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img
sda8: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  SYSLINUX 3.85 2010-02-20
    Boot sector info:   Syslinux looks at sector 1593904 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *          2,048   245,762,047   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda2         245,764,094   625,141,759   379,377,666   5 Extended
/dev/sda5         245,764,096   450,564,095   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda6         614,408,192   625,141,759    10,733,568  82 Linux swap / Solaris
/dev/sda7         450,566,144   610,213,887   159,647,744  83 Linux
/dev/sda8         610,215,936   614,406,143     4,190,208  82 Linux swap / Solaris
 
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1    *            137     3,842,047     3,841,911   b W95 FAT32
 
"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        BA9869439868FEEF                       ntfs       
/dev/sda5        51136EA21925F6BF                       ntfs       Data
/dev/sda6        316aa5fc-5882-4967-bd4d-a1fe880746e1   swap       
/dev/sda7        ba28fd7a-441d-44f6-ad4a-17f1bc32c275   ext4       
/dev/sda8        dfc979fe-9fe2-4410-9a24-0fa6dec53720   swap       
/dev/sdb1        9854-6253                              vfat       PENDRIVE
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /mnt                     ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
 
================================ sda1/boot.ini: ================================
--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------
=========================== sda7/boot/grub/grub.cfg: ===========================
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 set gfxpayload=$linux_gfx_mode
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux /boot/vmlinuz-3.0.0-13-generic root=UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 ro   quiet splash vt.handoff=7
 initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 echo 'Loading Linux 3.0.0-13-generic ...'
 linux /boot/vmlinuz-3.0.0-13-generic root=UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 ro recovery nomodeset 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 set gfxpayload=$linux_gfx_mode
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux /boot/vmlinuz-3.0.0-12-generic root=UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 ro   quiet splash vt.handoff=7
 initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 echo 'Loading Linux 3.0.0-12-generic ...'
 linux /boot/vmlinuz-3.0.0-12-generic root=UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 ro recovery nomodeset 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos7)'
 search --no-floppy --fs-uuid --set=root ba28fd7a-441d-44f6-ad4a-17f1bc32c275
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set=root BA9869439868FEEF
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
--------------------------------------------------------------------------------
=============================== sda7/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=ba28fd7a-441d-44f6-ad4a-17f1bc32c275 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=316aa5fc-5882-4967-bd4d-a1fe880746e1 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=dfc979fe-9fe2-4410-9a24-0fa6dec53720 none            swap    sw              0       0
--------------------------------------------------------------------------------
=================== sda7: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
 263.054244995 = 282.452344832  boot/grub/core.img                             1
 263.220489502 = 282.630848512  boot/grub/grub.cfg                             1
 261.851554871 = 281.160966144  boot/initrd.img-3.0.0-12-generic               2
 262.357421875 = 281.704136704  boot/initrd.img-3.0.0-13-generic               2
 255.015121460 = 273.820401664  boot/vmlinuz-3.0.0-12-generic                  1
 261.956466675 = 281.273614336  boot/vmlinuz-3.0.0-13-generic                  1
 280.971706390 = 301.691072512  grub/core.img                                  1
 261.851554871 = 281.160966144  initrd.img.old                                 2
 261.956466675 = 281.273614336  vmlinuz                                        1
 255.015121460 = 273.820401664  vmlinuz.old                                    1
============================== sdb1/syslinux.cfg: ==============================
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
--------------------------------------------------------------------------------
================= sdb1: Location of files loaded by Syslinux: ==================
           GiB - GB             File                                 Fragment(s)
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1
============== sdb1: Version of COM32(R) files used by Syslinux: ===============
 menu.c32                           :  COM32R module (v3.xx)
======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on sda2
00000000  86 e3 5b de 24 fb c5 1f  6a 64 dd 19 58 55 71 16  |..[.$...jd..XUq.|
00000010  30 33 17 2b 42 de c6 e5  9f b3 86 87 99 0c 3f fc  |03.+B.........?.|
00000020  b2 8a 5f 4e 1b 46 1a 51  5b 53 ff 02 0c bc 61 fc  |.._N.F.Q[S....a.|
00000030  3e 6c a2 84 bd 1b e2 a6  70 0f 50 82 77 d6 b2 a3  |>l......p.P.w...|
00000040  49 d8 06 70 48 8e 09 d3  ab 32 c8 a9 55 de 48 41  |I..pH....2..U.HA|
00000050  6b 3b e1 ca 2d 51 72 cb  68 b2 70 d0 df 8a 64 c3  |k;..-Qr.h.p...d.|
00000060  8f 0f b9 84 c0 5f 88 5f  c1 d7 62 17 93 92 ff a7  |....._._..b.....|
00000070  fd 77 fb b0 3d 63 65 a4  3c 96 f3 c5 e6 21 84 c3  |.w..=ce.<....!..|
00000080  45 a1 8c 8f 57 88 87 5d  a3 70 26 95 5d d2 7b 7c  |E...W..].p&.].{||
00000090  ed b6 5c 23 77 54 58 6e  4c 03 cd 8b 61 53 df a1  |..\#wTXnL...aS..|
000000a0  73 d7 33 7e cc 4a d7 6d  af df 7e 27 4d 36 9e 65  |s.3~.J.m..~'M6.e|
000000b0  4e 8a 0d 35 1b 11 ff c7  d4 5b a6 ee 2f 1b 9b 29  |N..5.....[../..)|
000000c0  58 9e 84 b3 0a f0 90 69  de f8 5e 4d b2 47 62 6a  |X......i..^M.Gbj|
000000d0  36 26 34 16 7f cb a9 86  96 a6 d5 47 dd 49 db 78  |6&4........G.I.x|
000000e0  82 68 a4 33 29 b7 64 b1  d8 fb e9 b9 bf 9f ef c1  |.h.3).d.........|
000000f0  32 fb f9 a6 f3 d7 fa 00  d7 36 66 4e 81 1b 7b 76  |2........6fN..{v|
00000100  a3 7f 57 64 73 00 9f a8  ed 10 5e 2f de 51 e3 c4  |..Wds.....^/.Q..|
00000110  b5 ff b7 b3 f9 f9 9d 43  46 fc b1 b0 83 51 94 f0  |.......CF....Q..|
00000120  76 00 8f 3c 88 ac 20 3a  32 54 7e 14 f5 32 16 b5  |v..<.. :2T~..2..|
00000130  6d e1 3b af 44 7d 58 2d  53 3a 7c a0 d3 8b bb 49  |m.;.D}X-S:|....I|
00000140  db 26 3c f0 c9 c8 d1 7f  ec f9 db 2d 6d 32 c5 73  |.&<........-m2.s|
00000150  15 78 fe 51 0a c4 c4 35  d9 70 9d d4 ff 3d f0 da  |.x.Q...5.p...=..|
00000160  0f df f2 55 f3 97 cb 42  35 a5 df 9d be 68 06 c7  |...U...B5....h..|
00000170  4a a7 4a 13 ed bf 13 1b  cd ec c5 7b 18 94 5f 41  |J.J........{.._A|
00000180  33 de 4a 5f 08 2c 45 df  49 e9 b6 d4 c4 8f 36 2e  |3.J_.,E.I.....6.|
00000190  9f 43 44 54 85 5c 99 49  bd be 53 36 6d 38 2b 53  |.CDT.\.I..S6m8+S|
000001a0  c8 ba 67 ef b4 38 f9 37  6c cb 68 f0 88 2e ad 83  |..g..8.7l.h.....|
000001b0  94 a3 4b 41 15 1d 39 eb  8d 9b ff d8 67 a7 00 1b  |..KA..9.....g...|
000001c0  da ff 07 51 c3 ff 02 00  00 00 00 00 35 0c 00 fe  |...Q........5...|
000001d0  ff ff 05 fe ff ff 02 08  f9 15 00 d0 a3 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
 
=============================== StdErr Messages: ===============================
unlzma: Decoder error

```

---

### Post by Quackers on 2011-11-21
You didn't re-install gawk I think.
Does the error message at boot mention a UUID number of the missing partition?
Also is the pc an older one?
Check in your bios to see if there is anything about a 137GB limit for the hard drive. It may be called "large drive" or LBA or something else. If there is a switch to turn large drives on then try it.
This is because some older bioses cannot "see" anything bootable beyond a 137GB limit. Your Ubuntu partition is beyond 137GB into the disc.

---

### Post by qv0 on 2011-11-22
> **Quackers said:**
> You didn't re-install gawk I think.
Does the error message at boot mention a UUID number of the missing partition?
Also is the pc an older one?
Check in your bios to see if there is anything about a 137GB limit for the hard drive. It may be called "large drive" or LBA or something else. If there is a switch to turn large drives on then try it.
This is because some older bioses cannot "see" anything bootable beyond a 137GB limit. Your Ubuntu partition is beyond 137GB into the disc.
 
gawk is installed. When it isn't installed, I get the following:
```
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```
There was nothing about awk or Math support in the latest output. Also, I can invoke gawk from the same command line.
 
As stated earlier, it is an older laptop (Inspiron 9300). There's no mention of LBA in the BIOS configuration menu, **but I'll bet you're correct - the problem probably is the 28-bit ATA limitation**. **If so, then presumably I'm screwed unless I want to repartition the WinXP file system down to something that would allow for a reasonable /boot partition within the 137GB, correct?**

---

### Post by Quackers on 2011-11-22
Once gawk is installed the first line of the boot script should say something like this
```
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks [COLOR="Red"]in partition 7 for /boot/grub[/COLOR]
    on this drive.
```
I'm not sure why your boot script doesn't do that if gawk was installed.

Yes, a separate boot partition early in the drive would fix any limit in bios. I'm not 100% sure that it's your problem, but it could be.

---

### Post by qv0 on 2011-11-22
> **Quackers said:**
> Once gawk is installed the first line of the boot script should say something like this
```
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks [COLOR=red]in partition 7 for /boot/grub[/COLOR]
    on this drive.
```
I'm not sure why your boot script doesn't do that if gawk was installed.
 
Yes, a separate boot partition early in the drive would fix any limit in bios. I'm not 100% sure that it's your problem, but it could be.
 
After a bit of research, it looks like early 9300s were limited to 28-bit addressing, but later 9300s were upgraded to SATA and had an LBA-capable BIOS. Mine is among the first category. :(
 
Anyway, I appreciate your help. My curiosity is probably going to get the better of me, so that WinXP partition might get pared down soon to find out if BIOS is really the problem. 200MB should be plenty for /boot...

---

### Post by qv0 on 2011-11-22
> **qv0 said:**
> ... My curiosity is probably going to get the better of me, so that WinXP partition might get pared down soon to find out if BIOS is really the problem. 200MB should be plenty for /boot...
 
That worked, so the problem was definitely my BIOS. Thanks for your help Quackers.

---

### Post by Quackers on 2011-11-22
You're welcome.
Very happy to hear that it's solved :-)

---

### Post by Rubi1200 on 2011-11-22
Glad to hear you got things worked out.

Good work from Quackers there :)

---

