---
title: "Help! Windows 8 has disappeared!"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by orenofhowick on 2013-04-27
I just bought an Acer laptop with Windows 8 preinstalled (no windows disk). I reduced the windows partition and tried to install LinuxMint but it seems I can't do that with the current partitioning format, so I turned to Ubuntu. I have had success installing Ubuntu but Grub2 doesn't appear when Iboot- it just goes straight into Ubunto!?

I have tried holding down shift during boot to no avail. I tried control-alt-delete during boot which didn't seem to do anything. If anybody knows what has gone wrong I would appreciate any insights.

The boot-info-script is as follows:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       821,247       819,200 Windows Recovery Environment (Windows)
/dev/sda2         821,248     1,435,647       614,400 EFI System partition
/dev/sda3       1,435,648     1,697,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,697,792   535,715,839   534,018,048 Data partition (Windows/Linux)
/dev/sda5     535,715,840   565,012,714    29,296,875 Swap partition (Linux)
/dev/sda6     945,315,840   976,773,119    31,457,280 Windows Recovery Environment (Windows)
/dev/sda7     565,014,528   936,105,983   371,091,456 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 20.0 GB, 20014718976 bytes
256 heads, 63 sectors/track, 2423 cylinders, total 39091248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1       7,839,744    39,090,175    31,250,432 -
/dev/sdb2           2,048     7,837,695     7,835,648 -

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FA363ED7363E951B                       ntfs       Recovery
/dev/sda2        8C41-7930                              vfat       ESP
/dev/sda4        665A45EB5A45B917                       ntfs       Acer
/dev/sda5        aabd7019-696c-41ac-985b-028ef251fee3   swap       
/dev/sda6        38F4481EF447DCAE                       ntfs       Push Button Reset
/dev/sda7        bdbce198-8be3-4ce1-aed0-09643a749b18   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw)
/dev/sda7        /                        ext4       (rw,errors=remount-ro)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt7)'
search --no-floppy --fs-uuid --set=root bdbce198-8be3-4ce1-aed0-09643a749b18
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt7)'
  search --no-floppy --fs-uuid --set=root bdbce198-8be3-4ce1-aed0-09643a749b18
  set locale_dir=($root)/boot/grub/locale
  set lang=en_NZ
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
menuentry 'Ubuntu, with Linux 3.5.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root bdbce198-8be3-4ce1-aed0-09643a749b18
    linux    /boot/vmlinuz-3.5.0-27-generic root=UUID=bdbce198-8be3-4ce1-aed0-09643a749b18 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root bdbce198-8be3-4ce1-aed0-09643a749b18
    echo    'Loading Linux 3.5.0-27-generic ...'
    linux    /boot/vmlinuz-3.5.0-27-generic root=UUID=bdbce198-8be3-4ce1-aed0-09643a749b18 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-27-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root bdbce198-8be3-4ce1-aed0-09643a749b18
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=bdbce198-8be3-4ce1-aed0-09643a749b18 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root bdbce198-8be3-4ce1-aed0-09643a749b18
    echo    'Loading Linux 3.5.0-23-generic ...'
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=bdbce198-8be3-4ce1-aed0-09643a749b18 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root bdbce198-8be3-4ce1-aed0-09643a749b18
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root bdbce198-8be3-4ce1-aed0-09643a749b18
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

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
UUID=bdbce198-8be3-4ce1-aed0-09643a749b18 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=8C41-7930  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda5 during installation
UUID=aabd7019-696c-41ac-985b-028ef251fee3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.5.0-23-generic               1
               =                boot/initrd.img-3.5.0-27-generic               1
               =                boot/vmlinuz-3.5.0-23-generic                  1
               =                boot/vmlinuz-3.5.0-27-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
