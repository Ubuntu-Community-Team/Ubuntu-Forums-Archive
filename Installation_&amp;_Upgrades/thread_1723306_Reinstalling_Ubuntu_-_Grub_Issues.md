---
title: "Reinstalling Ubuntu - Grub Issues?"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by Fraktal on 2011-04-06
So my install of Ubuntu 10.10 recently went corrupt, but I was using Windows 7. The problem with reinstalling it is this: I use grub bootloader to boot into either OS, but it's on my portable hardrive. Windows 7 is on my main drive (my last install of windows went corrupt as well, so I had to format it). So my idea is to wipe the portable hardrive, but I don't know whether it'll cause problems with booting?

---

### Post by tommcd on 2011-04-06
When you reinstall Windows, the Windows boot loader takes control of the MBR. You can reinstall grub2 fro the Ubuntu live CD. See this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Since you have Ubuntu on an external hard drive, it might be preferable to reinstall grub2 to the MBR of the external hard drive. Then set that drive to be the first boot device in the computer's BIOS. Set the internal hard drive that has Windows to be the second boot device.
This way, if the external hard drive is not connected, you will be able boot Windows normally. When the external drive is connected, you will then get the grub2 menu which should aloow you to boot either Windows or Ubuntu.
Since when you reinstalled Windows, it likely installed the Windows boot loader to the MBR of the internal drive. So reformatting the external drive should not cause problems when booting Windows.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by Fraktal on 2011-04-07
Well I tried turning off the external harddrive and booting into windows, but instead it led me to a grub message stating that it could not find the device. I did make boot from harddrive first. Also, thanks!

---

### Post by garvinrick4 on 2011-04-07
Put in Ubuntu install cd and choose try ubuntu and open a terminal and download this
script to your DESKTOP and then run code in a terminal will put a text file on Desktop
that says Results.txt open it and copy and paste to this thread. Highlight whole thing
once pasted to your message box and Hit # sign in upper right corner of Message box.
and submit. Will give a lot of users capabilities of fixing your boot in a flash. Now download
and run code in terminal:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by Fraktal on 2011-04-07
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,386,484    20,386,422   7 HPFS/NTFS
/dev/sda2    *     20,386,485   625,140,399   604,753,915   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   307,093,503   307,091,456  83 Linux
/dev/sdb2         307,095,550   320,172,031    13,076,482   5 Extended
/dev/sdb5         307,095,552   320,172,031    13,076,480  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86126BF0126BE421                       ntfs       Recovery                      
/dev/sda2        5AE8FAF8E8FAD16D                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8872424d-ec05-4b22-a8c3-57aa6edea2bc   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        78c0b86b-a1ce-47d1-a67c-145f4caa257d   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="16"
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8872424d-ec05-4b22-a8c3-57aa6edea2bc ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8872424d-ec05-4b22-a8c3-57aa6edea2bc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ae8faf8e8fad16d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

/dev/sr0 /media/2007.11.03_2329 udf,iso9660 defaults 0 0
UUID=86126BF0126BE421 /media/Recovery ntfs-3g defaults 0 0
UUID=EAF6DFADF6DF77F1 /media/EAF6DFADF6DF77F1 ntfs-3g defaults 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  49.0GB: boot/grub/grub.cfg
  38.8GB: boot/initrd.img-2.6.32-21-generic
  40.8GB: boot/initrd.img-2.6.32-22-generic
  40.9GB: boot/initrd.img-2.6.32-24-generic
  40.9GB: boot/initrd.img-2.6.32-25-generic
  40.9GB: boot/initrd.img-2.6.32-26-generic
  40.8GB: boot/initrd.img-2.6.32-27-generic
  42.9GB: boot/initrd.img-2.6.32-28-generic
  38.7GB: boot/vmlinuz-2.6.32-21-generic
  40.8GB: boot/vmlinuz-2.6.32-22-generic
  40.8GB: boot/vmlinuz-2.6.32-24-generic
  40.8GB: boot/vmlinuz-2.6.32-25-generic
  40.9GB: boot/vmlinuz-2.6.32-26-generic
  39.2GB: boot/vmlinuz-2.6.32-27-generic
  39.2GB: boot/vmlinuz-2.6.32-28-generic
  42.9GB: initrd.img
  40.8GB: initrd.img.old
  39.2GB: vmlinuz
  39.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  1d 72 0e 55 1d 42 51 10  29 c1 0b fd f0 14 04 df  |.r.U.BQ.).......|
