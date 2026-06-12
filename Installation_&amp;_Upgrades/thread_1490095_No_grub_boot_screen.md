---
title: "No grub boot screen"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by tedderst on 2010-05-21
I just installed Ubuntu on the second partition of my hard drive. I have Windows 7 installed on the first partition. My problem is is that when i rebooted after a successful OS installation and apparent grub install, it went straight to boot up Windows 7. There's probably a simple way to get the grub menu to appear that I'm unaware of, right?

---

### Post by lilsavalex on 2010-05-21
Thats exactly what always happens to me -_-

---

### Post by darkod on 2010-05-21
You missed important piece of information: do you have another hdd? Very often with multiple disks you think the bootloader (grub) went to one disk, but in fact it ended up on another.

Or, simply run the boot info script as per these instructions and post the content of the results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by tedderst on 2010-05-21
Here it is... wow I had to google how to do this. Also, I have no idea what sda3 is. I have 2 hdds. One with 3 parttions: windows 7, ubuntu and a swap partition. The other with 2 partitions for backup and media stuff.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
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

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   645,947,391   645,945,344   7 HPFS/NTFS
/dev/sda2         645,947,392 1,140,168,357   494,220,966   7 HPFS/NTFS
/dev/sda3       1,140,168,702 1,465,147,391   324,978,690   5 Extended
/dev/sda5       1,140,168,704 1,451,876,351   311,707,648  83 Linux
/dev/sda6       1,451,878,400 1,465,147,391    13,268,992  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sdb2         209,717,248 1,465,143,295 1,255,426,048   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        74D4E9E2D4E9A718                       ntfs                                     
/dev/sda2        82542BC3542BB8B5                       ntfs       Games                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65   ext4                                     
/dev/sda6        89f0d881-e734-4fb5-8a78-960f915b7deb   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FE587F62587F189B                       ntfs       Backup                        
/dev/sdb2        5CB88EB5B88E8CE8                       ntfs       Media                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65
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
search --no-floppy --fs-uuid --set 1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65
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
UUID=1ec4de2f-be4e-4aa9-a7d4-bf1d04716e65 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=89f0d881-e734-4fb5-8a78-960f915b7deb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 697.7GB: boot/grub/core.img
 686.9GB: boot/grub/grub.cfg
 697.7GB: boot/initrd.img-2.6.32-21-generic
 697.7GB: boot/vmlinuz-2.6.32-21-generic
 697.7GB: initrd.img
 697.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  7f 55 ab ba ae b2 2b 1c  63 1e 61 91 f9 a1 f9 a1  |.U....+.c.a.....|
