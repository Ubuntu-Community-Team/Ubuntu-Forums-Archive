---
title: "Installed alongside XP, can't boot into Ubuntu (10.10)"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by donovanh on 2010-10-20
Hi,

I've just installed 10.10 using the most basic options in the installer and allocated space on my boot disk to share it between Ubuntu with XP.

The installation seems to have gone ahead without any glitches, except on reboot, it boots straight into Windows with no option to select Ubuntu.

How can I fix this?

Cheers,

Don

---

### Post by Mark Phelps on 2010-10-20
First thing you want to do is confirm that MS Windows still works OK.  Asking because we're getting a lot of posts from folks who thought their side-by-side install went OK only to lose their MS Windows install as a side-effect.

Then, I would boot into an Ubuntu desktop CD and select the Try mode -- to run it in memory.  Once into a desktop, open a terminal and run "sudo fdisk -lu" (that's a lowercase L, not a one). That will list out your partitions so we can see what's installed.

Could be that all you would have to do is then reinstall GRUB from the Ubuntu CD.

---

### Post by drs305 on 2010-10-20
When you reboot as Mark suggests, you might hold down the SHIFT key just to see if the Grub menu displays. Normally if there is a glitch it's the other way around in a successful install - it boots directly to Ubuntu and doesn't display Windows.

It would certainly be odd if Grub was installed but was booting the Windows OS, but stranger things have happened; and holding the SHIFT key during the early stages of the boot doesn't take much extra effort.

---

### Post by donovanh on 2010-10-20
Thank you for the quick replies! Firstly, Windows seems fine.

I have two other harddrives, which include various files. They seem fine when I access them. However, Partition Magic shows the boot drive and one of the files drives as "bad", even though they do seem alright.

I booted into LiveCD and ran fdisk:

(The 64gb drive is my boot drive, and where I've installed Ubuntu alongside XP.

----
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c137426

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976735934   488367936    7  HPFS/NTFS
/dev/sda2       976735935   976768064       16065    f  W95 Ext'd (LBA)
/dev/sda5       976752000   976768064        8032+   7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x86518651

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   625121279   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbf7fbf7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    76148099    38074018+   7  HPFS/NTFS
/dev/sdb2        76144638   125033894    24444628+   5  Extended
/dev/sdb5        76144640   122927103    23391232   83  Linux
/dev/sdb6       122929152   125044735     1057792   82  Linux swap / Solaris

Disk /dev/sdh: 4008 MB, 4008706048 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7829504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x003dcf1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *          63     7829503     3914720+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(486, 254, 63) logical=(487, 92, 53)
----

Any ideas what this means?

Cheers,

D

---

### Post by drs305 on 2010-10-20
If the Ubuntu install went fine and it's booting to Windows, the most likely thing is that Grub was installed in one of the non-booting MBRs.

Please go to this site, download the script and run it from a LiveCD:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Post the contents of RESULTS.txt , which will show us what and where the boot files are as well as if/where the Ubuntu bootloader looks.

---

### Post by donovanh on 2010-10-20
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       76143952 sectors, but according to the info from 
                       fdisk, it has 76148036 sectors.
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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,735,934   976,735,872   7 HPFS/NTFS
/dev/sda2         976,735,935   976,768,064        32,130   f W95 Ext d (LBA)
/dev/sda5         976,752,000   976,768,064        16,065   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    76,148,099    76,148,037   7 HPFS/NTFS
/dev/sdb2          76,144,638   125,033,894    48,889,257   5 Extended
/dev/sdb5          76,144,640   122,927,103    46,782,464  83 Linux
/dev/sdb6         122,929,152   125,044,735     2,115,584  82 Linux swap / Solaris

/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb5
the logical partition /dev/sdb6 is not contained in the extended partition /dev/sdb2

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 4008 MB, 4008706048 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7829504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             63     7,829,503     7,829,441   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2E040B0C040AD72D                       ntfs       Photo Etc                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0AD3D40C7ED029F0                       ntfs                                     
/dev/sda                                                via_raid_member                               
/dev/sdb1        5AF0F25DF0F23EB7                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        fd2a31b8-6c20-477b-959e-e446ce7b7d28   ext4                                     
/dev/sdb6        91c8a503-9dda-45b2-bff1-7b9c87b23ea2   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        14A41690A4167508                       ntfs       Files                         
/dev/sdc: PTTYPE="dos" 
/dev/sdh1        F898-8E28                              vfat       DON                           
/dev/sdh: PTTYPE="dos" 
error: /dev/mapper/no: No such file or directory
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: raid: No such file or directory
error: sets: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdh1        /media/DON               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set fd2a31b8-6c20-477b-959e-e446ce7b7d28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set fd2a31b8-6c20-477b-959e-e446ce7b7d28
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
	search --no-floppy --fs-uuid --set fd2a31b8-6c20-477b-959e-e446ce7b7d28
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=fd2a31b8-6c20-477b-959e-e446ce7b7d28 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set fd2a31b8-6c20-477b-959e-e446ce7b7d28
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=fd2a31b8-6c20-477b-959e-e446ce7b7d28 ro single 
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
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set fd2a31b8-6c20-477b-959e-e446ce7b7d28
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set fd2a31b8-6c20-477b-959e-e446ce7b7d28
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 5af0f25df0f23eb7
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
UUID=fd2a31b8-6c20-477b-959e-e446ce7b7d28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=91c8a503-9dda-45b2-bff1-7b9c87b23ea2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  46.1GB: boot/grub/core.img
  54.2GB: boot/grub/grub.cfg
  39.3GB: boot/initrd.img-2.6.35-22-generic
  46.1GB: boot/vmlinuz-2.6.35-22-generic
  39.3GB: initrd.img
  46.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  00 00 00 89 9d e8 fb ff  ff 39 9d bc fb ff ff 0f  |.........9......|
00000010  84 cc 00 00 00 f6 47 21  01 6a 00 58 0f 95 c0 40  |......G!.j.X...@|
00000020  09 47 24 e9 b9 00 00 00  ff 15 ac 10 40 00 3b c3  |.G$.........@.;.|
00000030  89 85 e8 fb ff ff 75 0a  c7 85 e8 fb ff ff e3 03  |......u.........|
00000040  00 00 53 68 f8 ee 00 00  68 10 00 00 20 ff 76 30  |..Sh....h... .v0|
00000050  e8 6d b3 ff ff 83 c4 10  ff b5 e8 fb ff ff 6a 10  |.m............j.|
00000060  ff 76 30 e8 11 bb ff ff  ff b5 e4 fb ff ff ff 76  |.v0............v|
00000070  30 e8 ce ac ff ff eb 69  ff 15 ac 10 40 00 3b c3  |0......i....@.;.|
00000080  89 85 e8 fb ff ff 75 0a  c7 85 e8 fb ff ff e3 03  |......u.........|
00000090  00 00 53 68 f5 ee 00 00  68 10 00 00 20 ff 76 30  |..Sh....h... .v0|
000000a0  e8 1d b3 ff ff 83 c4 10  ff b5 e8 fb ff ff 6a 10  |..............j.|
000000b0  ff 76 30 e8 c1 ba ff ff  eb 27 53 68 f9 ee 00 00  |.v0......'Sh....|
000000c0  6a 20 ff 76 30 e8 f8 b2  ff ff 83 c4 10 ff b5 e4  |j .v0...........|
000000d0  fb ff ff ff 76 30 e8 69  ac ff ff 89 9d e8 fb ff  |....v0.i........|
000000e0  ff 8b 85 e8 fb ff ff 53  89 85 cc fb ff ff 8d 85  |.......S........|
000000f0  c4 fb ff ff 50 6a 0c ff  b5 dc fb ff ff ff 75 20  |....Pj........u |
00000100  ff b5 e0 fb ff ff ff 76  30 e8 63 2b 00 00 ff b5  |.......v0.c+....|
00000110  d8 fb ff ff e8 7f 08 01  00 8b 85 e8 fb ff ff 8b  |................|
00000120  4d fc 5f 5e 5b e8 0b fd  00 00 c9 c2 20 00 cc cc  |M._^[....... ...|
00000130  cc cc cc 8b ff 55 8b ec  83 ec 14 53 56 8b 75 08  |.....U.....SV.u.|
00000140  57 8b 7d 0c ff 77 10 ff  76 18 e8 3e 05 01 00 6a  |W.}..w..v..>...j|
00000150  ff ff 77 18 89 45 0c ff  77 14 ff 76 18 e8 00 f8  |..w..E..w..v....|
00000160  ff ff 8b d8 85 db 75 08  6a 08 58 e9 fa 00 00 00  |......u.j.X.....|
00000170  6a 00 6a 30 ff 76 30 e8  06 b2 ff ff 53 ff 75 14  |j.j0.v0.....S.u.|
00000180  89 45 08 ff 75 0c ff 75  10 6a 00 68 9c ef 00 00  |.E..u..u.j.h....|
00000190  50 ff 76 30 e8 29 b2 ff  ff 8b 45 10 83 65 f4 00  |P.v0.)....E..e..|
000001a0  83 c4 20 89 45 f0 8b 47  20 6a 00 89 45 f8 8d 45  |.. .E..G j..E..E|
000001b0  ec 50 6a 0b ff 75 1c 89  5d ec ff 75 20 ff 00 fe  |.Pj..u..]..u ...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d8 c9 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d8  c9 02 00 50 20 00 00 00  |...........P ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg no raid sets 
=============================== StdErr Messages: ===============================

