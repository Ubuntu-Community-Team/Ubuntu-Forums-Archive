---
title: "Ubuntu boot problem not solved with normal fixes."
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by abstr2ct on 2012-02-06
none of these works (and many others not listed): 
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
When i install ubuntu along with windows7 or alone i get either a black screen with cursor or a screen saying GRUB LOADING... and a cursor. (this happens with ubuntu x32 and x64 9.10, 10.04, 10.10, 11.10, debian, linux mint and fedora 14)
I have tried a workaround installing easyBCD for windows and trying to boot from that. I got the same message and then I installed NeoGrub from EASYBCD. Now i get that message:
(problems on mounting /dev on /root/dev, /sys on /root/sys, /proc on /root/proc.
then: Target filesystem doesn't have requested /sbin/init/. 
No init found. Try passing init=bootarg.

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)_

Any clues? I try installing ubuntu for a looooooooong period of time, local FOSS community has no clue and i am alone in the middle of nowhere.
Thank you in advance. 

Some pc data: 
Intel Core 2 Duo P 7450 @2.13 GHz, 4GB Ram, Clevo M760 TUN Motherboard, NVidia GeForce G 105M. LiveCD and LiveUSB both work.

---

### Post by darkod on 2012-02-06
Can you post the boot info script results? The link is in my signature.

---

