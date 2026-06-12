---
title: "Grub 2 missing in action"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by gearard on 2011-02-13
After a hard drive failure I installed Ubuntu 10.04 LTS in the secondary drive. The intention was to have keep the machine functional until I could reinstall XP and have a dual boot. I replaced the failing drive and reinstalled XP. The main reason for keeping windows is for using Itunes and a ton of music on the Ipod. I can get into the Ubuntu using Super Grub2 and did try repairing Grub 2 with rescutux. I can of course use the super grub2 disk to boot into Ubuntu but would like to repair Grub2 so I have the choice at boot without the disk. Here is the readout from the boot info script.

                  ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

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

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   268,414,019   227,448,270   f W95 Ext d (LBA)
/dev/sda5          40,965,813    61,448,624    20,482,812   7 HPFS/NTFS
/dev/sda6          61,448,688   102,414,374    40,965,687   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   184,426,199   184,426,137   7 HPFS/NTFS
/dev/sdb2         197,021,160   201,181,994     4,160,835  82 Linux swap / Solaris
/dev/sdb3         184,458,330   197,021,159    12,562,830  83 Linux
/dev/sdb4         201,294,448   283,723,964    82,429,517   5 Extended
/dev/sdb5         201,294,450   283,723,964    82,429,515  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142447 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204885504 bytes
1 heads, 63 sectors/track, 31008335 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,127 1,953,520,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C694C89894C88BFD                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2ECC7DF6CC7DB8A3                       ntfs                                     
/dev/sda6        06586026586016A9                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2C3802E63802AEC0                       ntfs       DRV2_VOL1                     
/dev/sdb2        2fff82ea-9fe5-47ea-afa3-dd892d43957e   swap                                     
/dev/sdb3        a8f6046f-aff5-40cd-a791-b853a0a9894e   ext3                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        86d520af-03fe-4aab-9f2c-07d11fc442b8   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B0908BE7908BB280                       ntfs       SimpleDrive                   
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        A26CCFB76CCF850F                       ntfs       FreeAgent GoFlex Drive        
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext3       (rw,errors=remount-ro)
/dev/sdb5        /home                    ext3       (rw)
/dev/sdc1        /media/SimpleDrive       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/FreeAgent GoFlex Drive fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 0 /NoExecute=OptIn 

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=a8f6046f-aff5-40cd-a791-b853a0a9894e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=a8f6046f-aff5-40cd-a791-b853a0a9894e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=a8f6046f-aff5-40cd-a791-b853a0a9894e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=a8f6046f-aff5-40cd-a791-b853a0a9894e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=a8f6046f-aff5-40cd-a791-b853a0a9894e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=a8f6046f-aff5-40cd-a791-b853a0a9894e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a8f6046f-aff5-40cd-a791-b853a0a9894e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a8f6046f-aff5-40cd-a791-b853a0a9894e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set a8f6046f-aff5-40cd-a791-b853a0a9894e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c694c89894c88bfd
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=a8f6046f-aff5-40cd-a791-b853a0a9894e /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=86d520af-03fe-4aab-9f2c-07d11fc442b8 /home           ext3    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=2fff82ea-9fe5-47ea-afa3-dd892d43957e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


  97.7GB: boot/grub/core.img
  97.8GB: boot/grub/grub.cfg
  97.7GB: boot/initrd.img-2.6.32-24-generic
  97.8GB: boot/initrd.img-2.6.32-25-generic
  97.8GB: boot/initrd.img-2.6.32-26-generic
  97.7GB: boot/initrd.img-2.6.32-27-generic
  97.7GB: boot/vmlinuz-2.6.32-24-generic
  97.8GB: boot/vmlinuz-2.6.32-25-generic
  97.8GB: boot/vmlinuz-2.6.32-26-generic
  97.7GB: boot/vmlinuz-2.6.32-27-generic
  97.7GB: initrd.img
  97.8GB: initrd.img.old
  97.7GB: vmlinuz
  97.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  e0 78 08 12 00 00 00 01  |.........x......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 99 1e fe 0a 00 fe  |......?.........|
000001d0  ff ff 82 fe ff ff e8 4d  be 0b 43 7d 3f 00 00 fe  |.......M..C}?...|
000001e0  ff ff 83 fe ff ff 5a 9c  fe 0a 8e b1 bf 00 00 fe  |......Z.........|
000001f0  ff ff 05 fe ff ff 70 82  ff 0b 4d c6 e9 04 55 aa  |......p...M...U.|
00000200

Unknown BootLoader  on sda2

00000000  ff 00 00 ff 10 ff ff ff  00 00 00 00 0d 00 00 00  |................|
00000010  05 00 00 00 05 00 00 00  00 00 00 00 01 01 00 00  |................|
00000020  01 00 00 00 01 00 00 00  88 58 45 01 1c a4 c7 2a  |.........XE....*|
00000030  00 00 00 00 01 00 00 00  f0 b3 c7 2a 0c 00 00 00  |...........*....|
00000040  0d 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 24 a4 c7 2a  00 00 00 00 01 00 00 00  |....$..*........|
00000070  28 a4 c7 2a 00 00 00 00  01 00 00 00 00 40 00 00  |(..*.........@..|
00000080  1d 92 f2 ff 10 ff ff ff  00 00 00 00 0d 00 00 00  |................|
00000090  05 00 00 00 05 00 00 00  00 00 00 00 01 00 00 00  |................|
000000a0  01 00 00 00 00 00 00 00  88 58 45 01 30 a4 c7 2a  |.........XE.0..*|
000000b0  00 00 00 00 01 00 00 00  10 b4 c7 2a 0c 00 00 00  |...........*....|
000000c0  0d 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 38 a4 c7 2a  00 00 00 00 01 00 00 00  |....8..*........|
000000f0  3c a4 c7 2a 00 00 00 00  01 00 00 00 00 40 00 00  |<..*.........@..|
00000100  4e 95 99 ff 10 ff ff ff  00 00 00 00 0d 00 00 00  |N...............|
00000110  05 00 00 00 05 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  01 00 00 00 01 01 00 00  88 58 45 01 44 a4 c7 2a  |.........XE.D..*|
00000130  00 00 00 00 01 00 00 00  30 b4 c7 2a 0c 00 00 00  |........0..*....|
00000140  0d 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 4c a4 c7 2a  00 00 00 00 01 00 00 00  |....L..*........|
00000170  50 a4 c7 2a 00 00 00 00  01 00 00 00 00 40 00 00  |P..*.........@..|
00000180  46 92 99 ff 10 ff ff ff  00 00 00 00 0d 00 00 00  |F...............|
00000190  05 00 00 00 05 00 00 00  00 00 00 00 01 01 00 00  |................|
000001a0  00 a0 17 21 01 00 00 00  01 00 00 00 00 00 00 00  |...!............|
000001b0  00 00 00 00 01 01 00 00  00 b0 17 21 01 00 00 01  |...........!....|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 fc 8a 38 01 00 00  |......?.....8...|
000001d0  c1 ff 05 fe ff ff 3b 8b  38 01 76 16 71 02 00 00  |......;.8.v.q...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2011-02-13
Put the sdb HD first to be read in the bios. Load grub2 to its mbr from a booted live Ubuntu cd, here is the link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Ask any questions if your unsure, it is just three commands.

---

### Post by gearard on 2011-02-13
Okay that is done. I was going through the motions but did not have the correct partition mounted. After Grub was reinstalled then I noticed I never changed the drive sequence in the Bios. Once that was done Grub2 reappeared at start up. Perception is everything.:D Thanks for the help.

---

