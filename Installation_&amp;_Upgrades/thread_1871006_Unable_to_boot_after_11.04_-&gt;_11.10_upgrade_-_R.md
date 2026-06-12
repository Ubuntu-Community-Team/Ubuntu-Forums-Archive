---
title: "Unable to boot after 11.04 -&gt; 11.10 upgrade - RAID problems?"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by mjec on 2011-10-28
So this is a bit of a curly one.

I have 2x 1TB SATA drives as striped RAID (so appearing as a 2TB disk) on which Ubuntu is installed (these are sda and sdb). I also have 1x 500Gb SATA drive with Windows 7 installed (sdc).

My Ubuntu installation is encrypted with LUKS: there's a 256 mb unencrypted boot partition; a 50Gb LVM which contains tmp and swap (random key) and 1950Gb root partition (password-based key).

On startup I get a timeout of dmraid-activate which means the device doesn't exist when cryptsetup tries to mount it. The error I end up with is "evms_activate is not available" but before that I see "udev killing /sbin/dmraid-activate"

I can start a live CD easily and mount the drive without any problem. So I started going through the initramfs and into dmraid-activate. I try each of the commands in turn and end up with:

```
root@ubuntu:/tmp/initrd/extracted# dmraid -i -r -cr /dev/sda
pdc_babdifjjd
root@ubuntu:/tmp/initrd/extracted# dmraid -i -r -cr /dev/sdb
ERROR: pdc: reading /dev/sdb[No such file or directory]
pdc_babdifjjd
```

Ok so it looks like it might be /dev/sdb? Still no timeout though and I mount fine in Live CD. That error goes to STDERR but doesn't halt and return code is still 0.

So at this point I'm stumped. Any help would be great!

I don't even know where to look for a log file showing those errors I get, and I'm not sure where to from here in debugging. I can't start up with previous kernel version. Is this a RAID driver issue? Is this a broken HDD? Most importantly is there anything I can do short of buying another 2TB of space and copying everything off, then reformatting?

I have a suspicion it's related to a change in how something is mounted between 11.04 and 11.10 but I'm not sure what that change may be. I also can't start with any of my grub entries - including 2.38 kernel series.

Some possibly-useful stuff follows.

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea750

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         256      499967      249856   83  Linux
/dev/sda2          499968    98156287    48828160   8e  Linux LVM
/dev/sda3        98156288  3906249983  1904046848   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeafc1624

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848  1953521663   976657408    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ba47bbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   976771071   488384512    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 4110 MB, 4110228480 bytes
154 heads, 38 sectors/track, 1371 cylinders, total 8027790 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc4690899

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048     8026111     4012032    b  W95 FAT32

Disk /dev/mapper/pdc_babdifjjd: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders, total 3906249984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x000ea750

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_babdifjjd1   *         256      499967      249856   83  Linux
/dev/mapper/pdc_babdifjjd2          499968    98156287    48828160   8e  Linux LVM
/dev/mapper/pdc_babdifjjd3        98156288  3906249983  1904046848   83  Linux

Disk /dev/mapper/pdc_babdifjjd1: 255 MB, 255852544 bytes
255 heads, 63 sectors/track, 31 cylinders, total 499712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_babdifjjd1 doesn't contain a valid partition table

Disk /dev/mapper/pdc_babdifjjd2: 50.0 GB, 50000035840 bytes
255 heads, 63 sectors/track, 6078 cylinders, total 97656320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_babdifjjd2 doesn't contain a valid partition table

Disk /dev/mapper/pdc_babdifjjd3: 1949.7 GB, 1949743972352 bytes
255 heads, 63 sectors/track, 237042 cylinders, total 3808093696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x08040000

