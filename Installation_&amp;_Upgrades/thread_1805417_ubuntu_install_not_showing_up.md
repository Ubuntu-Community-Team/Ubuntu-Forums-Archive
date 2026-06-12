---
title: "ubuntu install not showing up"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by eatinpaper on 2011-07-16
I just installed Ubuntu on a new partition on a hard drive that I was using to store files while using Windows 7. For whatever reason, when I start up my computer, Ubuntu is not shown as an available operating system. Only Windows 7 and Windows Vista-from two other separate hard drives-are shown. Why is this so and what can I do to fix this?

---

### Post by Quackers on 2011-07-16
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by bennyroger on 2011-07-16
Do you see a grub menu at startup? If not grub is not installed, try to install grub again from the live disk.

---

### Post by eatinpaper on 2011-07-16
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid d64d6df7-b313-4020-911c-e212165e9d01 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 519 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.0 GB, 64022175232 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125043311 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   125,040,639   125,038,592   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   369,864,342   369,864,280   7 NTFS / exFAT / HPFS
/dev/sdc2         369,864,702   488,396,799   118,532,098   5 Extended
/dev/sdc5         483,160,064   488,396,799     5,236,736  82 Linux swap / Solaris
/dev/sdc6         369,864,704   483,160,063   113,295,360  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *            249     3,967,487     3,967,239   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        E48C4F548C4F2082                       ntfs       
/dev/sdb1        02C03B4FC03B4865                       ntfs       
/dev/sdc1        FCC884B6C88470A6                       ntfs       
/dev/sdc5        754b0afa-76ad-45fc-960f-177971bd638f   swap       
/dev/sdc6        537d67a2-756d-4895-bc90-fc4a27c77db7   ext4       
/dev/sdd1        3636-6639                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc6        /media/537d67a2-756d-4895-bc90-fc4a27c77db7 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos6)'
search --no-floppy --fs-uuid --set=root 537d67a2-756d-4895-bc90-fc4a27c77db7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos6)'
search --no-floppy --fs-uuid --set=root 537d67a2-756d-4895-bc90-fc4a27c77db7
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
    set root='(/dev/sdc,msdos6)'
    search --no-floppy --fs-uuid --set=root 537d67a2-756d-4895-bc90-fc4a27c77db7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=537d67a2-756d-4895-bc90-fc4a27c77db7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos6)'
    search --no-floppy --fs-uuid --set=root 537d67a2-756d-4895-bc90-fc4a27c77db7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=537d67a2-756d-4895-bc90-fc4a27c77db7 ro single 
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
    set root='(/dev/sdc,msdos6)'
    search --no-floppy --fs-uuid --set=root 537d67a2-756d-4895-bc90-fc4a27c77db7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos6)'
    search --no-floppy --fs-uuid --set=root 537d67a2-756d-4895-bc90-fc4a27c77db7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 02C03B4FC03B4865
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root FCC884B6C88470A6
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

