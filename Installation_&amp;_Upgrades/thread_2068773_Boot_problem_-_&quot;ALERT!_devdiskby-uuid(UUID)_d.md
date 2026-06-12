---
title: "Boot problem - &quot;ALERT! /dev/disk/by-uuid/(UUID) does not exist&quot;, (initramfs)"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by ca_20gti on 2012-10-09
Hi everyone...

Sorry you have to see another initramfs issue but I have one which I have been working on for a week and tried several things that helped others including the

"If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."

I did have ubuntu 12.04 installed (upgraded from 10.04) and was having some issues so I reinstalled clean and since then I have been pulling my hair out trying to find the issue.

It will hang on the purple screen.. however if I turn off the "splash" option in grub it will show the problem. It will drop to (initramfs) but I can hit ctrl-D and it will finally boot up. I can also hit Ctrl-D when the purple screen is up .. I just need to wait a few minutes after bios post.



This install was done by the live CD..

Seems everything is fine until.....

[ 6.464023] ata1: link is slow to respond, please be patient (ready=0)
[ 11.000021] ata1: SRST failed (errno=-16)
[ 16.508021] ata1: link is slow to respond, please be patient (ready=0)
[ 21.044021] ata1: SRST failed (errno=-16)
[ 26.552021] ata1: link is slow to respond, please be patient (ready=0)
[ 51.024038] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 51.878306] ata1.00: ATA-8: WDC WD10EACS-00ZJB0, 01.01B01, max UDMA/133
[ 51.878310] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[ 51.893022] ata1.00: configured for UDMA/133
[ 51.893194] scsi 0:0:0:0: Direct-Access ATA WDC WD10EACS-00Z 01.0 PQ
: 0 ANSI: 5


Gave up waiting for root device. Common problems:
ALERT! /dev/disk/by-uuid/bunch of stuff does not exist. Dropping to a shell!
BusyBox v1.13.3 ...
(initramfs)




Thank you for your help.


