---
title: "Grub not working or something"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by lowryb on 2011-03-15
Hey, I've just recently wiped my hard disk and reinstalled windows and ubuntu.  However, the boot manager is not seeing linux at all. I installed windows 7 first (on a blank slate), and then proceeded to repartition the hard drive with an ubuntu live cd and installed linux.  The boot manager is automatically booting to windows 7 and is not seeing ubuntu at all.  Any direction on where to look to fix this problem would be greatly appreciated.  Thanks.

---

### Post by wojox on 2011-03-15
You could try reinstalling from a [Live-CD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD").

Did you let Ubuntu install Grub2 to the MBR at the end of the install?

---

### Post by Rubi1200 on 2011-03-15
Hi and welcome to the forums lowryb :)

So we can get a better overview of the current state of your setup, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Thanks.

---

### Post by lowryb on 2011-03-15
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,230,721,023 1,230,718,976   7 HPFS/NTFS
/dev/sda2       1,230,723,070 1,953,523,711   722,800,642   5 Extended
/dev/sda5       1,230,723,072 1,929,938,943   699,215,872  83 Linux
/dev/sda6       1,929,940,992 1,953,523,711    23,582,720  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A252AD0952ACE371                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1a254d12-8285-41bc-ba17-dc822adf9c35   ext4                                     
/dev/sda6        b5099451-41ba-4d60-b3d6-ad1b6851f485   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14FCD9A4FCD98082                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1a254d12-8285-41bc-ba17-dc822adf9c35
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1a254d12-8285-41bc-ba17-dc822adf9c35
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a254d12-8285-41bc-ba17-dc822adf9c35
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1a254d12-8285-41bc-ba17-dc822adf9c35 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a254d12-8285-41bc-ba17-dc822adf9c35
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1a254d12-8285-41bc-ba17-dc822adf9c35 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a254d12-8285-41bc-ba17-dc822adf9c35
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a254d12-8285-41bc-ba17-dc822adf9c35
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 14fcd9a4fcd98082
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
UUID=1a254d12-8285-41bc-ba17-dc822adf9c35 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b5099451-41ba-4d60-b3d6-ad1b6851f485 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 782.7GB: boot/grub/core.img
 778.4GB: boot/grub/grub.cfg
 630.6GB: boot/initrd.img-2.6.35-22-generic
 782.7GB: boot/vmlinuz-2.6.35-22-generic
 630.6GB: initrd.img
 782.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  51 5e 27 c4 ef 3b e7 51  35 13 b4 4f 35 20 89 4a  |Q^'..;.Q5..O5 .J|
00000010  ea ab 60 91 6a af 98 26  e4 58 b9 cb a3 79 b2 ab  |..`.j..&.X...y..|
00000020  ea f8 ab 06 5a 08 ec 57  c7 ea 11 86 d5 b7 0f 7b  |....Z..W.......{|
00000030  fe 02 b0 0a 38 ab 13 84  de 69 4f 6c 90 26 26 fe  |....8....iOl.&&.|
00000040  f3 5d 17 44 d3 a2 b4 46  e0 dc 6e 85 9b 51 9b ee  |.].D...F..n..Q..|
00000050  e2 fe 40 f3 1d 6c 9a d6  a8 76 d4 1e 99 85 46 e4  |..@..l...v....F.|
00000060  cc c2 e7 fe b7 1c 66 66  63 59 da 51 a8 a0 69 2f  |......ffcY.Q..i/|
00000070  ae c7 57 d0 e2 07 12 7d  bb 63 aa dd d6 6d fb 33  |..W....}.c...m.3|
00000080  b4 76 36 99 59 d5 d0 e7  d6 87 62 b2 57 90 00 23  |.v6.Y.....b.W..#|
00000090  3e c3 52 96 30 76 f3 37  cc d3 f9 13 7d 84 4f 47  |>.R.0v.7....}.OG|
000000a0  1c f2 c9 00 00 0d 16 21  00 4c ba 94 47 e0 c0 18  |.......!.L..G...|
000000b0  ff 8d e3 52 6d b6 38 e3  83 e1 c4 da b8 69 1a 2b  |...Rm.8......i.+|
000000c0  3d 34 db cd fe 3a a9 d1  06 52 8b 83 b4 f9 b4 6b  |=4...:...R.....k|
000000d0  21 ea ba 61 c0 84 09 c1  47 7c 04 ed a3 48 29 9a  |!..a....G|...H).|
000000e0  4e 13 15 b0 e1 43 23 86  13 68 7b 4d 93 3c 09 a6  |N....C#..h{M.<..|
000000f0  e1 c7 d2 8b 30 dc 8b a8  07 75 ac 93 e6 20 8f 19  |....0....u... ..|
00000100  19 e2 74 c0 da 7c cb ad  59 94 4f 12 cb d0 be 6a  |..t..|..Y.O....j|
00000110  c0 da 3d 12 78 40 61 18  60 50 40 c3 22 d0 1f 3d  |..=.x@a.`P@."..=|
00000120  00 7d 9a cf a4 2f 34 09  c5 5d fa a4 2d a0 ee c6  |.}.../4..]..-...|
00000130  07 6e ed d8 46 14 45 78  cc 6b 16 dd ce 63 c7 6e  |.n..F.Ex.k...c.n|
00000140  ef 80 d7 d6 de 29 72 9c  4a ea 0d 63 28 b5 7e 3e  |.....)r.J..c(.~>|
00000150  c1 24 60 31 18 55 0a d6  72 b2 ee c4 04 d3 33 dd  |.$`1.U..r.....3.|
00000160  9b f0 37 bd 39 93 f6 cb  28 70 7e 48 f5 91 ab ae  |..7.9...(p~H....|
00000170  33 d9 6d 8c ac 65 48 dc  9e 4a 64 8e 8c bd b4 cb  |3.m..eH..Jd.....|
00000180  0d fc 5b 6d df 25 60 72  97 81 4c 09 83 18 40 bf  |..[m.%`r..L...@.|
00000190  4e 6b 52 b1 d7 d3 95 85  5c 72 93 61 f6 81 f6 b8  |NkR.....\r.a....|
000001a0  85 89 cb dd df 6f ee 9f  16 02 68 10 b9 dd f3 65  |.....o....h....e|
000001b0  ff 6f 33 8a fc 57 af 5c  0d 20 11 00 a3 7b 00 fe  |.o3..W.\. ...{..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 ad 29 00 fe  |...........0.)..|
000001d0  ff ff 05 fe ff ff 02 30  ad 29 00 e0 67 01 00 00  |.......0.)..g...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 

```

---

### Post by drs305 on 2011-03-15
Your system is most likely booting from the Windows drive (currently sda). Try changing the boot order in BIOS to boot from the current sdb drive first.

---

### Post by lowryb on 2011-03-15
That is strange, there is no OS installed on sdb, it is only supposed to be an NTFS storage disk, so I have no idea how a boot record made it there.

---

### Post by drs305 on 2011-03-15
> **lowryb said:**
> That is strange, there is no OS installed on sdb, it is only supposed to be an NTFS storage disk, so I have no idea how a boot record made it there.

Well, try changing the boot order. Once it boots to Ubuntu, run the following after confirming which drive has the OSs (the commands need to be changed to the appropriate drive):

```
sudo grub-install /dev/sd**X**
```
Then you should be able to change the BIOS boot order back to normal.

---

### Post by lowryb on 2011-03-15
Awesome, everything is running smoothly now, thank you for your assistance!

---

