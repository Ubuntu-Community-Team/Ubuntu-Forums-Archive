---
title: "Ubuntu 10.10 Boot loader Issue"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by seanrich on 2010-10-14
I posted in another thread, but I thought I'd make my own after the suggestion from some of the other posters.

I do a fresh install of Ubuntu 10.10 from CD and USB. I've tried both, but no matter the installation media I get an error and the grub rescue prompt shows up.

It looks like: 

error: no such partition
grub rescue>

When I run ls it only shows (hd0) and (hd0, msdos1) no other partitions.

I've attached my Results.txt from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) so that someone may hopefully debug the problem.

---

### Post by jacob.david on 2010-10-14
Can you provide more details about what you are trying to do exactly with number of hard disks you have and partition information etc. It looks like you already have windows and trying to install Ubuntu with dual boot.

---

### Post by oldfred on 2010-10-14
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

You have already posted the results.txt (although having it in codes tags makes it easier for us to read it). The install looks normal to me.

drs305 suggests reinstalling grub. I would just do the simple reinstall first and then if that does not work follow the full chroot reinstall that often works when the first short version does not.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

If this does not work then try the full chroot as discussed in the Megathread.

---

### Post by seanrich on 2010-10-15
> **jacob.david said:**
> Can you provide more details about what you are trying to do exactly with number of hard disks you have and partition information etc. It looks like you already have windows and trying to install Ubuntu with dual boot.

Yes, I'm trying to dual boot with Vista.

---

### Post by seanrich on 2010-10-15
> **oldfred said:**
> Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

You have already posted the results.txt (although having it in codes tags makes it easier for us to read it). The install looks normal to me.

drs305 suggests reinstalling grub. I would just do the simple reinstall first and then if that does not work follow the full chroot reinstall that often works when the first short version does not.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

If this does not work then try the full chroot as discussed in the Megathread.

I've done both the reinstall and the chroot reinstall and I still get no love from grub. Grub installs just fine, but when I reboot I get the error message I mentioned above.

---

### Post by wilee-nilee on 2010-10-15
Lets get the script posted it is easier to read. I'm sure it might be important to at least identify if this script was run after the last grub install tries.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   563,343,454   563,341,407   7 HPFS/NTFS
/dev/sda2         563,345,406   976,773,119   413,427,714   5 Extended
/dev/sda5         563,345,408   964,737,023   401,391,616  83 Linux
/dev/sda6         964,739,072   976,773,119    12,034,048  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8002 MB, 8002732032 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,628,409    15,628,347   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E8B86403B863CE9E                       ntfs       Despierto                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        58874ff8-7375-498e-b17f-9ea177ad0ef2   ext4                                     
/dev/sda6        2f123ccb-a77a-4861-95cd-1aea9bb1ee36   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7AF3-51FB                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt                     vfat       (rw)


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
search --no-floppy --fs-uuid --set 58874ff8-7375-498e-b17f-9ea177ad0ef2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 58874ff8-7375-498e-b17f-9ea177ad0ef2
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
    search --no-floppy --fs-uuid --set 58874ff8-7375-498e-b17f-9ea177ad0ef2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=58874ff8-7375-498e-b17f-9ea177ad0ef2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 58874ff8-7375-498e-b17f-9ea177ad0ef2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=58874ff8-7375-498e-b17f-9ea177ad0ef2 ro single 
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
    search --no-floppy --fs-uuid --set 58874ff8-7375-498e-b17f-9ea177ad0ef2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 58874ff8-7375-498e-b17f-9ea177ad0ef2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e8b86403b863ce9e
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
UUID=58874ff8-7375-498e-b17f-9ea177ad0ef2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2f123ccb-a77a-4861-95cd-1aea9bb1ee36 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 417.4GB: boot/grub/core.img
 327.2GB: boot/grub/grub.cfg
 327.6GB: boot/initrd.img-2.6.35-22-generic
 288.7GB: boot/vmlinuz-2.6.35-22-generic
 327.6GB: initrd.img
 288.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  50 8b cf e8 93 23 ff ff  83 c6 0c eb bc 83 c6 08  |P....#..........|
