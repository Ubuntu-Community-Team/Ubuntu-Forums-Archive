---
title: "Can't boot into Windows XP"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by jdbartram on 2011-06-22
I just installed Ubuntu 11.04 from a USB drive per the instructions from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) to a Toshiba NB205 Netbook.

Ubuntu worked fine. I saw warnings about upgrading Grub somewhere, but forgot and clicked Install Updates in Update Manager.

When I start the computer, Grub version 1.99 runs. Selecting Ubuntu works, but selecting Microsoft Windows XP Home Edition goes to the "Windows did not start successfuly" screen. Selecting any of the choices gives the Windows XP screen very briefly and then goes back to GRUB.

I did not try booting into Windows XP before I installed upgrades, so I don't know if this is an installation problem or a Grub problem.

I know very little about Linux, and have not used the command line since DOS.

Thanks for any help.

---

### Post by kkrueger on 2011-06-22
Hey
    Not sure if this will do much, but if the warning was simply about updating grub the following command should do just that. 

```
 sudo update-grub 
```

    Let me know if it helps :D

---

### Post by jdbartram on 2011-06-22
Thanks for the suggestion. I tried it and have the same problem, can't boot into Windows XP. I think the message was to NOT upgrade Grub, but I'm not sure now.

---

### Post by garvinrick4 on 2011-06-22
gedit /boot/grub/grub.cfg
see if it has windows entry:

If it does then you have another problem besides update-grub
Here is a bootscript to run which will tell the whole story and make it easy to fix.
post results here, if need help just say so and will give complete instructions.
It is in a .zip file:
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by jdbartram on 2011-06-23
Thanks garvinrick4. There is a windows entry in Grub. Two in fact.. I think Toshiba put something in for recovery. Neither one will boot. The second one says something about not being able to find some files.

Here are the results of the boot info script.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   187,527,905   187,527,843   7 NTFS / exFAT / HPFS
/dev/sda2         296,849,070   312,576,704    15,727,635  1c Hidden W95 FAT32 (LBA)
/dev/sda3         187,529,214   296,847,359   109,318,146   5 Extended
/dev/sda5         187,529,216   292,673,535   105,144,320  83 Linux
/dev/sda6         292,675,584   296,847,359     4,171,776  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        54D0DC47D0DC30CA                       ntfs       TI100277P0G
/dev/sda2        0401-0163                              vfat       HDDRECOVERY
/dev/sda5        a08c737e-a82a-4271-b378-b6c4f25d068a   ext4       
/dev/sda6        7faf50da-2c23-4221-ac77-322236eb2089   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a08c737e-a82a-4271-b378-b6c4f25d068a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a08c737e-a82a-4271-b378-b6c4f25d068a
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a08c737e-a82a-4271-b378-b6c4f25d068a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a08c737e-a82a-4271-b378-b6c4f25d068a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a08c737e-a82a-4271-b378-b6c4f25d068a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a08c737e-a82a-4271-b378-b6c4f25d068a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a08c737e-a82a-4271-b378-b6c4f25d068a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a08c737e-a82a-4271-b378-b6c4f25d068a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 54D0DC47D0DC30CA
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 0401-0163
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
UUID=a08c737e-a82a-4271-b378-b6c4f25d068a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7faf50da-2c23-4221-ac77-322236eb2089 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 135.554931641 = 145.550999552  boot/grub/core.img                             1
 133.760971069 = 143.624749056  boot/grub/grub.cfg                             1
  91.120338440 = 97.839718400   boot/initrd.img-2.6.38-8-generic               1
 135.553203583 = 145.549144064  boot/vmlinuz-2.6.38-8-generic                  1
  91.120338440 = 97.839718400   initrd.img                                     1
 135.553203583 = 145.549144064  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  93 78 e0 41 ef f7 94 06  f8 4c 1b 3b 8e a1 2d f6  |.x.A.....L.;..-.|
