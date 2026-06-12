---
title: "Ubuntu XP boot problem"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by cooldoctormohitm on 2011-10-24
sir,...
           Mine ubuntu11.04 partition was missing after installing windows xp,but as i restored ubuntu11.04 using live usb now, I am unable to boot into my xp partition, even though i can see windows as well as ubuntu in boot list...and i m able to login into ubuntu, but as i try to login into xp part..i got such a error message-

error:no such device: 266041B560418DOD
error:device format: "dev sd,msdos 1" invalid: must be (f/h/dN,with 0<=N<128)
erorr:no such disk.


i want to login into xp as well as ubuntu..pls help regaring this..
additional info about my system ia attached: thank you

---

### Post by Rubi1200 on 2011-10-26
> **cooldoctormohitm said:**
> sir,...
           Mine ubuntu11.04 partition was missing after installing windows xp,but as i restored ubuntu11.04 using live usb now, I am unable to boot into my xp partition, even though i can see windows as well as ubuntu in boot list...and i m able to login into ubuntu, but as i try to login into xp part..i got such a error message-

error:no such device: 266041B560418DOD
error:device format: "dev sd,msdos 1" invalid: must be (f/h/dN,with 0<=N<128)
erorr:no such disk.


i want to login into xp as well as ubuntu..pls help regaring this..
additional info about my system ia attached: thank you

I have moved your post into its own thread.

Thanks for understanding.

---

### Post by Mark Phelps on 2011-10-26
I've pasted your script results here using Code tags -- so it's readable:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

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

/dev/sda1    *             63    34,812,854    34,812,792   7 NTFS / exFAT / HPFS
/dev/sda2          34,812,916   156,301,311   121,488,396   f W95 Extended (LBA)
/dev/sda5          34,812,918   131,074,334    96,261,417   7 NTFS / exFAT / HPFS
/dev/sda6         131,074,398   141,307,739    10,233,342   7 NTFS / exFAT / HPFS
/dev/sda7         141,307,803   143,347,994     2,040,192  82 Linux swap / Solaris
/dev/sda8         143,349,760   151,324,671     7,974,912  83 Linux
/dev/sda9         151,326,720   156,301,311     4,974,592  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        16DC2698DC2671E3                       ntfs       
/dev/sda5        0CA03E1FA03E0FA6                       ntfs       sounds
/dev/sda6        521045C41045B031                       ntfs       fun & work
/dev/sda7        2f2a9f06-a6ea-4009-bb3f-046143739097   swap       
/dev/sda8        5c5de28f-2575-4b47-b95a-42a2f8e22b1d   ext4       
/dev/sda9        43b2ddf0-e88a-45db-919c-e7db78c8df6b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/16DC2698DC2671E3  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[Boot Loader]
Timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS\
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS\="Microsoft Windows" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 5c5de28f-2575-4b47-b95a-42a2f8e22b1d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 5c5de28f-2575-4b47-b95a-42a2f8e22b1d
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
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 5c5de28f-2575-4b47-b95a-42a2f8e22b1d
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=5c5de28f-2575-4b47-b95a-42a2f8e22b1d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 5c5de28f-2575-4b47-b95a-42a2f8e22b1d
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=5c5de28f-2575-4b47-b95a-42a2f8e22b1d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 5c5de28f-2575-4b47-b95a-42a2f8e22b1d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 5c5de28f-2575-4b47-b95a-42a2f8e22b1d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 266041B560418D0D
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=5c5de28f-2575-4b47-b95a-42a2f8e22b1d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=43b2ddf0-e88a-45db-919c-e7db78c8df6b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  69.230453491 = 74.335633408   boot/grub/core.img                             1
  71.482368469 = 76.753608704   boot/grub/grub.cfg                             1
  69.995117188 = 75.156684800   boot/initrd.img-2.6.38-8-generic               2
  69.301914215 = 74.412363776   boot/vmlinuz-2.6.38-8-generic                  1
  69.995117188 = 75.156684800   initrd.img                                     2
  69.301914215 = 74.412363776   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  97 f2 fd 91 1f fe 16 d9  d2 ae 8a 34 a2 47 47 c8  |...........4.GG.|
