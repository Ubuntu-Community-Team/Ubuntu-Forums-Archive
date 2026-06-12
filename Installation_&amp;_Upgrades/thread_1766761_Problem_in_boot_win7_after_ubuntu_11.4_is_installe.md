---
title: "Problem in boot win7 after ubuntu 11.4 is installed"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by dd2119 on 2011-05-24
After installing ubuntu 11.4, i cannot dual boot  windows 7, i have searched the similar threads, but problem is not solved. My boot script info is :



============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos10)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 629026144 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 469. But according to the info from fdisk, 
                       sda5 starts at sector 81915904.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 NTFS / exFAT / HPFS
/dev/sda2          81,915,902   976,751,999   894,836,098   f W95 Extended (LBA)
/dev/sda5          81,915,904   165,804,031    83,888,128   7 NTFS / exFAT / HPFS
/dev/sda6         165,806,928   585,231,884   419,424,957   7 NTFS / exFAT / HPFS
/dev/sda7         585,231,948   624,294,447    39,062,500  82 Linux swap / Solaris
/dev/sda8         669,123,378   976,751,999   307,628,622   7 NTFS / exFAT / HPFS
/dev/sda9         665,475,072   669,122,559     3,647,488  82 Linux swap / Solaris
/dev/sda10        624,295,936   661,809,151    37,513,216  83 Linux
/dev/sda11        661,811,200   665,460,735     3,649,536  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5E4098114097EDD1                       ntfs       winxp
/dev/sda10       17565d2f-92cc-4c32-babb-1d069e1f8242   ext4       
/dev/sda11       34e829d8-597f-4d4c-b14e-cbfed90aa32b   swap       
/dev/sda5        58A6B47AA6B459E8                       ntfs       win7
/dev/sda6        D8108EA5108E8A68                       ntfs       backup
/dev/sda7        df1bc547-d8ff-4d7c-a6d3-8055d2273810   swap       
/dev/sda8        EC04CD7304CD4176                       ntfs       mybkp
/dev/sda9        011e8792-63b6-47e8-aa20-dae936ca6951   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/win7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /NOEXECUTE=OPTIN /FASTDETECT 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos10)'
search --no-floppy --fs-uuid --set=root 17565d2f-92cc-4c32-babb-1d069e1f8242
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos10)'
search --no-floppy --fs-uuid --set=root 17565d2f-92cc-4c32-babb-1d069e1f8242
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
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 17565d2f-92cc-4c32-babb-1d069e1f8242
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=17565d2f-92cc-4c32-babb-1d069e1f8242 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 17565d2f-92cc-4c32-babb-1d069e1f8242
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=17565d2f-92cc-4c32-babb-1d069e1f8242 ro single 
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
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 17565d2f-92cc-4c32-babb-1d069e1f8242
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 17565d2f-92cc-4c32-babb-1d069e1f8242
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5E4098114097EDD1
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

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda10      /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=34e829d8-597f-4d4c-b14e-cbfed90aa32b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 304.090641022 = 326.514839552  boot/grub/core.img                             1
 309.861679077 = 332.711444480  boot/grub/grub.cfg                             1
 298.715061188 = 320.742854656  boot/initrd.img-2.6.38-8-generic               1
 304.088912964 = 326.512984064  boot/vmlinuz-2.6.38-8-generic                  1
 298.715061188 = 320.742854656  initrd.img                                     1
 304.088912964 = 326.512984064  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  01 02 00 00 00 00 00 05  20 00 00 00 20 02 00 00  |........ ... ...|
00000010  00 10 18 00 a9 00 12 00  01 02 00 00 00 00 00 05  |................|
00000020  20 00 00 00 21 02 00 00  00 10 24 00 ff 01 1f 00  | ...!.....$.....|
00000030  01 05 00 00 00 00 00 05  15 00 00 00 17 1a 75 fe  |..............u.|
00000040  c1 b1 0c 1c cd 6f fd f6  e8 03 00 00 01 05 00 00  |.....o..........|
00000050  00 00 00 05 15 00 00 00  17 1a 75 fe c1 b1 0c 1c  |..........u.....|
00000060  cd 6f fd f6 e8 03 00 00  01 05 00 00 00 00 00 05  |.o..............|
00000070  15 00 00 00 17 1a 75 fe  c1 b1 0c 1c cd 6f fd f6  |......u......o..|
00000080  01 02 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  b6 ee 36 42 09 04 00 00  90 08 03 00 00 00 00 00  |..6B............|
000000a0  9c 00 00 00 01 00 14 88  6c 00 00 00 7c 00 00 00  |........l...|...|
000000b0  14 00 00 00 30 00 00 00  02 00 1c 00 01 00 00 00  |....0...........|
000000c0  11 10 14 00 01 00 00 00  01 01 00 00 00 00 00 10  |................|
000000d0  00 30 00 00 02 00 3c 00  02 00 00 00 00 00 18 00  |.0....<.........|
000000e0  ff 01 1f 00 01 02 00 00  00 00 00 05 20 00 00 00  |............ ...|
000000f0  20 02 00 00 00 00 14 00  ff 01 1f 00 01 01 00 00  | ...............|
00000100  00 00 00 05 12 00 00 00  57 00 41 00 0a 02 07 0a  |........W.A.....|
00000110  01 02 00 00 00 00 00 05  20 00 00 00 20 02 00 00  |........ ... ...|
00000120  01 01 00 00 00 00 00 05  12 00 00 00 00 00 00 00  |................|
00000130  f7 50 f8 04 0a 04 00 00  30 09 03 00 00 00 00 00  |.P......0.......|
00000140  64 04 00 00 01 00 04 84  34 04 00 00 44 04 00 00  |d.......4...D...|
00000150  00 00 00 00 14 00 00 00  02 00 20 04 34 00 00 00  |.......... .4...|
00000160  00 00 14 00 9f 01 12 00  01 01 00 00 00 00 00 01  |................|
00000170  00 00 00 00 00 00 14 00  9f 01 12 00 01 01 00 00  |................|
00000180  00 00 00 01 00 00 00 00  00 00 14 00 9f 01 12 00  |................|
00000190  01 01 00 00 00 00 00 01  00 00 00 00 00 00 14 00  |................|
000001a0  9f 01 12 00 01 01 00 00  00 00 00 01 00 00 00 00  |................|
000001b0  00 00 14 00 9f 01 12 00  01 01 00 00 00 00 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 08 00 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff 13 13  00 05 fc ea ff 18 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by enkrypt3d on 2011-05-24
Boot onto the windows CD and go into recovery mode and bring up the command prompt and type

bootrec.exe /fixmbr

bootrec.exe /fixboot

and that will recover your windows install... Not sure about recovering the other though. You can try booting onto the live cd and follow some of these links:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by Quackers on 2011-05-24
You appear to have installed grub to sda1. This is a NTFS partition for XP and Win 7's boot files. Running the above fix should sort out the Windows bootloader. You may need to re-install grub to /dev/sda afterwards to get Ubuntu booting again, then run sudo update-grub in the terminal to get XP and Win 7 booting from grub.

---

