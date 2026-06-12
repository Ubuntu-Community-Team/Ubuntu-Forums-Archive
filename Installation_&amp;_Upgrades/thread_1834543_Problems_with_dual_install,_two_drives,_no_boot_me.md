---
title: "Problems with dual install, two drives, no boot menu"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by Matt Gotts on 2011-08-27
Newbie query here, but I've just installed Xubuntu 10.10 on my XP system to dual boot and I'm having issues!

The PC has 2 drives, the XP boot partition is on one and teh Xubuntu one on the other.  After installation I reset as requested, but the PC just boots straight into XP and I have no way to access Xubuntu.

I'm guessing it's something to do with GRUB being on the wrong disc (this after a bit of Googling) but I have no idea how to remedy it as I'm not really that experienced (did fiddle a while back with Ubuntu but have forgotten it all).

Any advice as to how to access the Xubuntu partition and get a dual boot sorted would be very gratefully received.

Apologies if this is a common query - I have tried to search but with no luck.

Thanks

Matt

---

### Post by lindsay7 on 2011-08-27
Go into you bios setting and change the first boot drive to the drive with Linux on it.  Grub is probably installed on that drive.

---

### Post by Matt Gotts on 2011-08-28
Thanks - that's got Grub loading, problem now is that I get Grub Error 17 and nothing happens.  I've checked a couple of fixes from the net and neither work - the Partition table appears to be OK and when I try and edit Grub in the terminal on the Live CD it tells me grub is not installed.

Sorry to be a pain, I know this is probably simple but I'm getting a tad confused now!

---

### Post by oldfred on 2011-08-28
What version of Ubuntu. Grub error 17 is from grub legacy which Ubuntu has not used as the default since 9.04, but you could have it from upgrades to Ubuntu or if you changed boot loaders from grub2.

Post this from liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

If you just need to reinstall grub2's boot loader to sdb.
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Matt Gotts on 2011-09-01
Hi, sorry for delay in replying, been busy so couldn't get to PC to do this.

OK, I've downloaded the Boot Info program and got a results.txt.  I'm a little worried that this may confuse as I realised after the Desktop CD loaded that I'd left the BIOS switched to boot from the drive with XP on, rather than that with Xubuntu.  In answer to the query, I am running Xubuntu 10.10 installed from the said desktop CD, with Windows XP SP3 also installed.

Here's the Results file (hope this inserts...)

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb1 starts at sector 16128.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   160,055,594   160,055,532   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1              16,128    84,791,069    84,774,942   7 NTFS / exFAT / HPFS
/dev/sdb2          84,791,131   240,119,807   155,328,677   f W95 Extended (LBA)
/dev/sdb5          84,791,133   166,706,504    81,915,372   7 NTFS / exFAT / HPFS
/dev/sdb6    *    166,707,200   225,300,479    58,593,280  83 Linux
/dev/sdb7         225,302,528   240,119,807    14,817,280  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7208348C083450F9                       ntfs       Boot
/dev/sdb1        00000000495CD7A9                       ntfs       DOCUMENTS
/dev/sdb5        7EE854C2E85479FB                       ntfs       Spare
/dev/sdb6        33d0720c-ebe7-48ae-8f24-51f45bb0ffc7   ext3       
/dev/sdb7        57a72cd2-232a-4ef1-9272-ff4e4eb5f2e1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
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
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=33d0720c-ebe7-48ae-8f24-51f45bb0ffc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=33d0720c-ebe7-48ae-8f24-51f45bb0ffc7 ro single 
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
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7208348c083450f9
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
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=57a72cd2-232a-4ef1-9272-ff4e4eb5f2e1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 105.398578644 = 113.170862080  boot/grub/core.img                             1
 105.421947479 = 113.195954176  boot/grub/grub.cfg                             1
 105.463321686 = 113.240379392  boot/initrd.img-2.6.35-22-generic              5
 105.391822815 = 113.163608064  boot/vmlinuz-2.6.35-22-generic                 3
 105.463321686 = 113.240379392  initrd.img                                     5
 105.391822815 = 113.163608064  vmlinuz                                        3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  83 49 ed 1b 5e 1d 84 02  81 0f 99 57 ea 3e 07 d9  |.I..^......W.>..|
