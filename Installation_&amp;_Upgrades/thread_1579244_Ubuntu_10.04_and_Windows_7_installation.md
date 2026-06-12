---
title: "Ubuntu 10.04 and Windows 7 installation"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by jamespw on 2010-09-21
Hi guys,

I have a new machine arriving tomorrow and plan on installing ubuntu 10.04 x64 and windows 7 professional. I've only ever had a single HDD before, but now I have 2 * 640GB drives.

Does it matter what OS I install first?
Will I have to change anything relating to the HDDs boot order in the BIOS?
I only got 2 HDDs so in the event of needing to reinstall one of the OS's they're on completely different drives. Also, in the eventuality I need to reinstall one of the OSs is it simply a normal reinstall procedure, or because they're on two seperate drives will I need to do anything different?

Thanks!

---

### Post by oracle2b on 2010-09-21
Install windows 7 fist otherwise it'll overwrite the grub2 bootloader. If you should decide to remove the hard drives at anytime, I think you'll need to repair the windows installation to fix the mbr(This doesn't require re-installation of the whole OS).

---

### Post by jamespw on 2010-09-21
Thanks for the quick reply!
What about if I need to reinstall windows 7? Can this be done without messing up the mbr? Will I just have to do a sudo grub-update ?

---

### Post by wilee-nilee on 2010-09-21
> **jamespw said:**
> Thanks for the quick reply!
What about if I need to reinstall windows 7? Can this be done without messing up the mbr? Will I just have to do a sudo grub-update ?

Reloading the MBR with a MS bootloader or grub is easy, don't worry about it just ask for links or help on the forums.

W7 when installed will take over the MBR, every time just like Ubuntu will.

---

### Post by Mark Phelps on 2010-09-22
IF you want dual-boot and maximum flexibility, consider installing each OS to its own physical drive -- and do so with the other drive disconnected.

After that, connect both drives but boot from the Ubuntu drive, open a terminal, and run "sudo update-grub" -- which will autogenerate a new GRUB menu with an entry for Win7.

This leaves the MBR on your Win7 drive intact, and actually allows you to boot from either drive independent of the other -- should the need arise.

If you're NOT going to follow this route, then once you install Win7, use the Backup feature to create and burn a Win7 Repair CD.  You will likely need that later to repair the Win7 Boot Loader should it become damaged during the dual-boot setup.

---

### Post by apverma13 on 2010-09-23
I have installed ubuntu 10.04LTS along with windows 7. but during startup when i select window 7's entry in grub my computer restarts.

i have tried update-grub but nothing changes.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 1615. But according to the info from fdisk, 
                       sda6 starts at sector 61450240.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             208,894   156,280,319   156,071,426   f W95 Ext d (LBA)
/dev/sda5          20,482,938    61,448,624    40,965,687   b W95 FAT32
/dev/sda6          61,450,240   102,412,287    40,962,048   7 HPFS/NTFS
/dev/sda7         102,414,438   156,280,319    53,865,882   b W95 FAT32
/dev/sda8             208,896    20,482,047    20,273,152  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9468456A68454C64                       ntfs       System Reserved               
/dev/sda2: PTTYPE="dos" 
/dev/sda5        A0C9-1144                              vfat       MOVIES                        
/dev/sda6        58E04887E0486D76                       ntfs                                     
/dev/sda7        0CB3-B441                              vfat       SOFTWARES                     
/dev/sda8        12c1f332-3bd9-4768-adf0-50dde0df15fc   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /media/SOFTWARES         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
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
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=12c1f332-3bd9-4768-adf0-50dde0df15fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=12c1f332-3bd9-4768-adf0-50dde0df15fc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9468456a68454c64
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda8       /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


   7.1GB: boot/grub/core.img
   7.1GB: boot/grub/grub.cfg
   7.9GB: boot/initrd.img-2.6.32-21-generic
   7.7GB: boot/vmlinuz-2.6.32-21-generic
   7.9GB: initrd.img
   7.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  31 a2 35 85 f6 bc 50 88  fa 7f 50 db 4a 10 83 a6  |1.5...P...P.J...|
00000010  24 ea 02 65 7c 7c 7d 1e  2d 2f da db cc 3c b3 17  |$..e||}.-/...<..|
00000020  39 1c 9a 4e 43 96 ac 8a  f6 48 7d e9 30 c8 9a e0  |9..NC....H}.0...|
00000030  4d 27 d1 60 93 11 c9 18  78 4f 30 66 a6 49 70 d3  |M'.`....xO0f.Ip.|
00000040  c4 40 6e 59 bb 9e ba 5a  f0 13 be ae 8b 4d d9 38  |.@nY...Z.....M.8|
00000050  47 13 45 a1 b0 6b 79 13  f1 a5 85 58 ca 86 07 51  |G.E..ky....X...Q|
00000060  77 7d 9b 27 0b b2 ed 1a  e0 c1 fc 15 f1 8e ef 15  |w}.'............|
00000070  8c c3 48 44 ab 27 26 6c  bd 6a 9e 91 22 67 f9 34  |..HD.'&l.j.."g.4|
00000080  42 a3 25 ed e7 d5 f5 0d  ad 80 e0 c7 36 c6 cf 60  |B.%.........6..`|
00000090  c5 3e 4b dd be c1 8d c7  d6 f4 45 7c ae 1a 14 dc  |.>K.......E|....|
000000a0  41 f4 05 d9 70 63 a3 e3  1c f1 9f 75 35 f7 43 d9  |A...pc.....u5.C.|
000000b0  b7 7d 20 1b 75 1a 7a 34  b1 a5 ae e3 0d 7d 87 d7  |.} .u.z4.....}..|
000000c0  2b fd 3f 7b af d4 53 11  96 1c 42 37 56 9e 9c 5f  |+.?{..S...B7V.._|
000000d0  65 31 0e 16 3e 55 9f d6  21 3d 6b 72 52 40 53 06  |e1..>U..!=krR@S.|
000000e0  5e 9c c6 d1 04 82 5c 91  89 97 af 81 20 d2 cd 77  |^.....\..... ..w|
000000f0  33 21 71 3d 8d 6d 8c 15  6f 2d 9a 79 bb 94 92 50  |3!q=.m..o-.y...P|
00000100  8f 2f 9e 77 22 d1 9e 5b  fa 59 ed 92 d4 2e ec 9b  |./.w"..[.Y......|
00000110  88 bc 9e 08 e8 d5 e8 c2  5d 6e 76 c6 77 cb 9c b7  |........]nv.w...|
00000120  ac 11 6f a3 34 47 9d 80  ca af fb 4a e9 d7 c3 ce  |..o.4G.....J....|
00000130  e1 09 55 7c a0 77 72 8a  82 2e 1c 73 39 8d 29 26  |..U|.wr....s9.)&|
00000140  dd a1 51 8e 08 f8 31 be  95 fe 07 41 ad 58 56 1f  |..Q...1....A.XV.|
00000150  59 1f 8a de 04 71 d5 ff  50 c3 8a 91 f3 60 b7 74  |Y....q..P....`.t|
00000160  23 e5 e9 76 a6 5b b7 49  4a 18 10 07 f7 6c 8f 3e  |#..v.[.IJ....l.>|
00000170  65 3d 2b 74 84 66 08 65  41 83 6f 4a 51 65 c4 e9  |e=+t.f.eA.oJQe..|
00000180  cf 65 ec 99 df e5 93 c3  a8 f6 c4 f0 ac 9d 46 f6  |.e............F.|
00000190  4a 74 db eb 43 a0 2a dd  07 8d 3d d9 91 06 2c 68  |Jt..C.*...=...,h|
000001a0  53 cc 2f ba cb 34 5c 96  c7 97 ef d4 23 16 af c3  |S./..4\.....#...|
000001b0  4b e6 5a d9 26 92 4e 6c  6b 46 6b 63 eb 85 00 df  |K.Z.&.NlkFkc....|
000001c0  d3 ff 0b df d3 ff 7c 5b  35 01 37 16 71 02 00 df  |......|[5.7.q...|
000001d0  d3 ff 05 df d3 ff b3 71  a6 03 4f 0e 71 02 00 00  |.......q..O.q...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```help me out please

---

### Post by wilee-nilee on 2010-09-23
sda1:   Boot files/dirs:   /bootmgr /Boot/BCD /**grldr**

Probably the the culprit. This is grub4dos, we don't see  much of this, hopefully somebody who knows will respond.

Really you should start your own thread, you might get a better response.;)

---

### Post by jamespw on 2010-09-23
I installed win7 then ubuntu as intended, on separate drives, but ran into problems with the win7 boot loader. I tried repairing but had no joy, so I decided to admit defeat and just dual boot from the one HDD. I don't really have the time to mess around with it now as I need a working environment for development.

I shall try Mark Phelps' idea when I have time, although I'm not even sure how to selectively boot a specific hard drive on this new machine. The motherboard boot menu just gives me "hard drive". I knew where I was with IDE, but SATA...

---

