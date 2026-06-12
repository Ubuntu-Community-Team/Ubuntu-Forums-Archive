---
title: "Windows XP won't boot after Ubuntu upgrade"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by xanderwhite on 2010-05-09
I've been using Ubuntu for a few years now, on and off (still using WinXp for the likes of photoshop and some work stuff) And this is my first foray into this forum, as so far I've easily found all the answers to my questions! (Thanks to everyone of you!)

Anyway, I just upgraded  to 10.04 and now all I'm getting is a flashing cursor when I try to boot Windows in Grub.
I can load the Windows partition in linux no probs so I know it's all ok, although I'm going to backup before I try anything risky!

Anyway I've had a look around and can see people who've had the same prob but only really with Windows Vista and 7. So... just trying to figure if there's anyway of getting grub to load WindowsXP properly!?

I've run boot_info_script055.sh which was recommended for one of the Win7 answers and posted the output below.

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 404645842 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: ___________________________________________________ => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
______________________

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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   404,372,114   404,372,052   7 HPFS/NTFS
/dev/sda2         404,372,176   488,279,609    83,907,434   5 Extended
/dev/sda5         404,372,178   484,745,309    80,373,132  83 Linux
/dev/sda6         484,745,373   488,279,609     3,534,237  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C6A828D3A828C3B1                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7fae00f1-129f-4419-a78b-0157f302f4fe   ext4                                     
/dev/sda6        afd445b0-ff31-43e5-9c63-d7341a4561a5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2CC0D12BC0D0FBD0                       ntfs       1TB                           
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/1TB               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 7fae00f1-129f-4419-a78b-0157f302f4fe
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
search --no-floppy --fs-uuid --set 7fae00f1-129f-4419-a78b-0157f302f4fe
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7fae00f1-129f-4419-a78b-0157f302f4fe
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7fae00f1-129f-4419-a78b-0157f302f4fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7fae00f1-129f-4419-a78b-0157f302f4fe
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7fae00f1-129f-4419-a78b-0157f302f4fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7fae00f1-129f-4419-a78b-0157f302f4fe
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7fae00f1-129f-4419-a78b-0157f302f4fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7fae00f1-129f-4419-a78b-0157f302f4fe
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7fae00f1-129f-4419-a78b-0157f302f4fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7fae00f1-129f-4419-a78b-0157f302f4fe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7fae00f1-129f-4419-a78b-0157f302f4fe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c6a828d3a828c3b1
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
UUID=7fae00f1-129f-4419-a78b-0157f302f4fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=afd445b0-ff31-43e5-9c63-d7341a4561a5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 237.2GB: boot/grub/core.img
 224.7GB: boot/grub/grub.cfg
 237.2GB: boot/initrd.img-2.6.32-21-generic
 237.2GB: boot/initrd.img-2.6.32-22-generic
 237.2GB: boot/vmlinuz-2.6.32-21-generic
 237.2GB: boot/vmlinuz-2.6.32-22-generic
 237.2GB: initrd.img
 237.2GB: initrd.img.old
 237.2GB: vmlinuz
 237.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  00 14 c3 21 01 00 7d 00  00 54 68 72 65 61 64 69  |...!..}..Threadi|