00000010  f9 a0 2a e1 c0 6b 82 20  19 ca 3f d0 51 46 a2 b1  |..*..k. ..?.QF..|
00000020  ed 23 54 ba e7 ee 4e 9e  9b fa a3 a4 ad 88 3d 70  |.#T...N.......=p|
00000030  c9 86 60 1e 10 20 1d 70  20 80 60 1b 49 d2 0f b8  |..`.. .p .`.I...|
00000040  0a 72 09 68 72 00 68 20  ff 04 9b 8d 17 16 80 5f  |.r.hr.h ......._|
00000050  99 2f 4b 2d 17 fe 67 ec  fd 6b aa e8 12 eb bd de  |./K-..g..k......|
00000060  e5 df 36 8e 98 e0 8c 47  8d fe ac e0 53 67 73 35  |..6....G....Sgs5|
00000070  87 ee 6e 01 97 89 65 e3  bb ef c6 40 26 73 80 57  |..n...e....@&s.W|
00000080  ef 2f 55 5a 96 6f 2e a6  32 48 14 df cc c6 f9 23  |./UZ.o..2H.....#|
00000090  be df bf d3 01 0c 7f ef  31 5e 0c f3 31 c0 53 40  |........1^..1.S@|
000000a0  b3 82 f8 c9 2e 55 7f f1  ea ab 31 ab e4 aa 9b 1a  |.....U....1.....|
000000b0  e3 38 9b f4 61 55 d0 35  78 3a 2e 12 7e 68 20 09  |.8..aU.5x:..~h .|
000000c0  1b 41 47 59 e7 a9 0e 1c  64 f8 96 33 de 78 28 82  |.AGY....d..3.x(.|
000000d0  f1 e8 1a f9 13 d4 b4 f7  b8 0a 69 47 07 2a 41 e0  |..........iG.*A.|
000000e0  3f a1 06 1f aa b7 53 aa  06 2a fb c2 1f db 55 35  |?.....S..*....U5|
000000f0  a7 89 40 f0 10 21 dd 00  f2 ff 7b 3b 07 f2 9d 00  |..@..!....{;....|
00000100  d5 76 a9 11 39 ac 43 eb  1f ff 14 e1 18 21 d9 29  |.v..9.C......!.)|
00000110  b7 cb ee 43 e3 cc d6 fe  8e 99 bf 65 3e 9d 1e 61  |...C.......e>..a|
00000120  64 44 78 e0 cd 9e 08 b9  8d ef 75 77 17 45 81 93  |dDx.......uw.E..|
00000130  0c 21 7e 0f 51 91 09 42  28 30 d4 f0 14 d8 90 4b  |.!~.Q..B(0.....K|
00000140  04 57 79 fb d9 f0 2f 06  03 f9 76 d2 35 5e 29 77  |.Wy.../...v.5^)w|
00000150  ed 06 1d d8 9a 3f 86 c9  06 63 01 77 fe e3 c3 ff  |.....?...c.w....|
00000160  9a 7b 97 14 c4 ff a6 1f  6f 14 3a 5d ec 67 1f 7d  |.{......o.:].g.}|
00000170  ec ec cf a1 37 09 aa f4  5c 4f 93 43 57 2d 7d 5d  |....7...\O.CW-}]|
00000180  e2 f3 a8 92 82 11 d7 7e  8d 86 e9 86 00 85 4d b6  |.......~......M.|
00000190  93 a4 35 43 ae 06 f1 83  6f 45 6b 2a df c4 ae 80  |..5C....oEk*....|
000001a0  9c c8 df 98 9f 45 c4 6c  dd 3f d0 9d ed 22 46 f5  |.....E.l.?..."F.|
000001b0  79 84 89 bc 33 0c e9 f1  d8 5e 99 61 9b e8 00 fe  |y...3....^.a....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 94 12 00 fe  |...........H....|
000001d0  ff ff 05 fe ff ff 02 48  94 12 00 80 ca 00 00 00  |.......H........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by oldfred on 2010-05-22
You must be booting from sdb as it has windows in the MBR and grub is in sda. Switch boot drives in BIOS and you should boot grub.

You also have a windows boot partition in sdb1, but your windows install in sda1. Usually they are on the same drive. If it works I would not change but you rely on both drives working to boot. If one ever stops working you cannot boot the other.

ONce in Ubuntu run this and it should find the windows boot:
sudo update-grub

---

### Post by darkod on 2010-05-22
> **oldfred said:**
> You must be booting from sdb as it has windows in the MBR and grub is in sda. Switch boot drives in BIOS and you should boot grub.

You also have a windows boot partition in sdb1, but your windows install in sda1. Usually they are on the same drive. If it works I would not change but you rely on both drives working to boot. If one ever stops working you cannot boot the other.

ONce in Ubuntu run this and it should find the windows boot:
sudo update-grub

+1

I agreee. Somehow your win7 boot files went to /dev/sdb1 but for now you might leave things as they are. It's also a bit strange that during the install ubuntu didn't see win7 at all, it's not in grub.cfg. Hopefully update-grub will work but it may not if win7 didn't get detected earlier too.

Unless you had /dev/sdb unplugged when installing ubuntu.

Do as oldfred said, make sure you are booting from /dev/sda disk in BIOS (they are both 750GB but figure out which is which), and once you have booted ubuntu run:

sudo update-grub

See where that gets you.

---

### Post by tedderst on 2010-05-22
I changed the boot sequence, but the only operating system that grub shows is Windows 7! Would it help if I changed the boot partition to the other drive? But i have no idea where or how to do that. Is there a hidden folder somewhere?

---

### Post by oldfred on 2010-05-22
Your grub.cfg shows Ubuntu but not windows, so how are you getting just windows?

In fact once you are booted into ubuntu you should run
sudo update-grub

That will refresh everything in the grub.cfg menu and find windows.

---

### Post by tedderst on 2010-05-22
I don't know, I'm just telling you how it is. Both operating systems are on the same drive, just different partitions. Should I boot Ubuntu from the CD and then run sudo update-grub?

---

### Post by tedderst on 2010-05-22
Did that and I got error cannot find device for / (is /dev mounted?)

I'm going to reinstall ubuntu and see if that fixes it. Before I do I'm going to try and figure out how to change the windows boot partition to the drive it is supposed to be on.

---

### Post by oldfred on 2010-05-22
More info on windows boot partition:

Win7 system partition info
[http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/](http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/)

---

