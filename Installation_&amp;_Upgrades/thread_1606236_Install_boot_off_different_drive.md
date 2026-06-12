---
title: "Install boot off different drive"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by cromat on 2010-10-26
Hey all,

I just did a fresh install of Ubuntu 10.10 on a hard drive, I have a ssd with Windows 7 and the Ubuntu drive and then data drives.  When I go to boot my pc, my windows 7 drive happens to be first in the list and it will boot that automatically.  When I use the Bios to select which disc to alternatively boot off of and select the ubuntu disk it won't boot.  If I select a blank drive above the ubuntu drive in the array it will find ubuntu and boot it, any idea why?

I'm running a EVGA 780i Mobo.

---

### Post by ronparent on 2010-10-26
Apparently because that disk happened to be the default where grub installed the boot loader to. You can actually easily reinstall grub so that the boot loader is where you want it if where its at is not satisfactory.

---

### Post by cromat on 2010-10-26
There is no files on that drive what so ever, how is that possible that it is installed to that drive?

---

### Post by cromat on 2010-10-26
Nevermind, I think I see what your saying, grub saw that drive as the priority drive over the drive I installed it to so it used that as the place for the boot loader.  I'll have to verify that tonight.

---

### Post by oldfred on 2010-10-26
If you have multiple drives and multiple systems knowing this script is worthwhile:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

I rerun it before & after system changes to make sure I did what I thought I did. And save a copy as it documents what is where in case I ever have to recover things.

---

### Post by ronparent on 2010-10-26
cromat - That's correct. The drive need have nothing on it. The boot loader would just write to the MBR section of the disk anyway.

---

### Post by cromat on 2010-10-26
Yea, I'll confirm, and if I remember reading correctly moving the MBR to the drive can be done with a few commands, looked fairly simple.

Thanks!

---

### Post by cromat on 2010-10-26
I see that my Boot is on my 160gb drive and not the 320 like I originally intended, suggestions on how to move it?
 
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdg and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdh
 => Grub 2 is installed in the MBR of /dev/sdi and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdj

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdh2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdh5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdi1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdj1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   125,042,687   124,835,840   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *          2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1               2,048   601,374,719   601,372,672  83 Linux
/dev/sdh2         601,376,766   625,141,759    23,764,994   5 Extended
/dev/sdh5         601,376,768   625,141,759    23,764,992  82 Linux swap / Solaris


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdi1               2,048 1,465,145,343 1,465,143,296   7 HPFS/NTFS


Drive: sdj ___________________ _____________________________________________________

Disk /dev/sdj: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdj1               2,048   976,769,023   976,766,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        561802CE1802ACD5                       ntfs       System Reserved               
/dev/sda2        FEB40B3DB40AF843                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdg1        5EB00231B0020FE7                       ntfs                                     
/dev/sdg: PTTYPE="dos" 
/dev/sdh1        2284ac86-c6f3-48be-a2e6-f33ca78549d6   ext4                                     
/dev/sdh2: PTTYPE="dos" 
/dev/sdh5        f4280049-ce94-49b1-99b7-329d4a417232   swap                                     
/dev/sdh: PTTYPE="dos" 
/dev/sdi1        7EDC14DEDC14930F                       ntfs                                     
/dev/sdi: PTTYPE="dos" 
/dev/sdj1        2228B5AE28B58179                       ntfs                                     
/dev/sdj: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdh1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdg1        /media/5EB00231B0020FE7  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdj1        /media/2228B5AE28B58179  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdi1        /media/7EDC14DEDC14930F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdh1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 2284ac86-c6f3-48be-a2e6-f33ca78549d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 2284ac86-c6f3-48be-a2e6-f33ca78549d6
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
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 2284ac86-c6f3-48be-a2e6-f33ca78549d6
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2284ac86-c6f3-48be-a2e6-f33ca78549d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 2284ac86-c6f3-48be-a2e6-f33ca78549d6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2284ac86-c6f3-48be-a2e6-f33ca78549d6 ro single 
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
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 2284ac86-c6f3-48be-a2e6-f33ca78549d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 2284ac86-c6f3-48be-a2e6-f33ca78549d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 561802ce1802acd5
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

=============================== sdh1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdh1 during installation
UUID=2284ac86-c6f3-48be-a2e6-f33ca78549d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdh5 during installation
UUID=f4280049-ce94-49b1-99b7-329d4a417232 none            swap    sw              0       0

=================== sdh1: Location of files loaded by Grub: ===================


 171.9GB: boot/grub/core.img
 155.0GB: boot/grub/grub.cfg
  33.9GB: boot/initrd.img-2.6.35-22-generic
 171.9GB: boot/vmlinuz-2.6.35-22-generic
  33.9GB: initrd.img
 171.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdh2