5850cbb887c11947baf0379ca2d4c97e
Unknown GPT Partiton Type
dee2bfd3af3ddf11ba40e3a556d89593
Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 5e 1b  |.X.MSDOS5.0...^.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 0c 00  |........?.......|
00000020  00 60 09 00 51 02 00 00  00 00 00 00 02 00 00 00  |.`..Q...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 30 79 41 8c 4e  4f 20 4e 41 4d 45 20 20  |..)0yA.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sdb2

00000000  e8 32 07 71 c3 ce d3 04  28 00 00 00 00 00 00 00  |.2.q....(.......|
00000010  00 00 00 00 00 00 00 00  00 ff ff 1f 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 f8 1f 00 00 00 00  |................|
00000030  00 00 00 00 fe 40 e4 06  e2 26 dc 0d 10 7e d8 f9  |.....@...&...~..|
00000040  45 b4 6b fd 9e 9f e1 35  50 6e ff ff ff ff ff ff  |E.k....5Pn......|
00000050  01 00 09 07 00 00 20 10  00 00 10 30 05 00 00 00  |...... ....0....|
00000060  d0 11 ee 07 11 00 a1 01  00 00 c5 65 00 00 00 00  |...........e....|
00000070  30 c0 19 f0 6d fa 7f f8  18 04 00 00 80 00 00 40  |0...m..........@|
00000080  c2 40 00 80 50 40 00 2a  01 08 00 11 c0 00 00 90  |.@..P@.*........|
00000090  61 03 00 00 90 81 45 11  19 33 b4 13 00 78 40 80  |a.....E..3...x@.|
000000a0  84 2c e9 24 00 04 28 05  66 98 04 00 06 7c 08 04  |.,.$..(.f....|..|
000000b0  ff bb 2a 20 02 e7 cf f9  07 4d 0a 00 20 ca 5b fe  |..* .....M.. .[.|
000000c0  c7 31 00 15 2f cd 0b 9a  21 06 40 0b 20 00 02 30  |.1../...!.@. ..0|
000000d0  00 1a 1a 87 5a a4 05 64  00 10 47 68 19 70 fb ff  |....Z..d..Gh.p..|
000000e0  fd 86 2a e1 f0 79 ca ef  df 15 af af ef fd c1 67  |..*..y.........g|
000000f0  0f d8 a5 93 ff 9f 7f e8  07 ff d5 12 aa c7 6d 75  |..............mu|
00000100  f5 ed 62 d3 77 ef be 9e  f9 77 8a e1 b1 bb ff 8a  |..b.w....w......|
00000110  fe 6f bf a4 72 ff f5 ba  ef bb 54 00 ec f7 ff ff  |.o..r.....T.....|
00000120  f7 df df bf ff ff ff ff  ff bf ff bf f7 ff 7f ff  |................|
00000130  fb 9f d3 ff 66 ff 7f ff  ff df ee a7 66 ff ff ff  |....f.......f...|
00000140  f7 7f 3d a0 27 cf ff fe  fd df df 97 bf 47 7e ff  |..=.'........G~.|
00000150  b9 c7 83 02 fc ff ff 7f  ff 9f ff bf ff ff ff 7f  |................|
00000160  ff 9f ff f7 ff ff ff 7f  ff 9f ff ff ff ff ff ff  |................|
00000170  ff 9f ff ff ff ff ff ff  ff 9f ff ff ff ff ff ff  |................|
00000180  ff 9f ff bb ff ff ff ff  ff ff ff fd ff ff ff ff  |................|
00000190  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
000001a0  ff ff ff ff ff ff ff ff  ff ff ff fb ff ff ff ff  |................|
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
000001c0  fd ff ff ff f7 ff ff bf  ff 9f ff bf ff ff bf 7f  |................|
000001d0  ff 9f ff ff ff ff ff ff  fe 9f ff df ff ff 9f 7f  |................|
000001e0  ff 9f ff ff ff ff ff 7f  ff 9f ff ff ff ff ff 7f  |................|
000001f0  ff 9f ff bf ff ff ff ff  ff df 2f 7a 04 c3 bf 7f  |........../z....|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by MAFoElffen on 2013-04-28
The key to try is the left <Shift> key. Right after the BIOS POST messages, start pressing it repeatedly, not held down. If it still boots directly into Ubuntu without showing a menu... Then follow these instructions: **[Forcing Grub to Show Menu]("http://ubuntuforums.org/showpost.php?p=11469860&postcount=800") **But it boots into Ubuntu right??? 

With a dual-boot, it should have presented a menu if it found another OS present. In your case Windows 8. I see your GPT partition... But then:
```

### BEGIN /etc/grub.d/30_uefi-firmware 
###### END /etc/grub.d/30_uefi-firmware ###
...
GUID Partition Table detected

```
Since it didn't find that... It did't find your install of Win8. It wasn't running in uefi mode when it installed Ubuntu, so when it installed the boot loader, it again wasn't running in efi mode and didn't see Win8. Most new systems running Win8 are running on efi or secure boot... That's what I see going on.

I think "oldfred" summed it up best here:
[http://ubuntuforums.org/showthread.php?t=2134667&p=12600168#post12600168](http://ubuntuforums.org/showthread.php?t=2134667&p=12600168#post12600168)

Although his comment on: "[COLOR=#000000]Windows is not designed to multi-boot" is a little slighted. Windows Boot Manager can be made to multi-boot other OS'es, but it really favors other Windows OS'es and it is not easy to do for normal non-technical users.[/COLOR]

Advice? He recommends Yann's "Boot Repair ISO."  Another would be the Secure Boot ISO.

---

### Post by oldfred on 2013-04-28
Is this an UltraBook? 
It looks like the 20GB drive is a small SSD for caching Windows. That uses Intel SRT which somehow uses RAID and grub does not install to RAID from the desktop and with that type of RAID you do not want it installing inside the RAID anyway.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
      
 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by orenofhowick on 2013-04-29
Hi guys,

First of all thanks to you both for for replying. Unfortunately I didn't see either of your replies before wasting a lot of time on this problem and then finally solving it. 

In the (F12) boot menu Windows Boot Manager wasn't coming up,so in the (F2) menu I restored the boot to factory settings, disabling secure boot. This allowed me to boot to windows only, unless I changed the boot order (F2) to put the HDD boot ahead of Windows Boot Manager (which had now returned) allowing me to boot to Ubuntu only. I thithis was working because I set the Ubuntu boot sector to loadin the root drive (didn't specify a partition). Still no option at startup.

Then I burnt the ISO of "Boot Repair Disc" onto a DVD to run, but couldn't work out how to make the disc run at boot, even when I bumped the DVD reader to the top of the boot sequence! Finally I found a page that gave me simple instructions to upload and run Boot Repair disc from the Ubuntu console:
[http://askubuntu.com/questions/278192/cant-boot-windows-8-after-installing-ubuntu-12-10](http://askubuntu.com/questions/278192/cant-boot-windows-8-after-installing-ubuntu-12-10)
I ran recommended repair and done!

Took a while longer to fix my partition sizes and add more useful mount points to my existing partitions, but that was another story! Enjoying the steep learning curve on Ubuntu

Cheers

---

