---
title: "Windows 8 boot error"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by maiandros on 2012-12-17
Hello to all...

Here I am , asking for ur precious help.
I`ll try to be short on my problem`s description. 
I used to dual-boot with windows7 & Ubuntu...last year i wanted to install the new version of Ubuntu and by trying i managed to destroy my DualBoot.Back then i could only login into Ubuntu even though in my Grub menu i had the choice of Windows it had always given me a black blank screen.
Yesterday i decided to update from Win7 to Win8 and now there is no Grub menu, no Ubuntu...just windows 8. I`d love to have my dual Boot back...i need to gain access to my Ubuntu as soon as possible.
I`m pretty sure that there is nothing to do with Secure Booting or EFI cause my laptop is rather old...it is an Acer Aspire 5630.
I don`t know how to proceed on that by myself so i would appreciate any kind of help.
  
Here i`m posting the result of the Boot Info Script from a liveCD



```
                   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => FreeDOS (eXtended FDisk) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

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
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   132,038,234   132,038,172   7 NTFS / exFAT / HPFS
/dev/sda2         132,038,235   161,335,109    29,296,875  83 Linux
/dev/sda3         161,335,294   234,440,703    73,105,410   5 Extended
/dev/sda5         161,335,296   173,053,951    11,718,656  82 Linux swap / Solaris
/dev/sda6         173,056,000   234,440,703    61,384,704  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1998 MB, 1998585856 bytes
9 heads, 8 sectors/track, 54215 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                 512     3,903,487     3,902,976   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FA6852B9685273FB                       ntfs       
/dev/sda2        7d3c4347-5c2e-4093-9fb0-6ace68a18171   ext4       
/dev/sda5        9d7e09c0-139a-471b-bcc1-5a1a9468ea91   swap       
/dev/sda6        ba8c7e2b-36b6-4dd0-a400-c33c49d4a7e5   ext4       
/dev/sdc1        4CD2-4A09                              vfat       
/dev/sr0                                                iso9660    Ultimate Edition 3.5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/4CD2-4A09         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 7d3c4347-5c2e-4093-9fb0-6ace68a18171
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 7d3c4347-5c2e-4093-9fb0-6ace68a18171
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
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 7d3c4347-5c2e-4093-9fb0-6ace68a18171
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=7d3c4347-5c2e-4093-9fb0-6ace68a18171 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 7d3c4347-5c2e-4093-9fb0-6ace68a18171
    echo    'Loading Linux 3.2.0-34-generic ...'
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=7d3c4347-5c2e-4093-9fb0-6ace68a18171 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-34-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 7d3c4347-5c2e-4093-9fb0-6ace68a18171
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=7d3c4347-5c2e-4093-9fb0-6ace68a18171 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 7d3c4347-5c2e-4093-9fb0-6ace68a18171
    echo    'Loading Linux 3.2.0-33-generic ...'
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=7d3c4347-5c2e-4093-9fb0-6ace68a18171 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-33-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 7d3c4347-5c2e-4093-9fb0-6ace68a18171
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 7d3c4347-5c2e-4093-9fb0-6ace68a18171
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 055F8FDB3E227F2C
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=7d3c4347-5c2e-4093-9fb0-6ace68a18171 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ba8c7e2b-36b6-4dd0-a400-c33c49d4a7e5 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=9d7e09c0-139a-471b-bcc1-5a1a9468ea91 none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda2/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  75.554006100 = 81.125496320   boot/grub/core.img                             1
  66.131257534 = 71.007897088   boot/grub/grub.cfg                             1
  76.924153805 = 82.596681216   boot/initrd.img-3.2.0-33-generic               3
  68.872582912 = 73.951372800   boot/initrd.img-3.2.0-34-generic               3
  75.520051479 = 81.089037824   boot/vmlinuz-3.2.0-33-generic                  2
  65.988801479 = 70.854936064   boot/vmlinuz-3.2.0-34-generic                  1
  65.988801479 = 70.854936064   vmlinuz                                        1
  75.520051479 = 81.089037824   vmlinuz.old                                    2

================= sda2: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

  66.131310940 = 71.007954432   boot/extlinux/chain.c32                        1
  65.094293118 = 69.894465024   boot/extlinux/extlinux.conf                    1

============== sda2: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  63 f6 84 bc f4 e0 fc 69  fb 90 f3 83 63 dc fb 17  |c......i....c...|
00000010  33 c9 7b 0c e2 fc 15 9b  4e ce 77 44 fe ba 0d f8  |3.{.....N.wD....|
00000020  b2 e4 b9 a8 ef ff d3 d3  96 5e 7f a8 6d 7b ff a0  |.........^..m{..|
00000030  35 f9 1b 41 bb 65 f4 ef  62 51 ff 06 62 1f 86 28  |5..A.e..bQ..b..(|
00000040  85 aa 96 fb 57 7e 64 bf  42 a4 d7 1b c4 1f fb 3f  |....W~d.B......?|
00000050  51 bf 72 22 f4 c0 d9 7f  6b 89 ff cc 18 51 5f 22  |Q.r"....k....Q_"|
00000060  7f 8f 22 9d d3 6f ca 43  3f ce c7 d9 43 7b d7 63  |.."..o.C?...C{.c|
00000070  7c dc fd fa 46 60 5c a9  3a 67 ab 3e be 11 f4 a1  ||...F`\.:g.>....|
00000080  ca e7 4c cf a7 49 fb 64  bb 30 7d ab 4c e8 6b b9  |..L..I.d.0}.L.k.|
00000090  ef 44 f4 fd db 4a 2b bf  48 21 f6 e6 11 27 ab 3d  |.D...J+.H!...'.=|
000000a0  7f 0f 0b 36 8e e3 b7 2f  88 3f 21 e4 b1 e5 fe c4  |...6.../.?!.....|
000000b0  61 c8 cb b4 33 e2 7d 63  77 62 9f 72 f6 73 3c 12  |a...3.}cwb.r.s<.|
000000c0  52 b9 fd d1 4b e4 fc 84  1b 6f 29 d8 43 1d 3f 88  |R...K....o).C.?.|
000000d0  eb e5 02 79 e4 ff dc c9  aa 1f 37 86 3e aa 52 28  |...y......7.>.R(|
000000e0  85 6d 96 fb 61 30 8c d3  2a 89 fe 3e f7 21 df 0f  |.m..a0..*..>.!..|
000000f0  2c 12 cf 03 7b 62 3e 52  b8 fb 0a e5 41 d8 67 39  |,...{b>R....A.g9|
00000100  7b a8 39 d6 27 8b 3b 8f  1f 00 7e a3 e2 f6 57 74  |{.9.'.;...~...Wt|
00000110  4a e2 ef 2a b3 ea 07 b3  b1 d0 a9 5a 67 a1 3e 8b  |J..*.......Zg.>.|
00000120  6f c0 78 32 38 fb f0 07  f0 f7 2c c8 67 cb fd 8e  |o.x28.....,.g...|
00000130  59 58 df 6c c8 8f fb 16  fa 6b 4d fc b7 c5 f5 4f  |YX.l.....kM....O|
00000140  06 e2 ef e0 fa e3 85 f5  0f c6 7c 58 fc d1 66 56  |..........|X..fV|
00000150  b5 e5 af 6e 48 c8 9e a9  b0 ee 3f bc 23 f7 29 b8  |...nH.....?.#.).|
00000160  f7 18 bc c1 9f b2 b9 f3  d2 91 e4 be 24 77 1f 6d  |............$w.m|
00000170  22 d9 cf 03 3e 59 e8 ad  3b 39 ef c6 f8 2c fa cc  |"...>Y..;9...,..|
00000180  73 d8 1b 29 dc fe ad 37  e8 49 c5 e9 f3 91 c4 1f  |s..)...7.I......|
00000190  f0 b3 e8 3f f4 07 04 75  46 1e 05 bd df 40 da 13  |...?...uF....@..|
000001a0  0c 86 c8 e8 d8 18 43 42  62 48 7c a2 c1 20 18 22  |......CBbH|.. ."|
000001b0  4c 31 26 7c 0c 1b 1c 42  7e 86 44 99 86 1a 00 fe  |L1&|...B~.D.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 b2 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d0  b2 00 00 b0 a8 03 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



 
```

---

### Post by oldfred on 2012-12-17
Windows always installs its boot loader.

       [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

    
You can use your Ubuntu liveCD or download full repair ISO.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)
    
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by maiandros on 2012-12-17
Ok. I have already downloaded and installed Boot Repair disk.

The requested link [http://paste.ubuntu.com/1446222/](http://paste.ubuntu.com/1446222/) 
This time i had all my externals HDDs connected...hope it helped a little bit more.

---

### Post by oldfred on 2012-12-17
You can just let Boot-Repair reinstall grub to the MBR. I might not install it to all drives, especially if they are external, but it probably does not matter.

Or you can manually reinstall grub2's boot loader.

Since you have several large external drives, you might want to review this. I follow his logic, but just install Ubuntu to every drive.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by Thee on 2012-12-17
If you're stuck in Windows, there is an easy way to solve it.
I use it and it works like a charm:

[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

You can add as many OS's as you like to the Windows bootloader using this program.

Note, you need to register to download the free version.

Good luck!

---

### Post by maiandros on 2012-12-27
Ok...so Merry Xmas and Happiest New Year to all guys! 
Thanks to Oldfred I`ve managed to gain access to my Ubuntu again.
I`m facing other probs now but i guess i`ll leave u alone for now.. ;-))))
Thanks again...i`m marking it as SOLVED

---

