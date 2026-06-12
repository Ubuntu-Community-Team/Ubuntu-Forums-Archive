---
title: "Boot options missing.. (Dual Boot)"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by shsaifee on 2011-02-02
Hi friends,
 
I installed ubuntu 10.10 desktop on my PC which was already running Windows XP.
 
I had some problems with the XP and hence was adviced to use the XP CD to rectify these errors. After I inserted the XP CD and booted from that and repaired the errors, and booted again, I could no longer see Ubuntu as an option in the boot options, but the PC directly boots to Windows XP.
 
Can anyone help me as I have had tough time configuring all the softwares in Ubuntu and do not want to go thru that cycle again...
 
Any help would be much appreciated.
 
Cheers

---

### Post by lindsay7 on 2011-02-02
[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by presence1960 on 2011-02-02
If you can't figure out what to do on that link we can give you precise commands to run from the Ubuntu Live Cd. Do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by shsaifee on 2011-02-03
Hi,
 
As desired, I downloaded the script and run it via the LiveCD.
 
Here is the contents of the file RESULTS.TXT
 
 
```
 
Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Windows is installed in the MBR of /dev/sda
=> Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM
sda2: _________________________________________________________________________
File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 
sda5: _________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda6: _________________________________________________________________________
File system: swap
Boot sector type: -
Boot sector info: 
sdb1: _________________________________________________________________________
File system: vfat
Boot sector type: Unknown
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /boot/grub/grub.cfg
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sda1 * 63 214,730,475 214,730,413 7 HPFS/NTFS
/dev/sda2 214,730,750 312,580,095 97,849,346 5 Extended
/dev/sda5 214,730,752 308,484,095 93,753,344 83 Linux
/dev/sda6 308,486,144 312,580,095 4,093,952 82 Linux swap / Solaris
&#12288;
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sdb1 * 63 4,030,463 4,030,401 c W95 FAT32 (LBA)
&#12288;
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/loop0 squashfs 
/dev/sda1 F4243CDB243CA312 ntfs 
/dev/sda2: PTTYPE="dos" 
/dev/sda5 50912e7f-3fe8-43bf-bec9-af9e4f430aa5 ext4 
/dev/sda6 6edd976e-0bed-4197-a622-387512273b5d swap 
/dev/sda: PTTYPE="dos" 
/dev/sdb1 0FF1-1015 vfat PENDRIVE 
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
aufs / aufs (rw)
/dev/sdb1 /cdrom vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sda1 /media/F4243CDB243CA312 fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
&#12288;
================================ sda1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
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
search --no-floppy --fs-uuid --set 50912e7f-3fe8-43bf-bec9-af9e4f430aa5
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
load_video
insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 50912e7f-3fe8-43bf-bec9-af9e4f430aa5
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 50912e7f-3fe8-43bf-bec9-af9e4f430aa5
linux /boot/vmlinuz-2.6.35-24-generic root=UUID=50912e7f-3fe8-43bf-bec9-af9e4f430aa5 ro quiet splash
initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 50912e7f-3fe8-43bf-bec9-af9e4f430aa5
echo 'Loading Linux 2.6.35-24-generic ...'
linux /boot/vmlinuz-2.6.35-24-generic root=UUID=50912e7f-3fe8-43bf-bec9-af9e4f430aa5 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 50912e7f-3fe8-43bf-bec9-af9e4f430aa5
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=50912e7f-3fe8-43bf-bec9-af9e4f430aa5 ro quiet splash
initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 50912e7f-3fe8-43bf-bec9-af9e4f430aa5
echo 'Loading Linux 2.6.35-22-generic ...'
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=50912e7f-3fe8-43bf-bec9-af9e4f430aa5 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 50912e7f-3fe8-43bf-bec9-af9e4f430aa5
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 50912e7f-3fe8-43bf-bec9-af9e4f430aa5
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f4243cdb243ca312
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
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
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=50912e7f-3fe8-43bf-bec9-af9e4f430aa5 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=6edd976e-0bed-4197-a622-387512273b5d none swap sw 0 0
=================== sda5: Location of files loaded by Grub: ===================
&#12288;
114.3GB: boot/grub/core.img
138.0GB: boot/grub/grub.cfg
117.0GB: boot/initrd.img-2.6.35-22-generic
120.4GB: boot/initrd.img-2.6.35-24-generic
110.7GB: boot/vmlinuz-2.6.35-22-generic
115.2GB: boot/vmlinuz-2.6.35-24-generic
120.4GB: initrd.img
117.0GB: initrd.img.old
115.2GB: vmlinuz
110.7GB: vmlinuz.old
=========================== sdb1/boot/grub/grub.cfg: ===========================
&#12288;
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
linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
initrd /casper/initrd.lz
}
menuentry "Install Ubuntu" {
set gfxpayload=keep
linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
initrd /casper/initrd.lz
}
menuentry "Check disc for defects" {
set gfxpayload=keep
linux /casper/vmlinuz boot=casper integrity-check quiet splash --
initrd /casper/initrd.lz
}
=================== sdb1: Location of files loaded by Grub: ===================
&#12288;
??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader on sda2
00000000 b7 c0 cb aa 1a c4 96 58 48 34 99 70 f7 da 6e 6e |.......XH4.p..nn|
00000010 37 62 53 0f 24 f9 c2 d5 6c cd 53 32 19 06 9e 08 |7bS.$...l.S2....|
00000020 2a bf 61 d4 73 72 ad 9b 72 c7 fb 62 f3 49 89 3e |*.a.sr..r..b.I.>|
00000030 17 60 80 0c 3d 54 4e e6 37 3e fb ef be fb ef be |.`..=TN.7>......|
00000040 fb ff df 7d f7 da f4 e0 e7 f5 b7 0e 86 50 f0 e7 |...}.........P..|
00000050 8c 3f d8 6a 1e 05 95 7f f1 99 0c 9c 67 77 ae 34 |.?.j........gw.4|
00000060 e1 ce ef 67 08 66 38 73 f9 96 08 00 2a 28 70 e7 |...g.f8s....*(p.|
00000070 77 88 f8 4a 32 54 77 8e 4c 84 d0 f0 e7 0c a1 9f |w..J2Tw.L.......|
00000080 1e 73 be 47 0c 82 95 ec 1e 2e 3b e6 bb 47 f8 b6 |.s.G......;..G..|
00000090 e3 70 dc ae 87 88 e1 a2 aa ff a8 91 20 1d dd 66 |.p.......... ..f|
000000a0 48 6d 40 f3 47 7b 3d 0d 2a 50 ef 5f 47 91 25 13 |Hm@.G{=.*P._G.%.|
000000b0 ea 54 7e 81 c1 1b 59 71 73 6b f0 fc ce 9f 66 52 |.T~...Yqsk....fR|
000000c0 d9 bc f4 9c 76 e6 f2 47 27 20 0a ed c4 d5 03 a9 |....v..G' ......|
000000d0 fe bd 39 7b 9b d0 63 5d 9f dc 9e 4d c3 1d a2 ab |..9{..c]...M....|
000000e0 b4 50 9c a7 be 3e 90 0e df cd 59 ca b9 76 cd b2 |.P...>....Y..v..|
000000f0 a6 3b 75 f7 7e 4e 96 bd 3f 25 74 b7 68 5d e1 e3 |.;u.~N..?%t.h]..|
00000100 9d df 7d f7 df 7d f7 df 7d ff ef be fb ef 1b ef |..}..}..}.......|
00000110 be fb ef be fb ef be a4 3f ad 3d ed 72 91 fb 49 |........?.=.r..I|
00000120 65 7a 90 fe 3e aa 3d 49 b9 cf 35 a7 0f b0 ce 1f |ez..>.=I..5.....|
00000130 51 05 fa 53 7e 52 e7 8d 14 2d ca 80 27 da e5 23 |Q..S~R...-..'..#|
00000140 74 7a 38 dd a6 9c a4 3f b5 ca b5 ca 4d d0 80 48 |tz8....?....M..H|
00000150 67 10 8d 1c f5 26 e4 14 68 c4 6e 7d f7 ff be f9 |g....&..h.n}....|
00000160 7f a8 cf 8a 46 b0 fc 3d 2b b8 f0 52 34 d5 dc 52 |....F..=+..R4..R|
00000170 73 af 74 3e 0a 5e f6 e5 78 64 e8 78 73 c8 7d d0 |s.t>.^..xd.xs.}.|
00000180 f0 2a fd f3 bd 16 7b 09 78 71 5f ae 38 14 bb a1 |.*....{.xq_.8...|
00000190 f8 78 ec b0 94 14 97 f6 e8 4e 6a 65 27 18 ea 11 |.x.......Nje'...|
000001a0 f8 f4 c2 59 af 19 78 4d 34 69 0f 38 67 b8 6b 0f |...Y..xM4i.8g.k.|
000001b0 43 d3 1e fa db 93 90 ee af fc 98 6a c1 f9 00 fe |C..........j....|
000001c0 ff ff 83 fe ff ff 02 00 00 00 00 90 96 05 00 fe |................|
000001d0 ff ff 05 fe ff ff 02 90 96 05 00 80 3e 00 00 00 |............>...|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200
Unknown BootLoader on sdb1
00000000 eb 58 90 53 59 53 4c 49 4e 55 58 00 02 08 20 00 |.X.SYSLINUX... .|
00000010 02 00 00 00 00 f8 00 00 3f 00 ff 00 3f 00 00 00 |........?...?...|
00000020 c1 7f 3d 00 59 0f 00 00 00 00 00 00 02 00 00 00 |..=.Y...........|
00000030 01 00 06 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00000040 80 00 29 15 10 f1 0f 4e 4f 20 4e 41 4d 45 20 20 |..)....NO NAME |
00000050 20 20 46 41 54 33 32 20 20 20 fa fc 31 c9 8e d1 | FAT32 ..1...|
00000060 bc 76 7b 52 06 57 8e c1 b1 26 bf 78 7b f3 a5 8e |.v{R.W...&.x{...|
00000070 d9 bb 78 00 0f b4 37 0f a0 56 20 d2 78 1b 31 c0 |..x...7..V .x.1.|
00000080 b1 06 89 3f 89 47 02 f3 64 a5 8a 0e 18 7c 88 4d |...?.G..d....|.M|
00000090 bc 50 50 50 50 cd 13 eb 4b f6 45 b4 7f 75 25 38 |.PPPP...K.E..u%8|
000000a0 4d b8 74 20 66 3d 21 47 50 54 75 10 80 7d b8 ed |M.t f=!GPTu..}..|
000000b0 75 0a 66 ff 75 ec 66 ff 75 e8 eb 0f 51 51 66 ff |u.f.u.f.u...QQf.|
000000c0 75 bc eb 07 51 51 66 ff 36 1c 7c b4 08 cd 13 72 |u...QQf.6.|....r|
000000d0 13 20 e4 75 0f c1 ea 08 42 89 16 1a 7c 83 e1 3f |. .u....B...|..?|
000000e0 89 0e 18 7c fb bb aa 55 b4 41 8a 16 74 7b cd 13 |...|...U.A..t{..|
000000f0 72 10 81 fb 55 aa 75 0a f6 c1 01 74 05 c6 06 32 |r...U.u....t...2|
00000100 7d 00 66 b8 da 1e 00 00 66 ba 00 00 00 00 bb 00 |}.f.....f.......|
00000110 7e e8 10 00 66 81 3e 24 7e 34 be f5 72 75 76 ea |~...f.>$~4..ruv.|
00000120 38 7e 00 00 66 03 06 64 7b 66 13 16 68 7b b9 10 |8~..f..d{f..h{..|
00000130 00 eb 2b 66 52 66 50 06 53 6a 01 6a 10 89 e6 66 |..+fRfP.Sj.j...f|
00000140 60 b4 42 e8 7f 00 66 61 8d 64 10 72 01 c3 66 60 |`.B...fa.d.r..f`|
00000150 31 c0 e8 70 00 66 61 e2 da c6 06 32 7d 2b 66 60 |1..p.fa....2}+f`|
00000160 66 0f b7 36 18 7c 66 0f b7 3e 1a 7c 66 f7 f6 31 |f..6.|f..>.|f..1|
00000170 c9 87 ca 66 f7 f7 66 3d ff 03 00 00 77 17 c0 e4 |...f..f=....w...|
00000180 06 41 08 e1 88 c5 88 d6 b8 01 02 e8 37 00 66 61 |.A..........7.fa|
00000190 72 01 c3 e2 c9 31 f6 8e d6 bc 6c 7b 8e de 66 8f |r....1....l{..f.|
000001a0 06 78 00 be cc 7d e8 09 00 31 c0 cd 16 cd 19 f4 |.x...}...1......|
000001b0 eb fd 66 60 ac 20 c0 74 09 b4 0e bb 07 00 cd 10 |..f`. .t........|
000001c0 eb f2 66 61 c3 8a 16 74 7b cd 13 c3 42 6f 6f 74 |..fa...t{...Boot|
000001d0 20 65 72 72 6f 72 0d 0a 00 00 00 00 00 00 00 00 | error..........|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200
&#12288;
&#12288;

```

---

### Post by lindsay7 on 2011-02-03
The way it looks to me is that you have grub installed to sdb  and it needs to be installed in sda, do what I suggested in my earlier post.

---

### Post by shsaifee on 2011-02-03
Hi,
 
If I follow that procedure, will my windows XP get affected in anyway?
 
I mean, will that restore the options as before like having choices to make between ubuntu and windows XP at boot time?
 
Please excuse me, if I sound like a novice. 
 
Best Regards.

---

### Post by kansasnoob on 2011-02-03
> **shsaifee said:**
> Hi,
 
If I follow that procedure, will my windows XP get affected in anyway?
 
I mean, will that restore the options as before like having choices to make between ubuntu and windows XP at boot time?
 
Please excuse me, if I sound like a novice. 
 
Best Regards.

You should be OK, just that your Ubuntu is on sda5 so you run:

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

```
sudo umount /mnt
```

Then after booting into Ubuntu:

```
sudo update-grub
```

---

### Post by shsaifee on 2011-02-03
SOLVED.
 
Thanks Gurus!!!

---

