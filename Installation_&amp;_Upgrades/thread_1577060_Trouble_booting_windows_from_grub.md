---
title: "Trouble booting windows from grub"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by Anadon on 2010-09-18
I just installed Ubuntu 10.04 on my machine, it works fine.  The problem is that Windows 7 Pro won't boot anymore.  I looked and I'm pretty sure the correct patron is targeted with grub, I can view all the files, but I can't boot into it.  I tried a little tweaking with grub's settings for it and same result.

Clevo laptop
i7 Q 740
4 GB DDR3 1777 RAM
256 GB SSD

Windows 7 Professional 64 bit
Ubuntu 10.04 64 bit

hd0-windows protected recovery drive(I think, never been able to get on it)
hd1-windows
hd2-don't know that it exists
hd3-don't know that it exists
hd4-swap maybe?
hd5-ubuntu ext4 FS
hd6-swap maybe?  may not exist

---

### Post by Rubi1200 on 2010-09-18
Hi,
please boot the computer with the Ubuntu CD in live mode and then post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by Anadon on 2010-09-18
Ready for the block?


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

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

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.7 GB, 251658240000 bytes
255 heads, 63 sectors/track, 30595 cylinders, total 491520000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   351,412,735   351,205,888   7 HPFS/NTFS
/dev/sda3         351,414,270   491,517,951   140,103,682   5 Extended
/dev/sda5         351,414,272   485,715,967   134,301,696  83 Linux
/dev/sda6         485,718,016   491,517,951     5,799,936  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0E12EE4112EE2D81                       ntfs       System Reserved               
/dev/sda2        82DEF7D2DEF7BC8B                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        34dd32b0-2be8-4d95-90b0-949eaacd13d6   ext4                                     
/dev/sda6        55d47d78-132b-4dac-96f6-29e46fee238f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        755F608547CA7F68                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/82DEF7D2DEF7BC8B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
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
search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=34dd32b0-2be8-4d95-90b0-949eaacd13d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=34dd32b0-2be8-4d95-90b0-949eaacd13d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=34dd32b0-2be8-4d95-90b0-949eaacd13d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=34dd32b0-2be8-4d95-90b0-949eaacd13d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=34dd32b0-2be8-4d95-90b0-949eaacd13d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=34dd32b0-2be8-4d95-90b0-949eaacd13d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	linux	/boot/vmlinuz-2.6.31-11-rt root=UUID=34dd32b0-2be8-4d95-90b0-949eaacd13d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-rt
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	echo	'Loading Linux 2.6.31-11-rt ...'
	linux	/boot/vmlinuz-2.6.31-11-rt root=UUID=34dd32b0-2be8-4d95-90b0-949eaacd13d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-11-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34dd32b0-2be8-4d95-90b0-949eaacd13d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0e12ee4112ee2d81
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
UUID=34dd32b0-2be8-4d95-90b0-949eaacd13d6 /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda2 during installation
UUID=82DEF7D2DEF7BC8B /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=55d47d78-132b-4dac-96f6-29e46fee238f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 182.3GB: boot/grub/core.img
 191.2GB: boot/grub/grub.cfg
 184.1GB: boot/initrd.img-2.6.31-11-rt
 183.3GB: boot/initrd.img-2.6.32-21-generic
 183.6GB: boot/initrd.img-2.6.32-24-generic
 184.0GB: boot/initrd.img-2.6.32-25-generic
 182.8GB: boot/vmlinuz-2.6.31-11-rt
 183.2GB: boot/vmlinuz-2.6.32-21-generic
 183.3GB: boot/vmlinuz-2.6.32-24-generic
 182.9GB: boot/vmlinuz-2.6.32-25-generic
 184.1GB: initrd.img
 184.0GB: initrd.img.old
 182.8GB: vmlinuz
 182.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  3a 3b 3c 3d 3e 3f 40 41  42 43 44 45 46 47 48 49  |:;<=>?@ABCDEFGHI|