00000010  00 6e 67 4d 6f 64 65 6c  20 aa 00 c1 2b 41 20 3c  |.ngModel ...+A <|
00000020  61 e0 11 74 e0 11 fa 65  e0 0d 74 60 06 ff 37 00  |a..t...e..t`..7.|
00000030  0c 40 00 e1 33 d8 68 0d  23 ee 24 c1 0e 4e 80 00  |.@..3.h.#.$..N..|
00000040  e1 03 02 07 e0 00 54 79  70 65 4c 69 08 62 00 f0  |......TypeLi.b..|
00000050  60 06 6c 68 01 00 00 28  18 23 02 b0 94 4c 6e 25  |`.lh...(.#...Ln%|
00000060  e5 25 32 60 04 18 19 e5  25 85 86 01 e1 0f 7b 00  |.%2`....%.....{.|
00000070  36 00 44 00 31 00 00 43  00 35 00 39 00 30 15 60  |6.D.1..C.5.9.0.`|
00000080  00 2d 60 01 37 a0 02 45  00 2d 54 00 34 20 02 38  |.-`.7..E.-T.4 .8|
00000090  e0 03 2d e0 02 36 55 60  02 41 60 02 41 a0 02 36  |..-..6U`.A`.A..6|
000000a0  e0 02 45 10 00 33 00 41  20 8e 31 00 38 fc 00 32  |..E..3.A .1.8..2|
000000b0  20 00 00 5a e0 0b e1 51  e5 1a e9 69 d5 f5 52 70  | ..Z...Q...i..Rp|
000000c0  f4 1a 08 60 09 72 60 62  e1 1a 80 56 45 52 53 49  |...`.r`b...VERSI|
000000d0  4f 4e e2 28 53 e1 3e 61  03 60 15 e5 18 00 e2 1d  |ON.(S.>a.`......|
000000e0  31 85 e0 66 30 60 06 18  16 23 02 e1 40 11 e1 10  |1..f0`...#..@...|
000000f0  9c d4 33 e6 4f 10 04 00  66 00 e1 24 40 04 00 98  |..3.O...f..$@...|
00000100  60 04 40 24 ff ed e1 01  38 60 01 e5 79 0a 81 03  |`.@$....8`..y...|
00000110  64 00 e5 62 02 1b e0 01  4f 54 52 65 70 6f 10 72  |d..b....OTRepo.r|
00000120  74 73 2e 63 50 53 74 61  00 6e 64 61 72 64 44 61  |ts.cPSta.ndardDa|
00000130  79 ad e0 1e 41 e6 12 61  06 f8 e6 12 41 ff 68 d7  |y...A..a....A.h.|
00000140  e0 41 f5 7b e1 66 f8 80  14 e0 e0 09 e5 29 bd e9  |.A.{.f.......)..|
00000150  19 70 e0 02 44 15 62 c1  e5 19 18 60 95 af e5 19  |.p..D.b....`....|
00000160  e5 03 e1 00 e1 44 67 e0  c0 05 80 01 c0 43 6c 73  |.....Dg......Cls|
00000170  69 64 68 e3 26 e1 44 c2  40 60 20 5b 8b b8 07 e5  |idh.&.D.@` [....|
00000180  44 61 05 2e c0 60 02 e3  25 e5 44 44 e0 3d 42 00  |Da...`..%.DD.=B.|
00000190  aa 45 e0 44 46 20 44 34  20 41 44 a0 42 56 42 20  |.E.DF D4 AD.BVB |
000001a0  40 e1 44 37 60 02 43 60  02 39 55 e0 01 30 20 45  |@.D7`.C`.9U..0 E|
000001b0  2d e0 00 36 a0 23 36 55  60 6f 34 20 46 37 00 fe  |-..6.#6U`o4 F7..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 8c 65 ca 04 00 fe  |...........e....|
000001d0  ff ff 05 fe ff ff 8e 65  ca 04 dc ed 35 00 00 00  |.......e....5...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




Would appreciate any help in fixing this as I'm rather stuck without the Windows until I can sync my android phone, print to my Hiti printer and run all things in Linux! :)

Anyway thanks in advance for the help.

Alex

---

### Post by darkod on 2010-05-09
It seems somehow apart from being on the MBR of /dev/sda, Grub2 also ended up on your XP partition, /dev/sda1. So from the "good" grub2 on /dev/sda you jump into the "bad" grub2 on /dev/sda1 when selecting XP and it has nowhere to go.

[COLOR=Red]sda1[/COLOR]: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1[/COLOR]  and 
                       looks at sector 404645842 of the same hard drive  for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter  Block.
    Operating System:  [COLOR=Red]Windows XP[/COLOR]
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

Get your XP install cd and repair the boot process (instructions here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)). That should make it boot directly into XP since windows can't see linux partition by default. But don't panic. :)

Boot into live desktop with the 10.04 disc (Try Ubuntu option), and in terminal reinstall grub2 to the MBR:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should sort it out.

---

