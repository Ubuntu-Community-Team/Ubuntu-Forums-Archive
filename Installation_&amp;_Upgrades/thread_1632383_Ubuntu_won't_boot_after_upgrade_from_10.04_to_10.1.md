---
title: "Ubuntu won't boot after upgrade from 10.04 to 10.10"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by joshj70 on 2010-11-27
I have Ubuntu on my laptop and I updated it from 10.04 to 10.10 and now it wont boot at all, not even into recovery mode.

I updated yesterday and when I did I changed my update manager to update normal releases and to update unsupported updates and after i restarted it booted up and everything appeared fine except I noticed it was lagging really bad. I restarted it and then it it wouldn't open firefox, a terminal, or synaptics package manager, and after that it crashed and wont boot at all, but the grub menu is still working fine so i have no clue what happened.

I know that its very very hard for Linux to get viruses but I was wondering if one might have come through a backport after i set the update manager to get unsupported updates.

---

### Post by Rubi1200 on 2010-11-28
Hi and welcome to the forums :)

Please boot the computer with a LiveCD and choose to try Ubuntu.

Click on the link at the bottom of my post and run the boot info script (instructions included).

Post the results back here so we can help you troubleshoot the problem and offer solutions.

Thanks.

---

### Post by joshj70 on 2010-11-28
This was the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 50603264 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   617,623,551   617,621,504  83 Linux
/dev/sda2         617,625,598   625,141,759     7,516,162   5 Extended
/dev/sda5         617,625,600   625,141,759     7,516,160  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        61c79f31-a09b-4744-918b-8ac72558aece   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        06897cd4-e587-498d-99c1-18b2e03741f0   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8C1D-EEB5                              vfat       JOSH J                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 61c79f31-a09b-4744-918b-8ac72558aece
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 61c79f31-a09b-4744-918b-8ac72558aece
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 61c79f31-a09b-4744-918b-8ac72558aece
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=61c79f31-a09b-4744-918b-8ac72558aece ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 61c79f31-a09b-4744-918b-8ac72558aece
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=61c79f31-a09b-4744-918b-8ac72558aece ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 61c79f31-a09b-4744-918b-8ac72558aece
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=61c79f31-a09b-4744-918b-8ac72558aece ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 61c79f31-a09b-4744-918b-8ac72558aece
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=61c79f31-a09b-4744-918b-8ac72558aece ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 61c79f31-a09b-4744-918b-8ac72558aece
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 61c79f31-a09b-4744-918b-8ac72558aece
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=0fd0d683-956c-440b-98cf-cc88e6160085 /               ext4    errors=remount-ro 0       1
UUID=6369c5d1-d233-4ed3-aa2c-e1247a2019bb none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
  25.9GB: boot/grub/grub.cfg
  25.9GB: boot/initrd.img-2.6.32-21-generic
  27.9GB: boot/initrd.img-2.6.32-26-generic
  25.9GB: boot/vmlinuz-2.6.32-21-generic
  26.4GB: boot/vmlinuz-2.6.32-26-generic
  27.9GB: initrd.img
  26.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  85 ae 56 a4 10 c1 46 bf  a1 51 e5 56 98 8c 10 83  |..V...F..Q.V....|
