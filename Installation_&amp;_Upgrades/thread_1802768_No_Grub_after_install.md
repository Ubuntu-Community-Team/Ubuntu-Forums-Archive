---
title: "No Grub after install"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by Eirinjas on 2011-07-12
I installed Ubuntu 11.04 alongside a Win XP Pro installation and when the system boots straight into Windows, no menu.  I tried reinstalling Ubuntu, I tried reinstalling Grub2, but no luck so far.  Any ideas?

-Jas

---

### Post by YannBuntu on 2011-07-12
Hi,
try to press Shift key just after the BIOS (at the start of the computer) to make GRUB appear.

If it does not work, boot on a Ubuntu live-CD, then download the BootInfoScript ( [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) ), put it on your Desktop and launch it via the following command:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

then copy/paste here its output.

---

### Post by Quackers on 2011-07-12
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

### Post by Eirinjas on 2011-07-12
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 19bf037e-2673-4967-b6df-e8b96b540e21 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sdf2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdf3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdf5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   240,107,489   240,107,427   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 146.8 GB, 146815733760 bytes
255 heads, 63 sectors/track, 17849 cylinders, total 286749480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63        80,324        80,262  de Dell Utility
/dev/sdf2    *         80,325   143,412,254   143,331,930   7 NTFS / exFAT / HPFS
/dev/sdf3         143,413,246   286,748,671   143,335,426   5 Extended
/dev/sdf5         282,558,464   286,748,671     4,190,208  82 Linux swap / Solaris
/dev/sdf6         143,413,248   278,366,207   134,952,960  83 Linux
/dev/sdf7         278,368,256   282,550,271     4,182,016  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3A246D6E246D2DD7                       ntfs       
/dev/sdf1        07D3-0C10                              vfat       DellUtility
/dev/sdf2        A22C9D052C9CD59F                       ntfs       
/dev/sdf5        05f98838-1197-4db6-b7bd-68b3df26cc18   swap       
/dev/sdf6        19bf037e-2673-4967-b6df-e8b96b540e21   ext4       
/dev/sdf7        5d5a9904-8169-4299-9832-1c651fa8288e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sdf2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdf6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 19bf037e-2673-4967-b6df-e8b96b540e21
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 19bf037e-2673-4967-b6df-e8b96b540e21
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
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 19bf037e-2673-4967-b6df-e8b96b540e21
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=19bf037e-2673-4967-b6df-e8b96b540e21 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 19bf037e-2673-4967-b6df-e8b96b540e21
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=19bf037e-2673-4967-b6df-e8b96b540e21 ro single 
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
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 19bf037e-2673-4967-b6df-e8b96b540e21
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 19bf037e-2673-4967-b6df-e8b96b540e21
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root A22C9D052C9CD59F
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

=============================== sdf6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=5d5a9904-8169-4299-9832-1c651fa8288e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdf6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 102.518802643 = 110.078726144  boot/grub/core.img                             1
 129.109134674 = 138.629877760  boot/grub/grub.cfg                             1
  69.517799377 = 74.644168704   boot/initrd.img-2.6.38-8-generic               2
 102.517070770 = 110.076866560  boot/vmlinuz-2.6.38-8-generic                  1
  69.517799377 = 74.644168704   initrd.img                                     2
 102.517070770 = 110.076866560  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdf1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 4f 00  3f 00 ff 00 3f 00 00 00  |......O.?...?...|
00000020  86 39 01 00 80 00 29 10  0c d3 07 44 65 6c 6c 55  |.9....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 81 3e 72  04 45 44 74 1d ff 0e 13  |{.....>r.EDt....|
00000060  04 8b 0e 13 04 c1 e1 06  8e c1 b9 00 01 33 f6 33  |.............3.3|
00000070  ff f3 66 a5 c7 06 72 04  45 44 8e c0 bd 00 7c e8  |..f...r.ED....|.|
00000080  21 01 0f 82 bb 00 66 0f  b7 86 16 00 66 d1 e0 66  |!.....f.....f..f|
00000090  0f b7 9e 0e 00 66 03 c3  66 03 86 1c 00 66 89 86  |.....f..f....f..|
000000a0  3e 00 8b 86 11 00 c1 e8  04 89 86 46 00 bb 00 05  |>..........F....|
000000b0  e8 aa 00 0f 82 8a 00 ba  10 00 b9 0b 00 be f2 7d  |...............}|
000000c0  8b fb f3 a6 74 16 83 c3  20 4a 75 ee 66 ff 86 3e  |....t... Ju.f..>|
000000d0  00 ff 8e 46 00 75 d6 be  e1 7d eb 6d 66 0f b7 86  |...F.u...}.mf...|
000000e0  11 00 66 ba 20 00 00 00  66 f7 e2 66 0f b7 8e 0b  |..f. ...f..f....|
000000f0  00 66 03 c1 66 48 66 f7  f1 66 01 86 3e 00 66 8b  |.f..fHf..f..>.f.|
00000100  86 3e 00 66 89 46 fc 66  0f b7 47 1a 8b f8 2d 02  |.>.f.F.f..G...-.|
00000110  00 66 0f b6 9e 0d 00 66  f7 e3 66 01 86 3e 00 bb  |.f.....f..f..>..|
00000120  00 07 c7 86 46 00 04 00  e8 32 00 72 14 81 c3 00  |....F....2.r....|
00000130  02 66 ff 86 3e 00 ff 8e  46 00 75 ec ea 00 02 70  |.f..>...F.u....p|
00000140  00 be d4 7d eb 03 be e1  7d e8 02 00 eb fe ac 3c  |...}....}......<|
00000150  00 74 09 b4 0e bb 07 00  cd 10 eb f2 c3 66 8b 86  |.t...........f..|
00000160  3e 00 66 33 d2 66 0f b7  8e 18 00 66 f7 f1 66 42  |>.f3.f.....f..fB|
00000170  88 96 45 00 66 33 d2 66  0f b7 8e 1a 00 66 f7 f1  |..E.f3.f.....f..|
00000180  88 96 44 00 89 86 42 00  b8 01 02 8b 8e 42 00 c0  |..D...B......B..|
00000190  e5 06 0a ae 45 00 86 e9  8a b6 44 00 8a 96 24 00  |....E.....D...$.|
000001a0  cd 13 c3 80 3e c2 07 06  74 29 b8 01 02 bb 00 06  |....>...t)......|
000001b0  b9 01 00 b6 00 8a 96 24  00 cd 13 72 16 c6 06 c2  |.......$...r....|
000001c0  07 06 b8 01 03 bb 00 06  b9 01 00 b6 00 8a 96 24  |...............$|
000001d0  00 cd 13 c3 44 69 73 6b  20 65 72 72 6f 72 0d 0a  |....Disk error..|
000001e0  00 4d 69 73 73 69 6e 67  20 6c 6f 61 64 65 72 0d  |.Missing loader.|
000001f0  0a 00 49 4f 20 20 20 20  20 20 53 59 53 00 55 aa  |..IO      SYS.U.|
00000200

