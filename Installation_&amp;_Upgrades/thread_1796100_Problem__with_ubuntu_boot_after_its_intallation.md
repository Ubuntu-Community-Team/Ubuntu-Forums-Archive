---
title: "Problem  with ubuntu boot after its intallation"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by chrispap on 2011-07-03
Hello,
I 'm new to Ubuntu.I installed 11.04 by a CD and after the installation finish I did a restart but there was no choice for Ubuntu and Windows XP home edition booted automatically. I don't know if it helps but I have an external disk of 500gb with 300gb free space  and an internal of 70gb with 30gb free space.During the installation process I defined 50gb for Ubuntu but now when I check the internal the free space is the same after the installation.
Thanks,
Chris

---

### Post by dino99 on 2011-07-03
how to make an install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Rubi1200 on 2011-07-03
Hi and welcome to the forums chrispap :)

We need to get a better overview of what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by chrispap on 2011-07-04
[LEFT]              ```
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
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

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

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   127,678,789   127,678,727   7 NTFS / exFAT / HPFS
/dev/sda2         127,680,510   156,301,311    28,620,802   5 Extended
/dev/sda5         127,680,512   153,155,583    25,475,072  83 Linux
/dev/sda6         153,157,632   156,301,311     3,143,680  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FE44530F4452C9D3                       ntfs       
/dev/sda5        0155cf97-41f5-4a1d-9a8a-7347d14d22d6   ext4       
/dev/sda6        d822c9f7-7310-48f9-a57d-d19f225fe544   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/FE44530F4452C9D3  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/0155cf97-41f5-4a1d-9a8a-7347d14d22d6 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
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
search --no-floppy --fs-uuid --set=root 0155cf97-41f5-4a1d-9a8a-7347d14d22d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 0155cf97-41f5-4a1d-9a8a-7347d14d22d6
set locale_dir=($root)/boot/grub/locale
set lang=el_GR
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
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0155cf97-41f5-4a1d-9a8a-7347d14d22d6
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0155cf97-41f5-4a1d-9a8a-7347d14d22d6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.38-8-generic (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0155cf97-41f5-4a1d-9a8a-7347d14d22d6
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0155cf97-41f5-4a1d-9a8a-7347d14d22d6 ro single 
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
    search --no-floppy --fs-uuid --set=root 0155cf97-41f5-4a1d-9a8a-7347d14d22d6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0155cf97-41f5-4a1d-9a8a-7347d14d22d6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root FE44530F4452C9D3
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
UUID=0155cf97-41f5-4a1d-9a8a-7347d14d22d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d822c9f7-7310-48f9-a57d-d19f225fe544 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  69.184093475 = 74.285854720   boot/grub/core.img                             1
  61.356914520 = 65.881485312   boot/grub/grub.cfg                             1
  62.335937500 = 66.932703232   boot/initrd.img-2.6.38-8-generic               2
  69.182315826 = 74.283945984   boot/vmlinuz-2.6.38-8-generic                  1
  62.335937500 = 66.932703232   initrd.img                                     2
  69.182315826 = 74.283945984   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  4b 35 63 c2 ad b9 70 cc  f4 a6 cc ba d0 f8 15 90  |K5c...p.........|
00000010  6c 1d 66 08 c4 10 3f c1  31 9e 5e e7 dd 74 f7 ad  |l.f...?.1.^..t..|
00000020  6e 73 4c 7a d7 68 20 4c  59 a6 20 86 c0 73 bc f0  |nsLz.h LY. ..s..|
00000030  27 a4 c8 d3 50 4c 05 b4  85 28 74 29 1f 3e 37 6f  |'...PL...(t).>7o|
00000040  f5 a3 29 a9 c6 88 35 c6  91 f9 24 0e 00 4f db 6d  |..)...5...$..O.m|
00000050  02 60 60 ad b8 82 0f 48  4d 48 9c d7 76 33 e9 14  |.``....HMH..v3..|
00000060  ad 90 ea 37 22 30 63 e3  4b a6 fd 99 a2 4e 34 0a  |...7"0c.K....N4.|
00000070  aa bd 69 12 6d 74 17 03  a7 dc 85 30 27 bf 27 43  |..i.mt.....0'.'C|
00000080  4c c3 24 b1 50 1a 76 73  dc 66 06 c4 7e 79 18 07  |L.$.P.vs.f..~y..|
00000090  50 2a 99 4e 9c dd de 6b  78 6a 0a c9 45 38 3d 2a  |P*.N...kxj..E8=*|
000000a0  4c 04 61 13 6c 05 3a 4b  80 0a 38 6e e7 c4 81 e7  |L.a.l.:K..8n....|
000000b0  7b 22 99 60 e9 4b 4d a3  5f 03 70 d5 a6 cd 10 5c  |{".`.KM._.p....\|
000000c0  15 f7 79 38 81 c2 20 0a  86 7f 17 e6 c0 1c 80 a2  |..y8.. .........|
000000d0  63 2f 9c e2 1c 84 2d 60  1f a2 17 49 52 90 be 61  |c/....-`...IR..a|
000000e0  9d 11 bf 7f 89 64 d2 90  da 80 48 f1 b9 78 b4 33  |.....d....H..x.3|
000000f0  48 67 48 ab 88 dd cb a7  ff 51 0c 85 d2 a4 a5 1a  |HgH......Q......|
00000100  73 43 61 82 32 1d c3 54  04 ef ad ba 3e 3c 65 81  |sCa.2..T....><e.|
00000110  0e 2f 04 42 87 f3 f2 2d  0b 03 cc bf f4 9a fc 2d  |./.B...-.......-|
00000120  93 53 25 38 66 43 cc 01  0f e8 4f a4 e1 d6 5a de  |.S%8fC....O...Z.|
00000130  29 97 8a b2 34 d8 d1 87  34 85 56 18 e8 fb 74 13  |)...4...4.V...t.|
00000140  13 56 48 af ac 3a 52 b2  e1 67 01 53 9c f8 d4 3b  |.VH..:R..g.S...;|
00000150  68 60 20 44 8c a4 ba 4e  dc 40 06 45 7e 49 27 28  |h` D...N.@.E~I'(|
00000160  5a df 2a 40 9d 61 87 88  e8 dd 6a 9e 84 e6 88 3e  |Z.*@.a....j....>|
00000170  c2 8b 2d 2c 3a fc e9 63  23 46 20 2e 09 9c f1 90  |..-,:..c#F .....|
00000180  06 8a d0 e8 e9 a8 e1 1e  15 c2 71 b9 98 cd 03 cd  |..........q.....|
00000190  d2 61 db 18 d8 06 be cb  ff 1b 82 4e 0d c5 86 d5  |.a.........N....|
000001a0  91 38 34 77 ee eb e8 05  e9 39 8c 21 ba c0 8c 72  |.84w.....9.!...r|
000001b0  04 72 ca 37 05 45 06 8d  20 1c a3 c6 d0 c8 00 fe  |.r.7.E.. .......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 84 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b8  84 01 00 00 30 00 00 00  |............0...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```[/LEFT]

---

### Post by chrispap on 2011-07-04
I reinstalled it in my internal hard disk giving 15gb  to Ubuntu and 65 to Windows. After that my computer loads a message out of range 96kHz and there is no os boot after that.The code above is of my latest install.

---

### Post by Rubi1200 on 2011-07-04
The script results seem normal so I assume this is a graphics/monitor issue.

Although this post is old it seems to have some useful links and I think you should start there to find a solution:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

