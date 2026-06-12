---
title: "Neither BIOS nor WinXP recognize Ubuntu 10.10 partition"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Almighty Doer of Stuff on 2011-01-21
Hello. I'm new to Linux.

I'm trying to install Ubuntu 10.10 on my WinXP desktop computer. I used the LiveCD and manually configured the partitions. I resized my XP partition (the entire SATA HDD) and created a 37GB partition for Ubuntu, as well as a 3GB swap file. I installed the boot loader on the Ubuntu partition.

But BIOS doesn't recognize that the drive has separate partitions, and I can't boot into it from Windows either. I know I didn't modify WinXP's MBR, but should I have? I didn't know where it was.

I booted into the LiveCD again, and went into the disk manager. I Edited the Ubuntu partition and saw a checkbox that said "Bootable". I checked it and hit apply, hoping that might do it. I waited twenty minutes and the little circle was still spinning with no indication that it was actually doing anything or any warning of how long it would take, so I rebooted. Still no luck.

Someone told me that Ubuntu sometimes won't be bootable if you have both SATA and PATA drives in the system, which I do (although both XP and Ubuntu are on the same, SATA drive) and gave me a page that told me to use Grub4Dos. I fiddled around with that, only to come onto the Ubuntu website and find out that the page they gave me was outdated, before Ubuntu used GRUB2.

I really don't know what else to do to make my computer boot into Ubuntu. Any help you can provide me with is greatly appreciated!

---

### Post by endotherm on 2011-01-21
please post back the output of 
```
sudo fdisk -l
```

and look at this howto for the bootinfo script. it generates info for troubleshooting booting problems:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by presence1960 on 2011-01-21
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

We need to see exactly what you have there.

---

### Post by Almighty Doer of Stuff on 2011-01-21
Thanks for the quick replies!

I'm going to try that script now. I have to put it on my USB stick though, because Ubuntu won't recognize my wireless NIC. I don't know why. It says "firmware missing" which I assume means I have to install the drivers, but I can't do that until I can boot into my Ubuntu partition.

I shall report back shortly.

---

### Post by Almighty Doer of Stuff on 2011-01-21
Here it is. The obvious problem seems to be that there's a file missing, but I don't know if there's other problems too. That's why I'm asking you guys. :P

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 75889488 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       112,454       112,392  de Dell Utility
/dev/sdb2    *        112,455    71,423,001    71,310,547   7 HPFS/NTFS
/dev/sdb3         149,549,085   156,232,124     6,683,040  db CP/M / CTOS / ...
/dev/sdb4          71,423,998   149,549,055    78,125,058   5 Extended
/dev/sdb5          71,424,000   143,687,679    72,263,680  83 Linux
/dev/sdb6         143,689,728   149,549,055     5,859,328  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1039 MB, 1039663104 bytes
256 heads, 32 sectors/track, 247 cylinders, total 2030592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32     2,030,591     2,030,560   4 FAT16 <32M


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6A9CC9739CC93A79                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        07D6-041C                              vfat       DellUtility                   
/dev/sdb2        48E85142E8513004                       ntfs                                     
/dev/sdb3                                               vfat       DellRestore                   
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        8dadaa23-9b35-461b-9ca7-96f16c0ac0a2   ext4                                     
/dev/sdb6        985736e7-797f-4de8-ac94-2ca7f1b2a83a   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1                                               vfat       ADoS                   
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/ADoS       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sdb2/menu.lst: ================================

# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies /ntldr
chainloader /ntldr
savedefault --wait=2

title find and load BOOTMGR of Windows VISTA
fallback 2
find --set-root --ignore-floppies /bootmgr
chainloader /bootmgr
savedefault --wait=2

title find and load CMLDR, the Recovery Console of Windows NT/2K/XP
fallback 3
find --set-root --ignore-floppies /cmldr
chainloader /cmldr
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
savedefault --wait=2

title find and load IO.SYS of Windows 9x/Me
fallback 4
find --set-root /io.sys
chainloader /io.sys
savedefault --wait=2