ERROR: via: wrong # of devices in RAID set "via_chfcgigaia" [1/2] on /dev/sda
ERROR: removing inconsistent RAID set "via_chfcgigaia"
ERROR: no RAID set found
ERROR: via: wrong # of devices in RAID set "via_chfcgigaia" [1/2] on /dev/sda
ERROR: only one argument allowed for this option
ERROR: via: wrong # of devices in RAID set "via_chfcgigaia" [1/2] on /dev/sda
ERROR: removing inconsistent RAID set "via_chfcgigaia"
ERROR: no RAID set found
ERROR: via: wrong # of devices in RAID set "via_chfcgigaia" [1/2] on /dev/sda
ERROR: removing inconsistent RAID set "via_chfcgigaia"
ERROR: no RAID set found
ERROR: via: wrong # of devices in RAID set "via_chfcgigaia" [1/2] on /dev/sda
ERROR: only one argument allowed for this option

```

---

### Post by drs305 on 2010-10-20
Yes, Grub was installed in sda instead of sdb.

It's easy enough to fix from the LiveCD:
Mount your Ubuntu partition:
```
sudo mount /dev/sdb5 /mnt/
```

Install Grub2 to the sdb MBR:
```
sudo grub-install --root-directory=/mnt /dev/sdb
```

Note you don't use the partition number in this command.

After rebooting, you may need to run "sudo update-grub" if it doesn't pick up Windows in the Grub menu.

---

### Post by donovanh on 2010-10-20
Thank you for the edit, I'll check out the code tags.

It seems that sda1 has some leftover boot stuff from when I used it as the boot drive last year. If that has confused Ubuntu into putting bootloader into the wrong place, how would I best fix it?

One other thing I noticed... gparted shows the 64gb OS drive as "unallocated".

---

### Post by donovanh on 2010-10-20
Got it sorted. Thank you for your assistance!

I checked Disk Utility, and all the drives are showing up as they should. Windows also boots without any issue.

:guitar:

---

### Post by sanjeet252 on 2010-10-21
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,371   976,772,063   874,373,693   f W95 Ext d (LBA)
/dev/sda5         102,398,373   307,194,929   204,796,557   7 HPFS/NTFS
/dev/sda6         307,194,993   511,991,549   204,796,557   7 HPFS/NTFS
/dev/sda7         511,991,613   737,270,909   225,279,297   7 HPFS/NTFS
/dev/sda8         737,271,108   807,271,107    70,000,000   7 HPFS/NTFS
/dev/sda9         807,272,448   831,270,911    23,998,464  82 Linux swap / Solaris
/dev/sda10        831,272,960   861,270,015    29,997,056  83 Linux
/dev/sda11        861,272,064   976,772,063   115,500,000  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       172de4ba-e153-433f-9e4d-faf206e36615   ext3                                     
/dev/sda11       0bf50e21-ec04-49b4-bd7e-dbed77cd17d3   ext2                                     
/dev/sda1        80841A45841A3E5A                       ntfs       Programs                      
/dev/sda2: PTTYPE="dos" 
/dev/sda5        76248E54248E16F1                       ntfs       Music                         
/dev/sda6        CC809CA2809C9494                       ntfs       Files & Work                  
/dev/sda7        D29CA6A69CA68497                       ntfs       Pics & Vids                   
/dev/sda8        8658AE7758AE65A1                       ntfs       Ubuntu                        
/dev/sda9        63a84f1d-a396-4d21-bde5-673f3ee0c22f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

========================== sda10/boot/grub/grub.cfg: ==========================

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
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set 172de4ba-e153-433f-9e4d-faf206e36615
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set 172de4ba-e153-433f-9e4d-faf206e36615
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 172de4ba-e153-433f-9e4d-faf206e36615
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=172de4ba-e153-433f-9e4d-faf206e36615 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 172de4ba-e153-433f-9e4d-faf206e36615
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=172de4ba-e153-433f-9e4d-faf206e36615 ro single 
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 172de4ba-e153-433f-9e4d-faf206e36615
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 172de4ba-e153-433f-9e4d-faf206e36615
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 80841a45841a3e5a
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

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=172de4ba-e153-433f-9e4d-faf206e36615 /               ext3    errors=remount-ro 0       1
# /media/storage was on /dev/sda11 during installation
UUID=0bf50e21-ec04-49b4-bd7e-dbed77cd17d3 /media/storage  ext2    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=63a84f1d-a396-4d21-bde5-673f3ee0c22f none            swap    sw              0       0

=================== sda10: Location of files loaded by Grub: ===================


 434.8GB: boot/grub/core.img
 434.8GB: boot/grub/grub.cfg
 434.8GB: boot/initrd.img-2.6.35-22-generic
 434.7GB: boot/vmlinuz-2.6.35-22-generic
 434.8GB: initrd.img
 434.7GB: vmlinuz

```

---

### Post by drs305 on 2010-10-21
sanjeet252,

Welcome to Ubuntu and the Ubuntu forums.

Grub does not appear to be installed in the MBR. 

If you installed for the first time, this may be because the Grub files are too far into the disk to be recognized. I've been told that if this occurs immediately after an installation an "unknown filesystem" error message is generated. However, since you have Windows and no Grub, you may not get that message.

Check your BIOS and make sure that the settings permit large drives. I don't know the exact terminology. If you find such a setting and can change it in BIOS, reboot and see if Grub now works.

If you don't find a setting for large drives, or if that isn't the issue, you can try to reinstall Grub 2. 

Boot to the Live CD Desktop and run these commands to reinstall Grub to the MBR. In the first command you designate the partition (sda10) but in the second *only* the drive (sda).
```

sudo mount /dev/sda10 /mnt/
sudo grub-install --root-directory=/mnt /dev/sda
```

Note: I added code tags to your post. To generate the code tags while you are writing the post you click on the # icon in the post's menubar, then paste between the [noparse]```
 
```[/noparse] tags.

---

