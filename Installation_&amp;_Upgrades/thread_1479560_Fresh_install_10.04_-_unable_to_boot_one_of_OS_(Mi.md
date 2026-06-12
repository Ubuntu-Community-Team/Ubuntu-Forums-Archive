---
title: "Fresh install 10.04 - unable to boot one of OS (Mint)"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Danial on 2010-05-10
Hi,

Apologies if this was answered earlier.  Thanks in advance for your attention.  I admit that I am a noob - knows a little which makes it more dangerous than not knowing at all. :(

In brief, I am unable to boot one of the OS out of 3 I have installed. Everything is fresh install on newly formatted partitions.

Here are the details:
[LIST]
[*]Two HDs - one is Sata and second is IDE.
[/LIST]
[LIST]
[*]Win7 installed on IDE (sdb2) then Ubuntu 9.10 on Sata (sda2) and lastly Linux Mint on Sata (sda3).  Everyone was on its place - that is - Ubuntu 9.10 on sda2, Linux-Mint on sda3 and Win7 on sdb2.
[/LIST]  

Future of the day was bright and promising until I upgraded online to 10.04. After that, I was only able to boot to Win7 (IDE drive - sdb2 - not sure if it changed at that point or not) but no nix OS on Sata sda2 & sda3.  
[LIST]
[*]I downloaded 10.04 and installed from CD again on sda2.  Well, now I am able to boot into Win7 and Ubuntu 10.04 but no Linux-Mint.
[/LIST]
Another interesting thing is that sda and sdb have interchanged/swapped.  So now if I chcek it thru gparted or run boot script, Sata drive shows up as sdb and IDE is now sda.  In another post, I read that grub2  does that and make IDE drive as the first drive and Sata drive as second.  Well, I buy that but why I am unable to boot to second OS on the same Sata drive? Evidently, I am missing something and I take that it is mostly user error but please - 

With some guidance, I am sure I can learn something new. Here is the output of the boot_info_script055.sh:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=20e08ddc-06bc-4f21-96ba-92563ad5cb63)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - Main 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb12: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,233,404    10,233,342  82 Linux swap / Solaris
/dev/sda2    *     10,233,405    78,156,224    67,922,820   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    10,120,949    10,120,887  82 Linux swap / Solaris
/dev/sdb2    *     10,120,950    95,185,124    85,064,175  83 Linux
/dev/sdb3          95,185,125   180,249,299    85,064,175  83 Linux
/dev/sdb4         180,249,361   976,768,064   796,518,704   5 Extended
/dev/sdb5         180,249,363   285,716,024   105,466,662  83 Linux
/dev/sdb6         285,716,088   444,293,639   158,577,552  83 Linux
/dev/sdb7         444,293,703   602,871,254   158,577,552  83 Linux
/dev/sdb8         602,871,318   655,435,934    52,564,617  83 Linux
/dev/sdb9         655,435,998   708,000,614    52,564,617  83 Linux
/dev/sdb10        813,467,403   895,109,669    81,642,267  83 Linux
/dev/sdb11        895,109,733   976,768,064    81,658,332  83 Linux
/dev/sdb12        708,000,678   813,467,339   105,466,662   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        d898c458-3a28-4abf-9a28-c34d356c0046   swap       swap                          
/dev/sda2        66B8B439B8B40A17                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb10       ce1aca59-ceda-4aef-8230-eb2996535daf   ext4       Temp                          
/dev/sdb11       3f608fc3-eef3-4dfe-a755-5e83486bb0e5   ext4       Kachra                        
/dev/sdb12       73E1719801BBE72A                       ntfs       Win-apps                      
/dev/sdb1        3a7ce152-9022-42d2-8069-088a8ce8d58d   swap       swap                          
/dev/sdb2        84781de9-0f61-474c-a56e-d6f455826462   ext4                                     
/dev/sdb3        20e08ddc-06bc-4f21-96ba-92563ad5cb63   ext4       mint                          
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        6e000c7f-2221-490e-818d-62a8d5d61578   ext4       Download                      
/dev/sdb6        2c97211d-9eb8-4520-9ea7-c091e58b3a3b   ext4       Ganey                         
/dev/sdb7        846a0dc9-58ba-468d-9e19-1fc5b59715c4   ext4       Tasaveer                      
/dev/sdb8        b8aaa3ec-6996-486a-b9bb-aa3a954ff7c3   ext4       Kaghzat                       
/dev/sdb9        1d3711f4-d1cf-472d-b09b-f90667a033fa   ext4       Linux-doc                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
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
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 66b8b439b8b40a17
	chainloader +1
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda3) (on /dev/sdb3)" {
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 20e08ddc-06bc-4f21-96ba-92563ad5cb63
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=20e08ddc-06bc-4f21-96ba-92563ad5cb63 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode) (on /dev/sdb3)" {
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 20e08ddc-06bc-4f21-96ba-92563ad5cb63
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=20e08ddc-06bc-4f21-96ba-92563ad5cb63 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=84781de9-0f61-474c-a56e-d6f455826462 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=3a7ce152-9022-42d2-8069-088a8ce8d58d none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
UUID=d898c458-3a28-4abf-9a28-c34d356c0046 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  35.4GB: boot/grub/core.img
  46.2GB: boot/grub/grub.cfg
  35.4GB: boot/initrd.img-2.6.32-21-generic
  35.3GB: boot/initrd.img-2.6.32-22-generic
  35.3GB: boot/vmlinuz-2.6.32-21-generic
  35.4GB: boot/vmlinuz-2.6.32-22-generic
  35.3GB: initrd.img
  35.4GB: initrd.img.old
  35.4GB: vmlinuz
  35.3GB: vmlinuz.old