title find and boot 0PE.ISO
fallback 5
find --set-root /0PE/0PE.ISO
map /0PE/0PE.ISO (0xff) || map --mem /0PE/0PE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title find and boot MicroPE.ISO
fallback 6
find --set-root /boot/MicroPE.ISO
map /boot/MicroPE.ISO (0xff) || map --mem /boot/MicroPE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Parted Magic ISO
fallback 7
find --set-root /pmagic.iso
map /pmagic.iso (0xff) || map --mem /pmagic.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Ultimate Boot CD ISO
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title floppy (fd0)
chainloader (fd0)+1
rootnoverify (fd0)

title back to dos
quit

title reboot
reboot

title halt
halt

title MAXDOS.IMG
find --set-root --ignore-floppies /boot/MAXDOS.IMG
map --mem /boot/MAXDOS.IMG (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)



================================ sdb2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
c:\grldr = "sundry distros"
=================== sdb2: Location of files loaded by Grub: ===================


    ??GB: menu.lst

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 8dadaa23-9b35-461b-9ca7-96f16c0ac0a2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 8dadaa23-9b35-461b-9ca7-96f16c0ac0a2
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 8dadaa23-9b35-461b-9ca7-96f16c0ac0a2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8dadaa23-9b35-461b-9ca7-96f16c0ac0a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 8dadaa23-9b35-461b-9ca7-96f16c0ac0a2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8dadaa23-9b35-461b-9ca7-96f16c0ac0a2 ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 8dadaa23-9b35-461b-9ca7-96f16c0ac0a2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 8dadaa23-9b35-461b-9ca7-96f16c0ac0a2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sdb1)" {
    insmod part_msdos
    insmod fat
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 07d6-041c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 48e85142e8513004
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=8dadaa23-9b35-461b-9ca7-96f16c0ac0a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=985736e7-797f-4de8-ac94-2ca7f1b2a83a none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  64.7GB: boot/grub/grub.cfg
  62.6GB: boot/initrd.img-2.6.35-22-generic
  36.8GB: boot/vmlinuz-2.6.35-22-generic
  62.6GB: initrd.img
  36.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  b8 00 00 8e d0 bc 00 7c  8e d8 fc b9 80 00 8b f4  |.......|........|