00000000  f0 17 0e c4 74 7f 00 00  60 e6 0d c4 74 7f 00 00  |....t...`...t...|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  30 00 00 00 00 00 00 00  81 00 00 00 00 00 00 00  |0...............|
00000030  00 e7 0d c4 74 7f 00 00  e0 f5 0d c4 74 7f 00 00  |....t.......t...|
00000040  00 5d 00 00 b0 00 00 00  61 00 00 00 00 00 00 00  |.]......a.......|
00000050  40 f9 0d c4 74 7f 00 00  00 e7 0d c4 74 7f 00 00  |@...t.......t...|
00000060  4b 5d 00 00 00 00 00 00  41 00 00 00 00 00 00 00  |K]......A.......|
00000070  b0 ea 0d c4 74 7f 00 00  10 eb 0d c4 74 7f 00 00  |....t.......t...|
00000080  20 00 00 00 00 00 00 00  24 00 00 00 00 00 00 00  | .......$.......|
00000090  10 eb 0d c4 74 7f 00 00  00 00 00 c4 74 7f 00 00  |....t.......t...|
000000a0  b0 00 00 00 00 00 00 00  54 00 00 00 00 00 00 00  |........T.......|
000000b0  d0 0a 0e c4 74 7f 00 00  69 6f 6e 2d 76 6e 64 2e  |....t...ion-vnd.|
000000c0  6d 73 2d 70 6f 77 65 72  70 6f 69 6e 74 2e 70 72  |ms-powerpoint.pr|
000000d0  65 73 65 6e 74 61 74 69  6f 6e 2e 6d 61 63 72 6f  |esentation.macro|
000000e0  45 6e 61 62 6c 65 64 2e  31 32 00 00 00 00 00 00  |Enabled.12......|
000000f0  88 20 98 26 00 00 00 00  c1 07 00 00 00 00 00 00  |. .&............|
00000100  30 44 0e c4 74 7f 00 00  f0 17 0e c4 74 7f 00 00  |0D..t.......t...|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  a0 f5 0d c4 74 7f 00 00  69 6f 6e 2d 76 6e 64 2e  |....t...ion-vnd.|
00000130  6d 73 2d 77 6f 72 64 2e  64 6f 63 75 6d 65 6e 74  |ms-word.document|
00000140  2e 6d 61 63 72 6f 45 6e  61 62 6c 65 64 2e 31 32  |.macroEnabled.12|
00000150  00 b2 06 50 00 00 00 00  81 00 00 00 00 00 00 00  |...P............|
00000160  50 f5 0d c4 74 7f 00 00  50 24 0e c4 74 7f 00 00  |P...t...P$..t...|
00000170  20 00 00 00 00 00 00 00  34 00 00 00 00 00 00 00  | .......4.......|
00000180  b0 fe 0d c4 74 7f 00 00  6d 65 2d 61 70 70 6c 69  |....t...me-appli|
00000190  63 61 74 69 6f 6e 2d 78  2d 70 68 70 00 00 00 00  |cation-x-php....|
000001a0  50 00 00 00 00 00 00 00  34 00 00 00 00 00 00 00  |P.......4.......|
000001b0  f0 19 0e c4 74 7f 00 00  6d 65 2d 61 70 70 00 fe  |....t...me-app..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a0 6a 01 00 00  |............j...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 

```

---

### Post by oldfred on 2010-10-26
reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdh"  then just run:
sudo grub-install /dev/sd[COLOR=Red]h[/COLOR]
If that returns any errors run:
sudo grub-install --recheck /dev/sdh
Then:
sudo update-grub
to get grub to remember where to reinstall on updates, if drive always is sdh as this saves by drive not UUID:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by cromat on 2010-10-27
Thanks a lot, I'm going to give it a try tonight but I assume I won't have an issue moving it.

---

### Post by efflandt on 2010-10-28
This all brings up another question.  Where in the installation of Maverick can you chose where to install grub?

In 10.10 beta when I put "/" on a USB hard drive, there was something at the bottom of one of the dialogs to specify where to put grub, and that automatically defaulted to the USB drive.  I thought that was great that it obviously offered you a choice instead of hiding it behind an Advanced button.

But when I just installed 10.10 release on my internal drive, that option has disappeared from the release version.  So either the choice of where to put grub is missing, or I was not watching closely enough and missed it.  I wanted to put grub on sda4 to leave the mbr untouched, but it put grub in the mbr.

cromat's issue shows that hiding where it is going to put grub, and/or not offering a choice, can be a real problem if the installer makes an incorrect assumption, especially for multiple drives.  Not very user friendly.

---

### Post by oldfred on 2010-10-28
I see the combo box to install grub, but I always use manual install, as I create partitions in advance or am reinstalling to an existing partition.

It is my understanding that the auto install choices also auto install grub2 to the default drive. I think they wanted to hide it to avoid confusion, but they should at least let users know what they are doing.

---

