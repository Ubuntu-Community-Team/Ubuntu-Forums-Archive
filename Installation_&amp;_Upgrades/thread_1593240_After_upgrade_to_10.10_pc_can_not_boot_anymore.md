---
title: "After upgrade to 10.10 pc can not boot anymore"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by atahu on 2010-10-11
Hi,

I updated from 10.04 to 10.10, but during the installation there were several errors and finally after reboot ubuntu can not boot anymore. How can I solve this problem?

---

### Post by lechien73 on 2010-10-11
Could you provide more detail, please?

For example - can you remember any of the errors reported during the upgrade? When Ubuntu fails to boot, does it do so with an error? What hardware are you using? Can you successfully boot in with a Live CD and see your data?

---

### Post by Rubi1200 on 2010-10-11
We also need to know if this is a Wubi install; very important.

Thanks.

---

### Post by atahu on 2010-10-11
During upgrade the desktop panel crashed and there was a message that some packages couldnt be installed, but that the installation was completed. Nevertheless I couldnt run down the computer normally because there wasnt any desktop menu.

I have installed ubuntu from an alternate cd. I dont think that it was wubi.

---

### Post by chipbennett on 2010-10-11
> **atahu said:**
> During upgrade the desktop panel crashed and there was a message that some packages couldnt be installed, but that the installation was completed. Nevertheless I couldnt run down the computer normally because there wasnt any desktop menu.

I have installed ubuntu from an alternate cd. I dont think that it was wubi.

I had the same experience (Kubuntu 10.04 dist-upgrade to 10.10). I cannot recall what the packages were that failed to download. I will report back the exact boot error messages later this evening. (I am getting dumped into some sort of - GRUB, I think - recovery console.)

---

### Post by Rubi1200 on 2010-10-11
Hi atahu,
please use the LiveCD to boot the computer and post the results of the boot-script linked at the bottom of my post.

It will give us a better overview of your setup and make offering solutions easier.

Thanks.

---

### Post by atahu on 2010-10-11
Hi,