00000010  bf 00 06 8e c0 f3 66 a5  ea 2d 06 00 00 10 00 01  |......f..-......|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 e8 c5 00  |................|
00000030  b4 11 cd 16 74 48 3d 00  89 75 43 b4 10 cd 16 33  |....tH=..uC....3|
00000040  db c6 87 be 07 00 80 bf  c2 07 db 74 0e 83 c3 10  |...........t....|
00000050  83 fb 40 72 ec be 47 07  e9 92 00 c6 87 be 07 80  |..@r..G.........|
00000060  c6 87 c2 07 0c 2e c7 06  21 06 00 06 b8 43 00 86  |........!....C..|
00000070  c4 b2 80 be 1d 06 cd 13  72 db 0a e4 75 d7 33 db  |........r...u.3.|
00000080  33 c9 8a 87 be 07 3c 00  74 0c 3c 80 74 05 be 8a  |3.....<.t.<.t...|
00000090  07 eb 5a 41 8b eb 83 c3  10 83 fb 40 72 e4 be 95  |..ZA.......@r...|
000000a0  07 00 0c 80 f9 01 72 4b  77 43 be 58 07 8b c5 c1  |......rKwC.X....|
000000b0  e8 04 00 44 1b ff d7 66  8b 86 c6 07 66 2e a3 25  |...D...f....f..%|
000000c0  06 2e c7 06 21 06 00 7c  b4 42 b2 80 be 1d 06 cd  |....!..|.B......|
000000d0  13 be 80 07 72 17 0a e4  75 13 be 78 07 ff d7 be  |....r...u..x....|
000000e0  ab 07 81 3e fe 7d 55 aa  75 03 e9 13 75 ff d7 b4  |...>.}U.u...u...|
000000f0  00 cd 16 cd 18 b8 03 00  cd 10 b8 00 b8 8e c0 33  |...............3|
00000100  ff b8 20 1f b9 50 00 f3  ab b1 0c be 3b 07 bf 44  |.. ..P......;..D|
00000110  00 ac ab e2 fc b4 02 b7  00 ba 00 02 cd 10 b4 86  |................|
00000120  b9 1e 00 ba 80 84 cd 15  bf 2c 07 c3 ac 3c 00 74  |.........,...<.t|
00000130  09 b4 0e bb 07 00 cd 10  eb f2 c3 77 77 77 2e 64  |...........www.d|
00000140  65 6c 6c 2e 63 6f 6d 43  61 6e 6e 6f 74 20 72 65  |ell.comCannot re|
00000150  73 74 6f 72 65 0d 0a 00  4c 6f 61 64 69 6e 67 20  |store...Loading |
00000160  50 42 52 20 66 6f 72 20  64 65 73 63 72 69 70 74  |PBR for descript|
00000170  6f 72 20 31 2e 2e 2e 00  64 6f 6e 65 2e 0d 0a 00  |or 1....done....|
00000180  66 61 69 6c 65 64 2e 0d  0a 00 42 61 64 20 66 6c  |failed....Bad fl|
00000190  61 67 0d 0a 00 30 20 61  63 74 69 76 65 20 70 61  |ag...0 active pa|
000001a0  72 74 69 74 69 6f 6e 73  0d 0a 00 42 61 64 20 50  |rtitions...Bad P|
000001b0  42 52 0d 0a 00 00 00 00  8c 73 f4 d0 00 00 00 01  |BR.......s......|
000001c0  01 00 de fe 3f 06 3f 00  00 00 08 b7 01 00 80 00  |....?.?.........|
000001d0  01 07 07 fe ff ff 47 b7  01 00 d3 1c 40 04 00 00  |......G.....@...|
000001e0  c1 ff db fe ff ff 1d f0  e9 08 a0 f9 65 00 00 fe  |............e...|
000001f0  ff ff 05 fe ff ff fe d7  41 04 02 18 a8 04 55 aa  |........A.....U.|
00000200

Unknown BootLoader  on sdb4