00000010  4a 4b 4c 4d 4e 4f 50 51  52 53 54 55 56 57 58 59  |JKLMNOPQRSTUVWXY|
00000020  5a 5b 5c 5d 5e 5f 60 61  62 63 64 65 66 67 68 69  |Z[\]^_`abcdefghi|
00000030  6a 6b 6c 6d 6e 6f 70 71  72 73 74 75 76 77 78 79  |jklmnopqrstuvwxy|
00000040  7a 7b 7c 7d 7e 7f 80 81  82 83 84 85 86 87 88 89  |z{|}~...........|
00000050  8a 8b 8c 8d 8e 8f 90 91  92 93 94 95 96 97 98 99  |................|
00000060  9a 9b 9c 9d 9e 9f a0 a1  a2 a3 a4 a5 a6 a7 a8 a9  |................|
00000070  aa ab ac ad ae af b0 b1  b2 b3 b4 b5 b6 b7 b8 b9  |................|
00000080  ba bb bc bd be bf c0 c1  c2 c3 c4 c5 c6 c7 c8 c9  |................|
00000090  ca cb cc cd ce cf d0 d1  d2 d3 d4 d5 d6 d7 d8 d9  |................|
000000a0  da db dc dd de df e0 e1  e2 e3 e4 e5 e6 e7 e8 e9  |................|
000000b0  ea eb ec ed ee ef f0 f1  f2 f3 f4 f5 f6 f7 f8 f9  |................|
000000c0  fa fb fc fd fe ff 00 01  02 03 04 05 06 07 08 09  |................|
000000d0  0a 0b 0c 0d 0e 0f 10 11  12 13 14 15 16 17 18 19  |................|
000000e0  1a 1b 1c 1d 1e 1f 20 21  22 23 24 25 26 27 28 29  |...... !"#$%&'()|
000000f0  2a 2b 2c 2d 2e 2f 30 31  32 33 34 35 36 37 38 39  |*+,-./0123456789|
00000100  3a 3b 3c 3d 3e 3f 40 41  42 43 44 45 46 47 48 49  |:;<=>?@ABCDEFGHI|
00000110  4a 4b 4c 4d 4e 4f 50 51  52 53 54 55 56 57 58 59  |JKLMNOPQRSTUVWXY|
00000120  5a 5b 5c 5d 5e 5f 60 61  62 63 64 65 66 67 68 69  |Z[\]^_`abcdefghi|
00000130  6a 6b 6c 6d 6e 6f 70 71  72 73 74 75 76 77 78 79  |jklmnopqrstuvwxy|
00000140  7a 7b 7c 7d 7e 7f 80 81  82 83 84 85 86 87 88 89  |z{|}~...........|
00000150  8a 8b 8c 8d 8e 8f 90 91  92 93 94 95 96 97 98 99  |................|
00000160  9a 9b 9c 9d 9e 9f a0 a1  a2 a3 a4 a5 a6 a7 a8 a9  |................|
00000170  aa ab ac ad ae af b0 b1  b2 b3 b4 b5 b6 b7 b8 b9  |................|
00000180  ba bb bc bd be bf c0 c1  c2 c3 c4 c5 c6 c7 c8 c9  |................|
00000190  ca cb cc cd ce cf d0 d1  d2 d3 d4 d5 d6 d7 d8 d9  |................|
000001a0  da db dc dd de df e0 e1  e2 e3 e4 e5 e6 e7 e8 e9  |................|
000001b0  ea eb ec ed ee ef f0 f1  f2 f3 f4 f5 f6 f7 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 01 08 00 fe  |...........H....|
000001d0  ff ff 05 fe ff ff 02 48  01 08 00 88 58 00 00 00  |.......H....X...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Rubi1200 on 2010-09-18
Have you tried removing sdb (I assume this is an external drive) and then booting to see if you can get into Windows?

Does running ```
sudo update-grub
``` in Ubuntu and then rebooting get you into Windows?

---