00000010  56 8b cf e8 06 f5 ff ff  eb 40 83 c6 08 56 8b cf  |V........@...V..|
00000020  e8 40 f5 ff ff eb 33 8d  45 d8 50 8b cf e8 69 23  |.@....3.E.P...i#|
00000030  ff ff 39 5d d8 76 2b ff  75 d8 53 ff 15 f0 04 48  |..9].v+.u.S....H|
00000040  00 89 46 08 3b c3 75 05  e8 52 81 fe ff ff 75 d8  |..F.;.u..R....u.|
00000050  8b cf 50 e8 3f db fe ff  8b c7 e8 3d 45 02 00 c2  |..P.?......=E...|
00000060  08 00 89 5e 08 eb f1 57  8d 4d c8 89 5d d4 e8 41  |...^...W.M..]..A|
00000070  8f 01 00 8d 45 dc 50 8b  cf e8 1d 23 ff ff 8d 45  |....E.P....#...E|
00000080  e0 50 8b cf e8 ca 22 ff  ff 8d 45 e2 50 8b cf e8  |.P...."...E.P...|
00000090  bf 22 ff ff 6a 08 8d 45  e4 50 8b cf e8 f6 da fe  |."..j..E.P......|
000000a0  ff 66 83 3e 0d b8 44 d8  48 00 74 05 b8 54 cb 48  |.f.>..D.H.t..T.H|
000000b0  00 8d 7e 08 57 50 6a 17  53 8b 1d 68 08 48 00 8d  |..~.WPj.S..h.H..|
000000c0  45 dc 50 ff d3 3d 57 00  07 80 75 1c 66 83 3e 0d  |E.P..=W...u.f.>.|
000000d0  b8 44 d8 48 00 74 05 b8  54 cb 48 00 57 50 6a 07  |.D.H.t..T.H.WPj.|
000000e0  6a 00 8d 45 dc 50 ff d3  50 e8 8a dc ff ff 8b 07  |j..E.P..P.......|
000000f0  8b 08 83 65 fc 00 8d 55  d4 52 68 64 d9 48 00 50  |...e...U.Rhd.H.P|
00000100  ff 11 85 c0 7d 10 8b 3f  8b 07 8d 4d d4 51 68 14  |....}..?...M.Qh.|
00000110  df 48 00 57 ff 10 50 e8  5c dc ff ff 8b 45 d4 8b  |.H.W..P.\....E..|
00000120  08 8d 55 c8 52 50 ff 51  14 50 e8 49 dc ff ff 8b  |..U.RP.Q.P.I....|
00000130  45 d4 8b 08 83 4d fc ff  50 ff 51 08 8b 45 d8 e9  |E....M..P.Q..E..|
00000140  16 ff ff ff 8b 45 d4 85  c0 74 06 8b 08 50 ff 51  |.....E...t...P.Q|
00000150  08 8b 45 d0 8b 40 08 8b  08 50 ff 51 08 6a 00 6a  |..E..@...P.Q.j.j|
00000160  00 e8 d1 48 02 00 90 58  b8 42 00 58 b8 42 00 a6  |...H...X.B.X.B..|
00000170  b7 42 00 c6 b7 42 00 0d  b8 42 00 1a b8 42 00 fd  |.B...B...B...B..|
00000180  b7 42 00 1a b8 42 00 27  b8 42 00 67 b8 42 00 c6  |.B...B.'.B.g.B..|
00000190  b7 42 00 a6 b7 42 00 58  b8 42 00 67 b8 42 00 58  |.B...B.X.B.g.B.X|
000001a0  b8 42 00 58 b8 42 00 b6  b7 42 00 b6 b7 42 00 a6  |.B.X.B...B...B..|
000001b0  b7 42 00 d6 b7 42 00 e3  b7 42 00 f0 b7 42 00 fe  |.B...B...B...B..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 ec 17 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c0  ec 17 00 a8 b7 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 02 09  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  3b 78 ee 00 7f 3b 00 00  00 00 00 00 02 00 00 00  |;x...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 fb 51 f3 7a 4e  4f 20 4e 41 4d 45 20 20  |..).Q.zNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 f8 27 16 00  66 ba 00 00 00 00 bb 00  |}.f..'..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by seanrich on 2010-10-15
No, this was after a fresh install.

---

### Post by oldfred on 2010-10-15
Grub rescue is supposed to allow you to manually boot if you know partition.

Instructions in link above.

set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

---