=========================== sdb3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 20e08ddc-06bc-4f21-96ba-92563ad5cb63
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 20e08ddc-06bc-4f21-96ba-92563ad5cb63
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda3)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 20e08ddc-06bc-4f21-96ba-92563ad5cb63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=20e08ddc-06bc-4f21-96ba-92563ad5cb63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 20e08ddc-06bc-4f21-96ba-92563ad5cb63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=20e08ddc-06bc-4f21-96ba-92563ad5cb63 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=20e08ddc-06bc-4f21-96ba-92563ad5cb63 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=3a7ce152-9022-42d2-8069-088a8ce8d58d none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
UUID=d898c458-3a28-4abf-9a28-c34d356c0046 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


  49.1GB: boot/grub/core.img
  49.1GB: boot/grub/grub.cfg
  49.1GB: boot/initrd.img-2.6.31-14-generic
  49.1GB: boot/vmlinuz-2.6.31-14-generic
  49.1GB: initrd.img
  49.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  b6 b6 ff 29 a2 b0 3b f9  ec 05 fa ca 1d 29 7f 7f  |...)..;......)..|
00000010  a7 4f d9 43 ff d6 56 d7  f8 09 6c f9 bb 75 bd c4  |.O.C..V...l..u..|
00000020  17 16 03 a7 f1 72 3c 21  6f b7 fe 91 94 1c 07 f9  |.....r<!o.......|
00000030  5b 1e e9 6b 7d 70 2c c5  e7 b7 9a 5a fc f2 9c f6  |[..k}p,....Z....|
00000040  b7 d6 32 db e7 4f f6 ef  d7 1d 70 21 3c 78 23 d5  |..2..O....p!<x#.|
00000050  ac 1b 56 ed eb 58 26 6b  1b cd 7e 7f 90 5a fd 5b  |..V..X&k..~..Z.[|
00000060  ff 47 8e b1 b8 e8 74 ba  13 c5 f9 67 cb 9e d4 ad  |.G....t....g....|
00000070  e5 0e 22 3f c1 2b 88 99  ed 94 fe f0 49 fb f0 8d  |.."?.+......I...|
00000080  b9 63 c5 58 fe 10 f0 8d  63 26 b8 7c 22 b7 c7 95  |.c.X....c&.|"...|
00000090  b6 df 4d 63 f1 60 32 ff  f2 a1 28 e3 06 b1 82 70  |..Mc.`2...(....p|
000000a0  17 e2 ef c9 6c d6 32 c6  b1 90 ff c2 39 45 22 dd  |....l.2.....9E".|
000000b0  c6 38 9d 2c 56 e8 a7 cd  8c 12 7e 96 d6 ab 81 6d  |.8.,V.....~....m|
000000c0  6b 29 7c b4 9e 24 7e f8  91 42 78 ab 1e 83 94 ac  |k)|..$~..Bx.....|
000000d0  6b 1a df c4 68 34 0a 5f  db 96 c5 36 ec 06 fd 05  |k...h4._...6....|
000000e0  fa 68 a4 21 23 f3 34 9a  af aa 20 03 42 12 84 02  |.h.!#.4... .B...|
000000f0  29 20 09 09 60 12 eb 3b  78 e8 1c c9 17 70 ac 92  |) ..`..;x....p..|
00000100  20 9c 79 e3 d6 0b ac 9f  01 31 00 0f 80 9d 00 03  | .y......1......|
00000110  c0 57 c0 00 5d 3f f8 09  1c 00 3c f5 ff 3d 66 55  |.W..]?....<..=fU|
00000120  65 d3 e5 f0 12 58 00 78  09 4c 00 7c 04 a0 00 5e  |e....X.x.L.|...^|
00000130  02 7c 00 1f 01 25 00 0e  55 cb 88 be 12 bc a5 f5  |.|...%..U.......|
00000140  3e 02 55 00 1f 34 e2 5b  cd 0e 96 71 0a 18 36 d1  |>.U..4.[...q..6.|
00000150  e1 07 4b 7f 27 60 d9 95  59 5a 74 fd 95 b1 c4 6a  |..K.'`..YZt....j|
00000160  c1 37 ae 0f 35 f8 8c e9  f2 fe 23 8c 1b 32 97 ff  |.7..5.....#..2..|
00000170  8b bf 5f af de 03 0b 33  a8 b7 b8 86 a3 c0 42 c0  |.._....3......B.|
00000180  08 8c a1 66 28 78 41 ff  13 fc 05 6e fc bc d7 e5  |...f(xA....n....|
00000190  5c 38 36 f8 45 6a b8 1f  67 b2 28 7e 30 6d 5b b7  |\86.Ej..g.(~0m[.|
000001a0  2c 6b 1a b1 dd 2e 8f cf  c2 09 5a a5 fd bb 04 b6  |,k........Z.....|
000001b0  f7 eb 78 0f c0 44 80 0a  38 d3 58 cb 55 8e 00 fe  |..x..D..8.X.U...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 26 4b 49 06 00 fe  |..........&KI...|
000001d0  ff ff 05 fe ff ff 28 4b  49 06 cf b3 73 09 00 00  |......(KI...s...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Any help, guidance, walk thru, work around or a smack on my head is all appreciated.
Thanks, 

Danial

---

### Post by oldfred on 2010-05-10
with mixed IDE & SATA does your BIOS let you select boot drive. I only have SATA and set primary master to boot currently sdc.

If you boot the SATA sdb you should have grub2 from Ubuntu. 
Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

If you boot sda it says it is booting grub2 from Mint.
/dev/sdb3        20e08ddc-06bc-4f21-96ba-92563ad5cb63   ext4       mint

---

### Post by Danial on 2010-05-10
> **oldfred said:**
> with mixed IDE & SATA does your BIOS let you select boot drive. 

Fred,

Yes, BIOS let me choose the boot drive between sata and IDE.  I will give it a shot later and will post my results.

Thanks for looking into this and guiding me.

Danial

---

### Post by Danial on 2010-05-11
> **oldfred said:**
> with mixed IDE & SATA does your BIOS let you select boot drive. I only have SATA and set primary master to boot currently sdc.

If you boot the SATA sdb you should have grub2 from Ubuntu. 
Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

If you boot sda it says it is booting grub2 from Mint.
/dev/sdb3        20e08ddc-06bc-4f21-96ba-92563ad5cb63   ext4       mint

Well, 
I tried to boot from IDE but that simply hung up to after I choose Linux-Mint from the the OS menu.  I was trying to read the boot script (emphasis on trying) - all I noticed that for Mint it referenced wrong drive.  Anyway, I will try to read some about Grub menu and see from there.  If I am stuck (which I may) I will be back.  Leaving this thread open for few days and if not accomplished, I will close it - unless, you get a moment and you look into the script again to dig the problem.

Thanks for looking into it.

Danial

---

### Post by confused57 on 2010-05-12
I don't know much about grub2, although I'm somewhat fluent with legacy-grub(doesn't help here); but you might want to try a custom configfile entry to boot Mint:
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

Your entry might look something like this:
```
#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
menuentry "Configfile Boot on Linux Mint in /dev/sdb3" {
        configfile (hd1,3)/boot/grub/grub.cfg
}
EOF
```

You might be able to add to the 40_custom file in your /etc/grub.d, rather than using 06_custom as mentioned in the above link.

You might want to wait on oldfred to see what he thinks about this.

---

### Post by oldfred on 2010-05-12
Perhaps the grub in sda confused the grub.cfg for mint to think it is hd0?

More info on confused57 suggestion:
total custom menu/config file - meierfra 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

But as long as the grub.cfg in mint has hd0 I am not sure if it works. The device.map in Ubuntu and Mint may not agree or somehow they see the drive order differently. Check both device.map in /boot/grub.

I would also try just copy the first mint entry into Ubuntu's 40_custom twice once with hd0 and once with hd1 as the set root entry.

---

### Post by confused57 on 2010-05-12
I have an older computer with 3 drives, 1 ide and 2 sata, and with most distros the ide is recognized as /dev/sda, which agrees with it being the first boot drive in bios.  I've had a couple of distros recognize it as /dev/sdc and I found the workaround with legacy-grub was to use a configfile or chainloader entry in my main distro's menu.lst to boot the distro exception.  
It worked fine with legacy-grub and "should" work OK with grub2?  The key(for me) would be determining  the correct custom entry to boot to Mint's boot.cfg...in other words, Lucid would be "handing off" to Mint's boot.cfg, which boot into Mint, hopefully?

---

### Post by Danial on 2010-05-14
> **confused57 said:**
> ...try a custom configfile entry to boot Mint:
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

Your entry might look something like this:
```
#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
menuentry "Configfile Boot on Linux Mint in /dev/sdb3" {
        configfile (hd1,3)/boot/grub/grub.cfg
}
EOF
```

You might be able to add to the 40_custom file in your /etc/grub.d, rather than using 06_custom as mentioned in the above link.

You might want to wait on oldfred to see what he thinks about this.

> **oldfred said:**
> Perhaps the grub in sda confused the grub.cfg for mint to think it is hd0?

More info on confused57 suggestion:
total custom menu/config file - meierfra 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

But as long as the grub.cfg in mint has hd0 I am not sure if it works. The device.map in Ubuntu and Mint may not agree or somehow they see the drive order differently. Check both device.map in /boot/grub.

I would also try just copy the first mint entry into Ubuntu's 40_custom twice once with hd0 and once with hd1 as the set root entry.

I am sorry, I was away from my system for last few days.  Thanks a lot for your researches and responses in this issue. As you suggest, I will try to add on 40_custom menu entry.  I am reading or trying to understand before I digg into.  Once again thanks for the links (provided me a lot of material to learn).  Hopefully, I will be able to work on on this weekend and will post back results.  As of now I am leaving thread open for a while.

All your time and help is very appreicated.

Danial

---

### Post by kansasnoob on 2010-05-14
Since Mints grub2 is on the mbr of sda (the 40GB drive) I'd try updating Mints grub in a chroot, then on reboot go into BIOS and choose to boot the 40GB drive first. Then of course just see if Mint will boot. 

If you want to try that first read a bit about my chroot procedure just so you know what's up:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Then boot an Ubuntu or Mint Live CD (if you do it from your installed Ubuntu os-prober will not "find" Ubuntu), and from the Live Desktop copy-n-paste the following commands:

```
sudo mount /dev/sdb3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
update-grub
```

Wait for it to say done, then just exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Then, of course, reboot, choose to boot the 40GB drive first in BIOS and see what happens. If everything boots I'd still try to see what happens with Ubuntu's grub2 by simply booting into it and running:

```
sudo update-grub
```

Then, of course, switching the boot order again on reboot in BIOS just to see what happens.

If that doesn't work we might have to try generating a new Mint devicemap:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkdevicemap](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkdevicemap)

But that's something I've only done once so it's basically unexplored territory to me.

---