I get this:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unbekannter Dateisystemtyp „“

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x0007ae7f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   470,255,615   470,253,568  83 Linux
/dev/sda2         470,257,662   488,396,799    18,139,138   5 Extended
/dev/sda5         470,257,664   488,396,799    18,139,136  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Platte /dev/sdb: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x20caebab

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   470,254,679   470,254,617  83 Linux
/dev/sdb2         470,254,680   488,392,064    18,137,385   5 Extended
/dev/sdb5         470,254,743   488,392,064    18,137,322  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Platte /dev/sdc: 8019 MByte, 8019509248 Byte
175 Köpfe, 32 Sektoren/Spuren, 2796 Zylinder, zusammen 15663104 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x00021e92

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32    15,663,103    15,663,072   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        58aa7f24-a3af-4dff-bb97-f0fbbf7a752a   ext4                                     
/dev/sdb1        e83e369a-2aff-4d6a-968c-505fa289e096   ext3                                     
/dev/sdb5        dae1b2af-3ceb-4bf1-b8a1-785d10331caa   swap                                     
/dev/sdc1        4D9F-8AE9                              vfat       UDISK                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /win                     ext4       (rw)
/dev/sdc1        /media/UDISK             vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58aa7f24-a3af-4dff-bb97-f0fbbf7a752a
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

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=58aa7f24-a3af-4dff-bb97-f0fbbf7a752a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=bf8b9ffb-227f-4bf1-a214-773c20210948 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sda1: Location of files loaded by Grub: ===================


 131.1GB: boot/grub/core.img
 149.6GB: boot/grub/grub.cfg
 131.2GB: boot/initrd.img-2.6.32-21-generic
 131.2GB: boot/initrd.img-2.6.32-22-generic
 131.2GB: boot/initrd.img-2.6.32-23-generic
 154.2GB: boot/initrd.img-2.6.32-24-generic
 151.7GB: boot/initrd.img-2.6.32-25-generic
 131.1GB: boot/vmlinuz-2.6.32-21-generic
 131.1GB: boot/vmlinuz-2.6.32-22-generic
 131.1GB: boot/vmlinuz-2.6.32-23-generic
 131.3GB: boot/vmlinuz-2.6.32-24-generic
 131.3GB: boot/vmlinuz-2.6.32-25-generic
 131.3GB: boot/vmlinuz-2.6.35-22-generic
 151.7GB: initrd.img
 154.2GB: initrd.img.old
 131.3GB: vmlinuz
 131.3GB: vmlinuz.old

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=e83e369a-2aff-4d6a-968c-505fa289e096 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=dae1b2af-3ceb-4bf1-b8a1-785d10331caa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4b 0f 2c ff 00 cc 1a e6  d7 b5 bf c6 b2 7b dc 4d  |K.,..........{.M|
00000010  27 f7 41 9f 8e 99 aa 72  dd 8a bb 15 76 2a ec 55  |'.A....r....v*.U|
00000020  d8 ab b1 57 62 ae c5 5d  8a bb 15 76 2a ec 55 d8  |...Wb..]...v*.U.|
00000030  ab b1 57 62 ae c5 5d 8a  bb 15 40 eb 1f f1 ca be  |..Wb..]...@.....|
00000040  ef fe 8f 2e df ec 0e 59  8f ea 1e f6 bc 9f 4b 1c  |.......Y......K.|
00000050  45 3e 98 62 68 78 ed 4d  bb 66 ce ec d3 83 1a ad  |E>.bhx.M.f......|
00000060  9b 70 dc 6a c4 97 3b 90  36 3f ec 86 20 fa a8 2d  |.p.j..;.6?.. ..-|
00000070  0e a5 4e 84 6d 4f bb 2e  41 14 ef 02 76 ae df 76  |..N.mO..A...v..v|
00000080  28 76 2a e3 b0 26 86 83  73 4c 55 db 7d 15 a5 7b  |(v*..&..sLU.}..{|
00000090  57 15 70 dc 54 74 f1 c6  d2 ea e1 43 b0 2b b1 57  |W.p.Tt.....C.+.W|
000000a0  ff d1 f5 ff 00 e4 c7 fe  4b 0f 2c ff 00 cc 1a e6  |........K.,.....|
000000b0  d7 b5 bf c6 b2 7b dc 4d  27 f7 41 9f 8e 99 aa 72  |.....{.M'.A....r|
000000c0  dd 8a bb 15 76 2a ec 55  d8 ab b1 57 62 ae c5 5d  |....v*.U...Wb..]|
000000d0  8a bb 15 76 2a ec 55 d8  ab b1 57 62 ae c5 5d 8a  |...v*.U...Wb..].|
000000e0  bb 15 40 eb 1f f1 ca be  af fc b3 cb ff 00 10 39  |..@............9|
000000f0  38 7d 41 ab 2f d2 58 d3  4a 62 87 d5 61 cc 22 57  |8}A./.X.Jb..a."W|
00000100  80 eb d3 36 ae 04 18 a6  a1 e7 4b a8 d1 13 4a d0  |...6......K...J.|
00000110  af 35 2b b0 4b 49 6c 15  22 58 e3 24 85 6e 7d c1  |.5+.KIl."X.$.n}.|
00000120  23 6c 94 04 49 a2 68 77  b5 64 99 8f 21 65 0d 6d  |#l..I.hw.d..!e.m|
00000130  e7 2f 35 4c de 9b 79 32  f5 0f 50 4b c7 bf 8e 5f  |./5L..y2..PK..._|
00000140  2c 58 07 f1 82 e3 0c f9  64 7e 92 9b f9 53 cd 03  |,X......d~...S..|
00000150  cc f0 ea 05 ac 64 b0 bb  d3 2e da c6 f2 de 7a 54  |.....d........zT|
00000160  48 05 76 23 63 94 4b 84  7d 25 cd 8c ec 6e 11 fa  |H.v#c.K.}%...n..|
00000170  66 b1 a4 6b b6 bf 5b d1  6f 62 be b3 59 24 80 cf  |f..k..[.ob..Y$..|
00000180  0b 72 5f 56 06 31 c8 95  f1 56 04 1c 23 6e 6c 8a  |.r_V.1...V..#nl.|
00000190  ad fe a3 61 a5 59 cb 7f  a8 cc 90 db 40 86 47 91  |...a.Y......@.G.|
000001a0  88 a8 40 40 34 1d f9 12  aa 3d f2 32 42 09 fc d5  |..@@4....=.2B...|
000001b0  a2 45 62 d7 f7 52 9b 50  b6 c6 f0 c1 3a 18 00 fe  |.Eb..R.P....:...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 14 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Rubi1200 on 2010-10-11
The first thing that sticks out is that your swap partition on sda5 is not being mounted.

The other thing we need to know is did you remove GRUB from the 9.04 install so as to use GRUB2 in 10.04 for booting?

The first thing I would try is to edit the fstab file from the LiveCD and make sure the UUID is still correct (can be checked in GParted) and change the file if needs be. Save and reboot to see if it makes a difference.

---

### Post by atahu on 2010-10-11
I am using the live cd now. I dont know if I removed grub2 for mounting.

How would you edit the fstab?

---

### Post by Rubi1200 on 2010-10-11
> **atahu said:**
> I am using the live cd now. I dont know if I removed grub2 for mounting.

How would you edit the fstab?
But you were able to boot sdb and Ubuntu 9.04 before this happened right?

From the LiveCD, open GParted and right-click on the swap partition sda5 > Information will give you the UUID.

Then, mount the file-system on sda Places > drive and navigate to /etc/fstab.

Open the file and check if the UUID matches with what you saw in GParted. If no, change it and save the file. Reboot and let's see what happens.

There are other options, but let's try this first.

---

### Post by Noraphalem on 2010-10-11
Type into the terminal (recovery console):

sudo nano /etc/fstab

Ctrl + O: Save
Ctrl + X: Exit

---

### Post by oldfred on 2010-10-11
Your first boot entry is also missing its last line which should be something like this from my RC version:

initrd    /boot/initrd.img-2.6.35-22-generic

From liveCD not sure if you need sudo but you can edit fstab with 
gksudo gedit 

file will probably be /media/etc/fstab but you can use Nautilus to drill down and control L will change the path to a line you can copy to the terminal.

I think you should chroot into your system from liveCD and run updates.

Good example of chroot and grub reinstall by drs305
[http://ubuntuforums.org/showthread.php?t=1573100](http://ubuntuforums.org/showthread.php?t=1573100)

kansasnoob oneline chroot ------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

kansasnoob's change sda5 to correct partition (needs change if separate /boot)
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Commands once in chroot:
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub

sudo dpkg-reconfigure grub-pc

---

### Post by atahu on 2010-10-11
I get a message that the file  /var/lib/dpkg/status is wrong, I have to remove a sign, but when I try to do it with gedit I get this: gedit /var/lib/dpkg/status
No protocol specified

---

### Post by atahu on 2010-10-11
I can open the file with nano: this is the wrong package: and something with depends is wrong: but what should I change here?
Package: librecode0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 1308
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: recode
Version: 3.6-17
Depends: libc6 (>= ^R.7)

---

### Post by Rubi1200 on 2010-10-11
Are you still in the chroot environment that oldfred posted about before?

If yes, try running ```
sudo dpkg --configure -a
``` in the terminal and report any errors.

---

