---
title: "Live CD installed, no bootloader screen"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by Mr. Crumb on 2011-02-27
Hello, 

I've been a casual Ubuntu user for a little over a year via Wubi. Wubi stopped working for me, failing to load Ubuntu, and instead giving me some console message about BusyBox 1.13.3 dropping into a shell. I poked around, and found posts by other wubi uses having a similar issue, and that a frequent recommendation was to install Ubuntu via Live CD; so I uninstalled Ubuntu from WindowsXP, made a LiveCD, and installed it. 

I got to a point in the Live CD install where it wanted me to reboot. Instead I got a screen full of I/O errors, corresponding to a drv0 sector, or some such. I ended up using the reset button on the box. I was AFK during the reboot, so I don't know if a bootloader screen ever came up, but now it just loads WinXp with no choice to boot Ubuntu.

From WinXp I can see the Live CD was successful in creating it's own partition (as WinXp has gone from 80 to 50GB as planned). Windows seems to be fine, though

Can anyone help me with the proper way of figuring what's wrong (before I make it worse :P )

---

### Post by Mr. Crumb on 2011-02-27
System specs attached:

---

### Post by wilee-nilee on 2011-02-27
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will tell us what is where.

---

### Post by Mr. Crumb on 2011-02-27
Thanks for the reply :) 

boot info script results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,397,167   488,397,105   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    99,169,404    99,169,342   7 HPFS/NTFS
/dev/sdb2          99,170,302   156,301,311    57,131,010   5 Extended
/dev/sdb5          99,170,304   153,851,903    54,681,600  83 Linux
/dev/sdb6         153,853,952   156,301,311     2,447,360  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8054 MB, 8054636032 bytes
8 heads, 32 sectors/track, 61451 cylinders, total 15731711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32    15,731,710    15,731,679   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3E58295C58291465                       ntfs       DRV2_VOL1                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8440AB0A40AB0252                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f514b1f6-d99c-48a1-bc78-66429be03943   ext4                                     
/dev/sdb6        de11abf1-4f1c-4153-928d-e9b3501243f9   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        74A8-0353                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set f514b1f6-d99c-48a1-bc78-66429be03943
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set f514b1f6-d99c-48a1-bc78-66429be03943
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
    search --no-floppy --fs-uuid --set f514b1f6-d99c-48a1-bc78-66429be03943
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f514b1f6-d99c-48a1-bc78-66429be03943 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set f514b1f6-d99c-48a1-bc78-66429be03943
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f514b1f6-d99c-48a1-bc78-66429be03943 ro single 
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
    search --no-floppy --fs-uuid --set f514b1f6-d99c-48a1-bc78-66429be03943
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set f514b1f6-d99c-48a1-bc78-66429be03943
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8440ab0a40ab0252
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
UUID=f514b1f6-d99c-48a1-bc78-66429be03943 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=de11abf1-4f1c-4153-928d-e9b3501243f9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  59.5GB: boot/grub/core.img
  57.3GB: boot/grub/grub.cfg
  51.6GB: boot/initrd.img-2.6.35-22-generic
  59.5GB: boot/vmlinuz-2.6.35-22-generic
  51.6GB: initrd.img
  59.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  03 40 00 80 e9 38 02 00  00 8b 08 8d 55 14 52 68  |.@...8......U.Rh|