00000010  2a fe 66 38 e4 f6 e7 2b  6a 51 1d 4d 7d a6 b0 6a  |*.f8...+jQ.M}..j|
00000020  00 22 62 9c b6 49 28 8f  97 f3 a1 ce 65 21 a3 35  |."b..I(.....e!.5|
00000030  3e 34 af da fa 61 1f 6a  34 bc ee 57 e6 ed ff fb  |>4...a.j4..W....|
00000040  92 04 f8 80 03 0d 5c 5c  e1 e7 1a f2 4b 6b 2b ac  |......\\....Kk+.|
00000050  3c 47 5e 0d 59 83 71 a7  a8 6b c9 9b b0 ee 30 f2  |<G^.Y.q..k....0.|
00000060  a1 79 46 6b d8 b9 bb 21  8e 6d b5 ea c8 ba af 6a  |.yFk...!.m.....j|
00000070  db d1 e6 bf 5e af 4d 5b  5f 6b 6f 9d 30 ba 9d ba  |....^.M[_ko.0...|
00000080  4c 1a a2 bd 2d 74 b3 fb  38 85 8e 7a 26 eb 46 1d  |L...-t..8..z&.F.|
00000090  05 cf 59 42 4a 51 0b 8a  72 d1 b7 8e ff 65 4e 6d  |..YBJQ..r....eNm|
000000a0  d6 90 14 9c 96 e6 51 ac  a9 7c a3 82 33 b7 7c 77  |......Q..|..3.|w|
000000b0  41 98 ee ac 81 ab 2d a3  02 ea fc ea 73 df d6 62  |A.....-.....s..b|
000000c0  72 a6 79 1a cc 6a 74 69  0c ee f7 2e 48 37 54 36  |r.y..jti....H7T6|
000000d0  ec dc a8 b4 98 ff 46 5f  e4 dd 9f a2 ba 7a 36 8a  |......F_.....z6.|
000000e0  cd 5c 25 97 61 1f 29 3a  cd bd 0a 33 9d 91 d9 97  |.\%.a.):...3....|
000000f0  50 c6 55 64 20 c5 77 d7  e5 db 03 cb 59 b6 0a 6e  |P.Ud .w.....Y..n|
00000100  dd 6d 34 46 b3 8d 9b df  9c 5a de 3d 80 cb 17 d3  |.m4F.....Z.=....|
00000110  a2 92 8a 0d 55 69 3a ce  ea 53 ab cd d3 7a 4b 31  |....Ui:..S...zK1|
00000120  bf 3a 87 f5 fe d0 95 fa  a7 cd 4c 9d 5f 17 37 3c  |.:........L._.7<|
00000130  57 1f c3 f5 73 4d 71 7f  3a 69 c5 db 45 f7 fe b0  |W...sMq.:i..E...|
00000140  dc cd 40 f9 6f fc a7 59  5e 2d ae a7 aa e7 e1 44  |..@.o..Y^-.....D|
00000150  97 f0 f1 10 b2 b5 a8 0a  af d4 0f 4b b1 ac aa 4b  |...........K...K|
00000160  3c 51 90 41 2d 15 1c b6  ee ae 17 ca 54 64 64 99  |<Q.A-.......Tdd.|
00000170  69 ff fb 2b 7e 94 a7 99  1a a8 20 08 e9 de b3 cc  |i..+~..... .....|
00000180  be a5 3f 3a 5f 3a 8b ae  62 e9 2d 19 05 cb 4a 15  |..?:_:..b.-...J.|
00000190  b5 32 32 1b 97 ce 72 12  c7 60 ef 55 3b 26 aa 2c  |.22...r..`.U;&.,|
000001a0  da 22 b7 bd 7a fe 88 dd  28 fd 0f ca e2 44 f4 15  |."..z...(....D..|
000001b0  ec e8 a5 76 45 6c cc 53  56 ae 7c ee 75 86 00 01  |...vEl.SV.|.u...|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 29 d5 bc 05 00 00  |..........).....|
000001d0  c1 ff 05 fe ff ff 2b d5  bc 05 3d 26 9c 00 00 00  |......+...=&....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Mark Phelps on 2011-10-26
Boot into Ubuntu, open a terminal and enter "sudo update-grub".  That will rewrite the GRUB config file and you should then be able to select XP and boot into it.

---

