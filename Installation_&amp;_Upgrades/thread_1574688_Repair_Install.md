---
title: "Repair Install?"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by fireoftroy on 2010-09-14
Does Ubuntu 10.04 have a repair install option?  I believe my MBR got knocked out as the BIOS reports an unbootable disk.  I booted with the CD and confirmed all the data appears intact on the HDD, so I'm curious if there is a way to repair the MBR without completely reinstalling the software.

I started going through the install process but stopped when I got to the partition section.  The automatic option had the first partition with Winblows XP and the second with Ubuntu 10.04.1.  The manual option defaulted to first partition with Winblows, the second with Ubuntu 10.04 and a third with Ubuntu 10.04.1.  It appears that the automatic option will try to repair the existing OS, but I want to make an informed decision before proceeding.

---

### Post by Rubi1200 on 2010-09-14
There is no repair install option in Ubuntu.

Since you have the LiveCD, boot the computer and post the results of the bootscript linked to at the bottom of my post.

If there is a problem with the MBR, the results will let us know and make offering solutions a lot easier.

Thanks.

---

### Post by fireoftroy on 2010-09-16
Here is the output from the bootscript:

                Boot Info Script 0.55    dated February 15th, 2010                   

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #5 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    86,817,479    86,817,417   7 HPFS/NTFS
/dev/sda2          86,818,814   156,301,311    69,482,498   5 Extended
/dev/sda5          86,818,816   153,350,143    66,531,328  83 Linux
/dev/sda6         153,352,192   156,301,311     2,949,120  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    80,003,699    80,003,637   7 HPFS/NTFS
/dev/sdb2          80,003,700   156,296,384    76,292,685   f W95 Ext d (LBA)
/dev/sdb5          80,003,763   156,296,384    76,292,622   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                        

/dev/loop0                                              squashfs                                
/dev/sda1        968C58A68C5882A3                       ntfs       TARA                         
/dev/sda2: PTTYPE="dos"
/dev/sda5        f666f6a8-482a-42b4-9d1e-894015fb0d00   ext4                                    
/dev/sda6        a1b50e0d-12bc-4afb-9134-e98b3f0aaaf9   swap                                    
/dev/sda: PTTYPE="dos"
/dev/sdb1        7EA40CB4A40C70C7                       ntfs                                    
/dev/sdb2: PTTYPE="dos"
/dev/sdb5        C4540E40540E35A8                       ntfs                                    
/dev/sdb: PTTYPE="dos"

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/C4540E40540E35A8  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/f666f6a8-482a-42b4-9d1e-894015fb0d00 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=f666f6a8-482a-42b4-9d1e-894015fb0d00 ro   quiet splash
initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
echo 'Loading Linux 2.6.32-24-generic ...'
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=f666f6a8-482a-42b4-9d1e-894015fb0d00 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
linux /boot/vmlinuz-2.6.32-23-generic root=UUID=f666f6a8-482a-42b4-9d1e-894015fb0d00 ro   quiet splash
initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
echo 'Loading Linux 2.6.32-23-generic ...'
linux /boot/vmlinuz-2.6.32-23-generic root=UUID=f666f6a8-482a-42b4-9d1e-894015fb0d00 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
linux /boot/vmlinuz-2.6.32-22-generic root=UUID=f666f6a8-482a-42b4-9d1e-894015fb0d00 ro   quiet splash
initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
echo 'Loading Linux 2.6.32-22-generic ...'
linux /boot/vmlinuz-2.6.32-22-generic root=UUID=f666f6a8-482a-42b4-9d1e-894015fb0d00 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f666f6a8-482a-42b4-9d1e-894015fb0d00 ro   quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
echo 'Loading Linux 2.6.32-21-generic ...'
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f666f6a8-482a-42b4-9d1e-894015fb0d00 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f666f6a8-482a-42b4-9d1e-894015fb0d00
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 968c58a68c5882a3
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 7ea40cb4a40c70c7
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f666f6a8-482a-42b4-9d1e-894015fb0d00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a1b50e0d-12bc-4afb-9134-e98b3f0aaaf9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  74.6GB: boot/grub/core.img
  58.0GB: boot/grub/grub.cfg
  75.4GB: boot/initrd.img-2.6.32-21-generic
  75.4GB: boot/initrd.img-2.6.32-22-generic
  75.5GB: boot/initrd.img-2.6.32-23-generic
  46.6GB: boot/initrd.img-2.6.32-24-generic
  75.3GB: boot/vmlinuz-2.6.32-21-generic
  75.2GB: boot/vmlinuz-2.6.32-22-generic
  75.4GB: boot/vmlinuz-2.6.32-23-generic
  75.7GB: boot/vmlinuz-2.6.32-24-generic
  46.6GB: initrd.img
  75.5GB: initrd.img.old
  75.7GB: vmlinuz
  75.4GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  7f 59 bc 27 78 db cd 46  7c 5f 6b ad 62 a4 8e ba  |.Y.'x..F|_k.b...|
