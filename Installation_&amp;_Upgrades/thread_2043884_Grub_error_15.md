---
title: "Grub error 15"
date: 2012-08-17
forum: Installation &amp; Upgrades
---

### Post by sbub07 on 2012-08-17
hi all

i have installed ubuntu 11.10,after installation complete while loading from hard disk
it shows grub error 15,and not booting

i have attached below the boot info script output file

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #10 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of 
                       sda10 and looks at sector 2130389 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks for (,msdos10)/boot/grub on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

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

/dev/sda2    *            187   312,576,704   312,576,518   f W95 Extended (LBA)
/dev/sda5          57,352,237    77,834,924    20,482,688   7 NTFS / exFAT / HPFS
/dev/sda6          77,834,988   155,653,784    77,818,797   7 NTFS / exFAT / HPFS
/dev/sda7         155,653,848   233,472,644    77,818,797   7 NTFS / exFAT / HPFS
/dev/sda8         233,472,708   273,553,645    40,080,938   7 NTFS / exFAT / HPFS
/dev/sda9         273,554,883   312,560,639    39,005,757   7 NTFS / exFAT / HPFS
/dev/sda10                189    57,352,049    57,351,861  83 Linux
/dev/sda11        312,560,703   312,576,704        16,002  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda10       d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59   ext3       
/dev/sda11                                              swap       
/dev/sda5        E4A8936EA8933DCC                       ntfs       
/dev/sda6        32B8CBE5B8CBA627                       ntfs       Study
/dev/sda7        78D80841D808005C                       ntfs       Songs
/dev/sda8        F05097EB5097B6B6                       ntfs       Movies
/dev/sda9        58249C16249BF56A                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================== sda10/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59 ro recovery nomodeset 
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59
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

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=d1bb43bd-f63b-4f57-9ffc-c4bcfdb42b59 /               ext3    errors=remount-ro 0       1
/dev/sda11      none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               6
               =                boot/vmlinuz-3.0.0-12-generic                  3
               =                initrd.img                                     6
               =                vmlinuz                                        3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  01 05 00 00 00 00 00 05  15 00 00 00 2e 43 ac 40  |.............C.@|
00000010  3d e3 08 4d 23 5f 63 6b  01 02 00 00 00 00 00 00  |=..M#_ck........|
00000020  08 8a 2e d7 00 02 00 00  20 d8 00 00 00 00 00 00  |........ .......|
00000030  80 00 00 00 01 00 04 80  50 00 00 00 60 00 00 00  |........P...`...|
00000040  00 00 00 00 14 00 00 00  02 00 3c 00 02 00 00 00  |..........<.....|
00000050  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000060  20 00 00 00 20 02 00 00  00 00 14 00 ff 01 1f 00  | ... ...........|
00000070  01 01 00 00 00 00 00 05  12 00 00 00 41 cb b2 e1  |............A...|
00000080  c9 30 ab e1 01 02 00 00  00 00 00 05 20 00 00 00  |.0.......... ...|
00000090  20 02 00 00 01 01 00 00  00 00 00 05 12 00 00 00  | ...............|
000000a0  38 a2 32 91 01 02 00 00  a0 d8 00 00 00 00 00 00  |8.2.............|
000000b0  80 00 00 00 01 00 04 80  50 00 00 00 60 00 00 00  |........P...`...|
000000c0  00 00 00 00 14 00 00 00  02 00 3c 00 02 00 00 00  |..........<.....|
000000d0  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
000000e0  20 00 00 00 20 02 00 00  00 00 14 00 ff 01 1f 00  | ... ...........|
000000f0  01 01 00 00 00 00 00 05  12 00 00 00 00 00 00 00  |................|
00000100  a0 08 03 10 01 02 00 00  00 00 00 05 20 00 00 00  |............ ...|
00000110  20 02 00 00 01 01 00 00  00 00 00 05 12 00 00 00  | ...............|
00000120  f8 a1 31 8d 02 02 00 00  20 d9 00 00 00 00 00 00  |..1..... .......|
00000130  80 00 00 00 01 00 04 80  50 00 00 00 60 00 00 00  |........P...`...|
00000140  00 00 00 00 14 00 00 00  02 00 3c 00 02 00 00 00  |..........<.....|
00000150  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000160  20 00 00 00 20 02 00 00  00 00 14 00 ff 01 1f 00  | ... ...........|
00000170  01 01 00 00 00 00 00 05  12 00 00 00 00 00 00 00  |................|
00000180  80 08 01 08 01 02 00 00  00 00 00 05 20 00 00 00  |............ ...|
00000190  20 02 00 00 01 01 00 00  00 00 00 05 12 00 00 00  | ...............|
000001a0  20 b6 75 75 03 02 00 00  a0 d9 00 00 00 00 00 00  | .uu............|
000001b0  60 00 00 00 01 00 04 94  14 00 00 00 30 00 00 02  |`...........0...|
000001c0  fe ff 07 fe ff ff 72 1f  6b 03 80 8a 38 01 00 fe  |......r.k...8...|
000001d0  ff ff 05 fe ff ff f2 a9  a3 04 ec 6b a3 04 00 00  |...........k....|
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


please help me to solve this problem

thank you

---

### Post by oldfred on 2012-08-17
That is an old error from grub legacy (0.97). Ubuntu has used grub2 as the standard since 9.10, but you can still use it.

You installed grub2's boot loader to the partition PBR sda10 when you should install it to the MBR or sda.

Many like the gui way to repair, you can download into liveCD or download as a full liveCD of its own:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

You can also use Supergrub to boot and repair grub from inside your install or manually repair from liveCD:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda10 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda10 if not correct:
sudo fdisk -l
#confirm that linux is sda10
sudo mount /dev/sda10 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda


# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by sbub07 on 2012-08-20
Thank you

i got fixed the problem

---