### Post by Anadon on 2010-09-18
That's what I've been doing usually, but right now I'm copying all my window files should the worst happen.  Three things I noticed.  1. there is no boot loader.  2. even when there was a boot loader, windows wouldn't start.  3. I'm having a VERY hard time trying to re-install the windows boot loader.

---

### Post by Rubi1200 on 2010-09-18
Hmm, the funny thing is that the bootscript looked fairly normal for the most part.

Are you saying there is no GRUB menu at all or did you change some settings that may have hidden it?

Try holding down Shift as you boot to bring the menu up.

Backup is always a good idea.

What exactly is not working so far as reinstalling the Windows bootloader?

---

### Post by Anadon on 2010-09-18
============================= Boot Info Summary: ==============================

=> Windows is installed in the MBR of /dev/sda
=> No boot loader is installed in the MBR of /dev/sdb

sda1: __________________________________________________ _______________________

It says there's no bootloader.  Once I'm done backing up the data.  I'll be looking up how to reinstall the windows bootloader.  but I'd like to not have all may data be erased or spend my whole weekend re-doing everything.

---

### Post by Rubi1200 on 2010-09-18
Sorry, so why don't you reinstall GRUB? Surely that would be the easiest solution after you have finished backing up?

Here is the link:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

GRUB should detect Windows and then you can boot both systems.

---

### Post by Anadon on 2010-09-18
It partially worked.  Linux kernels are able to boot, but windows 7 will not, I just get an endless flashing underscore.  I also tries changing the boot parameters to use the 2nd NTFS patron (the main one) and same result.  No easy solution for you!  As a terrible chinese man might but it.

---

### Post by Anadon on 2010-09-18
The boot parameters for windows are:

insmod ntfs
set root='(hs0,1)'
search --no-floppy --fs-uuid --set 0e12ee4112ee2d81
chainloader +1

---

### Post by Anadon on 2010-09-18
Also, when I edited to bot parameters from GRUB for the windows 7 boot option and added an echo line, i did not see the text i entered for the echo.

---

### Post by Anadon on 2010-09-18
I just tried re-installing windows flat out.  FAILED.  DVD booted, installed the files, time comes for it to reboot, nothing starts.  No GRUB, no windows, nothing.  HELP!!!

---

### Post by wilee-nilee on 2010-09-18
> **Anadon said:**
> I just tried re-installing windows flat out.  FAILED.  DVD booted, installed the files, time comes for it to reboot, nothing starts.  No GRUB, no windows, nothing.  HELP!!!

Run the script again, but be sure to put it in code tags it is very hard to read otherwise. The instructions for code tags are in my signature, but you can also click on the # in the reply window and put the text between the generated code tags.

---

### Post by Anadon on 2010-09-18
I gave up and reformatted the drive.  I think the issue was made irrecoverable by the incorrect commands:
sudo mount /dev/sda1 /mnt
 grub-install --root-directory=/mnt/ /dev/sda

which likely corrupted something associated with windows booting.

moral, be careful where you install grub.

---

### Post by wilee-nilee on 2010-09-18
> **Anadon said:**
> I gave up and reformatted the drive.  I think the issue was made irrecoverable by the incorrect commands:
sudo mount /dev/sda1 /mnt
[COLOR="Red"]sudo[/COLOR] grub-install --root-directory=/mnt/ /dev/sda

which likely corrupted something associated with windows booting.

moral, be careful where you install grub.

Those commands were not the problem all they do is load grub to the MBR and mount the Ubuntu OS partition. The MBR can be reloaded with a recovery disc for windows.

The moral is know what your doing and if you think you don't; find somebody who does. Not saying you don't know but this quoted statement is just way off base. I also notice that the second command in your post has no sudo in front of it.

---

### Post by wilee-nilee on 2010-09-18
So since you also had problems with loading the MS bootloader to the mbr here are the full set of commands, and a link to the W7 forums for reference.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

The only command you should of had to run is the highlighted one.

Here is a W7 recovery cd link.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

