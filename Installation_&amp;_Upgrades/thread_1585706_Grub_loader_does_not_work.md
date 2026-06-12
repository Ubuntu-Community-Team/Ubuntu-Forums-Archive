---
title: "Grub loader does not work"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by scmeis1 on 2010-09-30
Hi, this is my first post into Ubuntu. I have always been a Redhat user, and ESXi User. I decided to try ubuntu because of it's strong recommendations as a file server. I have tried several fixes listed in the forums with no luck. I tried the live CD and I have no issues there. I tried gparted, and it sees all my drives. Seeing that most ask for the boot info script to be run, i was proactive. I know its a boot issue with were grub is pointing too. However, that is where I get stuck. I am not an expert at using grub. In a Nut shell, I had no issues installing. I choose the Jmicron 150G Raid 1 drive. Used full drive space with LVM. When it came to reboot I did, and it just sits after it does the boot from cdrom.  Any help is appreciated. I hate to go back to windows 7 for a file server/web server.  Oh Windows was installed at one point, I think that is where the script sees the GPT partitions. Thank you in advance!



Machine details:
AMD 1055T
8G Gskill
4850 ATI card
Intel Pro 10/100/1000 PT
LSI MegaRaid 84016E
20T drive space on Raid 5
3T on another Raid 5
150G on 2x JMircon Raid 1
4 x 1T Drives (not set up yet)
1T on Backup external Esata drive
GA-890FXA-UD5 MOBO

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 184432 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sdg
 => No boot loader is installed in the MBR of /dev/mapper/jmicron_OS

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb2 has 
                       1558278143 sectors, but according to the info from 
                       fdisk, it has 2632019967 sectors.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

jmicron_OS1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

jmicron_OS2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

jmicron_OS5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 19990.0 GB, 19989989949440 bytes
256 heads, 63 sectors/track, 2420817 cylinders, total 39042949120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34         2,081         2,048 -
/dev/sda2           2,082       262,177       260,096 Microsoft Windows
/dev/sda3         262,17810,051,919,83810,051,657,661 -

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2997.0 GB, 2996997980160 bytes
256 heads, 63 sectors/track, 362940 cylinders, total 5853511680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34       262,177       262,144 Microsoft Windows
/dev/sdb2         264,192 2,632,284,159 2,632,019,968 Linux or Data

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdc1 ends after the last sector of /dev/sdc

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794175 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               2,048    15,792,127    15,790,080   b W95 FAT32


Drive: jmicron_OS ___________________ _____________________________________________________

