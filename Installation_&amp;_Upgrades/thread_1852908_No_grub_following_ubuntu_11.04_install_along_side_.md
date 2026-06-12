---
title: "No grub following ubuntu 11.04 install along side XP"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by Darren_Thomas on 2011-10-01
Hey all,

I have installed Ubuntu 11.04 along side an existing install of Windows XP.

The installation seemed to go fine and i didn't notice any errors being reported during the process.

When i restarted, my machine just boots directly into windows and i get no option for Ubuntu :(

As i am running multi HDD's, i think i need to fix the grub? 

I have run the boot_info_script file (results below), but am unsure what commands to use next.

Thanks in advance

Darren


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 72bf6403-9bea-472f-988c-e629c787e43d root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 15176 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the /multiboot 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   438,586,997   438,584,950   7 NTFS / exFAT / HPFS
/dev/sdc2         438,587,390   488,396,799    49,809,410   5 Extended
/dev/sdc5         438,587,392   481,056,767    42,469,376  83 Linux
/dev/sdc6         481,058,816   488,396,799     7,337,984  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1998 MB, 1998585856 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63     3,887,729     3,887,667   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2EF8F900F8F8C6DD                       ntfs       External
/dev/sdb1        0E605A69605A5813                       ntfs       
/dev/sdc1        04CC5A65CC5A50D2                       ntfs       Storage
/dev/sdc5        72bf6403-9bea-472f-988c-e629c787e43d   ext4       
/dev/sdc6        66820c91-4f73-4f5d-afbc-7121236d4dbb   swap       
/dev/sdd1        11E3-3F27                              vfat       MULTIBOOT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
--------------------------------------------------------------------------------

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root 72bf6403-9bea-472f-988c-e629c787e43d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root 72bf6403-9bea-472f-988c-e629c787e43d
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 72bf6403-9bea-472f-988c-e629c787e43d
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=72bf6403-9bea-472f-988c-e629c787e43d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 72bf6403-9bea-472f-988c-e629c787e43d
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=72bf6403-9bea-472f-988c-e629c787e43d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 72bf6403-9bea-472f-988c-e629c787e43d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=72bf6403-9bea-472f-988c-e629c787e43d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 72bf6403-9bea-472f-988c-e629c787e43d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=72bf6403-9bea-472f-988c-e629c787e43d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 72bf6403-9bea-472f-988c-e629c787e43d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 72bf6403-9bea-472f-988c-e629c787e43d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 0E605A69605A5813
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

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=72bf6403-9bea-472f-988c-e629c787e43d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=66820c91-4f73-4f5d-afbc-7121236d4dbb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 217.287330627 = 233.310494720  boot/grub/core.img                             1
 211.387454987 = 226.975551488  boot/grub/grub.cfg                             1
 210.447265625 = 225.966030848  boot/initrd.img-2.6.38-11-generic              2
 211.013893127 = 226.574442496  boot/initrd.img-2.6.38-8-generic               2
 210.201480865 = 225.702121472  boot/vmlinuz-2.6.38-11-generic                 1
 217.286022186 = 233.309089792  boot/vmlinuz-2.6.38-8-generic                  1
 210.447265625 = 225.966030848  initrd.img                                     2
 211.013893127 = 226.574442496  initrd.img.old                                 2
 210.201480865 = 225.702121472  vmlinuz                                        1
 217.286022186 = 233.309089792  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  68 cd cf 7c 1d 00 ed 28  e0 7d c7 a3 e2 2c 84 94  |h..|...(.}...,..|
00000010  dc 26 48 d1 ba d0 51 85  06 8d 67 da b3 81 81 a9  |.&H...Q...g.....|
00000020  08 01 94 43 2c b2 b6 ee  06 a0 0d 03 40 a8 18 48  |...C,.......@..H|
00000030  18 c4 b4 e2 fb f3 64 94  e5 be c8 5f 38 81 0d 62  |......d...._8..b|
00000040  8d b6 1c 60 14 26 0d 0c  37 32 48 d0 0c 40 60 8c  |...`.&..72H..@`.|
00000050  9e ae 6c 5e 26 06 6c e0  1e 40 19 93 1c 30 31 8f  |..l^&.l..@...01.|
00000060  e2 b5 16 1a 37 7f 8f 3a  f2 0e e6 5a 0c 30 01 e8  |....7..:...Z.0..|
00000070  16 24 b6 38 e8 34 b0 d7  e9 0c ee 4a ed f0 c3 b8  |.$.8.4.....J....|
00000080  98 07 60 5c 6b 9f bc 1a  4a 5a c3 80 ec 18 19 b3  |..`\k...JZ......|
00000090  84 f1 a1 f2 52 71 cb ba  d0 8c 5b ee 84 6e 4a 48  |....Rq....[..nJH|
000000a0  a5 c5 81 41 88 08 e8 61  26 34 05 7a 33 6e cb 14  |...A...a&4.z3n..|
000000b0  7d b1 2b 8c e1 39 27 8a  9d 23 55 95 47 91 f9 9b  |}.+..9'..#U.G...|
000000c0  d7 13 8c b2 ea 4a 85 a5  1e de 7b 8f b2 39 76 dd  |.....J....{..9v.|
000000d0  db 91 4b 50 94 6e 2c f8  e0 02 c3 38 75 36 3d 22  |..KP.n,....8u6="|
000000e0  14 34 96 de 98 01 e8 92  38 ab c7 5d 43 0d 96 de  |.4......8..]C...|
000000f0  46 c9 2a 19 1b f8 48 02  da 2f 7c b8 a6 5d db 55  |F.*...H../|..].U|
00000100  f4 f8 12 39 bf a6 e0 71  77 d1 ba 0c 00 76 4d c4  |...9...qw....vM.|
00000110  b6 25 08 f0 06 a8 42 39  fb 1a 06 e0 13 93 48 60  |.%....B9......H`|
00000120  37 c0 60 94 1a 59 0c a5  70 1b 02 27 fd 8e 70 24  |7.`..Y..p..'..p$|
00000130  2f c0 20 40 0e fe 1a 80  d2 61 29 2c 71 49 76 c4  |/. @.....a),qIv.|
00000140  18 98 18 18 a6 1a 30 70  f1 26 58 8b cc 00 7a 03  |......0p.&X...z.|
00000150  ae 51 30 06 24 c2 d2 71  4e 17 00 3d 00 7b b1 34  |.Q0.$..qN..=.{.4|
00000160  86 e5 29 01 b8 2c 5c c1  bc b4 23 1b cf 73 db 1c  |..)..,\...#..s..|
00000170  b8 01 69 09 80 42 42 02  5c 99 9b e8 66 0d c3 50  |..i..BB.\...f..P|
00000180  e3 82 f1 16 41 6a e3 6d  86 18 80 28 4c 2c 30 86  |....Aj.m...(L,0.|
00000190  94 06 f0 2c 02 47 1d 00  2d 0c 4e 01 d0 0d 89 a9  |...,.G..-.N.....|
000001a0  29 c5 0a 80 16 94 03 a2  16 21 70 d0 18 96 31 03  |)........!p...1.|
000001b0  40 50 2d 8f 68 86 00 fc  0a 93 43 50 51 08 00 fe  |@P-.h.....CPQ...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 88 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 08  88 02 00 00 70 00 00 00  |............p...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

no raid sets 

=============================== StdErr Messages: ===============================

ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdc to RAID set "sil_aiagebahfhaj"
ERROR: no RAID set found
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdc to RAID set "sil_aiagebahfhaj"
ERROR: only one argument allowed for this option
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdc to RAID set "sil_aiagebahfhaj"
ERROR: no RAID set found
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdc to RAID set "sil_aiagebahfhaj"
ERROR: no RAID set found
unlzma: Decoder error
unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdc to RAID set "sil_aiagebahfhaj"
ERROR: only one argument allowed for this option

```

---

### Post by Hakunka-Matata on 2011-10-01
Hi, What drive is BIOS booting first?  If it is not sdc, I would try setting BIOS to boot sdc first, that looks like it should work.

---

### Post by oldfred on 2011-10-01
+1 on Hakunka-Matata's suggestion of booting from sdc.

The script has some errors related to RAID:
> ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdc to RAID set "sil_aiagebahfhaj"
ERROR: no RAID set found


It used to be that grub would not install if a drive had old RAID info in it. Was this drive in a RAID set or did you at one time turn RAID on in BIOS? But grub does look correct.

---