Unknown BootLoader on sdf3

00000000  df 17 10 50 83 80 96 96  00 4a 83 00 50 00 00 48  |...P.....J..P..H|
00000010  8a b1 b1 22 2e 2e 2e 36  cf a5 18 70 52 50 50 10  |..."...6...pRPP.|
00000020  9d 01 88 81 5e 00 4e 88  ed 44 7a f1 f8 97 49 88  |....^.N..Dz...I.|
00000030  00 4e 82 13 25 00 4e 82  0a f6 10 4f 83 59 81 86  |.N..%.N....O.Y..|
00000040  00 f2 83 04 23 50 00 01  88 00 77 e0 22 22 2e 25  |....#P....w."".%|
00000050  cf 10 01 85 e0 2e 48 79  79 60 f1 40 9d 10 4f 11  |......Hyy`.@..O.|
00000060  3a 8a 5e 39 0b 44 1c cb  c1 9f 9d 20 33 ab 81 75  |:.^9.D..... 3..u|
00000070  03 ad 00 4d 97 99 4b 08  d4 7d 17 10 10 02 4a 96  |...M..K..}....J.|
00000080  23 23 50 77 e0 e0 cf cf  12 16 12 cf 13 3b 84 25  |##Pw.........;.%|
00000090  48 0a 0a ca 10 09 81 30  00 4e 96 03 23 02 23 23  |H......0.N..#.##|
000000a0  ac 07 07 39 39 1c 1f 1f  29 ce cc d6 83 2f 2f 25  |...99...)....//%|
000000b0  75 00 4a 8a 09 09 99 4b  4b 08 df 7d 7d 17 00 4e  |u.J....KK..}}..N|
000000c0  82 00 02 01 da 81 cd 00  50 90 22 2e 36 36 25 25  |........P.".66%%|
000000d0  7d b9 f7 12 cf 48 22 0a  22 50 c8 01 0a 81 30 00  |}....H"."P....0.|
000000e0  4f 94 03 ce d9 a8 23 ac  ec ec af 39 dc d8 4e 55  |O.....#....9..NU|
000000f0  47 9c 2f 2f 6f 0b 10 4c  86 26 99 4b 59 59 07 00  |G.//o..L.&.KYY..|
00000100  4c 8d 10 1f 00 02 00 00  02 02 4a 04 96 80 23 01  |L.........J...#.|
00000110  3e 82 50 77 01 39 82 25  b9 10 01 85 f7 eb 8d 22  |>.Pw.9.%......."|
00000120  fd 30 4c 81 30 10 4c 85  45 6d e7 e7 d9 01 d7 81  |.0L.0.L.Em......|
00000130  ac 01 89 98 48 d2 e9 d6  af cc 12 af 61 26 26 26  |....H.......a&&&|
00000140  99 99 57 99 4b d4 17 72  17 17 98 10 20 9a 81 04  |..W.K..r.... ...|
00000150  22 77 85 96 23 96 2f 01  01 a0 85 c5 fd fd 22 8d  |"w..#./.......".|
00000160  10 50 85 99 a5 99 f7 eb  30 9b 81 e5 00 4d 83 ce  |.P......0....M..|
00000170  ce ce 00 9b 22 73 91 07  39 b2 b2 7a ae aa 12 88  |...."s..9..z....|
00000180  e4 7c 7c 09 57 1c 1c 1c  00 9b 81 1f 00 4e 00 9b  |.||.W........N..|
00000190  00 9a 12 29 85 23 23 05  96 23 21 6e 87 8e 8e 8e  |...).##..#!n....|
000001a0  c5 fd 22 a5 20 a2 00 01  20 9e 10 9c 81 ce 00 9b  |..". ... .......|
000001b0  30 4f 96 af 35 d8 4f 36  97 eb 93 88 88 2f 00 fe  |0O..5.O6...../..|
000001c0  ff ff 82 fe ff ff 02 30  4b 08 00 f0 3f 00 00 fe  |.......0K...?...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 38 0b 08 00 00  |...........8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by Quackers on 2011-07-12
If /dev/sdf is the first bootable hard drive in your bios settings, then that is where you should install grub.
Grub is presently installed to /dev/sda, but as you say that Windows is booting directly I am assuming that /dev/sdf is first bootable hard drive. Is that correct?

EDIT  On the other hand you could try making /dev/sda the first bootable drive in bios and see if grub works from there. It could do :-)

---

