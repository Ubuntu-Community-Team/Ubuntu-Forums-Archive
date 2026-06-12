---
title: "Toshiba Satellite - Ubuntu 12.04, Windows not booting?"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by NatGeo on 2012-05-27
Hi, new here. I installed Ubuntu 12.04 (64 bit!) earlier today on a Toshiba Satellite, it went swimmingly. I allocated ~ 200 GB for Ubuntu, which left about 420 GB for Windows to run on. Ubuntu is running without a hitch, but whenever I try to load Windows (either /dev/sda1 or /dev/sda2 ), it stops at the part where it says "Starting Windows", then flashes a blue screen momentarily before restarting. I can enter recovery ( /dev/sda3 ) but that's about it. For reference:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......2..9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1496075 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   826,652,979   823,578,932   7 NTFS / exFAT / HPFS
/dev/sda3       1,219,489,792 1,250,263,039    30,773,248  17 Hidden NTFS / HPFS
/dev/sda4         826,654,718 1,219,489,791   392,835,074   5 Extended
/dev/sda5         826,654,720 1,202,819,071   376,164,352  83 Linux
/dev/sda6       1,202,821,120 1,219,489,791    16,668,672  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2048 MB, 2048729600 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001425 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            245     3,999,743     3,999,499   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1AD8F56ED8F54911                       ntfs       System
/dev/sda2        EACC1BA7CC1B6D57                       ntfs       TI106320W0D
/dev/sda3        4CC841EBC841D43C                       ntfs       HDDRECOVERY
/dev/sda5        4590f8c3-d468-46b7-a2dd-2ba5e6983e99   ext4       
/dev/sda6        2a53ebde-0f8f-42eb-ace6-b452f37f3fdf   swap       
/dev/sdb1        DA74-E37F                              vfat       
/dev/sr1                                                iso9660    U3 System

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/DA74-E37F         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


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
search --no-floppy --fs-uuid --set=root 4590f8c3-d468-46b7-a2dd-2ba5e6983e99
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 4590f8c3-d468-46b7-a2dd-2ba5e6983e99
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4590f8c3-d468-46b7-a2dd-2ba5e6983e99
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=4590f8c3-d468-46b7-a2dd-2ba5e6983e99 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4590f8c3-d468-46b7-a2dd-2ba5e6983e99
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=4590f8c3-d468-46b7-a2dd-2ba5e6983e99 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4590f8c3-d468-46b7-a2dd-2ba5e6983e99
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4590f8c3-d468-46b7-a2dd-2ba5e6983e99
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1AD8F56ED8F54911
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root EACC1BA7CC1B6D57
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 4CC841EBC841D43C
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=4590f8c3-d468-46b7-a2dd-2ba5e6983e99 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2a53ebde-0f8f-42eb-ace6-b452f37f3fdf none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

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
 
label ubnentry6 
menu label Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry7 
menu label Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- 
 
label ubnentry8 
menu label Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- 
 
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 6b 16 00 fe  |............k...|
000001d0  ff ff 05 fe ff ff 02 d0  6b 16 00 60 fe 00 00 00  |........k..`....|
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
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```I ran sudo grub-install /dev/sda and sudo update-grub ; neither of these pulled up anything. Any thoughts? Please help!

---

### Post by wilee-nilee on 2012-05-27
Did you resize windows and check that it boots before the ubuntu install?

Do you have a recovery or install disc for window?

Keep all response to the thread, not any PM's please.

---

### Post by NatGeo on 2012-05-27
> **wilee-nilee said:**
> Did you resize windows and check that it boots before the ubuntu install?

Do you have a recovery or install disc for window?

Keep all response to the thread, not any PM's please.

Sorry, didn't know the rule about PMs :P

Anyways, no, I resized and installed all at once using the installer on the disc. Shouldn't have been necessary but in hindsight might have been a good idea...

[]("http://paste.ubuntu.com/1012354/")

---

### Post by Mark Phelps on 2012-05-28
One side-effect of using the SLIDER to resize win7 OS paritions is that it sometimes results in filesystem corruption -- rendering Win7 unbootable as a result.

If you don't have a Win7 install DVD, then you can try using boot-repair to fix it:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by NatGeo on 2012-05-28
I tried boot-repair; this is what happened the two times i tried it:

[http://paste.ubuntu.com/1012349/](http://paste.ubuntu.com/1012349/)

[http://paste.ubuntu.com/1012354/](http://paste.ubuntu.com/1012354/)

I'm not too good with this stuff, do you have any suggestions after this?

EDIT: Talked with a friend, who suggested booting /dev/sda3 - this worked, and i'm typing this on windows right now! thanks a lot haha

---

### Post by NatGeo on 2012-05-29
Bumping to say that this has been solved! see post above.

Thanks guys :D

---

