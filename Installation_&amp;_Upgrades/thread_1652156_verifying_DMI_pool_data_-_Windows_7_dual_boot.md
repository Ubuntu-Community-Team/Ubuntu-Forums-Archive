---
title: "verifying DMI pool data - Windows 7 dual boot"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by Shannonb1 on 2010-12-24
I installed ubuntu 10.10 on a machine that had windows 7 x64.  itts installed on a seperate HD, but now when I boot to the harddrive with windows 7 all i get is "verifying DMI pool data" how do I fix this so I can get back to windows 7 as well please?

---

### Post by Quackers on 2010-12-24
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Shannonb1 on 2010-12-24
I can get into ubuntu, I cant get into windows 7 by the way.


Here are the results


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
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

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders, total 156312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,856,255   149,854,208  83 Linux
/dev/sdb2         149,858,302   156,311,551     6,453,250   5 Extended
/dev/sdb5         149,858,304   156,311,551     6,453,248  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E028C04228C01A04                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        66105d9c-6a5c-4236-b0b1-90688aff5aaf   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        07d2d86d-c885-44c1-b829-66c04a46c2b4   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         B048-9C2A                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc         /media/B048-9C2A         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set 66105d9c-6a5c-4236-b0b1-90688aff5aaf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 66105d9c-6a5c-4236-b0b1-90688aff5aaf
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 66105d9c-6a5c-4236-b0b1-90688aff5aaf
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=66105d9c-6a5c-4236-b0b1-90688aff5aaf ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 66105d9c-6a5c-4236-b0b1-90688aff5aaf
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=66105d9c-6a5c-4236-b0b1-90688aff5aaf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 66105d9c-6a5c-4236-b0b1-90688aff5aaf
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 66105d9c-6a5c-4236-b0b1-90688aff5aaf
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
UUID=66105d9c-6a5c-4236-b0b1-90688aff5aaf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=07d2d86d-c885-44c1-b829-66c04a46c2b4 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  45.2GB: boot/grub/core.img
  73.2GB: boot/grub/grub.cfg
   1.8GB: boot/initrd.img-2.6.35-24-generic-pae
  45.2GB: boot/vmlinuz-2.6.35-24-generic-pae
   1.8GB: initrd.img
  45.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ef f7 0e 65 9c 5c f4 18  8d cc 5a 57 81 1c 0c 60  |...e.\....ZW...`|
00000010  47 25 e8 04 1e 88 f3 f4  15 36 1e c4 51 14 e6 bb  |G%.......6..Q...|
00000020  bc 98 41 41 68 5c d3 7e  26 d0 c3 4c 0a ca 0c 14  |..AAh\.~&..L....|
00000030  14 d4 10 a7 7f 00 00 e3  80 c2 d8 32 91 63 ca b3  |...........2.c..|
00000040  9b bf 3c cb 9c 4d 9f ee  30 f4 6b a4 87 d9 13 2c  |..<..M..0.k....,|
00000050  a9 e9 eb 54 b1 6f d8 9f  fd be c2 ca 9d b8 2c 01  |...T.o........,.|
00000060  9e 65 09 37 02 b0 4f cf  85 b4 49 ac cf c6 d7 05  |.e.7..O...I.....|
00000070  88 08 90 ef b5 75 36 7f  3c 00 51 9e 0f cd bd 35  |.....u6.<.Q....5|
00000080  9f 43 0b 87 e1 89 ed c9  2c 1c 3e 71 d2 61 4d c3  |.C......,.>q.aM.|
00000090  8e e0 85 fd fc 9e 1b 7c  e7 5d 99 9b fd 47 e5 40  |.......|.]...G.@|
000000a0  6e 35 f6 c4 e3 33 ba 8f  5d c3 e6 4e 3a 37 53 15  |n5...3..]..N:7S.|
000000b0  3c 00 1c f0 d4 b0 87 4a  94 52 ed 1f 7d 8d c3 43  |<......J.R..}..C|
000000c0  2b c8 ed 46 b8 2c ef 07  10 42 a1 3b df 6f 88 8c  |+..F.,...B.;.o..|
000000d0  06 9c 86 0f 38 0d aa 48  51 b7 62 f9 cc 64 8f 12  |....8..HQ.b..d..|
000000e0  e3 8d 35 96 e8 7e ce 59  82 12 1f 07 20 22 a0 d1  |..5..~.Y.... "..|
000000f0  07 72 34 d6 c9 71 8f 0e  86 c9 1b 43 69 66 e7 f9  |.r4..q.....Cif..|
00000100  b8 9d 93 c4 63 82 33 56  4a bd 86 e7 90 73 83 62  |....c.3VJ....s.b|
00000110  bc 34 e0 ab 30 bd ba bf  28 a5 a3 8b 38 23 6a 73  |.4..0...(...8#js|
00000120  df 9e ae ac 03 38 15 07  da 2b e6 94 82 c0 6f ed  |.....8...+....o.|
00000130  75 bc b0 58 4f 9e 60 4a  0a 96 4f 1c ef 70 81 e8  |u..XO.`J..O..p..|
00000140  c8 f7 14 28 a1 02 40 7a  de 13 e4 20 00 3d ac 82  |...(..@z... .=..|
00000150  31 43 19 90 15 0c 48 43  79 cf 23 c3 8e cb c1 03  |1C....HCy.#.....|
00000160  13 d6 fb 24 0e b4 66 8d  96 dc 05 78 e3 04 65 f4  |...$..f....x..e.|
00000170  51 79 64 3c ef 32 bf 53  46 0e 63 2a 69 47 db 72  |Qyd<.2.SF.c*iG.r|
00000180  1c 87 4e 0f ee 93 4d 4e  20 49 42 12 25 6c 43 08  |..N...MN IB.%lC.|
00000190  1c 00 84 4d c7 e6 d4 a9  3a 4f 0f e4 d3 03 83 ce  |...M....:O......|
000001a0  71 b4 6d 51 50 5b 6d 55  2b 6d 2b 4c 95 71 22 27  |q.mQP[mU+m+L.q"'|
000001b0  8c 1b 20 81 e3 98 03 e7  38 81 c0 c1 b6 39 00 fe  |.. .....8....9..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 62 00 00 00  |...........xb...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Quackers on 2010-12-24
Do you have a Windows 7/vista repair disc (not recovery discs)?

---

### Post by Shannonb1 on 2010-12-24
Dont believe that I have a repair disc, I know I did not make one.  Can I download it somewhere?

---

### Post by Quackers on 2010-12-24
Yes below. You need to burn the image (not burn the files).

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

After the disc is burned if you boot from it and select the repair option then run Startup Repair (up to 3 times may be necessary) then reboot, hopefully into Windows.
You will need to set the cd drive as first boot device in the bios (and the Windows drive as second boot device).

---

### Post by Shannonb1 on 2010-12-24
Ok quackers did that, but it doesn't list any of my hard drives but I can click load drivers and see the drives andante windows structure, ?help

---

### Post by Quackers on 2010-12-24
You don't need it to show any drives. Just choose the repair option and then run Startup repair up to 3 times.

---

### Post by Shannonb1 on 2010-12-24
YEs, I did it like 10 times, same result, the diagnostics say that there was no install on this partition, reason being the repair tool isn't seeing my c drive I believe

---

### Post by Shannonb1 on 2010-12-24
Also the drive shows up in the bios as well as i can access it from within ubuntu. However evn in this repair tool if I launch cmd, it won't let me go to the c: drive

---

### Post by Quackers on 2010-12-24
Try going into repair once again and then choose the command prompt option.
In the command prompt window type ```
bootrec.exe /fixmbr
``` (note the space between the two parts) and hit enter. What does that report please?

---

### Post by Shannonb1 on 2010-12-24
Completed successfully, i removed a. USB drive and it saw the c drive in recovery, changed the boot order to put te c drive back in front and now I don't see it in the recovery console anymore

---

### Post by Shannonb1 on 2010-12-24
Ok now in ubuntu i see under system start up configuration the option for windows 7, i changed to that, when the comp launched it showed me Linux, windows options, so i am good now.

So big thanks and in closing here is what i think worked

Remove all USB drives, thumb drives..
Use startup configuration in Linux
Change primary boot to win 7 and it then using grub, which i had installed' grub 2 actually, i was able to pick



Lesson learned , man I was cussing linux

---