=============================== sdc6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc6       /               ext4    errors=remount-ro 0       1
/dev/sdc5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdc6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 200.499267578 = 215.284449280  boot/grub/core.img                             1
 213.101169586 = 228.815638528  boot/grub/grub.cfg                             1
 225.371799469 = 241.991127040  boot/initrd.img-2.6.38-8-generic               2
 200.497539520 = 215.282593792  boot/vmlinuz-2.6.38-8-generic                  1
 225.371799469 = 241.991127040  initrd.img                                     2
 200.497539520 = 215.282593792  vmlinuz                                        1

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  3b 66 ac 5a c5 12 33 4b  2b 09 49 c9 c6 78 ae 59  |;f.Z..3K+.I..x.Y|
00000010  a7 cd ca 88 73 ee 36 e2  ea 29 18 0b 6b 71 16 1b  |....s.6..)..kq..|
00000020  1f 2f 7f c6 94 3b f9 7b  9f 95 27 9c 75 cd 10 bc  |./...;.{..'.u...|
00000030  74 90 f7 19 2c d6 d2 5b  b9 65 2e d1 e7 85 e0 9a  |t...,..[.e......|
00000040  a7 19 97 cf 7c 42 63 81  80 20 96 c9 34 aa 41 c2  |....|Bc.. ..4.A.|
00000050  ed 1a 47 dd 83 b8 b7 36  c8 ae 93 cb 2c 80 b0 e0  |..G....6....,...|
00000060  11 c0 fa d2 43 7b e5 42  b1 25 ba bc 64 e0 93 9c  |....C{.B.%..d...|
00000070  7e 74 f9 65 38 dc e6 e5  6e c3 ad 54 5c 47 3b 33  |~t.e8...n..T\G;3|
00000080  35 a9 60 59 32 a4 77 e3  20 f6 c5 53 79 1e 08 c8  |5.`Y2.w. ..Sy...|
00000090  2a 6e 13 1c 28 3c fd 05  5f fc bd e5 e8 76 e9 25  |*n..(<.._....v.%|
000000a0  a0 b6 c9 35 d5 b8 24 79  0a 32 76 37 5f a5 4e d1  |...5..$y.2v7_.N.|
000000b0  ac 7f 39 21 98 28 27 3c  11 ed 5d 0a 5c da 1c b2  |..9!.('<..].\...|
000000c0  8c 91 35 a5 c4 89 78 c2  28 42 be de 1b bf 35 04  |..5...x.(B....5.|
000000d0  88 04 8c 44 d9 5c e4 9f  5f 6a 99 27 04 ec 5a 8f  |...D.\.._j.'..Z.|
000000e0  56 22 95 f3 d6 3d 8e 4b  0f bd 8c 80 7d 49 a9 20  |V"...=.K....}I. |
000000f0  47 73 e5 89 7c bc 9e a4  e3 35 8c e7 f6 49 7b 8a  |Gs..|....5...I{.|
00000100  4c 22 20 55 15 a5 ce 43  0c 67 3f e3 51 32 5c 4f  |L" U...C.g?.Q2\O|
00000110  16 15 48 8c f7 c6 36 8a  52 93 e5 34 5b d8 96 01  |..H...6.R..4[...|
00000120  6d 0c ad 80 82 60 03 1c  71 bf ff 00 af 55 35 05  |m....`..q....U5.|
00000130  bb b8 b6 32 c2 c6 14 63  b4 9c fe 95 9c 9f bc 93  |...2...c........|
00000140  d8 ca d7 9d 99 0c c6 cd  a2 11 36 7e d0 c9 93 81  |..........6~....|
00000150  c6 2a b2 c1 2a b0 99 71  95 3f 29 61 90 7d ab 79  |.*..*..q.?)a.}.y|
00000160  4f 91 58 ea 7a a4 90 c8  5b 12 34 4f 08 60 0f 2c  |O.X.z...[.4O.`.,|
00000170  4f 5a 91 74 e8 88 59 09  44 6c e4 94 6f bc 2b 3e  |OZ.t..Y.Dl..o.+>|
00000180  6b 49 34 8c 24 ac c7 87  74 7f 2c 7c fe 98 1c fe  |kI4.$...t.,|....|
00000190  54 c9 14 3a 99 03 33 30  e4 93 de a5 df 99 dc d5  |T..:..30........|
000001a0  46 f7 63 e4 69 6d 89 70  7c d0 47 45 07 24 55 79  |F.c.im.p|.GE.$Uy|
000001b0  2e d5 6d a3 12 a6 24 39  07 23 af e5 f8 d7 00 fe  |..m...$9.#......|
000001c0  ff ff 82 fe ff ff 02 c0  c0 06 00 e8 4f 00 00 fe  |............O...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 c0 c0 06 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by garvinrick4 on 2011-07-16
You have put grub2 in sda by mistake, take your windows disk and put windows bootmanager back in.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

Ubuntu is on sdc drive must boot sdc first in boot order in Bios. 
After you boot into Ubuntu open a terminal "ctrl/alt/t" and run
```
sudo update-grub
```Will put all your installs as a boot option in drive sdc 
You cannot boot a drive with Windows on it only and have another operating system be present in menu entry.
Ubuntu's use of grub2 has a package called os-prober that finds other operating systems and
puts it in your menu entries and config file so as to be bootable. Windows bootmanager does not do this.

---

### Post by eatinpaper on 2011-07-16
Thank you! I followed what you said and now I finally am on Ubuntu from my hard drive.

---

### Post by garvinrick4 on 2011-07-16
Quackers and I say Welcome to Ubuntu Linux, I think you are going to make a fine Ubuntu
user. Enjoy Linux and use these Forums and Google search.

---