00000010  fd 68 03 24 82 17 f9 20  84 07 7e 8c 8a 24 8c 20  |.h.$... ..~..$. |
00000020  b5 11 0c c3 29 80 0d d0  02 74 80 ec 34 bf bf 0e  |....)....t..4...|
00000030  80 2f e5 b9 33 3f e1 f0  02 d0 dc 92 60 68 16 f8  |./..3?......`h..|
00000040  04 79 3f 67 27 af 40 05  60 17 06 84 f0 1f a9 51  |.y?g'.@.`......Q|
00000050  60 0c 4b 2c 34 98 84 00  0d 73 31 19 a0 0c 80 30  |`.K,4....s1....0|
00000060  60 28 1b d2 e0 10 b9 06  88 c8 1d 98 00 dc 04 f9  |`(..............|
00000070  01 a3 00 70 8c 64 01 72  72 00 35 21 fd fe c1 71  |...p.d.rr.5!...q|
00000080  0c 30 b7 e7 85 34 80 c2  61 27 a5 a0 04 e0 27 0c  |.0...4..a'....'.|
00000090  e0 20 4f 80 18 20 b0 03  f4 6a 22 82 d0 60 60 0d  |. O.. ...j"..``.|
000000a0  83 30 60 19 72 21 03 44  34 21 f0 19 2c 02 21 a4  |.0`.r!.D4!..,.!.|
000000b0  81 f2 09 a9 c4 30 13 24  97 80 21 71 10 03 40 0b  |.....0.$..!q..@.|
000000c0  d2 01 59 64 00 3a 3a 00  66 4c e0 60 37 27 71 6f  |..Yd.::.fL.`7'qo|
000000d0  b3 1d 02 00 18 00 ec bc  03 b2 17 0c 2c ae 03 d4  |............,...|
000000e0  16 5b bb e3 28 8c 38 20  30 84 19 c0 0c c0 76 57  |.[..(.8 0.....vW|
000000f0  28 28 7c 01 80 08 32 00  14 14 1a 4d e4 fe 37 6d  |((|...2....M..7m|
00000100  00 c4 98 08 40 14 df 90  20 05 a0 30 18 02 02 52  |....@... ..0...R|
00000110  4a 0e 57 e9 6c 16 f0 08  40 77 c0 c2 00 c1 3c 96  |J.W.l...@w....<.|
00000120  30 0d c0 0c 80 30 0c 00  12 ec 03 b2 8a 01 12 43  |0....0.........C|
00000130  09 79 f0 8b 0b 81 a1 80  50 b0 42 01 34 00 eb 38  |.y......P.B.4..8|
00000140  04 09 d0 15 21 a7 00 ec  94 c5 20 70 42 4a ce 47  |....!..... pBJ.G|
00000150  c6 c8 e8 00 a8 04 04 c2  40 b7 c8 00 17 2e 00 60  |........@......`|
00000160  01 7f e0 18 80 ec b4 a4  46 02 e5 96 94 8c d0 02  |........F.......|
00000170  77 60 d2 6b 13 bb 9b 02  00 14 80 ec 10 bf e8 98  |w`.k............|
00000180  4c 41 1d 54 7f 90 be f7  40 1e db 0f 01 1b 7d 37  |LA.T....@.....}7|
00000190  de df be d9 08 6d cc f9  b7 eb a0 5b 76 fe 1f 3d  |.....m.....[v..=|
000001a0  88 bd 9e 19 5c 81 fb 60  77 e8 b2 e8 c6 fc 2c 46  |....\..`w.....,F|
000001b0  00 1e 75 96 c8 15 24 b4  94 df d0 fe fa 01 00 fe  |..u...$.........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 c7 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by wilee-nilee on 2011-04-07
You need the MS bootloader in the mbr of sda so with the external unplugged follow these instructions, and notice the windows 7 forums link for a visual and the recovery disc down load if needed.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following command:
**BootRec.exe /fixmbr** 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Your windows should boot now without the external plugged in. Now plug in the external boot Ubuntu from it and in the terminal run.
```
sudo update-grub
```

You can now boot Ubuntu from that hd and windows from the internal or the external.

This is the same info that tommcd gave you if you don't understand let us know.;)

---

### Post by Quackers on 2011-04-07
For the second part of wilee-nilee's instructions you will need to set the boot order in the bios so that the external drive boots before the internal drive.

---

### Post by garvinrick4 on 2011-04-08
Fraktal, let the users helping you know if there suggestions to you worked and or the results.
If in fact you are up and running go to thread tools in upper left of your thread and mark as
solved.

---

### Post by Fraktal on 2011-04-08
[COLOR=Red]Success![/COLOR] Thank you guys, especially wilee-nilee for giving such precise instructions.

---

