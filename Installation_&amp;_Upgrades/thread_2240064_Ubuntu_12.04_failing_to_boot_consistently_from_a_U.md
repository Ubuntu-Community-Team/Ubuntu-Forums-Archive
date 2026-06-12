---
title: "Ubuntu 12.04 failing to boot consistently from a USB stick."
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by oisin_nz on 2014-08-17
Hi, 

I have created a bootable [SIZE=2]Ubuntu[/SIZE] 12.04 install on a 16Gb USB stick as per the instructions at [COLOR=#000000][FONT=Arial]http://ubuntuforums.org/showthread.php?t=2060493. [SIZE=2]It is not performing as expected though in that it frequently fails to boot. The most perplexing thing about this is that the behaviour is not deterministic, it will behave differently from attempt to attempt, sometimes booting, other time failing for the exact same hardware setup. The failed attempts always start the same though, I can see the activity LED on the USB stick (the laptop itself is configured to boot from USB by default) and then I will see error messages at the top of a blank screen:

error: file not found
error: no suitable mode found
error: no video mode activated

after this point the next error message can change from attempt to attempt 
error: invalid extent / error: out of memory / error: invalid architecture independent ELF magic. 

If I wait around for long enough (minutes) it may ultimately bring up the boot menu but no matter what option I choose (boot Ubuntu/ boot Ubuntu recovery/ boot older Linux versions) I will never manage to successfully boot. 

So, does anyone know what is going on here? In parallel with this full install I also have a Ubuntu Live install on another 4Gb USB stick and this seems to be bullet-proof boot-wise; I have never seen it fail, is there any way to get the full install to boot as consistently and reliably as the Live version ?

Running bootinfoscript yields the following (The machine is a Dell laptop with a Windows XP install on the hard-drive) :

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Restore: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 2048.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2    *        144,585    71,810,549    71,665,965   7 NTFS / exFAT / HPFS
/dev/sda3          71,826,615    78,124,094     6,297,480  db CP/M / CTOS / ...


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 15.6 GB, 15623782400 bytes
64 heads, 32 sectors/track, 14900 cylinders, total 30515200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048       976,895       974,848   b W95 FAT32
/dev/sdc2    *        976,896    16,601,087    15,624,192  83 Linux
/dev/sdc3          16,601,088    27,342,847    10,741,760  83 Linux
/dev/sdc4          27,342,848    30,513,151     3,170,304  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 f87c955e-f268-4f44-a48d-fe8494557260   swap       
/dev/sda1        07D5-0B18                              vfat       DellUtility
/dev/sda2        A22816AB28167F0B                       ntfs       
/dev/sda3                                               vfat       DellRestore
/dev/sdc1        1A22-7467                              vfat       
/dev/sdc2        2fd61b9b-f55b-4d72-b692-f610fe3ac714   ext4       
/dev/sdc3        87bd7e6e-f2d7-48fd-ae7c-bd90e4a1f25c   ext2       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc2        /                        ext4       (rw,errors=remount-ro)
/dev/sdc3        /home                    ext2       (rw)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdc2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set=root 2fd61b9b-f55b-4d72-b692-f610fe3ac714
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos2)'
  search --no-floppy --fs-uuid --set=root 2fd61b9b-f55b-4d72-b692-f610fe3ac714
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
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
menuentry 'Ubuntu, with Linux 3.11.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 2fd61b9b-f55b-4d72-b692-f610fe3ac714
    linux    /boot/vmlinuz-3.11.0-26-generic root=UUID=2fd61b9b-f55b-4d72-b692-f610fe3ac714 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.11.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 2fd61b9b-f55b-4d72-b692-f610fe3ac714
    echo    'Loading Linux 3.11.0-26-generic ...'
    linux    /boot/vmlinuz-3.11.0-26-generic root=UUID=2fd61b9b-f55b-4d72-b692-f610fe3ac714 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.11.0-26-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.11.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 2fd61b9b-f55b-4d72-b692-f610fe3ac714
    linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=2fd61b9b-f55b-4d72-b692-f610fe3ac714 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.11.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 2fd61b9b-f55b-4d72-b692-f610fe3ac714
    echo    'Loading Linux 3.11.0-15-generic ...'
    linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=2fd61b9b-f55b-4d72-b692-f610fe3ac714 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.11.0-15-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 2fd61b9b-f55b-4d72-b692-f610fe3ac714
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 2fd61b9b-f55b-4d72-b692-f610fe3ac714
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 07D5-0B18
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root A22816AB28167F0B
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
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

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc2 during installation
UUID=2fd61b9b-f55b-4d72-b692-f610fe3ac714 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=87bd7e6e-f2d7-48fd-ae7c-bd90e4a1f25c /home           ext2    defaults        0       2
# swap was on /dev/sdc4 during installation
#UUID=61fcd8b6-a284-4a79-bd84-a42f7b4e1cfb none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.11.0-15-generic              1
               =                boot/initrd.img-3.11.0-26-generic              1
               =                boot/vmlinuz-3.11.0-15-generic                 2
               =                boot/vmlinuz-3.11.0-26-generic                 1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 4a 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.J.Dell 8.0.....|
