---
title: "Grub error 15 after Lucid Upgade"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2010-05-14
I have just tried to upgrade to Lucid and received the grub error 15. After checking here I downloaded the bootinfoscript from [http://bootinfoscript.sourcefrge.net]("http://bootinfoscript.sourcefrge.net") As advised by this I am posting the results file for analysis below:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 1024. But according to the info from fdisk, 
                       sda6 starts at sector 106778624.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    43,006,004    43,005,942   7 HPFS/NTFS
/dev/sda2          43,006,005   312,560,639   269,554,635   f W95 Ext d (LBA)
/dev/sda5          43,006,068   106,777,599    63,771,532   7 HPFS/NTFS
/dev/sda6         106,778,624   312,559,615   205,780,992   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,496,379   312,496,317   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    21,061,214    21,061,152  83 Linux
/dev/sdc2          21,061,339    78,124,094    57,062,756   5 Extended
/dev/sdc5          74,830,833    78,124,094     3,293,262  82 Linux swap / Solaris
/dev/sdc6          21,061,341    74,830,769    53,769,429  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        572FEA5B7FC6993D                       ntfs       Black XP                      
/dev/sda2: PTTYPE="dos" 
/dev/sda5        B8DC366FDC3627D0                       ntfs       XP                            
/dev/sda6        76041EDF041EA1E3                       ntfs       Space                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EA743026742FF44B                       ntfs       MY DATA                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3d926c2d-98e9-46b6-b9dc-d0e719e4e770   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        9c2c8fa2-de6e-47d3-9d08-2467af924cc5   swap                                     
/dev/sdc6        8815b3ac-6091-4da3-a06a-4f6e5e253548   ext4       Home                          
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro,relatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 3d926c2d-98e9-46b6-b9dc-d0e719e4e770
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 3d926c2d-98e9-46b6-b9dc-d0e719e4e770
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
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 3d926c2d-98e9-46b6-b9dc-d0e719e4e770
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=3d926c2d-98e9-46b6-b9dc-d0e719e4e770 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 3d926c2d-98e9-46b6-b9dc-d0e719e4e770
	echo	Loading Linux 2.6.32-16-generic ...
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=3d926c2d-98e9-46b6-b9dc-d0e719e4e770 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 3d926c2d-98e9-46b6-b9dc-d0e719e4e770
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 3d926c2d-98e9-46b6-b9dc-d0e719e4e770
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 572fea5b7fc6993d
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=3d926c2d-98e9-46b6-b9dc-d0e719e4e770 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc6 during installation
UUID=8815b3ac-6091-4da3-a06a-4f6e5e253548 /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=9c2c8fa2-de6e-47d3-9d08-2467af924cc5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
   8.8GB: boot/grub/grub.cfg
   2.4GB: boot/initrd.img-2.6.32-16-generic
   2.3GB: boot/vmlinuz-2.6.32-16-generic
   2.4GB: initrd.img
   2.3GB: vmlinuz

=============================== sdc6/etc/fstab: ===============================

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdc5 swap swap defaults 0 0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  14 49 ca bc 3a c5 b4 6e  47 0a cc 00 c6 e5 2e 24  |.I..:..nG......$|
00000010  ee 05 f0 df a2 b1 86 c7  89 6b 72 e4 0d cd a7 e8  |.........kr.....|
00000020  2e 48 8f bd e5 22 65 c1  d1 10 6d 30 67 b7 3a 3d  |.H..."e...m0g.:=|
00000030  50 97 01 d1 9a 28 26 62  b0 52 9b 22 da eb 3c d3  |P....(&b.R."..<.|
00000040  0c 50 6e a5 35 57 cd 44  66 17 e6 d5 2a e7 4d c8  |.Pn.5W.Df...*.M.|
00000050  19 6d 50 4e 54 77 1b 4d  ef c8 e4 45 56 39 de 53  |.mPNTw.M...EV9.S|
00000060  87 0e ac bb 8d 31 0d 02  a0 4c 65 77 21 de 53 ed  |.....1...Lew!.S.|
00000070  36 93 53 a3 07 ef cb 43  3b 3c a0 09 51 96 3d 8a  |6.S....C;<..Q.=.|
00000080  a5 4d 12 3a 70 a4 9f 89  e6 13 6f 48 74 66 20 73  |.M.:p.....oHtf s|
00000090  12 c2 06 47 af d7 91 81  bc 49 d5 0d 13 3e 0c c1  |...G.....I...>..|
000000a0  e9 08 be e6 3d a3 dd f6  64 9c 8e 20 f1 19 6d 02  |....=...d.. ..m.|
000000b0  69 21 03 dc c6 be a6 e2  74 04 89 68 3e 53 b7 16  |i!......t..h>S..|
000000c0  a7 13 03 af 79 60 3a 93  48 b1 ec 1a 32 b6 c1 ba  |....y`:.H...2...|
000000d0  ea 40 de 33 9a 78 4c 42  b8 58 e2 b4 47 24 61 67  |.@.3.xLB.X..G$ag|
000000e0  a0 cf b9 e8 40 96 33 54  b8 af 2a 39 49 20 0d cb  |....@.3T..*9I ..|
000000f0  66 b6 01 c0 52 a6 03 11  19 8f 6d 52 bb e8 16 4c  |f...R.....mR...L|
00000100  6e 86 db a0 76 91 0e 18  34 51 98 ab 21 ca 9a d7  |n...v...4Q..!...|
00000110  b7 f9 33 b7 80 13 07 21  68 6c cf d9 45 b6 38 0a  |..3....!hl..E.8.|
00000120  77 68 7d 55 c3 c4 41 08  6e 73 07 8e 28 8a 49 dc  |wh}U..A.ns..(.I.|
00000130  0e f8 55 dc d2 e4 13 07  69 45 ab 08 8b a6 81 d4  |..U.....iE......|
00000140  71 e0 71 11 ca 98 eb 29  7c 4e 2c 5e d2 50 d3 ba  |q.q....)|N,^.P..|
00000150  f4 00 fd 14 94 06 d4 dd  46 7a 5b 2d 5c 65 91 b8  |........Fz[-\e..|
00000160  37 f7 09 38 eb ec 81 47  67 da cd a4 ce 1e 48 bf  |7..8...Gg.....H.|
00000170  43 57 54 e9 81 a8 df 85  b1 e6 69 89 83 10 bd 59  |CWT.......i....Y|
00000180  9f d0 eb 72 65 e5 06 30  c6 5a 2e 98 99 50 36 b6  |...re..0.Z...P6.|
00000190  01 0a 55 dd c6 19 0d 56  9d b8 4e 0f 3c 48 23 d6  |..U....V..N.<H#.|
000001a0  be 44 89 98 56 c0 35 73  0e 98 b5 2c 63 8f 15 15  |.D..V.5s...,c...|
000001b0  ea 41 da aa 07 94 38 0c  a2 1e a0 58 99 1e 00 fe  |.A....8....X....|
000001c0  ff ff 82 fe ff ff 16 75  34 03 4e 40 32 00 00 fe  |.......u4.N@2...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 d6 74 34 03 00 00  |...........t4...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```
Could somebody please take a look and let me know what they think. Thanks very much.

---

### Post by kansasnoob on 2010-05-14
What I see is two functional OS's:

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM


> sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


Not sure what's up here (we can revisit that later):

> sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab


So Lucid on sdc1 has grub2 and it's installed to the mbr of sda (maybe):

>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.


Anyway both sdb and sdc have legacy grub mbrs but you have no legacy grub files so the easiest thing would be to mount and chroot Ubuntu on sdc1 and install it's grub2 to all three drives mbrs like this (please copy-n-paste):

```
sudo mount /dev/sdc1 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

```
grub-install /dev/sdc
```

Note: if any of those three "grub-install" commands returns errors run "grub-install --recheck /dev/sd**[COLOR="Red"]X[/COLOR]**", of course replacing the **[COLOR="Red"]X[/COLOR]** with the proper device letter.

Then just exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

---

### Post by Julian David Pitt on 2010-05-14
Hi Kansasnoob
Thank you very much that, that sure fixed it for me my friend. I am not sure I understood what you did by the various mounts at the start, is there any chance you could explain that? I now see the different versions of grub was what was causing my issue. Is it worth me running the bootinfo script again as I saw some errors briefly on start up and you also mentioned:
> Not sure what's up here (we can revisit that later):
Thanks again.

---

### Post by kansasnoob on 2010-05-14
I'm fairly cooked right now, heck of a day :( But I've simply come to prefer restoring grub in a chroot so it deals with the installed operating systems packages rather than the packages on the Live CD. That's fairly critical now that we're dealing with systems that may have legacy grub or grub2.

But that is not always foolproof. I've not written full notes yet but I should. I've been intending to. A somewhat longer form of my mount and chroot procedure can be read here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

I shortened things for just installing grub to an mbr because it's not all needed in every circumstance.

Regarding the errors that you see, what are they? Do they appear when you boot all operating systems or only the one on sdc6?

That Lucid seems to be missing some boot files, but I'm also concerned about them both still showing (development branch). Are they properly updated?

When were your two Lucid's installed?

---

