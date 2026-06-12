---
title: "Vista + Ubuntu 12.04, no boot selection"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by unuscione on 2012-09-18
Hello, I've searched a bit on the forum for an answer to similar problem, but I'm a bit puzzled with the different answers, so I prefer to ask exactly for some insight on my problem here. 

I've tested Ubuntu 12.04 live CD, liked it and decided to install it.

I have 2 physical HDs, both mounted as basic partition, one running Vista 32 bit, the other used as storage.

From Vista I've prepared the volume, by empty enough space (> 100GB), move the MTF to the middle of the disk, shrinked the partition of about 16 GB and left those blank.

Started the Live CD, I've installed Ubuntu (downloading the upgrades etc) seemingly without problem.

Only that there's no boot option asked at the restart, and Vista loads itself automatically.

When I've checked with Vista own volume manager I noticed that since I left mounted a virtual CD by mistake, that was treated as primary partition too, counting the one storage drive, plus the one pertition with Vista, Ubuntu  and the automatically created  swap volume, there were now 5 primary partitions, and I've read on the foruma that it bars the installation to work. So that may be a possible reason.
Not that unmounting the CD solves anything, probably because the boot information simply is not there?

Anyway I've used bootinfoscript to retrive the info pertaining the problem and the result is here below.

I would also add, that since I had a bad experience with EasyBCD years ago (I don't remember if i deleted the drives by accident with it, or did I uninstalled the program and something did broke) I would prefer a different option to try.

Thanks in advance"```
                   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 251cd4fd-9366-4344-8d03-96b16e9f3fd4 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   944,003,063   944,001,016   7 NTFS / exFAT / HPFS
/dev/sda2         944,003,070   976,771,071    32,768,002   5 Extended
/dev/sda5         944,003,072   972,580,863    28,577,792  83 Linux
/dev/sda6         972,582,912   976,771,071     4,188,160  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   781,420,543   781,418,496   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D616415B16413E2D                       ntfs       
/dev/sda5        251cd4fd-9366-4344-8d03-96b16e9f3fd4   ext4       
/dev/sda6        a737e065-9bdc-4b16-9d1d-9255f620c10a   swap       
/dev/sdb1        28167ADF167AAD86                       ntfs       Volume
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/D616415B16413E2D  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/251cd4fd-9366-4344-8d03-96b16e9f3fd4 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 251cd4fd-9366-4344-8d03-96b16e9f3fd4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 251cd4fd-9366-4344-8d03-96b16e9f3fd4
  set locale_dir=($root)/boot/grub/locale
  set lang=it_IT
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
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, con Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 251cd4fd-9366-4344-8d03-96b16e9f3fd4
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=251cd4fd-9366-4344-8d03-96b16e9f3fd4 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, con Linux 3.2.0-29-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 251cd4fd-9366-4344-8d03-96b16e9f3fd4
    echo    'Caricamento Linux 3.2.0-29-generic-pae...'
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=251cd4fd-9366-4344-8d03-96b16e9f3fd4 ro recovery nomodeset 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 251cd4fd-9366-4344-8d03-96b16e9f3fd4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 251cd4fd-9366-4344-8d03-96b16e9f3fd4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root D616415B16413E2D
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=251cd4fd-9366-4344-8d03-96b16e9f3fd4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a737e065-9bdc-4b16-9d1d-9255f620c10a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-29-generic-pae           1
               =                boot/vmlinuz-3.2.0-29-generic-pae              1
               =                initrd.img                                     1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  20 7d bb d8 ca c3 2a 49  28 cd 16 1c fc 5c f6 c4  | }....*I(....\..|
00000010  9b 60 c3 41 fc bd c1 48  0e b4 0b d5 81 d7 b7 ef  |.`.A...H........|
00000020  f8 f6 fa 13 7c fb f8 0d  b2 80 bb f6 17 49 b3 c8  |....|........I..|
00000030  ad 8a 32 e8 4d 18 8a eb  cc ba 93 72 5d f4 27 2c  |..2.M......r].',|
00000040  7f e0 fd f9 97 f1 f9 cb  9f f2 9d bc 96 7e 1e 01  |.............~..|
00000050  28 9a e7 ae 09 08 94 35  b0 8f e1 4f 92 44 8c 9a  |(......5...O.D..|
00000060  2d c0 10 21 8b 3f 6b 51  ea ce f7 e7 c2 98 dd 06  |-..!.?kQ........|
00000070  0d 5e e9 52 30 d8 01 a9  b0 31 4a a9 03 ae 43 69  |.^.R0....1J...Ci|
00000080  3c 5d 92 8a 6e ca 74 67  73 74 53 d4 eb 8b 0a 6c  |<]..n.tgstS....l|
00000090  98 86 6c 24 0c b6 06 b1  11 ae 86 5c 16 00 15 ce  |..l$.......\....|
000000a0  4b aa 80 14 82 3c 22 18  d2 6d 86 da cc 3a 3c 5b  |K....<"..m...:<[|
000000b0  72 b3 e3 f3 0e 5f a2 49  92 14 d1 68 58 92 cc 5b  |r...._.I...hX..[|
000000c0  f2 20 dd 7d e3 f2 a5 58  1e 6e 3e f6 91 b9 f6 d9  |. .}...X.n>.....|
000000d0  34 8d fd ca 42 21 d5 63  35 d0 38 ac 8a ef 93 79  |4...B!.c5.8....y|
000000e0  3f 8a 02 dd 15 cb af f3  6c 9b 86 af ad a6 70 e0  |?.......l.....p.|
000000f0  4f 01 ca 60 db 14 fa ac  61 d9 9c f7 76 80 8d dc  |O..`....a...v...|
00000100  2b de c9 cf 2e 14 b1 92  de d8 46 91 67 19 9f 5d  |+.........F.g..]|
00000110  57 2c 04 43 a4 45 ed 4c  0d fb 8e 2f 3e 74 9f cf  |W,.C.E.L.../>t..|
00000120  e7 ce 3f b7 72 b0 f4 1c  c0 0c e8 a2 40 00 4b c8  |..?.r.......@.K.|
00000130  77 ed 66 da 8a cd 86 9c  d2 3c de b1 b7 82 d8 e3  |w.f......<......|
00000140  f1 4b 4d d4 47 3f b1 02  63 80 cd 19 70 eb 9f 37  |.KM.G?..c...p..7|
00000150  f0 7f cd cc 43 8c 54 af  89 19 b7 5f 1e 6c c2 bb  |....C.T...._.l..|
00000160  51 5b f5 92 c9 7b 3d fe  68 23 b9 9b 30 da c2 82  |Q[...{=.h#..0...|
00000170  f3 3c d7 7f 6e 39 df 6b  9d 68 1b 7c a1 ac 8e 22  |.<..n9.k.h.|..."|
00000180  aa 9c 4d b8 c3 e8 1b 76  47 2f 9e 27 69 fe dc af  |..M....vG/.'i...|
00000190  1a 78 77 6d fe 7b ca ac  c3 52 c3 25 e8 4e 7d a9  |.xwm.{...R.%.N}.|
000001a0  b5 8e 5c bd a4 8a 2a 43  e9 a5 e5 66 37 f4 0e 6c  |..\...*C...f7..l|
000001b0  0d 33 e2 78 c6 db e3 19  92 6b 00 d4 f5 f8 00 fe  |.3.x.....k......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 b4 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 10  b4 01 00 f0 3f 00 00 00  |............?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

P.S. the "xz: (stdin): Compressed data is corrupt "  at the end and the not compliation problem reported at the end of the results here, are they of relevance?

---

### Post by YannBuntu on 2012-09-19
Hello
Your Boot-Info is incomplete. Please follow this tutorial and indicate the resulting Boot-Info URL: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by unuscione on 2012-09-19
Thanks I did exactly that, following an advice on another forum, and it solved the problem: apparently the mounting data referred to the wrong HD, the external one, in the setup.

Thanks anyway!

---

### Post by youngunix on 2012-09-19
Can you please mark your thread as SOLVED. thank you.

---