Disk /dev/mapper/jmicron_OS: 150.0 GB, 150021865472 bytes
255 heads, 63 sectors/track, 18239 cylinders, total 293011456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/jmicron_OS1              2,048       499,711       497,664  83 Linux
/dev/mapper/jmicron_OS2            501,758   293,011,455   292,509,698   5 Extended
/dev/mapper/jmicron_OS5            501,760   293,011,455   292,509,696  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/jmicron_OS1 70482ded-c843-4969-a9b1-01078f13b0e3   ext2                                     
/dev/mapper/jmicron_OS5 ilvCI7-dyir-cvlf-JJjc-TTxC-mmaV-FKK1wF LVM2_member                               
/dev/mapper/jmicron_OS: PTTYPE="dos" 
/dev/sda: PTTYPE="gpt" 
/dev/sdb2        106A79B86A799AE4                       ntfs       Storage                       
/dev/sdb: PTTYPE="gpt" 
/dev/sdc                                                promise_fasttrack_raid_member                               
/dev/sdd1        FEAEB551AEB502E7                       ntfs                                     
/dev/sdd                                                promise_fasttrack_raid_member                               
/dev/sde                                                promise_fasttrack_raid_member                               
/dev/sdf                                                promise_fasttrack_raid_member                               
/dev/sdg1        744F-257B                              vfat       NEW VOLUME                    
/dev/sdg: PTTYPE="dos" 
/dev/sdh                                                promise_fasttrack_raid_member                               
/dev/sdi                                                promise_fasttrack_raid_member                               
error: and: No such file or directory
error: /dev/mapper//dev/sdh:: No such file or directory
error: /dev/mapper//dev/sdi:: No such file or directory
error: /dev/mapper/jmicron_OS2: No such file or directory
error: /dev/sdc1: No such file or directory
error: discovered: No such file or directory
error: formats: No such file or directory
error: "jmicron": No such file or directory
error: jmicron)!: No such file or directory
error: "pdc": No such file or directory
error: (using: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
jmicron_OS
jmicron_OS1
jmicron_OS5

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /media/NEW VOLUME        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


========================== jmicron_OS1/grub/grub.cfg: ==========================

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
insmod lvm
insmod ext2
set root='(mcse001-root)'
search --no-floppy --fs-uuid --set c62ec665-0134-4f4d-b948-4e487de90791
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
set root='(hd8,1)'
search --no-floppy --fs-uuid --set 70482ded-c843-4969-a9b1-01078f13b0e3
set locale_dir=($root)/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd8,1)'
    search --no-floppy --fs-uuid --set 70482ded-c843-4969-a9b1-01078f13b0e3
    linux    /vmlinuz-2.6.32-24-server root=/dev/mapper/mcse001-root ro   quiet
    initrd    /initrd.img-2.6.32-24-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd8,1)'
    search --no-floppy --fs-uuid --set 70482ded-c843-4969-a9b1-01078f13b0e3
    echo    'Loading Linux 2.6.32-24-server ...'
    linux    /vmlinuz-2.6.32-24-server root=/dev/mapper/mcse001-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd8,1)'
    search --no-floppy --fs-uuid --set 70482ded-c843-4969-a9b1-01078f13b0e3
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd8,1)'
    search --no-floppy --fs-uuid --set 70482ded-c843-4969-a9b1-01078f13b0e3
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

================ jmicron_OS1: Location of files loaded by Grub: ================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-24-server
    .0GB: vmlinuz-2.6.32-24-server
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown GPT Partiton Type
aac808588f7ee04285d2e1e90434cfb3
Unknown GPT Partiton Type
a0609baf3114624fbc683311714a69ad
Unknown BootLoader  on sda3