00000010  13 05 32 49 b1 fa 72 1e  f3 ac e1 b0 ab 8f 84 b6  |..2I..r.........|
00000020  cf cc 8f 3c af 8f 03 61  99 5a 5f a8 51 e8 37 94  |...<...a.Z_.Q.7.|
00000030  68 a3 0d e2 46 87 30 3b  40 29 47 67 2b 52 45 b8  |h...F.0;@)Gg+RE.|
00000040  75 6d 63 32 af 56 8b b8  5f ab 93 86 52 9c 03 65  |umc2.V.._...R..e|
00000050  0b 84 8f 8f 68 7e 5f d5  0b 59 d2 98 f1 46 67 16  |....h~_..Y...Fg.|
00000060  83 62 01 31 73 71 b6 32  55 8c 1d d1 fc 8a c4 09  |.b.1sq.2U.......|
00000070  4f 94 b7 05 6f b3 68 a0  0c bf ab 9e 65 21 ed 29  |O...o.h.....e!.)|
00000080  17 22 e4 e0 7c ba 4d b9  ab 1e 14 d6 62 6e 73 92  |."..|.M.....bns.|
00000090  bd a3 e0 4a 84 66 21 ed  90 88 9c 93 d4 fa 99 03  |...J.f!.........|
000000a0  65 6a ac 81 70 cc 40 82  0c 29 09 d0 23 2f f9 c4  |ej..p.@..)..#/..|
000000b0  f9 85 21 9b ce 2c 5e 8a  61 d0 35 9e 3c 25 f9 5b  |..!..,^.a.5.<%.[|
000000c0  6d 7b 3d bc b2 ae 28 92  02 5a 60 43 24 b8 46 18  |m{=...(..Z`C$.F.|
000000d0  d2 ab 28 d4 0a 60 62 e0  6a c6 a4 7d f5 5c e6 5a  |..(..`b.j..}.\.Z|
000000e0  7a 79 4e ed 30 c0 ee 1c  95 b1 d9 8f 6b ad 3e 06  |zyN.0.......k.>.|
000000f0  c3 8f ef fc 8d eb 02 ac  be 07 50 2d 2f f9 aa ca  |..........P-/...|
00000100  ff 93 32 91 2f 03 c0 e9  19 38 b2 8a 6a 9d 1f c6  |..2./....8..j...|
00000110  cf 01 4e e4 ff 7e ae 29  0c c7 8c 99 06 50 5c 3d  |..N..~.).....P\=|
00000120  a3 c1 ea 9c 01 20 c3 ff  02 00 f1 67 7c b8 87 55  |..... .....g|..U|
00000130  aa f1 a0 36 1b 84 24 93  58 d8 cf 4e ae d8 85 fd  |...6..$.X..N....|
00000140  e8 e1 01 f1 18 80 d6 53  fe 15 4e 62 33 a1 0b 4a  |.......S..Nb3..J|
00000150  bb 83 6a 44 3a 06 e5 43  1c 06 d4 c1 21 b5 39 3e  |..jD:..C....!.9>|
00000160  70 dd 97 cd 28 26 34 9f  a7 3d 81 e4 e9 1c 8d 7a  |p...(&4..=.....z|
00000170  0d 86 e8 9e 31 fd b5 0a  c4 00 6d 95 f3 a1 bb 89  |....1.....m.....|
00000180  ff 54 e4 84 db eb 66 41  5d 58 2f 22 cf 1a b1 38  |.T....fA]X/"...8|
00000190  1b 18 aa c7 a4 e4 da 39  e4 78 43 4a 88 03 b9 38  |.......9.xCJ...8|
000001a0  f0 a6 9a a4 fa 8a a8 7b  14 36 c8 d2 28 e1 dc c8  |.......{.6..(...|
000001b0  98 f6 13 ca f0 36 50 43  d0 60 f3 e0 c2 70 00 fe  |.....6PC.`...p..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 72 00 00 00  |............r...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Rubi1200 on 2010-11-28
Whatever happened, it seems the upgrade did not work.
The script reports that you still have 10.04 installed.

The booting problem is likely caused by the fact that GRUB is installed to the partition rather than the MBR of the drive.

To rectify this, you need to use a LiveCD and run the following commands:
```
sudo mount /dev/sda1 /mnt

```
```
sudo grub-install --root-directory=/mnt/ /dev/sda

```
Run this after rebooting:
```
sudo update-grub
```

All of this should hopefully get you booting into Ubuntu again and then you can try upgrading again.

---

### Post by sikander3786 on 2010-11-28
Hope re-installation of Grub as advised by **Rubi** lets you boot into Ubuntu successfully and then we can focus on other problems ;-)


> but the grub menu is still working fine so i have no clue what happened.


Can you boot into Recovery mode and drop to the root shell? (if Grub re-installation doesn't work).

@Rubi: Wouldn't it be better to chroot, purge Grub and then re-install....?

---

### Post by joshj70 on 2010-11-28
I reinstalled grub and I am able to get back on my system but it's still really laggy but i can get into a terminal and stuff now.

---

### Post by Rubi1200 on 2010-11-29
I am glad you got things sorted out :)

The problem with being "laggy" may have other causes and I suggest you start a new thread to deal with that issue.

In any event, please mark this thread Solved using the Thread Tools near the top of the page if you think the problem has been resolved.

Thanks.

---

### Post by joshj70 on 2010-11-29
Ok.

Thank you for the help.

---