00000010  1a 82 0f 1d 89 48 15 76  b8 67 1c 6e a9 9a 32 68  |.....H.v.g.n..2h|
00000020  79 0b 4d db 65 80 e5 8e  9c 10 2e 50 0b dc fb b5  |y.M.e......P....|
00000030  b7 9a 73 8b e9 8b 5b a0  19 f7 aa 5c 8f c6 80 74  |..s...[....\...t|
00000040  5b 39 70 7e 75 ea 27 01  40 53 07 31 da 62 16 6c  |[9p~u.'.@S.1.b.l|
00000050  24 28 e7 93 f3 b4 f5 41  ed 58 1c 08 cd 8f 5e 3d  |$(.....A.X....^=|
00000060  cf bb f5 01 cb b6 98 c8  20 6b 56 e1 ba 1c 33 df  |........ kV...3.|
00000070  b0 fc 68 56 11 36 37 91  92 81 cd d5 95 5b 2d 6f  |..hV.67......[-o|
00000080  8b 55 8e 08 f5 52 0e 92  cb dd 7f 19 b3 d6 fa 6a  |.U...R.........j|
00000090  2c 2a e9 b6 58 36 82 8a  82 41 cb fa 32 a8 9e 52  |,*..X6...A..2..R|
000000a0  6e 99 4e 8d 31 44 6d 50  89 4c 0e 34 75 b5 42 25  |n.N.1DmP.L.4u.B%|
000000b0  14 60 61 60 ce 2b 84 9f  50 a1 ba fc fb 8d 59 bb  |.`a`.+..P.....Y.|
000000c0  43 72 30 0a 3d 48 3d 98  33 bb 61 07 e7 3a ee 59  |Cr0.=H=.3.a..:.Y|
000000d0  f3 83 80 88 73 86 bc 55  e8 b7 8b 16 b9 2f 19 d4  |....s..U...../..|
000000e0  8f 31 89 74 73 24 85 07  32 21 d4 29 e7 3d 9e ed  |.1.ts$..2!.).=..|
000000f0  d6 aa 81 14 21 cb 8c 33  07 3d 0a 8a 0a cf 8e 3f  |....!..3.=.....?|
00000100  dd f6 d0 a8 8c 46 fd 63  1f 09 e2 6c 8d 5e c7 a8  |.....F.c...l.^..|
00000110  c7 45 db 21 b6 4f 2a a1  5c 34 be 8d 34 91 01 e0  |.E.!.O*.\4..4...|
00000120  a3 c4 07 ac a1 9d 5e 10  b0 68 b9 87 b2 95 e2 ae  |......^..h......|
00000130  07 5f 32 5c f8 33 f4 3e  5b 5c b2 5b 16 5f b6 55  |._2\.3.>[\.[._.U|
00000140  42 2f 3d cf 21 1b 6d ed  5f ed 34 46 f1 b1 28 49  |B/=.!.m._.4F..(I|
00000150  bd b7 85 e3 85 8a 48 3c  d6 0f a6 b6 d7 16 36 c0  |......H<......6.|
00000160  38 d8 e4 9c fe 87 a9 13  c4 31 0d f4 c9 1a 69 ec  |8........1....i.|
00000170  2c f6 fd 3c a3 11 80 01  f1 27 bd 05 43 ca 5f 72  |,..<.....'..C._r|
00000180  48 0f e1 5c e0 cd 37 2d  ad 8b ac 74 39 05 c9 1f  |H..\..7-...t9...|
00000190  03 4f 1f 94 df 90 82 14  ef ad 6a 0e 73 5a 77 8d  |.O........j.sZw.|
000001a0  2d b8 3a 2f fa 49 94 e3  96 10 bb 58 73 68 42 b4  |-.:/.I.....XshB.|
000001b0  82 e4 bb f4 9b f0 bf ab  67 88 35 49 61 70 00 fe  |........g.5Iap..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 f7 03 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff 02 30  f7 03 00 08 2d 00 00 00  |.......0....-...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Thanks for looking into this!

---

### Post by fireoftroy on 2010-09-21
Looking through the MBR report, I don't see any glaring errors, but then again I don't know what a healthy report looks like, so I don't really have a reference point.

If I reinstall Ubuntu 10.04 from the live CD, will it completely erase all users, system settings, etc?  For example, if I've setup Apache, will I need to completely reconfigure it if I reinstall Ubuntu or will all the installed software remain relatively the same?

Thanks!

---

### Post by Rubi1200 on 2010-09-21
> **fireoftroy said:**
> Looking through the MBR report, I don't see any glaring errors, but then again I don't know what a healthy report looks like, so I don't really have a reference point.

If I reinstall Ubuntu 10.04 from the live CD, will it completely erase all users, system settings, etc?  For example, if I've setup Apache, will I need to completely reconfigure it if I reinstall Ubuntu or will all the installed software remain relatively the same?

Thanks!
Yes, but you have 2 drives sda and sdb; have you tried changing the boot order in BIOS?

If you reinstall it will completely reformat and wipe out whatever was there, so yes you would have to also reinstall Apache etc.

But, first things first, try changing the boot order or even switching from Master to Slave and see if that changes anything.

We could also reinstall GRUB and see if that helps.

Let us know please.

---

### Post by fireoftroy on 2010-09-23
Thankfully this was not relating to the MBR.  Long story short, I had removed a CD-ROM drive which was the slave on the same channel as the primary HDD.  When I looked a second time, the jumper on the HDD was set to master with slave present.  I pulled the jumper, powered up, and what do you know, it worked!

As the saying goes, measure twice, cut once.

Thanks for the help!!!

---

### Post by Rubi1200 on 2010-09-23
> **fireoftroy said:**
> Thankfully this was not relating to the MBR.  Long story short, I had removed a CD-ROM drive which was the slave on the same channel as the primary HDD.  When I looked a second time, the jumper on the HDD was set to master with slave present.  I pulled the jumper, powered up, and what do you know, it worked!

As the saying goes, measure twice, cut once.

Thanks for the help!!!
I am glad you got it sorted out :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