00000000  83 96 55 b0 f2 86 b7 4f  e8 53 66 d1 da e9 46 4c  |..U....O.Sf...FL|
00000010  54 71 ef a5 bc 34 e7 8d  67 d1 5e 6d 06 43 f8 b6  |Tq...4..g.^m.C..|
00000020  dc 21 6c ef 84 0e 2d b0  10 35 f6 e9 4d 74 0f ce  |.!l...-..5..Mt..|
00000030  79 f4 dc d4 d9 56 f6 da  a9 f0 b5 8f 46 24 e4 51  |y....V......F$.Q|
00000040  65 e3 08 1c 21 7c 9b 43  08 87 d9 22 27 8d ba 65  |e...!|.C..."'..e|
00000050  fc c4 c0 f8 d3 b3 7f 96  25 14 18 af 71 14 e3 7c  |........%...q..||
00000060  fa 4d 1c e5 36 b7 38 47  71 7b 16 ca b7 38 84 72  |.M..6.8Gq{...8.r|
00000070  13 7a 49 5b 16 b6 77 79  37 2e 54 61 db e8 28 b6  |.zI[..wy7.Ta..(.|
00000080  56 ad 26 8e e8 01 b7 38  8d 52 9e 85 68 9b 43 88  |V.&....8.R..h.C.|
00000090  b6 70 ec 6f 80 bd 49 8a  85 e8 2c d3 48 6d cb 4a  |.p.o..I...,.Hm.J|
000000a0  b5 46 07 0d 06 be d9 78  66 a9 8a 81 f5 8e 32 30  |.F.....xf.....20|
000000b0  b9 56 4c 9c b1 b3 a0 e8  5a 33 38 c1 8c 35 4c 69  |.VL.....Z38..5Li|
000000c0  64 7b 35 ee 16 af f9 fb  de 88 8a 97 ed 25 10 df  |d{5..........%..|
000000d0  b6 ea 5a fa 51 ee 2e b7  38 21 76 85 83 6c db c7  |..Z.Q...8!v..l..|
000000e0  8f 73 d9 d6 da bb 53 2a  b6 57 96 40 ac 3b 97 6d  |.s....S*.W.@.;.m|
000000f0  3b a4 bf 03 b4 b3 cc e0  08 9f 28 b9 99 ff ff 40  |;.........(....@|
00000100  ec a7 36 73 84 a1 1c f2  fa 65 0c 86 7e 1b 90 32  |..6s.....e..~..2|
00000110  c4 b5 90 2d de cc fb a3  1a 97 ea 60 fb 9b bc 86  |...-.......`....|
00000120  10 d2 3d b0 f2 c9 be af  e1 73 2d 01 c8 fd a1 72  |..=......s-....r|
00000130  e8 f8 c8 a1 51 f7 f9 ba  3d 07 e7 6b 3b 56 ed 0a  |....Q...=..k;V..|
00000140  9c 7b 21 12 ec be 30 3b  83 1b b5 25 95 d3 b6 d4  |.{!...0;...%....|
00000150  04 e3 f8 ae ae f8 cc f7  15 b5 2c c8 d4 62 8d 32  |..........,..b.2|
00000160  91 f7 35 b9 28 d3 2f 1d  da e1 cf 14 35 d6 64 6a  |..5.(./.....5.dj|
00000170  f4 f0 fc d8 07 54 3a 25  a3 03 b8 86 39 22 de 2f  |.....T:%....9"./|
00000180  6d 04 75 4c 51 cc 95 dd  ec 69 0d 21 a5 87 7d 95  |m.uLQ....i.!..}.|
00000190  24 47 23 63 3c 03 eb e3  ec 4f d3 7a 37 db 74 32  |$G#c<....O.z7.t2|
000001a0  98 6d 3a 19 39 0c af 2b  30 0e bb 2b b8 27 f4 d9  |.m:.9..+0..+.'..|
000001b0  b0 4b 3e bd 0f 92 5c ae  a7 42 6f 2d 2f 1b 00 fe  |.K>...\..Bo-/...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 a8 4e 04 00 fe  |............N...|
000001d0  ff ff 05 fe ff ff 02 a8  4e 04 00 70 59 00 00 00  |........N..pY...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 3c 90 2d 5d 6d 77 56  49 48 43 00 02 20 01 00  |.<.-]mwVIHC.. ..|
00000010  02 00 02 00 00 f8 f8 00  20 00 00 01 20 00 00 00  |........ ... ...|
00000020  e0 fb 1e 00 80 00 29 00  00 00 00 4e 4f 20 4e 41  |......)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200

```

---

### Post by oldfred on 2011-01-21
You do not install grub2 to a partition normally. YOu have to install it to an MBR. 

You windows is in sdb but your windows boot is in sda. That leaves sdb open to install grub2 to and then set BIOS to boot sdb and then you should be able to boot either. Sometimes windows/grub get confused when windows is on sdb so we will see if it works or not.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb5 and want grub2 in drive sdb's MBR:
#Find linux partition, change sdb5 if not correct:
sudo fdisk -l
#confirm that linux is sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# After rebooting into working system
sudo update-grub

---

### Post by Almighty Doer of Stuff on 2011-01-21
Do I need to format the Ubuntu partition and reinstall it first, or is there another way?

---

### Post by oldfred on 2011-01-21
No you do not have to reinstall, just reinstall grub2 to the MBR. 

The grub installed to the partition will sit there and be obsolete, but the space is not used anyway, so it does not matter whether it has some data or just zeros.

---

### Post by Almighty Doer of Stuff on 2011-01-21
Thanks a lot for the help! I can not boot into either operating system successfully!

Now to see if I can get my Internet working.

---