Output of the boot script
```

Boot Info Script 0.61 [1 April 2012]


============================= Boot Info Summary: ===============================

=> No boot loader is installed in the MBR of /dev/sda.
=> No boot loader is installed in the MBR of /dev/sdb.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for (,msdos1)/boot/grub on this drive.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and uses an
embedded config file:

---------------------------------------------------------------------------
search.fs_uuid c3ca07d4-cab3-4a23-bd7b-cf15fe0120b7 root
set prefix=($root)/boot/grub
---------------------------------------------------------------------------
-----.

sda1: __________________________________________________________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files:

sdb1: __________________________________________________________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files:

sdc1: __________________________________________________________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 12.04.1 LTS
Boot files: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sdc5: __________________________________________________________________________

File system: swap
Boot sector type: -
Boot sector info:

sdd1: __________________________________________________________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files:

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 2,048 1,953,523,711 1,953,521,664 83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdb1 63 1,465,144,064 1,465,144,002 83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 146.8 GB, 146815737856 bytes
255 heads, 63 sectors/track, 17849 cylinders, total 286749488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdc1 * 2,048 269,973,503 269,971,456 83 Linux
/dev/sdc2 269,975,550 286,748,671 16,773,122 5 Extended
/dev/sdc5 269,975,552 286,748,671 16,773,120 82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 300.0 GB, 300000000000 bytes
255 heads, 63 sectors/track, 36472 cylinders, total 585937500 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdd1 63 585,922,679 585,922,617 83 Linux


"blkid" output: ________________________________________________________________

Device UUID TYPE LABEL

/dev/sda1 fbd8fae6-18de-42e3-b11e-67ed091000a4 ext4 Minerva
/dev/sdb1 6c0255e2-2f97-4b6b-a723-94c1f6f75ab2 ext4 Drive-Y
/dev/sdc1 106e677b-ef40-42f5-b967-69035452de38 ext4
/dev/sdc5 6fd2047b-1b1a-4f26-ac8b-a0edc5d3209a swap
/dev/sdd1 df3ee783-0191-4afb-a708-8ae4c1c206f2 ext4 Drive6

================================ Mount points: =================================

Device Mount_Point Type Options

/dev/sdc1 / ext4 (rw,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 106e677b-ef40-42f5-b967-69035452de38
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 106e677b-ef40-42f5-b967-69035452de38
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
menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 106e677b-ef40-42f5-b967-69035452de38
linux /boot/vmlinuz-3.2.0-31-generic root=UUID=106e677b-ef40-42f5-b967-69035452de38 ro quiet splash $vt_handoff
initrd /boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 106e677b-ef40-42f5-b967-69035452de38
echo 'Loading Linux 3.2.0-31-generic ...'
linux /boot/vmlinuz-3.2.0-31-generic root=UUID=106e677b-ef40-42f5-b967-69035452de38 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.2.0-31-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 106e677b-ef40-42f5-b967-69035452de38
linux /boot/vmlinuz-3.2.0-29-generic root=UUID=106e677b-ef40-42f5-b967-69035452de38 ro quiet splash $vt_handoff
initrd /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 106e677b-ef40-42f5-b967-69035452de38
echo 'Loading Linux 3.2.0-29-generic ...'
linux /boot/vmlinuz-3.2.0-29-generic root=UUID=106e677b-ef40-42f5-b967-69035452de38 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 106e677b-ef40-42f5-b967-69035452de38
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 106e677b-ef40-42f5-b967-69035452de38
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdc1 during installation
UUID=106e677b-ef40-42f5-b967-69035452de38 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdc5 during installation
UUID=74eb35d5-fc76-4275-95b1-f7e8dbabfc9c none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

GiB - GB File Fragment(s)

36.233379364 = 38.905294848 boot/grub/core.img 1
36.233386993 = 38.905303040 boot/grub/grub.cfg 1
27.761825562 = 29.809033216 boot/initrd.img-3.2.0-29-generic 2
1.011283875 = 1.085857792 boot/initrd.img-3.2.0-31-generic 2
36.188037872 = 38.856609792 boot/vmlinuz-3.2.0-29-generic 1
0.743881226 = 0.798736384 boot/vmlinuz-3.2.0-31-generic 1
1.011283875 = 1.085857792 initrd.img 2
27.761825562 = 29.809033216 initrd.img.old 2
0.743881226 = 0.798736384 vmlinuz 1
36.188037872 = 38.856609792 vmlinuz.old 1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000 ca b4 89 09 08 0e 91 26 4b 48 51 23 5c 08 c7 21 |.......&KHQ#\..!|
00000010 23 12 21 82 25 33 01 57 c2 14 40 0c 70 d3 2a ad |#.!.%3.W..@.p.*.|
00000020 4c 39 2b 92 37 48 94 9e 3e 70 d3 26 19 1b d2 75 |L9+.7H..>p.&...u|
00000030 53 e5 01 7c 03 de 2e 9a 1a 42 6c 12 04 b8 09 42 |S..|.....Bl....B|
00000040 6b 55 89 8e 82 68 0e ea 2a 79 c3 6a 10 34 07 7b |kU...h..*y.j.4.{|
00000050 51 a2 1c 7f d6 12 6b f5 20 02 f8 d3 53 dd 9c 2a |Q.....k. ...S..*|
00000060 e5 e0 1a 2a b7 1a 7b 8f e5 25 25 55 ce 29 55 c9 |...*..{..%%U.)U.|
00000070 4c ac be d2 d5 2d 44 c1 7a 46 9e 49 99 d9 22 b3 |L....-D.zF.I..".|
00000080 71 47 21 21 44 89 8d 52 25 cc 00 dd 68 24 12 87 |qG!!D..R%...h$..|
00000090 25 94 c4 6b 52 5a 23 73 5c 1b 23 d4 05 e9 0c cd |%..kRZ#s\.#.....|
000000a0 a0 7d d2 5c 61 aa 01 20 91 74 50 cc f6 65 30 3d |.}.\a.. .tP..e0=|
000000b0 b3 41 ba 08 05 c7 10 68 00 31 b5 de 0c 34 d5 a2 |.A.....h.1...4..|
000000c0 e9 ea cd a9 d2 16 52 35 39 a4 71 d5 4d b2 76 5e |......R59.q.M.v^|
000000d0 df 6b 31 bb 86 b4 5e b8 d3 89 a6 1e 46 3d 7a e4 |.k1...^.....F=z.|
000000e0 f9 eb b4 9b 45 a7 06 03 6f 02 e2 a0 24 f1 53 82 |....E...o...$.S.|
000000f0 47 37 b3 94 77 fa 4e 1e 4d 0e a6 19 c8 89 7c 23 |G7..w.N.M.....|#|
00000100 ce 49 f4 3d 77 62 0b 88 84 a2 e0 87 18 ba e1 99 |.I.=wb..........|
00000110 df 32 75 9b 73 00 09 89 a7 8c e2 ec e0 ca ab 03 |.2u.s...........|
00000120 2e db 47 38 4d 7e c9 e1 05 5c 93 6a a2 42 c1 a0 |..G8M~...\.j.B..|
00000130 3a 4a 80 8f e7 13 25 d7 5f 50 3b d6 8b df 54 c4 |:J....%._P;...T.|
00000140 75 5f b2 36 a5 a0 c7 66 a9 1d fa 7b 7e 92 2e a5 |u_.6...f...{~...|
00000150 59 10 72 81 df ee 2a ba b0 04 ee c7 8d 03 4a 1e |Y.r...*.......J.|
00000160 e0 2a 86 35 e5 18 5a 27 04 af b6 05 bd 41 41 26 |.*.5..Z'.....AA&|
00000170 66 b1 2a c6 8e 8b 91 6d da 24 92 4a 8c 33 43 05 |f.*....m.$.J.3C.|
00000180 ae 4d 75 f5 62 3e cd c6 28 68 50 15 5d 48 15 e4 |.Mu.b>..(hP.]H..|
00000190 56 d7 03 ec 59 73 88 53 3d 22 42 7e 30 af 71 53 |V...Ys.S="B~0.qS|
000001a0 56 24 13 91 69 f5 c0 0a 9a 67 e2 30 94 6f a5 fd |V$..i....g.0.o..|
000001b0 a7 27 b3 5f b8 15 a0 ab 8e 94 79 fc a2 52 00 fe |.'._......y..R..|
000001c0 ff ff 82 fe ff ff 02 00 00 00 00 f0 ff 00 00 00 |................|
000001d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt


```

