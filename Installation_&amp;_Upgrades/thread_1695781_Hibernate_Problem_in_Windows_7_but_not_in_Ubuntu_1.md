---
title: "Hibernate Problem in Windows 7 but not in Ubuntu 10.10"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by mexarhos on 2011-02-26
Hello to you all! 
I recently installed Ubuntu 10.10 in my pc and for the last week I've been trying to enable hibernation in Windows 7. I have read more than 100 threads (and followed their instructions) with no result. 
My configuration is:
hda: Windows 7
hdc: Ubuntu 10.10 (GRUB)
The BIOS is set to boot from hdc. When I select windows from GRUB, windows start up, but when I choose "hibernate" they just pop up the log in screen. However, when I set BIOS to boot from hda windows start (without GRUB) and DO hibernate when I choose to. BUT, when I switch on the pc (immediately after a successful windows hibernation) I get "Resuming Windows" regardless what disk I choose to boot from (using BIOS)! I do not get the GRUB screen but I don't get the chance to launch the BBS popup either (I see the message but there is no response when I press F8 ). It seems like the system always boots from hda after a successful windows hibernation and there is nothing I can do to change this! On the other hand, Ubuntu always hibernates normally... I'm willing to post any information needed but I would appreciate it if the answers are not like "Repair Windows" or "Reinstall Ubuntu" because I want to solve the problem but find out its cause as well.
Thanks in advance to anyone spending the time even to read this post,
Mick
PS. I have ubuntu 10.04 with Vista installed in the same disk in my laptop and hibernation works perfectly for both systems.

---

### Post by mexarhos on 2011-02-28
Here's some more information. Both disks are flagged bootable in Ubuntu and Active in Windows. hda is marked as boot in Windows. Hibernate option is (obviously) available in windows in any case (startup with or without grub), Hybrid sleep mode is set to off. Any post appreciated! It shows that I'm not alone...

---

### Post by amsterdamharu on 2011-02-28
I think the problem might be that grub is on hdc and you keep switching in the bios. I haven't got much experience with Windows 7 but it could be started from grub and as far as I know hibernate doesn't need to write to the mbr on hda.

So you could install grub on hda's mbr and the rest in hdc? wherever the /boot directory is.

Could you post the output of the boot info script?
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Copy it to your Desktop (it usually is in Downloads).
Run the following commands:
```
cd ~/Desktop
sudo bash boot_info_script*
```
To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
There should be a file on your Desktop named RESULTS.txt please post the content of this file here too using &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by mexarhos on 2011-02-28
Thank you for your reply amsterdamharu.
First of all a correction in my first post:
hda=sda
hdc=sdb1
About your comments:
I prefer grub installed on a disk other than the windows one because in this way I can remove this disk and still have a bootable windows system. I used to have a similar configuration with Windows XP and Ubuntu 9.04 which worked perfectly.
Windows 7 start normally using grub. The difference I stated is that when started using grub, windows hibernation does not work (it leads to the login screen). When windows is started using windows boot loader directly, hibernation works but the next time I turn on the pc grub is completely bypassed (although I use BIOS to boot from the disk it is installed - see first post too) and windows resumes automatically.
Bellow is the output of the boot info script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   230,277,119   230,275,072  83 Linux
/dev/sdb2         230,279,166   240,119,807     9,840,642   5 Extended
/dev/sdb5         230,279,168   240,119,807     9,840,640  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C4D63DCED63DC20A                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ee5b5077-7dbe-4ece-9df3-fba6c157d139   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        1dfafcb1-fe2e-4c0f-9e90-7a72dfc743f4   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D024722624721028                       ntfs       Media                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
set default="6"
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
search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ee5b5077-7dbe-4ece-9df3-fba6c157d139 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ee5b5077-7dbe-4ece-9df3-fba6c157d139 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ee5b5077-7dbe-4ece-9df3-fba6c157d139 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ee5b5077-7dbe-4ece-9df3-fba6c157d139 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c4d63dced63dc20a
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set d024722624721028
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
search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ee5b5077-7dbe-4ece-9df3-fba6c157d139 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ee5b5077-7dbe-4ece-9df3-fba6c157d139 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ee5b5077-7dbe-4ece-9df3-fba6c157d139 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ee5b5077-7dbe-4ece-9df3-fba6c157d139 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ee5b5077-7dbe-4ece-9df3-fba6c157d139
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c4d63dced63dc20a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.save ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
parttool hd0,2 boot+
### END /etc/grub.d/40_custom.save ###

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
# / was on /dev/sdb1 during installation
UUID=ee5b5077-7dbe-4ece-9df3-fba6c157d139 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1dfafcb1-fe2e-4c0f-9e90-7a72dfc743f4 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
  30.6GB: boot/grub/grub.cfg
  24.2GB: boot/grub/menu.lst
   1.4GB: boot/initrd.img-2.6.35-22-generic
   1.4GB: boot/initrd.img-2.6.35-25-generic
  13.1GB: boot/vmlinuz-2.6.35-22-generic
  13.1GB: boot/vmlinuz-2.6.35-25-generic
   1.4GB: initrd.img
   1.4GB: initrd.img.old
  13.1GB: vmlinuz
  13.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  2b 55 6a 61 86 66 39 16  3b d4 62 a5 4e 6c 08 0d  |+Uja.f9.;.b.Nl..|