00000010  38 a1 b9 00 50 ff 51 10  85 c0 79 07 8b f8 e9 1e  |8...P.Q...y.....|
00000020  02 00 00 8b 45 fc 39 5d  14 8b 08 74 08 6a 01 50  |....E.9]...t.j.P|
00000030  ff 51 60 eb e7 50 ff 51  58 eb e1 68 14 9a b9 00  |.Q`..P.QX..h....|
00000040  ff 75 0c e8 4a ad 28 00  59 85 c0 59 75 44 8b 45  |.u..J.(.Y..YuD.E|
00000050  10 3b c3 74 aa 8b 08 8d  55 ec 52 68 38 a1 b9 00  |.;.t....U.Rh8...|
00000060  50 ff 51 10 85 c0 78 b4  8b 45 fc 8d 55 10 52 50  |P.Q...x..E..U.RP|
00000070  8b 08 ff 51 24 39 5d ec  74 06 83 4d 10 08 eb 04  |...Q$9].t..M....|
00000080  83 65 10 f7 8b 45 fc ff  75 10 8b 08 50 ff 51 28  |.e...E..u...P.Q(|
00000090  eb 8a 68 3c 9a b9 00 ff  75 0c e8 f3 ac 28 00 59  |..h<....u....(.Y|
000000a0  85 c0 59 75 59 39 5d 10  0f 84 51 ff ff ff 68 ac  |..YuY9]...Q...h.|
000000b0  0c b2 00 8d 4d 0c ff 75  14 89 5d 0c ff d7 39 5d  |....M..u..]...9]|
000000c0  0c 75 08 8d 4d 0c e9 3c  01 00 00 8b 45 10 8d 55  |.u..M..<....E..U|
000000d0  e8 52 68 38 a1 b9 00 8b  08 50 ff 51 10 8b f8 85  |.Rh8.....P.Q....|
000000e0  ff 78 11 8b 45 0c ff 75  e8 8b 08 50 ff 91 d0 00  |.x..E..u...P....|
000000f0  00 00 8b f8 8d 4d 0c ff  d6 e9 43 01 00 00 68 e8  |.....M....C...h.|
00000100  99 b9 00 ff 75 0c e8 87  ac 28 00 59 85 c0 59 75  |....u....(.Y..Yu|
00000110  5c 39 5d 10 0f 84 e5 fe  ff ff 68 ac 0c b2 00 8d  |\9].......h.....|
00000120  4d f8 ff 75 14 89 5d f8  ff d7 39 5d f8 75 08 8d  |M..u..]...9].u..|
00000130  4d f8 e9 d0 00 00 00 8b  45 10 8d 55 e4 52 68 38  |M.......E..U.Rh8|
00000140  a1 b9 00 8b 08 50 ff 51  10 8b f8 85 ff 79 05 8d  |.....P.Q.....y..|
00000150  4d f8 eb a3 8b 45 f8 33  d2 39 5d e4 8b 08 0f 94  |M....E.3.9].....|
00000160  c2 52 50 ff 91 f0 00 00  00 8b f8 eb e2 68 b4 99  |.RP..........h..|
00000170  b9 00 ff 75 0c e8 18 ac  28 00 59 85 c0 59 75 53  |...u....(.Y..YuS|
00000180  39 5d 10 0f 84 76 fe ff  ff 68 9c 0c b2 00 8d 4d  |9]...v...h.....M|
00000190  f4 ff 75 14 89 5d f4 ff  d7 39 5d f4 75 05 8d 4d  |..u..]...9].u..M|
000001a0  f4 eb 64 8b 45 10 8d 55  e0 52 68 38 a1 b9 00 8b  |..d.E..U.Rh8....|
000001b0  08 50 ff 51 10 8b f8 85  ff 79 08 8d 4d f4 00 fe  |.P.Q.....y..M...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 42 03 00 fe  |...........`B...|
000001d0  ff ff 05 fe ff ff 02 60  42 03 00 60 25 00 00 00  |.......`B..`%...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2011-02-27
So the Hd where both XP and Ubuntu are=sdb has no bootloader it was put in sda no big deal. So make sure the sdb Hd is the first read in the bios then boot the Maverick live cd and run these two commands.
```
sudo mount /dev/sdb5 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sdb
```
Reboot to the grub menu choose the Ubuntu install once in in a terminal run.
```
sudo update-grub
```

These commands are from this link, defaulting to them.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Mr. Crumb on 2011-02-27
Thanks, I will reboot shortly having run the commands you suggested. 

It printed some errors, so I thought I'd post term window before prodceding:
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sdb
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
ubuntu@ubuntu:~$ 

```

---

### Post by Mr. Crumb on 2011-02-27
> **wilee-nilee said:**
> So the Hd where both XP and Ubuntu are=sdb has no bootloader it was put in sda no big deal. So make sure the sdb Hd is the first read in the bios then boot the Maverick live cd and run these two commands.
```
sudo mount /dev/sdb5 /mnt
```then
```
sudo grub-install --root-directory=/mnt /dev/sdb
```Reboot to the grub menu choose the Ubuntu install once in in a terminal run.
```
sudo update-grub
```These commands are from this link, defaulting to them.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

Great! I can boot either OS without issue (though Ubuntu is now the default OS to load...)

Thanks for the help :D I'll [s]mark[/s] consider this [s]as[/s] Solved, though if anyone has any comment on the warnings from installing grub you might put my mind to ease on the "future problems" part of that.

---

### Post by wilee-nilee on 2011-02-27
The flexnet warnings are regarding proprietary MS used programs like Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others, grub has a way around that as of now.

---