00000000  eb da c6 2f 0e b3 17 cf  f2 12 47 e0 44 a2 8a 66  |.../......G.D..f|
00000010  ba 2b 56 f7 64 0d dc 25  0a 97 3f 24 1c 3a d3 ef  |.+V.d..%..?$.:..|
00000020  19 7e 07 42 50 1d e2 5e  7b f1 b7 a7 4d 18 4b f3  |.~.BP..^{...M.K.|
00000030  b7 d9 8f a3 f8 36 6f 35  8c e7 88 6a 5b 33 c7 b5  |.....6o5...j[3..|
00000040  f8 87 fa d8 42 eb e0 54  2a 21 57 ff a1 9e c3 2f  |....B..T*!W..../|
00000050  a4 50 31 1e c2 fe d1 14  8e 69 f5 4a d7 88 2f 6c  |.P1......i.J../l|
00000060  93 c0 c1 d0 2a 69 91 41  8f 3d 37 ad 61 23 e8 ce  |....*i.A.=7.a#..|
00000070  95 b8 56 ca 36 b7 ea 50  fc eb 91 af 37 15 c2 d7  |..V.6..P....7...|
00000080  47 1f c2 5d 15 0b 9a 2d  07 07 b3 61 3d ea 53 ba  |G..]...-...a=.S.|
00000090  ce 45 d1 90 9b 75 19 ca  42 61 f9 9c 3d 86 59 5c  |.E...u..Ba..=.Y\|
000000a0  70 c7 c9 ed 2d c1 b3 32  1b 95 74 2d 6b 59 80 c5  |p...-..2..t-kY..|
000000b0  0d 4b 96 45 73 86 d1 35  47 11 9c 7b 07 c9 0f 2d  |.K.Es..5G..{...-|
000000c0  2c 89 cd 5a 88 33 d3 5a  0f a3 55 ca 70 ed 84 d7  |,..Z.3.Z..U.p...|
000000d0  5d 91 99 87 b0 0d 14 f6  75 83 82 2f 39 7f 9d ed  |].......u../9...|
000000e0  8d 20 77 65 01 a2 aa 87  49 b0 5f e9 0b 1d 10 b5  |. we....I._.....|
000000f0  3e 29 0b 24 a1 d7 76 c1  31 6e 35 13 fb f5 e9 ea  |>).$..v.1n5.....|
00000100  1b 3c 10 d3 67 57 a3 fd  46 46 65 ff 2a 1a f1 61  |.<..gW..FFe.*..a|
00000110  7f ef 50 88 cd 57 10 0f  91 a6 0e 67 9f 56 8c d4  |..P..W.....g.V..|
00000120  9b 98 db 53 ba d2 ea f5  22 ec 6c d6 75 aa ee f7  |...S....".l.u...|
00000130  4b 86 28 a5 33 c7 6a 3d  82 c8 1c 11 5b 6d a9 58  |K.(.3.j=....[m.X|
00000140  64 02 af 1d b3 89 e5 06  83 f8 38 b1 e7 f7 65 d3  |d.........8...e.|
00000150  6d 7f dd 79 fb 49 99 37  35 30 4f fc 5e 7b ac 6f  |m..y.I.750O.^{.o|
00000160  61 62 95 32 52 4a 89 f3  d0 d4 89 93 ab a7 30 14  |ab.2RJ........0.|
00000170  f1 07 08 4a 27 6d e6 9d  b9 2e ea 88 e9 b7 39 af  |...J'm........9.|
00000180  30 38 fc ef 42 3d 30 c8  2f 00 d7 35 b3 53 1b 93  |08..B=0./..5.S..|
00000190  cf 28 18 77 21 53 7f 6c  66 81 e7 e3 ad cb fa b8  |.(.w!S.lf.......|
000001a0  e2 a2 33 3f 94 7b 79 a5  b8 c8 84 56 e9 3b f5 75  |..3?.{y....V.;.u|
000001b0  1d 42 53 b4 9d f6 b7 4a  5c 93 38 68 83 8f bf a5  |.BS....J\.8h....|
000001c0  68 ee d3 63 ec 86 b2 ad  94 68 b8 b4 0c 56 7a 6a  |h..c.....h...Vzj|
000001d0  95 ab e1 7b 6e 19 a7 0d  73 24 0e 4a 43 96 78 ec  |...{n...s$.JC.x.|
000001e0  18 b3 bd 8f b5 b0 d9 47  9e d3 3b 61 94 ae f4 d4  |.......G..;a....|
000001f0  59 21 84 30 ad e9 c6 96  f0 9f 05 d0 d7 ae ff 7d  |Y!.0...........}|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on jmicron_OS2



=======Devices which don't seem to have a corresponding hard drive==============

sdi: "pdc" and "jmicron" formats discovered (using jmicron)! sdh: "pdc" and "jmicron" formats discovered (using jmicron)! 
=============================== StdErr Messages: ===============================

ERROR: pdc: zero sectors on /dev/sdf
ERROR: pdc: setting up RAID device /dev/sdf
ERROR: pdc: zero sectors on /dev/sde
ERROR: pdc: setting up RAID device /dev/sde
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: pdc: zero sectors on /dev/sdf
ERROR: pdc: setting up RAID device /dev/sdf
ERROR: pdc: zero sectors on /dev/sde
ERROR: pdc: setting up RAID device /dev/sde
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: jmicron: wrong # of devices in RAID set "jmicron_OS" [1/2] on /dev/sdi
ERROR: jmicron: wrong # of devices in RAID set "jmicron_OS" [1/2] on /dev/sdh
ERROR: only one argument allowed for this option
ERROR: pdc: zero sectors on /dev/sdf
ERROR: pdc: setting up RAID device /dev/sdf
ERROR: pdc: zero sectors on /dev/sde
ERROR: pdc: setting up RAID device /dev/sde
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: pdc: zero sectors on /dev/sdf
ERROR: pdc: setting up RAID device /dev/sdf
ERROR: pdc: zero sectors on /dev/sde
ERROR: pdc: setting up RAID device /dev/sde
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/mapper/jmicron_OS2: No such file or directory
hexdump: /dev/mapper/jmicron_OS2: No such file or directory
ERROR: pdc: zero sectors on /dev/sdf
ERROR: pdc: setting up RAID device /dev/sdf
ERROR: pdc: zero sectors on /dev/sde
ERROR: pdc: setting up RAID device /dev/sde
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: jmicron: wrong # of devices in RAID set "jmicron_OS" [1/2] on /dev/sdi
ERROR: jmicron: wrong # of devices in RAID set "jmicron_OS" [1/2] on /dev/sdh
ERROR: only one argument allowed for this option

```

---

### Post by 23dornot23d on 2010-09-30
=> **[COLOR=Red]Grub 2 is installed in the MBR of /dev/sda[/COLOR]** and looks at sector 184432 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/jmicron_OS1 70482ded-c843-4969-a9b1-01078f13b0e3   ext2                                     
/dev/mapper/jmicron_OS5 ilvCI7-dyir-cvlf-JJjc-TTxC-mmaV-FKK1wF LVM2_member                               
/dev/mapper/jmicron_OS: PTTYPE="dos" 
[COLOR=Red]**/dev/sda: PTTYPE="gpt" **[/COLOR]
/dev/sdb2        106A79B86A799AE4                       ntfs       Storage                       
/dev/sdb: PTTYPE="gpt" 

I have a feeling it is something to do with GPT ..... but I know little about it ..... other than it caused [_**one other user some problems a while back**_]("http://ubuntuforums.org/showthread.php?t=1577965") ........

I have [COLOR=Blue][_**left a message with this user**_]("http://ubuntuforums.org/member.php?u=1032238") [/COLOR]as they might be able to help you with _**GPT**_ ........ more than I can ......

One other user that knows all about _**Grub2**_ is here [COLOR=Blue]**[LINK]("http://ubuntuforums.org/member.php?u=223945")**[/COLOR]-drs305

I hope that they can help you ....

---

### Post by srs5694 on 2010-10-01
> **scmeis1 said:**
> I know its a boot issue with were grub is pointing too. However, that is where I get stuck. I am not an expert at using grub. In a Nut shell, I had no issues installing. I choose the Jmicron 150G Raid 1 drive. Used full drive space with LVM. When it came to reboot I did, and it just sits after it does the boot from cdrom.  Any help is appreciated. I hate to go back to windows 7 for a file server/web server.  Oh Windows was installed at one point, I think that is where the script sees the GPT partitions. Thank you in advance!

Windows can't boot from GPT on BIOS-based computers; however, you've got some huge drives in RAID arrays, so Windows may have created GPT layouts to use those drives as data drives. Any other OS would have to do the same thing (or use only part of the drive space). Also, if your computer uses an EFI for firmware, Windows would have to boot from GPT.

> => Grub 2 is installed in the MBR of /dev/sda and looks at sector 184432 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.

This is at least part of the issue. See more below....

> jmicron_OS1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

Here's another part of the puzzle. It looks to me as if you've got GRUB's stage0 boot loader code installed in the MBR of /dev/sda, but you've got GRUB's stage1 and configuration file tucked away inside an LVM logical volume or RAID device on a different physical disk. Theoretically, GRUB 2 should be able to handle this, but you've got so many different disks on this computer that it's not surprising that GRUB is getting confused. (It's easy to confuse GRUB with such setups, in my experience.)

Another issue that could crop up, although I don't think it's the cause of your immediate problems, is that some people have reported problems with GRUB 2 on systems that have a mixture of MBR and GPT disks. There's a simple configuration file fix for this, but I don't recall what it is. A user here called "oldfred" has posted this fix information, IIRC; you might try searching his old posts.

> Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 19990.0 GB, 19989989949440 bytes
256 heads, 63 sectors/track, 2420817 cylinders, total 39042949120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34         2,081         2,048 -
/dev/sda2           2,082       262,177       260,096 Microsoft Windows
/dev/sda3         262,17810,051,919,83810,051,657,661 -

What I recommend is this: Shrink one of the partitions on /dev/sda by about 200MB and create two new partition:


[list]
[*]A small (~1MB) [BIOS Boot Partition,](http://grub.enbug.org/BIOS_Boot_Partition) which GRUB 2 uses to hold its stage1 code on GPT-based systems. If you don't have a BIOS Boot Partition (and you don't), reliability will suffer, as described on the page to which I linked.
[*]A larger (~200MB) partition to serve as a Linux /boot partition. Having this partition on the same drive as the BIOS Boot Partition and the stage0 boot loader code can only improve reliability. The same is true of keeping this partition out of the LVM.
[/list]


You can then re-install Ubuntu. With any luck, it will then work, although it's possible you'll run into the mixed MBR/GPT issues I mentioned earlier. Those can at least be overcome with a small configuration file tweak.

Note that if Windows boots from the partition on /dev/sda, you should use Windows tools to resize the Windows partition. Such a resizing operation is always a risk, so performing a backup is wise, if it's at all practical. If not, you might consider performing similar actions on some other drive and then using the BIOS's options to boot from that other drive rather than from /dev/sda.

> Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdc1 ends after the last sector of /dev/sdc

This doesn't seem to be related to your boot problem, but it appears that the protective partition in the MBR of /dev/sdc is malformed; it should end at the end of the disk, not at sector 4,294,967,295. I don't know offhand how various OSes and utilities will react to this. I recommend you fix it by using my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program: Launch it on the disk, type "p" to view the partition table so you know you're working on the correct disk, type "x" to enter the experts' menu, type "n" to create a fresh protective MBR, and type "w" to save your changes.

> 
Drive: jmicron_OS ___________________ __________________________________________________  ___

Disk /dev/mapper/jmicron_OS: 150.0 GB, 150021865472 bytes
255 heads, 63 sectors/track, 18239 cylinders, total 293011456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/jmicron_OS1              2,048       499,711       497,664  83 Linux
/dev/mapper/jmicron_OS2            501,758   293,011,455   292,509,698   5 Extended
/dev/mapper/jmicron_OS5            501,760   293,011,455   292,509,696  8e Linux LVM

Is the /dev/mapper/jmicron_OS file a software RAID configuration? If so, this makes sense; but if /dev/mapper/jmicron_OS is an LVM device, it makes little sense to carve an LVM up into another LVM.

---

### Post by psusi on 2010-10-01
Unless you have to dual boot with windows, you should not use the fake hardware raid.  Go into the bios, delete all of the raid arrays, and reinstall.  This time set up software raid.

---

### Post by oldfred on 2010-10-01
I think this is/was the fix that srs5694 mentioned. It has been fixed in the newest grub with Maverick but I do not know if any of the older versions have been updated. It resolved an issue of booting a gpt disk but then booting into another system on a MBR disk.

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" posted by meierfra.
or:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)
I added insmod part_msdos to 40_custom & both windows on sda1 and Ubuntu
on sdc5 booted without any issues.

---

### Post by psusi on 2010-10-01
No, those are definitely unrelated to this issue since grub is not loading at all.  It isn't loading at all because it doesn't appear to have been installed correctly.

---

### Post by scmeis1 on 2010-10-01
I actually considered loading up the live CD again, reformatting the drives to get rid of the GPT. 

I DO NOT use windows on this, I tried windows to get what I needed done, which did not do what I wanted.

I do not have any software raids. I have 1x 20T array, (actually 22T) when the RMA is finished. 

I had another 3T Raid 5 array, however, Ubuntu only saw the individual drives, not the RAID (SB850 - Raid). The boot partition I wanted on my RAID 1 (150G) drives. They are 10k Raptor drives, hence the reason for putting the boot and system partitions on it.

I have a single Terabyte external drive for backups on the main box. This is just for strictly backups of other boxes.

I am also considering just pulling the Raid card and letting the server build. I will try every suggestion in here. 

I will first format the drives and divide up the primary boot drives. 

Considering how good I am with veritas file systems and Solaris, this makes me feel very out of place not being able to get this to work.


Thank you all!!! I will report back results.

---

### Post by psusi on 2010-10-01
The problem is that the jmicron controller is a fake hardware raid.  That is why the individual drives attached to it show up.  Don't use the fake raid support and you will be better off.  Go into the bios and blow away the array and when you install, the individual drives will show up and you can use them to form a software raid.

---

### Post by oldfred on 2010-10-01
I do not know RAID, but saved these links.

Raid install of Lucid:
[http://ubuntuforums.org/showthread.php?t=1458699](http://ubuntuforums.org/showthread.php?t=1458699)
[http://ubuntuforums.org/showthread.php?t=1469169](http://ubuntuforums.org/showthread.php?t=1469169)

Hardware Raid boot
[http://ubuntuforums.org/showthread.php?t=1564502](http://ubuntuforums.org/showthread.php?t=1564502)

---

### Post by srs5694 on 2010-10-01
With a 20 TiB hardware RAID array, you *need* GPT; MBR tops out at 2 TiB, assuming the standard 512-byte sector size. (In theory, MBR could handle up to 20 TiB with a large enough sector size. You'd probably need an 8192-byte sector size to do the job. I have no idea if your RAID controller could do this or how Linux would react, though.)

If the JMicron board is doing software RAID (which would explain the device filenames), then I concur with psusi; controller-based software RAID seems to cause a lot of problems. Disable it and, if you want RAID on those drives, use Linux's variety of software RAID instead. Note that many motherboards and some plug-in disk controllers advertise themselves as having RAID support when in fact they've just got a few "hooks" for special software RAID drivers. This is very different from real hardware RAID; with the latter, Linux "sees" a single drive (/dev/sda, /dev/sdb, or whatever). With software RAID, even if it's on a "RAID-capable" controller, Linux "sees" the individual drives and then builds its own separate RAID device (/dev/md# or something in /dev/mapper).

---

### Post by Skaperen on 2010-10-02
MBR "practically" tops out at 2 TiB (minus 1 sector).  However, it can be stretched to 4 TiB (minus 2 sectors) if you have a cooperative partitioning tool.  The 2 TiB limit applies to the starting sector and the size.  So a partition beginning at sector 4294967295 and having a size of 4294967295 sectors could be done.  It's just not very flexible.  But you might want to note this for your "bag of tricks" just in case it can be used somewhere.

---

### Post by srs5694 on 2010-10-02
> **Skaperen said:**
> MBR "practically" tops out at 2 TiB (minus 1 sector).  However, it can be stretched to 4 TiB (minus 2 sectors) if you have a cooperative partitioning tool.  The 2 TiB limit applies to the starting sector and the size.  So a partition beginning at sector 4294967295 and having a size of 4294967295 sectors could be done.  It's just not very flexible.  But you might want to note this for your "bag of tricks" just in case it can be used somewhere.

This is basically true; however, to the best of my knowledge, every OS that handles such configurations correctly can also handle GPT. See [this page,](http://nessus.rodsbooks.com/gdisk/workarounds.html) where I provide details. (Older MBR-only OSes tend to flake out with such configurations, perhaps because of 32-bit sector pointers in the OS code itself.) One caveat: I haven't tested Windows Vista or 7 in this way. If they could handle such setups, it's conceivable that this trick would be useful with them on a boot disk, since they can't boot from GPT on BIOS-based systems. (They can handle GPT on non-boot disks, though.)

---