00000010  02 00 02 00 00 f8 8d 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  8a 34 02 00 80 00 29 18  0b d5 07 44 65 6c 6c 55  |.4....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 30 33 c0 8e d0  |...........03...|
00000050  bc 00 07 fc b9 80 00 8e  d8 be 00 7c b8 00 20 8e  |...........|.. .|
00000060  c0 33 ff f3 66 a5 ea 6b  00 00 20 8e d8 b8 01 02  |.3..f..k.. .....|
00000070  b9 01 00 b6 00 8a 16 24  00 bb 00 02 cd 13 0f 82  |.......$........|
00000080  e0 00 80 3e c2 03 06 74  0e c6 06 c2 03 06 b8 01  |...>...t........|
00000090  03 cd 13 0f 82 cb 00 66  0f b7 06 16 00 66 d1 e0  |.......f.....f..|
000000a0  66 40 66 03 06 1c 00 66  a3 3e 00 8b 2e 11 00 89  |f@f....f.>......|
000000b0  2e 44 00 c1 ed 04 e8 cb  00 4d 75 fa b9 0b 00 be  |.D.......Mu.....|
000000c0  ea 01 8b fd f3 a6 74 0f  83 c5 20 ff 0e 44 00 75  |......t... ..D.u|
000000d0  eb be e0 01 e9 8e 00 26  8b 46 1a a3 46 00 66 a1  |.......&.F..F.f.|
000000e0  1c 00 66 40 66 a3 3e 00  c7 06 48 00 00 00 8b 2e  |..f@f.>...H.....|
000000f0  16 00 e8 8f 00 4d 75 fa  c7 06 4a 00 70 00 c7 06  |.....Mu...J.p...|
00000100  48 00 00 00 66 0f b7 06  46 00 66 83 e8 02 66 0f  |H...f...F.f...f.|
00000110  b6 0e 0d 00 66 f7 e1 66  0f b7 0e 16 00 66 d1 e1  |....f..f.....f..|
00000120  66 41 66 03 0e 1c 00 66  03 c1 66 0f b7 0e 11 00  |fAf....f..f.....|
00000130  66 c1 e9 04 66 03 c1 66  a3 3e 00 0f b6 2e 0d 00  |f...f..f.>......|
00000140  e8 41 00 4d 75 fa 8b 36  46 00 b8 00 30 d1 e6 73  |.A.Mu..6F...0..s|
00000150  03 05 00 10 8e c0 26 ad  3d f8 ff 73 0d a3 46 00  |......&.=..s..F.|
00000160  eb a2 be d5 01 e8 0d 00  eb fe 8a 16 24 00 33 ed  |............$.3.|
00000170  ea 00 00 70 00 ac 3c 00  74 09 b4 0e bb 07 00 cd  |...p..<.t.......|
00000180  10 eb f2 c3 66 a1 3e 00  66 33 d2 66 0f b7 0e 18  |....f.>.f3.f....|
00000190  00 66 f7 f1 fe c2 88 16  25 00 32 d2 66 0f b7 0e  |.f......%.2.f...|
000001a0  1a 00 66 f7 f1 8a f2 8b  c8 b8 01 02 c0 e5 06 0a  |..f.............|
000001b0  2e 25 00 86 e9 8a 16 24  00 c4 1e 48 00 cd 13 72  |.%.....$...H...r|
000001c0  a1 66 ff 06 3e 00 81 06  48 00 00 02 75 06 81 06  |.f..>...H...u...|
000001d0  4a 00 00 10 c3 44 69 73  6b 20 65 72 72 6f 72 00  |J....Disk error.|
000001e0  4e 6f 20 6c 6f 61 64 65  72 00 44 45 4c 4c 42 49  |No loader.DELLBI|
000001f0  4f 20 42 49 4e 00 00 00  00 00 00 00 00 80 55 aa  |O BIN.........U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
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


```[/SIZE]
[/FONT][/COLOR]

---