### Post by abstr2ct on 2012-02-06
Sorry for delaying. Here they are.
```
              Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /NST/menu.lst /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 578608488 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   539,674,623   539,467,776   7 NTFS / exFAT / HPFS
/dev/sda3         539,676,670   976,771,071   437,094,402   5 Extended
/dev/sda5         539,676,672   543,674,367     3,997,696  82 Linux swap / Solaris
/dev/sda6         543,676,416   586,983,423    43,307,008  83 Linux
/dev/sda7         586,985,472   976,771,071   389,785,600  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0A66F23D66F228D9                       ntfs       System Reserved
/dev/sda2        9098F71198F6F516                       ntfs       
/dev/sda5        8c9c2594-32e3-4e7e-b8bc-8c0ef94acea6   swap       
/dev/sda6        e8696f0e-1fd1-4114-9804-8b2b6717f98e   ext4       
/dev/sda7        ae981ddb-fa6b-4287-92ec-93f6508cc4fc   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================== sda2/NST/menu.lst: ==============================

--------------------------------------------------------------------------------
# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD/ 
 
default 0 
timeout 0.1 
 
title Ubuntu 11.10 05 
root (hd0,5) 
kernel /boot/vmlinuz-3.0.0-12-generic 
initrd /boot/initrd.img-3.0.0-12-generic--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             NST/menu.lst                                   1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e8696f0e-1fd1-4114-9804-8b2b6717f98e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e8696f0e-1fd1-4114-9804-8b2b6717f98e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0A66F23D66F228D9
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=e8696f0e-1fd1-4114-9804-8b2b6717f98e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=ae981ddb-fa6b-4287-92ec-93f6508cc4fc /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8c9c2594-32e3-4e7e-b8bc-8c0ef94acea6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  60 53 62 3b 4f 08 91 15  24 e7 30 73 b6 c2 ed 79  |`Sb;O...$.0s...y|
00000010  4b c2 f6 91 e9 fa 1d 3b  13 78 ab aa ba fb 42 04  |K......;.x....B.|
00000020  e2 e8 9f ac e2 03 6c 96  b2 76 86 51 00 e7 2c 60  |......l..v.Q..,`|
00000030  d3 75 65 db 14 fc 1b d5  26 22 03 10 df 88 52 a5  |.ue.....&"....R.|
00000040  3b 2f af 9c 5f 2d bb 6f  e3 a5 52 98 f6 28 db 4b  |;/.._-.o..R..(.K|
00000050  a5 c6 d4 42 b1 34 ce 4b  8c 70 19 3b 53 f8 3b f8  |...B.4.K.p.;S.;.|
00000060  1b 29 7c e2 c1 05 34 29  7f 31 47 fd e7 7d f8 16  |.)|...4).1G..}..|
00000070  fb 39 78 2c d5 c9 fd 78  30 e3 10 a6 f9 50 91 d0  |.9x,...x0....P..|
00000080  9a 26 8b ec 6d b7 e8 eb  d4 e8 75 7d d2 df ba 09  |.&..m.....u}....|
00000090  d4 55 51 0c 7d b5 54 1e  89 fc 28 fc 57 47 03 f2  |.UQ.}.T...(.WG..|
000000a0  c6 ba 26 81 36 8c 99 f6  90 14 23 0a 86 f9 3c 4c  |..&.6.....#...<L|
000000b0  35 54 fd 91 53 33 b5 8d  f3 6c c7 74 8d 9b 49 bd  |5T..S3...l.t..I.|
000000c0  b1 e9 57 e6 3e 63 3c 26  fc db 68 a5 44 33 fb d3  |..W.>c<&..h.D3..|
000000d0  ba a6 23 b5 10 30 8a 88  a2 b3 50 9c fc e2 23 b8  |..#..0....P...#.|
000000e0  a2 81 7b 02 f2 2f 7a 33  b8 27 87 49 21 ab 4a 6f  |..{../z3.'.I!.Jo|
000000f0  8c 96 2a 0b e4 f1 3a 23  58 d4 5a 9b 06 48 45 cc  |..*...:#X.Z..HE.|
00000100  92 af 0d d6 2d 49 2a d1  ad 92 d8 2c 79 ea f0 a8  |....-I*....,y...|
00000110  bb 87 6d d1 03 f6 66 33  46 1f fd 65 ff 28 ad 9f  |..m...f3F..e.(..|
00000120  db 08 6b 80 ab 55 fa 84  4d df c7 cb e9 c3 97 5a  |..k..U..M......Z|
00000130  0a b7 47 7c 1e 92 c1 7a  fc 37 83 38 62 2f 48 5c  |..G|...z.7.8b/H\|
00000140  d3 91 f8 73 2f 9e 35 b6  b2 2e 91 a6 e2 95 16 1e  |...s/.5.........|
00000150  d8 9e 60 bf a8 33 3d b4  f0 5a 09 d1 6e 5d 87 bc  |..`..3=..Z..n]..|
00000160  9b 83 8f 8a 12 a9 6a 25  b7 66 4c 0f 14 47 4c 58  |......j%.fL..GLX|
00000170  0b b9 33 40 fe 71 ae 08  73 6f 1a 0b f3 e2 30 4e  |..3@.q..so....0N|
00000180  a8 2d a7 d9 62 00 20 8f  5b 94 00 2a b7 f8 e3 b8  |.-..b. .[..*....|
00000190  3f 60 15 f0 42 74 3e 8e  14 63 1e 54 33 92 21 3a  |?`..Bt>..c.T3.!:|
000001a0  5b 1b 58 d5 8c d6 26 5e  19 87 c1 e7 a0 43 13 88  |[.X...&^.....C..|
000001b0  2c d0 e6 c2 89 e2 8e 9b  f4 c9 f9 35 4f 4c 00 fe  |,..........5OL..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 3d 00 00 fe  |............=...|
000001d0  ff ff 05 fe ff ff 02 00  3d 00 00 d8 94 02 00 00  |........=.......|
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

### Post by darkod on 2012-02-06
I know it is something tried before, but I would try to reinstall grub2 to the MBR again. Boot with the 11.10 cd in live mode and in terminal try:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Restart and see if it changed anything.

If it doesn't boot, please boot again in live mode and specify the error and what happens exactly.

The script results look normal apart from the fact you have windows bootloader on the MBR since previous installs didn't work as you said yourself.

---

### Post by abstr2ct on 2012-02-06
black screen with cursor again. this is the new boot script
If GRUB worked shouldn't it load even to find itself pointing at nowhere?
Is there any alternative or anything i can do to make my machine digest linux? Please :S :confused:```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /NST/menu.lst /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 578608488 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   539,674,623   539,467,776   7 NTFS / exFAT / HPFS
/dev/sda3         539,676,670   976,771,071   437,094,402   5 Extended
/dev/sda5         539,676,672   543,674,367     3,997,696  82 Linux swap / Solaris
/dev/sda6         543,676,416   586,983,423    43,307,008  83 Linux
/dev/sda7         586,985,472   976,771,071   389,785,600  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0A66F23D66F228D9                       ntfs       System Reserved
/dev/sda2        9098F71198F6F516                       ntfs       
/dev/sda5        8c9c2594-32e3-4e7e-b8bc-8c0ef94acea6   swap       
/dev/sda6        e8696f0e-1fd1-4114-9804-8b2b6717f98e   ext4       
/dev/sda7        ae981ddb-fa6b-4287-92ec-93f6508cc4fc   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================== sda2/NST/menu.lst: ==============================

--------------------------------------------------------------------------------
# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD/ 
 
default 0 
timeout 0.1 
 
title Ubuntu 11.10 05 
root (hd0,5) 
kernel /boot/vmlinuz-3.0.0-12-generic 
initrd /boot/initrd.img-3.0.0-12-generic--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             NST/menu.lst                                   1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e8696f0e-1fd1-4114-9804-8b2b6717f98e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e8696f0e-1fd1-4114-9804-8b2b6717f98e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e8696f0e-1fd1-4114-9804-8b2b6717f98e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0A66F23D66F228D9
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=e8696f0e-1fd1-4114-9804-8b2b6717f98e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=ae981ddb-fa6b-4287-92ec-93f6508cc4fc /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8c9c2594-32e3-4e7e-b8bc-8c0ef94acea6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  60 53 62 3b 4f 08 91 15  24 e7 30 73 b6 c2 ed 79  |`Sb;O...$.0s...y|
00000010  4b c2 f6 91 e9 fa 1d 3b  13 78 ab aa ba fb 42 04  |K......;.x....B.|
00000020  e2 e8 9f ac e2 03 6c 96  b2 76 86 51 00 e7 2c 60  |......l..v.Q..,`|
00000030  d3 75 65 db 14 fc 1b d5  26 22 03 10 df 88 52 a5  |.ue.....&"....R.|
00000040  3b 2f af 9c 5f 2d bb 6f  e3 a5 52 98 f6 28 db 4b  |;/.._-.o..R..(.K|
00000050  a5 c6 d4 42 b1 34 ce 4b  8c 70 19 3b 53 f8 3b f8  |...B.4.K.p.;S.;.|
00000060  1b 29 7c e2 c1 05 34 29  7f 31 47 fd e7 7d f8 16  |.)|...4).1G..}..|
00000070  fb 39 78 2c d5 c9 fd 78  30 e3 10 a6 f9 50 91 d0  |.9x,...x0....P..|
00000080  9a 26 8b ec 6d b7 e8 eb  d4 e8 75 7d d2 df ba 09  |.&..m.....u}....|
00000090  d4 55 51 0c 7d b5 54 1e  89 fc 28 fc 57 47 03 f2  |.UQ.}.T...(.WG..|
000000a0  c6 ba 26 81 36 8c 99 f6  90 14 23 0a 86 f9 3c 4c  |..&.6.....#...<L|
000000b0  35 54 fd 91 53 33 b5 8d  f3 6c c7 74 8d 9b 49 bd  |5T..S3...l.t..I.|
000000c0  b1 e9 57 e6 3e 63 3c 26  fc db 68 a5 44 33 fb d3  |..W.>c<&..h.D3..|
000000d0  ba a6 23 b5 10 30 8a 88  a2 b3 50 9c fc e2 23 b8  |..#..0....P...#.|
000000e0  a2 81 7b 02 f2 2f 7a 33  b8 27 87 49 21 ab 4a 6f  |..{../z3.'.I!.Jo|
000000f0  8c 96 2a 0b e4 f1 3a 23  58 d4 5a 9b 06 48 45 cc  |..*...:#X.Z..HE.|
00000100  92 af 0d d6 2d 49 2a d1  ad 92 d8 2c 79 ea f0 a8  |....-I*....,y...|
00000110  bb 87 6d d1 03 f6 66 33  46 1f fd 65 ff 28 ad 9f  |..m...f3F..e.(..|
00000120  db 08 6b 80 ab 55 fa 84  4d df c7 cb e9 c3 97 5a  |..k..U..M......Z|
00000130  0a b7 47 7c 1e 92 c1 7a  fc 37 83 38 62 2f 48 5c  |..G|...z.7.8b/H\|
00000140  d3 91 f8 73 2f 9e 35 b6  b2 2e 91 a6 e2 95 16 1e  |...s/.5.........|
00000150  d8 9e 60 bf a8 33 3d b4  f0 5a 09 d1 6e 5d 87 bc  |..`..3=..Z..n]..|
00000160  9b 83 8f 8a 12 a9 6a 25  b7 66 4c 0f 14 47 4c 58  |......j%.fL..GLX|
00000170  0b b9 33 40 fe 71 ae 08  73 6f 1a 0b f3 e2 30 4e  |..3@.q..so....0N|
00000180  a8 2d a7 d9 62 00 20 8f  5b 94 00 2a b7 f8 e3 b8  |.-..b. .[..*....|
00000190  3f 60 15 f0 42 74 3e 8e  14 63 1e 54 33 92 21 3a  |?`..Bt>..c.T3.!:|
000001a0  5b 1b 58 d5 8c d6 26 5e  19 87 c1 e7 a0 43 13 88  |[.X...&^.....C..|
000001b0  2c d0 e6 c2 89 e2 8e 9b  f4 c9 f9 35 4f 4c 00 fe  |,..........5OL..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 3d 00 00 fe  |............=...|
000001d0  ff ff 05 fe ff ff 02 00  3d 00 00 d8 94 02 00 00  |........=.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by abstr2ct on 2012-02-06
Also my windows 7 istallation is all ****** up (even though this is irrelevant)

---

### Post by darkod on 2012-02-07
So, you are getting a black screen without even seeing the boot menu, right?

Or after you select to boot ubuntu/windows?

---

### Post by abstr2ct on 2012-02-07
No boot menu or anything. It stucks after listing devices from BIOS.

---