00000010  da f4 3b 7d 47 e3 ed e3  af 76 21 3c 54 14 cc 25  |..;}G....v!<T..%|
00000020  fd a5 1b 31 16 20 76 fe  3b ed ca 49 91 be dc 79  |...1. v.;..I...y|
00000030  7d 5b 64 77 f9 5f 22 10  60 18 cc 25 8d fd 93 7b  |}[dw._".`..%...{|
00000040  15 56 f0 45 1c 30 81 68  de 3a f7 ef b8 9a d5 2c  |.V.E.0.h.:.....,|
00000050  ef 3b 9d ad fb 3c a0 2a  4b 6c 2a 59 fb 92 5a 1e  |.;...<.*Kl*Y..Z.|
00000060  84 ef fa 4a d5 00 6d f5  75 61 e5 4b c7 48 49 32  |...J..m.ua.K.HI2|
00000070  92 cf 56 4f c0 39 eb 67  fc 1f da e9 a8 e6 c3 f0  |..VO.9.g........|
00000080  2b 76 73 f4 2c a0 55 89  ef cb c1 af 9d cf 37 4c  |+vs.,.U.......7L|
00000090  eb 88 b0 6b 46 ad 1b fa  4c f6 c4 d4 f5 ed 46 fb  |...kF...L.....F.|
000000a0  ed a4 f7 30 1d e8 f6 c5  b0 c6 26 66 1a 55 0d a3  |...0......&f.U..|
000000b0  e5 fa fc 20 bc a6 f2 c7  30 7d d7 fd f4 ed e6 6d  |... ....0}.....m|
000000c0  51 69 94 23 fc 8e 58 ba  2a e6 e7 5a 26 50 cc bb  |Qi.#..X.*..Z&P..|
000000d0  43 ec a4 f7 91 35 47 78  2f c1 8c 31 6d 67 33 f6  |C....5Gx/..1mg3.|
000000e0  85 84 23 3c cc e1 a8 86  94 ed e9 47 1f 92 f7 06  |..#<.......G....|
000000f0  0a ad f5 29 bc cc 9d f0  66 fe 9e d8 b1 2c 19 29  |...)....f....,.)|
00000100  f4 3a 6d d0 af 7f de c5  cf 2c e8 3a 10 73 4f f9  |.:m......,.:.sO.|
00000110  f8 77 52 8b 03 0a 88 93  88 00 73 34 26 b6 44 db  |.wR.......s4&.D.|
00000120  4f 62 06 89 57 81 c2 5e  72 49 80 31 e0 c9 1c 6c  |Ob..W..^rI.1...l|
00000130  b4 c9 9f 4e f6 2c 05 85  b3 73 b6 00 33 2b cc c0  |...N.,...s..3+..|
00000140  f1 4e c7 dd d9 1b 1e 02  01 05 44 9e 4f 90 f9 b2  |.N........D.O...|
00000150  cd c8 af 65 d4 0d 1b 0a  4f b4 68 bc 6e 87 b5 ad  |...e....O.h.n...|
00000160  31 ef 05 19 dc 5d 7f f7  a2 42 b2 33 4f 56 e2 1d  |1....]...B.3OV..|
00000170  3c 57 24 65 93 10 d3 a9  11 c3 d1 56 2a ae a7 ca  |<W$e.......V*...|
00000180  d1 b2 eb 7b 81 6b 8a 2b  e6 0b 33 0e c6 bb 8f ae  |...{.k.+..3.....|
00000190  cd 5b 57 48 2a d6 e6 bf  1a 40 7b 34 8a 23 cc 2c  |.[WH*....@{4.#.,|
000001a0  d9 fe 60 bd f7 fe 9a f6  6d 5b e0 5d f3 8c 51 c5  |..`.....m[.]..Q.|
000001b0  78 c8 a7 54 11 c6 47 66  75 5c a9 50 db 7e 00 fe  |x..T..Gfu\.P.~..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 44 06 00 fe  |...........`D...|
000001d0  ff ff 05 fe ff ff 02 60  44 06 00 b0 3f 00 00 00  |.......`D...?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by hakimoerton on 2011-06-23
I too have stuffed up my windoze boot when upgrading grub 2

Have two HDDs, one with Vista and one with 10.04. I would choose which disk to load at boot time. Ran update this morning and in 7 days of updates, Grub 2 was updated. I was asked if I wanted to place grub on each disk and (foolishly) said yes. Now I can only boot into lucid. Physically disconnecting the lucid drive just gives a grub> prompt.

Ran boot_info_script and the results are:
```

---------------------------------------------------------------------------
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /ntdetect.com

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 565127 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 1 for /boot/grub.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    18,426,554    18,426,492  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     18,426,555   323,131,409   304,704,855   7 NTFS / exFAT / HPFS
/dev/sda3         323,131,410   625,137,344   302,005,935   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    16,386,299    16,386,237  83 Linux
/dev/sdb2          16,386,300   614,052,494   597,666,195  83 Linux
/dev/sdb3         614,052,495   625,137,344    11,084,850   5 Extended
/dev/sdb5         614,052,558   625,137,344    11,084,787  82 Linux swap / Solaris


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 8010 MB, 8010301440 bytes
16 heads, 16 sectors/track, 61113 cylinders, total 15645120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1               8,064    15,645,119    15,637,056   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8E90F0B816D9B5D2                       ntfs       PQSERVICE
/dev/sda2        2694E4DF94E4B28B                       ntfs       ACER
/dev/sda3        04C09010C09009D6                       ntfs       DATA
/dev/sdb1        0033ad3c-ef20-4c4e-9057-c02c791f1256   ext4       
/dev/sdb2        ac1b2b3e-a341-42c3-bad3-adbc9920d7d1   ext4       /home
/dev/sdb5        e410a8ff-bc61-4aed-ac36-a981344e2073   swap       
/dev/sdg1        AE72-E1B2                              vfat       USB DISK

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb2        /home                    ext4       (rw)
/dev/sdg1        /media/USB DISK          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=0033ad3c-ef20-4c4e-9057-c02c791f1256 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=0033ad3c-ef20-4c4e-9057-c02c791f1256 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0033ad3c-ef20-4c4e-9057-c02c791f1256 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0033ad3c-ef20-4c4e-9057-c02c791f1256 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0033ad3c-ef20-4c4e-9057-c02c791f1256 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0033ad3c-ef20-4c4e-9057-c02c791f1256 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=0033ad3c-ef20-4c4e-9057-c02c791f1256 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=0033ad3c-ef20-4c4e-9057-c02c791f1256 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0033ad3c-ef20-4c4e-9057-c02c791f1256
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8E90F0B816D9B5D2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 2694E4DF94E4B28B
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0033ad3c-ef20-4c4e-9057-c02c791f1256 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=ac1b2b3e-a341-42c3-bad3-adbc9920d7d1 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=e410a8ff-bc61-4aed-ac36-a981344e2073 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.269500256 = 0.289373696    boot/grub/core.img                             1
   3.403556347 = 3.654540800    boot/grub/grub.cfg                             1
   3.846614361 = 4.130270720    boot/initrd.img-2.6.31-14-generic              1
   2.867724895 = 3.079196160    boot/initrd.img-2.6.32-22-generic              1
   2.882453442 = 3.095010816    boot/initrd.img-2.6.32-23-generic              1
   4.707461834 = 5.054598656    boot/initrd.img-2.6.32-32-generic              1
   2.373076916 = 2.548071936    boot/vmlinuz-2.6.31-14-generic                 2
   2.097533703 = 2.252209664    boot/vmlinuz-2.6.32-22-generic                 1
   2.077235699 = 2.230414848    boot/vmlinuz-2.6.32-23-generic                 1
   2.913341045 = 3.128176128    boot/vmlinuz-2.6.32-32-generic                 1
   4.707461834 = 5.054598656    initrd.img                                     1
   2.882453442 = 3.095010816    initrd.img.old                                 1
   2.913341045 = 3.128176128    vmlinuz                                        1
   2.077235699 = 2.230414848    vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

--------------------------------------------------------------------------

```
The pc is an Acer Aspire E700 MMX 3 4GB ram, system and data partitions on each HDD

Help please.
Hakim

---

### Post by drs305 on 2011-06-23
I think you should target Windows as the problem here. The "Windows did not start successfuly" message is not one that Grub would generate.

Using a Windows repair disk will probably help you recover Windows, and then you can reinstall Grub2 from the Ubuntu LiveCD by mounting your Ubuntu partition and installing Grub to the MBR (not the partition).

Here is one 'repair' link:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by jdbartram on 2011-06-23
[[COLOR=#d40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")drs305, I tried the instructions for Windows XP that you linked to - running the installation CD - and I got a blue screen.

---

### Post by westie457 on 2011-06-23
> **drs305 said:**
> I think you should target Windows as the problem here. The "Windows did not start successfuly" message is not one that Grub would generate.

Using a Windows repair disk will probably help you recover Windows, and then you can reinstall Grub2 from the Ubuntu LiveCD by mounting your Ubuntu partition and installing Grub to the MBR (not the partition).

Here is one 'repair' link:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

Hello, do you have a Windows Install DVD? If yes stick that in the DVD-drive and re-boot. You should get a line of text on screen saying "Press any key to boot from CD/DVD"

The Windows DVD overrides any settings that you have in your BIOS.


In the next window select your Country and keyboard layout. Press Enter.

When the Install window appears select the option to repair your computer.

You might have to enter your Windows password as well

The next window will have several options - start-up repair, restore from an image, restore to an earlier point with System Restore, Memtest and 1 or 2 others.

Select Start-up repair, the system will then look for Windows installations. If it cannot find any that match the DVD it will stop and let you know. It should find only one ie whatever Windows you installed, click on continue and wait following any prompts that come up.

Look through the report that is displayed after. It might say at the end that the OS booted correctly. Try re-booting, if the repairs were successful then you will be in Windows. If unsuccessful you will be at the repair screen again. DO NOT PANIC.

Select the last option which is "Open a Command-Prompt"

Enter these commands 1 at a time -ignoring the quote marks-pressing enter after each

"bootrec /fixmbr"
"bootrec /fixboot"
"bootrec /rebuildbcd"

Type in exit or quit then Reboot.

You will now have a working system without any Grub prompt and you will be free to reinstall Grub as previously suggested

---

### Post by westie457 on 2011-06-23
On second thoughts use the link that 'drs305' posted. My post is for Windows 7 boot recovery.

---

### Post by jdbartram on 2011-06-23
westie457, as I mentioned to drs305 above, when I run a Windows XP install disc, I never get to the point where I can choose to do anything. I end up with a blue screen that says,

A problem has been detected and windows has been shut down to prevent damage to your computer ...

There was no install disc that came with this netbook, so I am using one from a Dell desktop. I wouldn't think that would matter though.

---

### Post by Je Et on 2011-06-23
Try booting from recovery mode and then update grub. You did say if you had a side by side or separate HHD installation... should work with either. 

Je Et

---

### Post by jdbartram on 2011-06-23
Je Et, if I try to boot into the second windows partition from grub, I get C:\BIN\ERRORDIALOG.EXE message that says, "Windows cannot find 'C:BIN\ERRORDIALOG.EXE'. mAKE SURE YOU TYPED THE NAME CORRECTLY, AND THEN TRY AGAIN. ... (of course, I didn't type it, it ran from a file).

Clicking OK, give a C\BIN\BOOTPRIORITY.EXE message that says, "Windows cannot find 'C:\BIN\BOOTPRIORITY.EXE' ...

Clicking OK takes me back to the GRUB choices

So, that doesn't help.

---

### Post by hakimoerton on 2011-06-23
> **westie457 said:**
> Hello, do you have a Windows Install DVD? If yes stick that in the DVD-drive and re-boot. You should get a line of text on screen saying "Press any key to boot from CD/DVD"

The Windows DVD overrides any settings that you have in your BIOS.


In the next window select your Country and keyboard layout. Press Enter.

When the Install window appears select the option to repair your computer.

You might have to enter your Windows password as well

The next window will have several options - start-up repair, restore from an image, restore to an earlier point with System Restore, Memtest and 1 or 2 others.

Select Start-up repair, the system will then look for Windows installations. If it cannot find any that match the DVD it will stop and let you know. It should find only one ie whatever Windows you installed, click on continue and wait following any prompts that come up.

Look through the report that is displayed after. It might say at the end that the OS booted correctly. Try re-booting, if the repairs were successful then you will be in Windows. If unsuccessful you will be at the repair screen again. DO NOT PANIC.

Select the last option which is "Open a Command-Prompt"

Enter these commands 1 at a time -ignoring the quote marks-pressing enter after each

"bootrec /fixmbr"
"bootrec /fixboot"
"bootrec /rebuildbcd"

Type in exit or quit then Reboot.

You will now have a working system without any Grub prompt and you will be free to reinstall Grub as previously suggested

Thank you very much. Worked like a charm on my Vista/Lucid setup.
Needed the bootrec commands but then rebooted straight back into Vista, as desired.

All so I could watch an Aussie play tennis at Wimbledon. Use a tuner card to access digital channels and Lucid won't recognise the card.

Again, many thanks.
Hakim

---

### Post by garvinrick4 on 2011-06-23
> **jdbartram said:**
> westie457, as I mentioned to drs305 above, when I run a Windows XP install disc, I never get to the point where I can choose to do anything. I end up with a blue screen that says,
 
A problem has been detected and windows has been shut down to prevent damage to your computer ...
 
There was no install disc that came with this netbook, so I am using one from a Dell desktop. I wouldn't think that would matter though.
Try using the Ubuntu install Cd or USB and choose Try Ubuntu when it boots up get internet
connection and then:
[FONT=Times New Roman]#Restore basic windows boot loader - universe enabled 
```
sudo apt-get install lilo
```
```
sudo lilo -M [[COLOR=#3465a4]/dev/sda[/COLOR]]("file:///C:/dev/sda") mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR
Now reboot and see if Windows boots now. If it does we can put grub back to boot both.
[/FONT]

---

### Post by jdbartram on 2011-06-23
garvinrick4, thanks for the follow up. I followed your instructions. At one point after the first line, there was a message that said I needed to run liloconfig ( 8 ) and execute /sbin/lilo or else lilo wouldn't work. These two commands did not seem to be valid (got error messages). However, when I ran the second line, (sudo lilo -M /dev/sda mbr), I got a message that the mbr had been successfully reloaded or whatever. 

Now the computer does not come up in grub, but goes to the "Windows did not start successfully ..." screen. Choosing any of the choices (Safe Mode(s) or boot Windows Normally), results in the Windows XP logo screen for a few seconds and then back to the "Windows did not start successfully" screen.

---

### Post by westie457 on 2011-06-23
> **jdbartram said:**
> westie457, as I mentioned to drs305 above, when I run a Windows XP install disc, I never get to the point where I can choose to do anything. I end up with a blue screen that says,

A problem has been detected and windows has been shut down to prevent damage to your computer ...

There was no install disc that came with this netbook, so I am using one from a Dell desktop. I wouldn't think that would matter though.

Hi, it probably does make a difference. The Dell CD is an OEM Disc and ot is looking for certain components and codes built-in to Dell equipment. If you can borrwo a genuine CD use that with no problem. Or using a LiveCD download and burn a windows recovery-disc. Something like BartPE should do it. Find it here [http://www.nu2.nu/pebuilder/]("http://www.nu2.nu/pebuilder/")

---

### Post by westie457 on 2011-06-23
> **jdbartram said:**
> garvinrick4, thanks for the follow up. I followed your instructions. At one point after the first line, there was a message that said I needed to run liloconfig ( 8 ) and execute /sbin/lilo or else lilo wouldn't work. These two commands did not seem to be valid (got error messages). However, when I ran the second line, (sudo lilo -M /dev/sda mbr), I got a message that the mbr had been successfully reloaded or whatever. 

Now the computer does not come up in grub, but goes to the "Windows did not start successfully ..." screen. Choosing any of the choices (Safe Mode(s) or boot Windows Normally), results in the Windows XP logo screen for a few seconds and then back to the "Windows did not start successfully" screen.

You are nearly there. Try again and immediately after the POST screen start tapping the F8 key. This will bring up a menu with various options. Somewhere on that screen should be choose advanced options. use the TAB key to highlight. Hit Enter you should then get an option to repair your computer using a command prompt. type in the commands that were provided in the link 'drs305' posted earlier. Reboot and XP should be back.

Then come back here to ask fixing Grub using a LiveCD.

One question. Did 'Rescatux' fail to fix Grub for you?

---

### Post by jdbartram on 2011-06-24
westie457, tapping the F8 screen did bring up some more choices. None of them gave the option to repair the computer. All resulted in looping back to the "Windows did not start successfully..." screen.

I did not use Rescatux.

---

### Post by jdbartram on 2011-06-24
kkrueger, garvinrick4, hakimoerton, drs305, westie457 and Je Et, 

Thanks for your replies and attempts to help me. Since none of your suggestions seemed to be making any difference, I decided that probably some part of Windows XP had been messed up during the Ubuntu installation, so I restored it from a Recovery disk I had created after purchasing the netbook.

Following the restoration of XP, I installed Ubuntu from a CD this time (used a usb memory drive before). I ran upgrades from Ubuntu and this time Windows XP can be booted OK.

So, other than having to reinstall some software in XP, I have a functional laptop with both XP and Ubuntu.

Thanks again for trying to help!

Dave B.

---