---

### Post by oldfred on 2012-10-10
In BIOS are you booting from sdc or sdd? sdc should work better. Some have had issues with grub on different drives. 

I do now boot 12.10 on sdd4 from sda's MBR so that is not always a problem. And sda is MBR and sdd is gpt. 
With 10.04 I had issues chain booting XP in MBR drive (sda) from a gpt drive (sdb). But that long since has been fixed in grub.

---

### Post by ca_20gti on 2012-10-10
I boot from sdc in the bios, I have also rearranged the drives used other drives for the boot disc and all render the same result.

I forgot to mention but I tried the Ubuntu boot-repair and it still didn't work. I did find out last night..  If I unplug 1 of the 2 sata drives (only because i forgot to plug one in),  it will boot fine. So I tried this with both sata drives and it booted.. but as soon as I plug in which ever is disconnected it goes right back to initramfs prompt

So I am really not sure what's going on now...

---

### Post by darkod on 2012-10-10
Please edit the first post and put the bootinfo results in CODE tags. Much better for reading.

And what happens if you boot without the 1TB disk because that is the disk mentioned in those boot errors.

---

### Post by ca_20gti on 2012-10-10
Ok Done :)


It will boot fine.. Could the drive be bad and causing this issue?

---

### Post by darkod on 2012-10-10
The messages you posted sound like that. Out of four, there is only one disk mentioned in those messages, that's for a reason. And the message saying it's slow and might take more time.

That enough for the timeout to locate the root partition to end, and the message gave up waiting for root is consequence of that.

You can do disk checks with smartmontools, you will have to google or look at the man page for detailed options. That is a linux tool for readin the SMART data of disks.

PS. Try different sata data and power cable, it might not be the disk itself. Swap the cables with another disk and watch if again the WD model is specified in the error messages. Try a few test boots. If the WD is always in the error messages, including with new cables, it points towards disk with problems.

---

### Post by ca_20gti on 2012-10-10
I will try that when I get home!

thx

---

### Post by ca_20gti on 2012-10-10
Looks like it was indeed a bad HD making it hang. I replaced the drive with another 1TB I have and it is working great.

Thank you for your suggestions.

---