Disk /dev/mapper/pdc_babdifjjd3 doesn't contain a valid partition table
```

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Truecrypt Boot Loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/pdc_babdifjjd and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and looks for (,msdos1)/grub on this drive.

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 15712 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the /multiboot 
                       directory. The integrity check of the ADV area failed. 
                       According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 2048.
    Operating System:  
    Boot files:        

pdc_babdifjjd1: ________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

pdc_babdifjjd2: ________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

pdc_babdifjjd3: ________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  

temp-swap': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

temp-tmp': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4110 MB, 4110228480 bytes
154 heads, 38 sectors/track, 1371 cylinders, total 8027790 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048     8,026,111     8,024,064   b W95 FAT32


Drive: pdc_babdifjjd _____________________________________________________________________

Disk /dev/mapper/pdc_babdifjjd: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders, total 3906249984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_babdifjjd1   *            256       499,967       499,712  83 Linux
/dev/mapper/pdc_babdifjjd2            499,968    98,156,287    97,656,320  8e Linux LVM
/dev/mapper/pdc_babdifjjd3         98,156,288 3,906,249,983 3,808,093,696  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/pdc_babdifjjd1 3e25ba8d-8be0-44c3-b766-d760752af421   ext2       
/dev/mapper/pdc_babdifjjd2 tVfvOd-f4Yp-ngYE-wH9t-2ZDn-iyL4-DlIpMf LVM2_member 
/dev/mapper/pdc_babdifjjd3 1a8ca10e-c467-42cc-a789-7cd77ac4965e   crypto_LUKS 
/dev/sda                                                promise_fasttrack_raid_member 
/dev/sdc1        0A12C08212C073EB                       ntfs       
/dev/sdd1        ED06-2ED8                              vfat       MULTIBOOT

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
pdc_babdifjjd
pdc_babdifjjd1
pdc_babdifjjd2
pdc_babdifjjd3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/pdc_babdifjjd1 /media/3e25ba8d-8be0-44c3-b766-d760752af421 ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


======================== pdc_babdifjjd1/grub/grub.cfg: =========================

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
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
if loadfont /grub/unicode.pf2 ; then
  set gfxmode=1920x1080,1600x1200,640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd3,msdos1)'
  search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
  set locale_dir=($root)/grub/locale
  set lang=en_AU
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
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	linux	/vmlinuz-3.0.0-12-generic root=/dev/mapper/pdc_babdifjjd3_crypt ro   quiet splash vt.handoff=7
	initrd	/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/vmlinuz-3.0.0-12-generic root=/dev/mapper/pdc_babdifjjd3_crypt ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	linux	/vmlinuz-2.6.38-11-generic root=/dev/mapper/pdc_babdifjjd3_crypt ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/vmlinuz-2.6.38-11-generic root=/dev/mapper/pdc_babdifjjd3_crypt ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	linux	/vmlinuz-2.6.38-10-generic root=/dev/mapper/pdc_babdifjjd3_crypt ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/vmlinuz-2.6.38-10-generic root=/dev/mapper/pdc_babdifjjd3_crypt ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	linux	/vmlinuz-2.6.38-8-generic root=/dev/mapper/pdc_babdifjjd3_crypt ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=/dev/mapper/pdc_babdifjjd3_crypt ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root 3e25ba8d-8be0-44c3-b766-d760752af421
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 0A12C08212C073EB
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7" {
    set root=(hd1,0)
    chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============== pdc_babdifjjd1: Location of files loaded by Grub: ===============

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  2
               =                grub/grub.cfg                                  1
               =                initrd.img-2.6.38-10-generic                  83
               =                initrd.img-2.6.38-11-generic                  83
               =                initrd.img-2.6.38-8-generic                   84
               =                initrd.img-3.0.0-12-generic                   90
               =                vmlinuz-2.6.38-10-generic                     29
               =                vmlinuz-2.6.38-11-generic                     22
               =                vmlinuz-2.6.38-8-generic                      35
               =                vmlinuz-3.0.0-12-generic                      23

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  98 e8 48 f6 cf a0 b9 92  eb 09 fb c3 33 86 c8 07  |..H.........3...|
00000010  2c 83 ba c8 07 2c 93 f8  a1 f8 00 fe ec 25 f2 e5  |,....,.......%..|
00000020  58 fc 02 8e d7 03 9e 0f  e0 e7 fd 79 3e 60 0a 87  |X..........y>`..|
00000030  9b f8 80 02 5b 7c 40 69  c5 69 e1 03 9a 02 c1 aa  |....[|@i.i......|
00000040  ba 95 0d ad f6 f8 80 dd  dc a5 d9 03 ff 27 6b 77  |.............'kw|
00000050  65 22 1f b0 62 c5 d8 73  6f bc ac eb 9e c7 af 9a  |e"..b..so.......|
00000060  14 bd 28 7e ef fe ec ec  8f 4d a1 cb 52 7d 77 64  |..(~.....M..R}wd|
00000070  5d 96 f6 1c 9b 75 6c 8d  be 46 9c 2f fa bf b2 b5  |]....ul..F./....|
00000080  e7 ea 7d 3f f9 e7 64 52  c0 58 7f 0e e4 d9 7a be  |..}?..dR.X....z.|
00000090  cb 35 ac dd c0 c2 73 4e  5c 78 6e 13 cc b3 a7 74  |.5....sN\xn....t|
000000a0  52 43 ad 45 f7 b0 69 2d  ba 83 f5 da af c4 d0 83  |RC.E..i-........|
000000b0  f3 fc c6 6c e0 37 2e bb  9c e2 37 f2 fe 10 fa 34  |...l.7....7....4|
000000c0  dc 36 4d 09 ed 0f b7 cd  be 34 f4 9b 70 db d5 5f  |.6M......4..p.._|
000000d0  85 de 0d b7 cd 51 42 bb  08 de e3 ea be de b2 bc  |.....QB.........|
000000e0  be 43 9b b5 ed 1b 98 ef  2f 77 6e 1d ed 8a 7b 23  |.C....../wn...{#|
000000f0  07 be ef 8d 1c 3f e3 ce  22 24 10 4a 41 79 8e bc  |.....?.."$.JAy..|
00000100  45 24 9e 0f 5a e9 93 eb  a4 c1 ae 2b c9 ae 5f 6a  |E$..Z......+.._j|
00000110  d7 21 da 89 3a 6a b0 7b  40 b4 13 f5 d3 60 b7 2e  |.!..:j.{@....`..|
00000120  c9 6e f5 c9 f9 8e f2 d8  78 83 ee 28 8f ee 49 28  |.n......x..(..I(|
00000130  a2 17 b9 e2 c0 7d 40 be  55 af 91 70 d5 db de c7  |.....}@.U..p....|
00000140  56 53 0d fa b4 37 da e7  4a e8 23 7d 7f 41 aa d5  |VS...7..J.#}.A..|
00000150  27 14 c8 b4 0a 49 56 e7  c5 14 6d 04 67 bf 3a 40  |'....IV...m.g.:@|
00000160  01 79 14 e0 51 56 e9 3c  8a 7e 9c 25 9a 3f e6 90  |.y..QV.<.~.%.?..|
00000170  35 77 e3 06 a4 93 f7 34  f5 7a 7d f8 33 56 06 de  |5w.....4.z}.3V..|
00000180  e8 25 c1 d3 2c 00 5c 9d  5f d5 aa 5d 28 d5 1b 02  |.%..,.\._..](...|
00000190  f5 8d c1 80 15 9e e6 54  16 76 5e 78 5e 3b a4 8b  |.......T.v^x^;..|
000001a0  4e 81 2f 82 29 f2 96 b8  5d a5 05 85 c5 c5 45 73  |N./.)...].....Es|
000001b0  67 16 cc 75 e5 97 16 95  79 cb 8b e4 8a 58 57 71  |g..u....y....XWq|
000001c0  a9 ab c9 38 77 16 14 9d  0e 45 ec 9f 3a 9f f3 4d  |...8w....E..:..M|
000001d0  af e5 97 e1 93 86 a6 98  4e 41 99 92 29 76 cb 30  |........NA..)v.0|
000001e0  e6 93 5c 72 7a 89 e7 8e  e4 eb e4 0d 03 52 69 a8  |..\rz........Ri.|
000001f0  f9 a4 a3 82 63 ab 7c 52  16 4c 58 aa f0 70 32 49  |....c.|R.LX..p2I|
00000200

Unknown BootLoader on sdb2

00000000  b1 fe 0e 04 5a f3 eb e9  71 45 d2 72 9b 73 9c 73  |....Z...qE.r.s.s|
00000010  e0 f3 4b 32 b8 23 3c 7b  03 75 30 c6 e1 8a a9 d8  |..K2.#<{.u0.....|
00000020  96 37 b5 7a 46 32 06 f5  45 88 a3 45 d7 c8 9a 68  |.7.zF2..E..E...h|
00000030  97 6c ed 01 3f 3b 12 fa  03 68 6d 3d 10 b1 1b c5  |.l..?;...hm=....|
00000040  72 74 3a 1e cf ab 1b a4  fa 1c 1b af 05 d8 ff 74  |rt:............t|
00000050  c5 f7 8b c5 35 31 aa 28  4b f4 07 13 69 48 a2 c8  |....51.(K...iH..|
00000060  b4 29 93 09 e8 a1 7e 80  8f d5 00 8d bf 96 a9 d6  |.)....~.........|
00000070  d9 ec 91 1b d1 96 4c 8b  0b 66 a8 e7 e4 36 47 f3  |......L..f...6G.|
00000080  77 78 c5 6d f1 9e 01 2e  be 37 f1 44 e9 c6 36 9f  |wx.m.....7.D..6.|
00000090  1e e0 ed 6b f1 c9 2c 74  03 7e 75 6b 27 7a a6 13  |...k..,t.~uk'z..|
000000a0  19 b2 67 b4 84 ec 82 04  0b 3e af 9c 8f bc 41 03  |..g......>....A.|
000000b0  4e ac f2 f2 27 95 98 8c  cb 76 ca d4 09 c6 d3 5a  |N...'....v.....Z|
000000c0  a3 fb 12 b1 29 e9 38 c3  ff fb 1c 97 35 fb 71 c1  |....).8.....5.q.|
000000d0  40 2c 4a 27 e3 20 0a 33  df b7 27 1b 39 bb f5 69  |@,J'. .3..'.9..i|
000000e0  56 5a c2 6a 13 dc 37 d7  a7 5f 24 8a f1 4a 91 36  |VZ.j..7.._$..J.6|
000000f0  05 e5 34 20 c4 d2 89 ab  2c 77 4a 83 b4 bf c8 99  |..4 ....,wJ.....|
00000100  59 b0 44 b5 05 79 63 c5  44 19 ec 4d 94 1b de f5  |Y.D..yc.D..M....|
00000110  3e 3b db da 52 dc fe ea  a2 1d 6c 19 5d 53 15 c2  |>;..R.....l.]S..|
00000120  e7 2d 46 a9 1d a3 8c cc  67 1c 9e d7 79 10 08 1c  |.-F.....g...y...|
00000130  51 03 fa cf 51 3d db 33  83 01 5a d7 f7 6f be 39  |Q...Q=.3..Z..o.9|
00000140  47 90 73 89 fb c5 71 93  6c 0f 09 7c 36 5f 23 46  |G.s...q.l..|6_#F|
00000150  0e 93 04 f5 c6 b3 1d a9  b9 19 f2 37 89 ef f9 cd  |...........7....|
00000160  1c 57 f6 dd 5a f6 90 cf  d5 6f 74 91 7f 29 37 07  |.W..Z....ot..)7.|
00000170  a1 60 b2 a7 32 5c 7a d1  b8 e3 55 09 e1 74 cf 84  |.`..2\z...U..t..|
00000180  71 2e 3c d0 e8 db 2a f3  d8 a0 5d c3 83 f5 a0 38  |q.<...*...]....8|
00000190  73 d2 a9 e0 29 8a 3f bc  89 fa 6e 5d c0 71 0b 1c  |s...).?...n].q..|
000001a0  63 18 65 68 fa ee 1b 5f  9d c6 b8 8c 9e 05 fa 8c  |c.eh..._........|
000001b0  2e 45 b8 5b c2 16 e2 ee  c2 05 da 0b ab 88 d2 83  |.E.[............|
000001c0  9e f6 27 12 ed 91 a3 7e  c0 cf 7a 3e 43 94 ad 6b  |..'....~..z>C..k|
000001d0  02 ef 23 15 9a f8 34 31  24 70 79 6a 3c 9d 4e 5d  |..#...41$pyj<.N]|
000001e0  95 6d 9f 04 e3 bc 23 62  b7 e0 28 1f 18 f1 7d c6  |.m....#b..(...}.|
000001f0  ca 8f 82 72 9f 3d 84 fc  15 2f aa 36 cb 69 ee 91  |...r.=.../.6.i..|
00000200

Unknown BootLoader on pdc_babdifjjd3

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 09 00 00 00 00 20  |............... |
00000070  4c e8 3f 1e 2d bd 9d 5d  56 82 f6 33 83 e8 2d d0  |L.?.-..]V..3..-.|
00000080  3a 49 09 dc 6b a1 84 0a  94 b6 c3 2c 73 fa c6 e1  |:I..k......,s...|
00000090  b0 07 74 c2 49 84 4b c9  37 c8 ee 31 b0 d3 12 6c  |..t.I.K.7..1...l|
000000a0  99 49 ed 2c 00 00 8d 1d  31 61 38 63 61 31 30 65  |.I.,....1a8ca10e|
000000b0  2d 63 34 36 37 2d 34 32  63 63 2d 61 37 38 39 2d  |-c467-42cc-a789-|
000000c0  37 63 64 37 37 61 63 34  39 36 35 65 00 00 00 00  |7cd77ac4965e....|
000000d0  00 ac 71 f3 00 02 34 fe  11 49 f5 eb 01 73 97 c2  |..q...4..I...s..|
000000e0  a6 49 2c b7 e4 2e 49 55  a8 fb 59 d1 4c 28 b3 b6  |.I,...IU..Y.L(..|
000000f0  bf c4 e1 42 ff d4 ea d9  00 00 00 08 00 00 0f a0  |...B............|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader on temp-swap'


Unknown BootLoader on temp-tmp'



=============================== StdErr Messages: ===============================

ERROR: pdc: reading /dev/sdb[No such file or directory]
ERROR: pdc: reading /dev/sdb[No such file or directory]
ERROR: pdc: reading /dev/sdb[No such file or directory]
unlzma: Decoder error
./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/temp-swap': No such file or directory
hexdump: /dev/mapper/temp-swap': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/temp-tmp': No such file or directory
hexdump: /dev/mapper/temp-tmp': No such file or directory

```

```
root@ubuntu:~# lshw | grep -B 2 -A 100 -i raid
                resources: irq:48 ioport:ce00(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:fdf00000-fdf1ffff
        *-storage
             description: RAID bus controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [Non-RAID5 mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:22 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f3ff
           *-disk:0
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 1AJ1
                serial: S246JD2B402810
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ea750
              *-volume:0 UNCLAIMED
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   capacity: 244MiB
                   capabilities: primary bootable
              *-volume:1 UNCLAIMED
                   description: Linux LVM Physical Volume partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   capacity: 46GiB
                   capabilities: primary multi
              *-volume:2 UNCLAIMED
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   capacity: 1815GiB
                   capabilities: primary
           *-disk:1
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 1AJ1
                serial: S246J90Z469803
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=eafc1624
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   capacity: 100MiB
                   capabilities: primary bootable
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   capacity: 931GiB
                   capabilities: primary
           *-disk:2
                description: ATA Disk
                product: WDC WD5000AAJS-0
                vendor: Western Digital
                physical id: 2
                bus info: scsi@2:0.0.0
                logical name: /dev/sdc
                version: 12.0
                serial: WD-WCAS81086126
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4ba47bbe
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: dcb6037c-27f3-f041-b2f5-f8fc157355b7
                   size: 465GiB
                   capacity: 465GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-08-25 18:13:53 filesystem=ntfs state=clean
           *-cdrom
                description: DVD-RAM writer
```

---