00000010  9e e0 ff e4 76 20 12 0c  fe dd 3d a3 3d db 61 fb  |....v ....=.=.a.|
00000020  75 a6 55 a3 d2 53 55 7c  8f 0c f5 f1 82 bf f5 05  |u.U..SU|........|
00000030  b6 19 c4 4b ed d9 63 2e  7c 17 cd ff df b8 3b 86  |...K..c.|.....;.|
00000040  9d dc 31 a1 8d 9a 28 08  19 8b 5f b5 27 3b 6c a7  |..1...(..._.';l.|
00000050  65 28 c7 e1 dd 3e 25 31  ad d6 eb 17 c9 52 fb 5b  |e(...>%1.....R.[|
00000060  54 19 f6 0f 03 58 ea 85  50 4c 04 57 49 6c 86 92  |T....X..PL.WIl..|
00000070  8b 0f 56 5c 20 e8 44 b4  d1 db eb cd e3 bf 40 45  |..V\ .D.......@E|
00000080  b2 4c c5 bd 26 3f 1f 21  69 06 08 2a 62 8c f6 2e  |.L..&?.!i..*b...|
00000090  f4 df 3d 8f 6c d8 18 5b  2d 80 2c 37 f3 a1 06 8c  |..=.l..[-.,7....|
000000a0  88 b0 90 ee 7c c6 4d 33  b4 50 0f 52 d8 47 55 ec  |....|.M3.P.R.GU.|
000000b0  c1 ff 51 b3 9f 81 06 42  ee ff db 7c 55 d3 3e bc  |..Q....B...|U.>.|
000000c0  e0 c7 9e 30 fb 3d 5c 34  43 66 11 a0 e0 9b 67 19  |...0.=\4Cf....g.|
000000d0  d9 bf 9d b4 86 bd c5 57  50 b9 cc 14 bc 54 e5 7d  |.......WP....T.}|
000000e0  07 fc 18 1e 2e bd 58 2c  fb 8d 5a cd 7b b9 71 43  |......X,..Z.{.qC|
000000f0  c4 5c 30 e3 3b 3d c7 7e  6f 1c fc cb 79 03 f7 ea  |.\0.;=.~o...y...|
00000100  00 33 bd ef f8 70 37 20  90 03 0d 8d a8 ad f6 6a  |.3...p7 .......j|
00000110  a3 94 71 f0 fa 0e f7 6f  39 da b4 8c 76 6c 18 04  |..q....o9...vl..|
00000120  38 f0 82 1d e0 54 62 66  ab ba 84 07 22 84 83 66  |8....Tbf...."..f|
00000130  63 a5 fe 4d 8e 65 af 2f  c1 25 44 d2 f0 48 16 ad  |c..M.e./.%D..H..|
00000140  e9 21 f2 37 59 4b b8 74  d1 78 fc ac bd 0e 32 e1  |.!.7YK.t.x....2.|
00000150  f0 92 a9 02 c4 60 a1 3d  f1 c0 04 94 f2 b4 70 ed  |.....`.=......p.|
00000160  c0 b3 d1 53 1a 5c b0 17  40 25 f9 82 ea 1f 1f 6c  |...S.\..@%.....l|
00000170  4f 01 19 f3 60 6a 7b 8f  aa ec 5b e1 82 42 e8 12  |O...`j{...[..B..|
00000180  05 d2 ea 5c 9b e8 60 fa  c9 ed f5 9b 5f 2c 06 c1  |...\..`....._,..|
00000190  37 7a a8 02 12 44 4c 6c  af 0f 16 96 42 b6 8f 3a  |7z...DLl....B..:|
000001a0  ec 7b ec 72 4a 42 d1 17  e6 69 0f 13 02 be db fa  |.{.rJB...i......|
000001b0  6f 91 96 c1 c4 2a 6c 77  1f 56 9f e3 46 96 00 fe  |o....*lw.V..F...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 ec ed e1 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff ee ed  e1 04 b7 12 7e 03 00 00  |............~...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

I'll reset the PC now and boot with the BIOS switched to boot from the second HDD with Xubuntu on.  For reference, if I boot as the PC is now, XP loads without any hint of Linux, if I boot with the second HDD as boot I get Grub Error 17.

I also tried to follow the 'restore the boot loader' link but got an error that grub (as a command) wasn't recognised.

Back soon...

---

### Post by Matt Gotts on 2011-09-01
OK, booted with second drive as main, run same thing and here's the result

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb1 starts at sector 16128.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   160,055,594   160,055,532   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1              16,128    84,791,069    84,774,942   7 NTFS / exFAT / HPFS
/dev/sdb2          84,791,131   240,119,807   155,328,677   f W95 Extended (LBA)
/dev/sdb5          84,791,133   166,706,504    81,915,372   7 NTFS / exFAT / HPFS
/dev/sdb6    *    166,707,200   225,300,479    58,593,280  83 Linux
/dev/sdb7         225,302,528   240,119,807    14,817,280  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7208348C083450F9                       ntfs       Boot
/dev/sdb1        00000000495CD7A9                       ntfs       DOCUMENTS
/dev/sdb5        7EE854C2E85479FB                       ntfs       Spare
/dev/sdb6        33d0720c-ebe7-48ae-8f24-51f45bb0ffc7   ext3       
/dev/sdb7        57a72cd2-232a-4ef1-9272-ff4e4eb5f2e1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
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
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=33d0720c-ebe7-48ae-8f24-51f45bb0ffc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=33d0720c-ebe7-48ae-8f24-51f45bb0ffc7 ro single 
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
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 33d0720c-ebe7-48ae-8f24-51f45bb0ffc7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7208348c083450f9
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
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=57a72cd2-232a-4ef1-9272-ff4e4eb5f2e1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 105.398578644 = 113.170862080  boot/grub/core.img                             1
 105.421947479 = 113.195954176  boot/grub/grub.cfg                             1
 105.463321686 = 113.240379392  boot/initrd.img-2.6.35-22-generic              5
 105.391822815 = 113.163608064  boot/vmlinuz-2.6.35-22-generic                 3
 105.463321686 = 113.240379392  initrd.img                                     5
 105.391822815 = 113.163608064  vmlinuz                                        3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  83 49 ed 1b 5e 1d 84 02  81 0f 99 57 ea 3e 07 d9  |.I..^......W.>..|
00000010  9e e0 ff e4 76 20 12 0c  fe dd 3d a3 3d db 61 fb  |....v ....=.=.a.|
00000020  75 a6 55 a3 d2 53 55 7c  8f 0c f5 f1 82 bf f5 05  |u.U..SU|........|
00000030  b6 19 c4 4b ed d9 63 2e  7c 17 cd ff df b8 3b 86  |...K..c.|.....;.|
00000040  9d dc 31 a1 8d 9a 28 08  19 8b 5f b5 27 3b 6c a7  |..1...(..._.';l.|
00000050  65 28 c7 e1 dd 3e 25 31  ad d6 eb 17 c9 52 fb 5b  |e(...>%1.....R.[|
00000060  54 19 f6 0f 03 58 ea 85  50 4c 04 57 49 6c 86 92  |T....X..PL.WIl..|
00000070  8b 0f 56 5c 20 e8 44 b4  d1 db eb cd e3 bf 40 45  |..V\ .D.......@E|
00000080  b2 4c c5 bd 26 3f 1f 21  69 06 08 2a 62 8c f6 2e  |.L..&?.!i..*b...|
00000090  f4 df 3d 8f 6c d8 18 5b  2d 80 2c 37 f3 a1 06 8c  |..=.l..[-.,7....|
000000a0  88 b0 90 ee 7c c6 4d 33  b4 50 0f 52 d8 47 55 ec  |....|.M3.P.R.GU.|
000000b0  c1 ff 51 b3 9f 81 06 42  ee ff db 7c 55 d3 3e bc  |..Q....B...|U.>.|
000000c0  e0 c7 9e 30 fb 3d 5c 34  43 66 11 a0 e0 9b 67 19  |...0.=\4Cf....g.|
000000d0  d9 bf 9d b4 86 bd c5 57  50 b9 cc 14 bc 54 e5 7d  |.......WP....T.}|
000000e0  07 fc 18 1e 2e bd 58 2c  fb 8d 5a cd 7b b9 71 43  |......X,..Z.{.qC|
000000f0  c4 5c 30 e3 3b 3d c7 7e  6f 1c fc cb 79 03 f7 ea  |.\0.;=.~o...y...|
00000100  00 33 bd ef f8 70 37 20  90 03 0d 8d a8 ad f6 6a  |.3...p7 .......j|
00000110  a3 94 71 f0 fa 0e f7 6f  39 da b4 8c 76 6c 18 04  |..q....o9...vl..|
00000120  38 f0 82 1d e0 54 62 66  ab ba 84 07 22 84 83 66  |8....Tbf...."..f|
00000130  63 a5 fe 4d 8e 65 af 2f  c1 25 44 d2 f0 48 16 ad  |c..M.e./.%D..H..|
00000140  e9 21 f2 37 59 4b b8 74  d1 78 fc ac bd 0e 32 e1  |.!.7YK.t.x....2.|
00000150  f0 92 a9 02 c4 60 a1 3d  f1 c0 04 94 f2 b4 70 ed  |.....`.=......p.|
00000160  c0 b3 d1 53 1a 5c b0 17  40 25 f9 82 ea 1f 1f 6c  |...S.\..@%.....l|
00000170  4f 01 19 f3 60 6a 7b 8f  aa ec 5b e1 82 42 e8 12  |O...`j{...[..B..|
00000180  05 d2 ea 5c 9b e8 60 fa  c9 ed f5 9b 5f 2c 06 c1  |...\..`....._,..|
00000190  37 7a a8 02 12 44 4c 6c  af 0f 16 96 42 b6 8f 3a  |7z...DLl....B..:|
000001a0  ec 7b ec 72 4a 42 d1 17  e6 69 0f 13 02 be db fa  |.{.rJB...i......|
000001b0  6f 91 96 c1 c4 2a 6c 77  1f 56 9f e3 46 96 00 fe  |o....*lw.V..F...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 ec ed e1 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff ee ed  e1 04 b7 12 7e 03 00 00  |............~...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Hope this helps, like I said I'm very grateful for the assistance.

Matt

---

### Post by oldfred on 2011-09-01
Your 10.10 Maverick uses grub2, but you have an old grub legacy MBR looking in sdb1 to boot.

You should just install grub2's boot loader to the MBR of sdb and it should work. You have what looks like a valid grub.cfg with windows already as a choice if you then boot sdb. Leave the windows boot loader in sda and if you every have problems with sdb you can at least boot sda by changing BIOS.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb6 and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdb6 if not correct:
sudo fdisk -l
#confirm that linux is sdb6
sudo mount /dev/sdb6/mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

Grub does not use boot flag, windows does. But a few BIOS need a boot flag on a primary partition to let you boot at all. I would just move the boot flag on sdb to any primary partition. But if you have had grub try to boot without a BIOS error then it is not important.

---

### Post by Hakunka-Matata on 2011-09-02
[B]

sudo mount /dev/sdxy /mnt[/B]                                          
# e.g.* sdb6*

**sudo grub-install --root-directory=/mnt /dev/sdx**    
**# example:**  *sudo grub-install --root-directory=/mnt /dev/sd**a***

# in grub 1.99, introduced with ubuntu 11.04, natty narwhal, a new switch is available
**sudo grub-install --boot-directory=/mnt/boot /dev/sdx**

---

### Post by Matt Gotts on 2011-09-08
Fantastic - I am now writing this from within my Xubuntu install which successfully boots.  Thanks everyone for the help.

Small note that there should have been an extra space in the mount instruction above - once I realised that everything was easy.

Now to sort my silent PC...!!!:lolflag:

---