00000010  08 62 03 01 6c 15 c7 e3  a7 7a 3c fd 5d 52 fe 75  |.b..l....z<.]R.u|
00000020  d0 15 37 6b b0 db c7 56  5f 71 71 0c f9 0a 75 c2  |..7k...V_qq...u.|
00000030  78 f5 76 6c db 46 1e da  60 35 65 ad 83 9c 7d 5d  |x.vl.F..`5e...}]|
00000040  d2 20 ca 59 ae c1 ab e3  ba ce 6d 03 48 7a c2 0b  |. .Y......m.Hz..|
00000050  0b 26 ce 47 9c 6e fc 05  a7 23 78 0c 58 05 4c fa  |.&.G.n...#x.X.L.|
00000060  13 d8 4c 3b 63 ff 7c 3f  24 11 52 10 31 38 53 d4  |..L;c.|?$.R.18S.|
00000070  2d 1e 84 18 1d be ab 35  32 51 fa 2f 4f 47 57 3b  |-......52Q./OGW;|
00000080  9a 51 22 16 1b 12 94 e5  63 65 cd dd 83 b3 29 eb  |.Q".....ce....).|
00000090  a1 02 5a e3 e4 c1 eb e0  9a 0e d1 e9 87 7d 6b f1  |..Z..........}k.|
000000a0  3b 8b 5d 22 82 2e f1 ef  33 3f 14 ca bc e9 df 67  |;.]"....3?.....g|
000000b0  c6 39 73 c8 2f 7a 78 ae  66 b4 53 53 6c 6b 12 cf  |.9s./zx.f.SSlk..|
000000c0  2d 8f 11 9b c4 de f8 7d  18 ec aa 92 7d 2b e6 e2  |-......}....}+..|
000000d0  d8 a3 46 bc 43 1d 34 bb  c4 c3 38 45 cb 38 1c 71  |..F.C.4...8E.8.q|
000000e0  bc 9d 75 4b 9c 9d c6 6e  9b 78 4e 39 a9 a7 fc ec  |..uK...n.xN9....|
000000f0  a4 d8 2e f6 2e 0a e3 e9  0f 0c b8 2a ee 55 87 30  |...........*.U.0|
00000100  f4 14 21 d0 a1 c6 19 aa  2a ba 23 26 7e 0b 25 b8  |..!.....*.#&~.%.|
00000110  3f e8 e2 d7 aa b3 6b 0f  79 cf 8d 7e 93 ee 96 d3  |?.....k.y..~....|
00000120  fa 9a 37 b6 b8 f5 1a 74  28 a2 ab bc 18 bf fb a3  |..7....t(.......|
00000130  71 81 f0 63 cd d8 6a 51  4b 7f 3d 8f 73 43 8b 29  |q..c..jQK.=.sC.)|
00000140  49 83 0b e9 58 38 a0 dd  92 d6 1c 05 8c 6e f2 49  |I...X8.......n.I|
00000150  eb bb 20 46 51 ba f2 d3  4f 80 1f 76 21 aa 5b 00  |.. FQ...O..v!.[.|
00000160  88 85 e2 fb 71 38 22 a4  a4 22 c5 1d 3b cc 8a 50  |....q8".."..;..P|
00000170  11 bd a3 df b4 75 80 63  1d e2 14 f5 e8 7a 50 12  |.....u.c.....zP.|
00000180  54 65 d0 e5 84 a0 0a 47  d7 06 d3 e2 9b 38 05 25  |Te.....G.....8.%|
00000190  8d 7e 07 07 b6 0b 18 45  17 76 1e 5a 6d cd 06 f3  |.~.....E.v.Zm...|
000001a0  f1 8b 3c a5 f1 b6 26 3a  83 c8 5a 60 25 5d f4 d0  |..<...&:..Z`%]..|
000001b0  8c 28 20 fe a9 41 a4 9d  94 c8 44 75 30 be 00 fe  |.( ..A....Du0...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 28 96 00 00 00  |...........(....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

What's strange about this is that there is a second windows menu entry (menuentry "Windows 7 (loader) (on /dev/sdc1)" {) which should not exist and does not actually appear in the startup choices of grub or in startup manager. This disk (sdc1) used to have Windows XP installed but it does not any more and it does not contain a boot folder...
Thank you,

---

### Post by sofiamarcella on 2011-02-28
thank's guy... finished I have answered .... I'll try  [IMG]http://freeimagestocks.com/content/5/love.gif[/IMG]:guitar::P:P:P

---

### Post by mexarhos on 2011-02-28
> **sofiamarcella said:**
> thank's guy... finished I have answered .... I'll try  [IMG]http://freeimagestocks.com/content/5/love.gif[/IMG]:guitar::P:P:P

Obviously this was meant to be somewhere else. The problem remains...

---

### Post by Mark Phelps on 2011-03-01
If hibernate works find in Ubuntu but not in Win7, then you need a Win7 solution.

Hate to point this out -- but this is an Ubuntu forum, not a Windows 7 forum.

Suggest you post you concerns to [www.sevenforums.com](www.sevenforums.com) -- a Windows 7 forum.  You might have better luck getting detailed advice there.

---

### Post by mexarhos on 2011-03-01
Thank you for your reply Mark. 
I will have to disagree with you. If you read carefully you will see that windows 7 hibernation works fine when I bypass grub and boot from the disk that contains windows. In addition, windows hibernate worked perfectly before I installed Ubuntu. I have searched sevenforums (among other windows fora) and the solutions found there do not work for me, not to mention that they are much less technical than the ones found here. Following your way of thinking, someone on a windows forum would write: "If hibernate works fine when you bypass GRUB , then you need a GRUB solution"...
So, given that you have thousands of posts in this forum, I would really appreciate it if you gave a look at the output of the boot info script and maybe point out what might be wrong.
In any case... Thanks

---

### Post by mexarhos on 2011-03-03
I did an "update-grub" but nothing changed (not even the strange 2nd windows entry). Since I had no new suggestions I tried some changes in windows power management that didn't make a difference. Could ext2fsd cause the hibernation problem?

---

### Post by Quatrix on 2011-08-22
mexarhos, did you ever figure this out?  I have the same problem with GRUB/Ubuntu on one drive and Windows 7 on another.  I can hibernate if I go through the Windows boot loader but not GRUB.  The GRUB and Windows 7 partitions are both marked boot/active.  I've seen marking partitions boot/active advertised as a fix when everything is on one drive, but having Windows 7 on a different drive seems to introduce more complications.

And you DID post in the right place.  Because the problem only occurs when booting through GRUB and users are more technical here, you're more likely to get help here than on sevenforums.com.

---

### Post by cr@ss on 2011-11-28
I ran into what I believe is the same problem.  You can find a work-around to it here: [http://archimedesden.wordpress.com/2011/11/29/windows-hibernate-where-did-my-bios-options-go/](http://archimedesden.wordpress.com/2011/11/29/windows-hibernate-where-did-my-bios-options-go/)

They idea is that the machine is not completely shutdown after hibernating.  That is hitting the power button does not do a cold boot.  By forcing a cold boot you're able to boot the way you want.

So actually this is neither an Ubuntu, Grub, nor Windows issue.  But this forum is still the best place to ask.  Hope this help someone else.

---

