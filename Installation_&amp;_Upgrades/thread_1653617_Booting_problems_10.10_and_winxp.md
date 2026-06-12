---
title: "Booting problems 10.10 and winxp"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by jerry85 on 2010-12-27
I'm unable to boot ubuntu or windows. 
for the moment I'm using the supergrubdisk, tried to fix problems with the disk, but it seems to be a different grub version. also tried startupmanager, but it didn't work: [http://ubuntuforums.org/showthread.php?t=1652813](http://ubuntuforums.org/showthread.php?t=1652813)

can anyone help me?
thanks!!


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   398,267,414   193,470,795   f W95 Ext d (LBA)
/dev/sda5         204,796,683   398,267,414   193,470,732   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   307,884,031   307,881,984  83 Linux
/dev/sdb2         307,886,078   320,172,031    12,285,954   5 Extended
/dev/sdb5         307,886,080   320,172,031    12,285,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BC88C13688C0EFC6                       ntfs       WINDOWS                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        FE280E0B280DC41D                       ntfs       Muziek                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        799cba96-7827-4dec-a528-49ab6a974478   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0c20e0d5-31e5-43af-9b65-9619ce1f9b7e   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sr0         /media/CDROM             iso9660    (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda5        /media/Muziek            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin /usepmtimer 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 799cba96-7827-4dec-a528-49ab6a974478
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 799cba96-7827-4dec-a528-49ab6a974478
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 799cba96-7827-4dec-a528-49ab6a974478
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=799cba96-7827-4dec-a528-49ab6a974478 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 799cba96-7827-4dec-a528-49ab6a974478
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=799cba96-7827-4dec-a528-49ab6a974478 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 799cba96-7827-4dec-a528-49ab6a974478
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 799cba96-7827-4dec-a528-49ab6a974478
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bc88c13688c0efc6
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0c20e0d5-31e5-43af-9b65-9619ce1f9b7e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 137.5GB: boot/grub/core.img
 120.4GB: boot/grub/grub.cfg
 120.5GB: boot/initrd.img-2.6.35-22-generic
 137.5GB: boot/vmlinuz-2.6.35-22-generic
 120.5GB: initrd.img
 137.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  d6 f3 ff 02 8a 8d fe 5c  ed 54 a7 e2 25 f8 8c 5c  |.......\.T..%..\|
00000010  9f 19 7f d5 17 51 f9 7e  db 55 ab ac fc a2 30 e3  |.....Q.~.U....0.|
00000020  66 ab 15 a9 97 f7 27 73  d0 5f fa a2 bb 21 36 50  |f.....'s._...!6P|
00000030  d7 b3 31 ab 16 79 e3 c9  6c db 49 f9 57 2d 82 cb  |..1..y..l.I.W-..|
00000040  5a d8 42 8a 04 91 c1 41  f0 f9 43 38 18 0c 79 ac  |Z.B....A..C8..y.|
00000050  9b 04 46 b6 93 70 a0 a7  a6 e9 d3 f1 81 c4 7c 56  |..F..p........|V|
00000060  07 00 9b 87 9e f0 f0 62  91 d7 61 e3 a3 f0 80 1a  |.......b..a.....|
00000070  0a ed 99 ea 96 51 70 fa  fa a8 51 2f 67 5c a4 75  |.....Qp...Q/g\.u|
00000080  eb 6b 0a e4 7e fb 2f 99  e3 64 8f 0d 84 18 b8 7d  |.k..~./..d.....}|
00000090  74 21 0f b5 b3 c5 c5 d0  75 21 30 66 44 fd 5e 7c  |t!......u!0fD.^||
000000a0  ce c3 ea b4 88 4a aa d4  6e 7f 46 a3 e0 9e aa 76  |.....J..n.F....v|
000000b0  9e d8 a1 e1 02 7c be ed  c5 5e b2 70 e8 fb df 57  |.....|...^.p...W|
000000c0  fe db ed 59 56 bc 3e 32  f5 54 7c aa 8f 47 96 97  |...YV.>2.T|..G..|
000000d0  ce 7b ff a3 a5 5a b0 05  2a 57 f1 fd fc d5 5b ef  |.{...Z..*W....[.|
000000e0  d8 3b 6d 28 f7 32 4f 4b  c3 3a 5c c4 a2 5e 46 ee  |.;m(.2OK.:\..^F.|
000000f0  48 0c 2e c2 ed 6a 8f d1  d1 bb 8f fe 89 37 ea a5  |H....j.......7..|
00000100  1f df ff 24 4b 56 63 78  d5 b1 67 83 c0 40 76 0c  |...$KVcx..g..@v.|
00000110  08 21 07 c1 0c 7d 07 9e  bb 39 9f 77 0c 09 23 e0  |.!...}...9.w..#.|
00000120  40 12 01 bf 15 8f 8b ff  0b ab 7e a0 17 64 92 c7  |@.........~..d..|
00000130  a9 fd 3c 3f a8 21 04 00  40 51 22 a1 f8 fe 64 b2  |..<?.!..@Q"...d.|
00000140  30 67 e2 48 30 fd 5c 03  83 ef 10 83 2b fc 00 e8  |0g.H0.\.....+...|
00000150  3e 06 cf ab 1f 2b 92 4d  8a 95 f8 7b 2c 32 0d f0  |>....+.M...{,2..|
00000160  80 10 82 07 ed 80 7f e9  b6 78 59 2f e4 af cf 1c  |.........xY/....|
00000170  1f c4 07 01 40 58 4a aa  aa bb af 99 be 3c 25 84  |....@XJ......<%.|
00000180  11 2a 89 17 55 09 65 c2  59 76 e7 2c 53 08 24 57  |.*..U.e.Yv.,S.$W|
00000190  4f 17 fa 19 f3 c3 f1 c2  01 78 95 07 f2 cf b3 08  |O........x......|
000001a0  41 00 18 79 27 bc 3c 12  d5 a8 55 b7 2d fd 45 65  |A..y'.<...U.-.Ee|
000001b0  b6 39 ca b2 4b cb 62 f5  d5 39 90 7c 0c 0c 00 fe  |.9..K.b..9.|....|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 0c 21 88 0b 00 00  |......?....!....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  00 00 01 ba 44 02 c5 d4  cc 01 01 89 c3 f8 00 00  |....D...........|
00000010  01 e0 07 ec 81 00 00 82  3b 1b 9b b0 f0 0e 2b ec  |........;.....+.|
00000020  57 4b 7f c7 36 cb 69 2c  2a a3 03 18 98 2d 08 72  |WK..6.i,*....-.r|
00000030  36 e3 74 42 0c 09 3d 19  f9 2f cb 0c ee ec 9c 7a  |6.tB..=../.....z|
00000040  c6 1c cb e3 c0 d4 dd ba  f3 bb 33 c8 01 d1 0b 90  |..........3.....|
00000050  cb 51 35 62 36 53 c6 5c  a4 66 76 c1 06 b9 e6 c1  |.Q5b6S.\.fv.....|
00000060  2c 10 76 3a 42 b9 66 f0  3b ad 84 19 8c 1d 9c e5  |,.v:B.f.;.......|
00000070  d6 42 06 01 82 59 e7 24  f1 96 1d 41 0f 4b 7f bb  |.B...Y.$...A.K..|
00000080  2c 76 f8 7c a1 bf f4 3b  e9 fe 64 1d a9 9d 23 31  |,v.|...;..d...#1|
00000090  c3 c4 5c e5 30 cc 41 30  7d ad d6 90 30 27 b1 c7  |..\.0.A0}...0'..|
000000a0  8f 17 15 f0 f1 a2 dd c3  a0 94 8f 7c 88 af 96 07  |...........|....|
000000b0  c5 91 b4 18 50 c0 c1 bb  72 7f 8d a2 86 d1 7e 66  |....P...r.....~f|
000000c0  23 93 af 60 3c ae 28 75  24 94 97 61 ac 74 52 f9  |#..`<.(u$..a.tR.|
000000d0  ef f9 8a 32 66 1f 45 08  c4 c8 07 24 ac db 73 97  |...2f.E....$..s.|
000000e0  f7 57 83 06 9e bd f8 0f  04 5b 2c ee 01 15 17 b7  |.W.......[,.....|
000000f0  77 71 2a 01 a4 52 02 47  85 35 d1 21 d8 62 c3 06  |wq*..R.G.5.!.b..|
00000100  06 0c c0 37 19 b8 ce 46  66 a0 cc 57 c8 2c 29 68  |...7...Ff..W.,)h|
00000110  df 3c 18 4d e4 94 21 c7  a8 ce 3b 52 7f 18 92 5e  |.<.M..!...;R...^|
00000120  c7 98 e8 40 11 88 4c 03  64 e0 97 10 d8 83 77 29  |...@..L.d.....w)|
00000130  19 64 e7 29 b6 0f 53 1c  41 a0 3e 38 3d a1 a8 2d  |.d.)..S.A.>8=..-|
00000140  07 30 af 92 cc 14 d4 9d  c6 21 9f e3 8f 19 8f 8a  |.0.......!......|
00000150  ec d9 78 05 77 68 ca 0a  06 32 32 0d 66 86 6c 9f  |..x.wh...22.f.l.|
00000160  d4 1e 90 0f a7 01 42 b7  e2 ba f2 a2 8a 5b 96 45  |......B......[.E|
00000170  3e 80 26 62 5b 99 3a 1e  e2 6c 98 19 93 90 9e 57  |>.&b[.:..l.....W|
00000180  71 bd b2 7f e1 2f 21 20  58 09 1a 72 40 23 98 97  |q..../! X..r@#..|
00000190  d2 47 1b d9 93 15 b8 c2  96 8e 91 fb 9e e1 d1 4e  |.G.............N|
000001a0  4b c3 38 04 52 68 91 6c  b3 d0 8c 5e 42 4b cf c6  |K.8.Rh.l...^BK..|
000001b0  25 f3 e1 d2 4a e8 4e e3  45 07 45 62 b0 42 00 fe  |%...J.N.E.Eb.B..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by dino99 on 2010-12-27
grub2 is installed on /dev/sda

did you get a grub menu when booting ?

you need to select the ubuntu hdd into bios to boot on if you have several hdds

As ubuntu is installed on /dev/sdb (no grub installed on it), i suppose that the grub on /dev/sda is from an other installation, right ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by jerry85 on 2010-12-27
correct! the grub on sda might be the fix of the winxp mbr from my suse-attempt.

however, it is strange that ubuntu didn't install grub at install on its own hd, so perhaps ubuntu installed the grub (it ís v2 on sda) over the mbr of windows?

there is no grub menu at startup, only a black screen after bios loading with a white blinking cursor..

Is there a way to repair the Grub and MBR without having to re-install my ubuntu?

--> will now try to set bios, but as I recall, there is no option to select preferred hd, just 'boot from hd, dvd, disk,.. etc'

 back in 5!


btw: thanks for the fast reply!

---

### Post by jerry85 on 2010-12-27
checked my boot and no luck..

Is there no gui for boot-settings available for grub2? started checking the posts but nothing really jumps out.

---

### Post by Quackers on 2010-12-27
Do you have a XP repair disc?
The mbr of sda should have Windows bootloader installed but it has grub there.
If you repair the mbr you can then boot Windows.
Then you can run the live cd and install grub to the mbr of sdb which will then make Ubuntu bootable (if you make the second hard drive the first boot device in the bios). Grub would then pick up the XP installation and be able to boot that too.

---

### Post by jerry85 on 2010-12-27
Thanks Quackers!

I'm gonna try, but it might take a while.. my bios hasn't got the option to select the bootable disk, so this means physically changing the master slave priority right?

---

### Post by Quackers on 2010-12-27
So your bios doesn't allow booting from the second hard drive? What kind of drive is it please?

---

### Post by jerry85 on 2010-12-27
Both of them are ATA maxtor drives.
here is some more detailed info:

```

jeroen@jeroen-Ubuntu:~$ lspci -vv
00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 815d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 8
    Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64
    Kernel modules: amd64-agp

00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: d8000000-d9ffffff
    Prefetchable memory behind bridge: c0000000-cfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 80200000-803fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 80400000-805fffff
    Prefetchable memory behind bridge: 80600000-807fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: da000000-dbffffff
    Prefetchable memory behind bridge: 80800000-809fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 80a00000-80bfffff
    Prefetchable memory behind bridge: 80c00000-80dfffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46) (prog-if 10 [OHCI])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at dc000000 (32-bit, non-prefetchable) [size=2K]
    Region 1: I/O ports at d000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 20
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    Region 4: I/O ports at d400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 21
    Region 4: I/O ports at d800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 21
    Region 4: I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at e000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at e400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
    Subsystem: VIA Technologies, Inc. USB 2.0
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Interrupt: pin C routed to IRQ 21
    Region 0: Memory at dc001000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Subsystem: ASUSTeK Computer Inc. Device 8174
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 22
    Region 0: I/O ports at e800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 22
    Region 0: I/O ports at 4400 [size=256]
    Capabilities: <access denied>
    Kernel modules: snd-via82xx-modem

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel driver in use: k8temp
    Kernel modules: k8temp

02:00.0 VGA compatible controller: ATI Technologies Inc RV380 0x3e50 [Radeon X600] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 014e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 24
    Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at b000 [size=256]
    Region 2: Memory at d9000000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at d8000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

02:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600] (Secondary)
    Subsystem: ASUSTeK Computer Inc. Device 014f
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: Memory at d9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 36
    Region 0: Memory at db000000 (64-bit, non-prefetchable) [size=16K]
    Region 2: I/O ports at c000 [size=256]
    Expansion ROM at da000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

```

---

### Post by Quackers on 2010-12-27
Are they internal drives?
Does the bios see both drives?

---

### Post by jerry85 on 2010-12-27
yes, both are internal and the bios sees them at startup.
it is after the 'bios reading'  mem check that the black screen shows up. 

I've googled it, and apparently there are bois' that don't have the option to select the bootable HD. so I'll have to open up the computer I guess..

---

### Post by Quackers on 2010-12-27
No need I think.
Leave sda as the bootable device and run fixmbr from the Windows XP installation disc or repair disc, if you have one. When Windows is bootable we can re-install grub.

---

### Post by jerry85 on 2010-12-27
super!! sounds good :) 
I'm prepping my penndrive right now.. 

windows problem should be solved in a few moments

---

### Post by Quackers on 2010-12-27
Your pc boots from a usb stick but not from your second hard drive? I presume you are making a Windows repair usb stick?

---

### Post by jerry85 on 2010-12-29
I solved the problem :)

btw, I'm sorry that it took me so long to reply, but I got called away from my computer and had to put things on a hold for a while.

anyway! I did solve the problem using trying many things, like re-installing and or updating grub2, using the tutorial found on the ubuntu helpsite:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
some other sites:
[http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05](http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05)

and finally succeeded using the rescatux-disk :)
[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

first I re-installed my windows mbr with the supergrubdisk, for the usbstick gave problems booting (another reason it took me so long replying..)

the only thing I don't understand is, why practically everything I try in the linux shell keeps failing.. just needs some time I think..

but finally I can start using ubuntu to the fullest!! only have to get my soundcard driver working..

thanks for the help Quackers and dino99!

---

