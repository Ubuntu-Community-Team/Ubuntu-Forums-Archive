---
title: "HELP! Can't boot back into WIn XP"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by jim78 on 2011-01-24
I had two xp partitions on my hd - one for net and one for photoshop. I deleted the net xp partition and replaced it with Ubuntu, but now I can't boot into my second xp partition that's still there. Does this have something to do with the MBR/Bootloader etc? If so, how do i go about fixing it?

Any help would be greatly appreciated as I really need access to my photoshop partition.

---

### Post by Quackers on 2011-01-24
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by jim78 on 2011-01-24
Contents of results.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdg5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     9,764,863     9,762,816  83 Linux
/dev/sda2           9,766,910   312,576,704   302,809,795   f W95 Ext d (LBA)
/dev/sda5    *     41,078,268    92,727,179    51,648,912   7 HPFS/NTFS
/dev/sda6          92,727,243   312,576,704   219,849,462   7 HPFS/NTFS
/dev/sda7           9,766,912    37,171,199    27,404,288  83 Linux
/dev/sda8          37,173,248    41,076,735     3,903,488  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,126   116,177,247   116,161,122   f W95 Ext d (LBA)
/dev/sdb5              16,128   116,177,247   116,161,120   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1              16,126   383,556,894   383,540,769   f W95 Ext d (LBA)
/dev/sdg5              16,128   383,556,894   383,540,767   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9e930a25-679e-4aaf-ba11-5eaf47789802   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        D87C164C7C162632                       ntfs       Photoshop                     
/dev/sda6        01CBB7EC0E0A9310                       ntfs       Photography 1                 
/dev/sda7        febe9bb4-b39d-4656-b0d7-b3012afd8f9c   ext4                                     
/dev/sda8        7beaf6c1-3e76-475a-905e-7a54e4e20854   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        01CBAD0F465D5EB0                       ntfs       Photography 2                 
/dev/sdb: PTTYPE="dos" 
/dev/sdg1: PTTYPE="dos" 
/dev/sdg5        19DB-0766                              vfat                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sdg5        /media/19DB-0766         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/Ubuntu 10.04 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 9e930a25-679e-4aaf-ba11-5eaf47789802
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 9e930a25-679e-4aaf-ba11-5eaf47789802
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9e930a25-679e-4aaf-ba11-5eaf47789802
	linux	/boot/vmlinuz-2.6.32-27-generic-pae root=UUID=9e930a25-679e-4aaf-ba11-5eaf47789802 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9e930a25-679e-4aaf-ba11-5eaf47789802
	echo	'Loading Linux 2.6.32-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-27-generic-pae root=UUID=9e930a25-679e-4aaf-ba11-5eaf47789802 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9e930a25-679e-4aaf-ba11-5eaf47789802
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9e930a25-679e-4aaf-ba11-5eaf47789802
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9e930a25-679e-4aaf-ba11-5eaf47789802 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=febe9bb4-b39d-4656-b0d7-b3012afd8f9c /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=7beaf6c1-3e76-475a-905e-7a54e4e20854 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.1GB: boot/grub/core.img
    .3GB: boot/grub/grub.cfg
   3.0GB: boot/initrd.img-2.6.32-27-generic-pae
   4.0GB: boot/vmlinuz-2.6.32-27-generic-pae
   3.0GB: initrd.img
   4.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  61 00 72 00 65 00 20 00  79 00 6f 00 75 00 20 00  |a.r.e. .y.o.u. .|
00000010  61 00 72 00 65 00 20 00  69 00 6e 00 73 00 74 00  |a.r.e. .i.n.s.t.|
00000020  61 00 6c 00 6c 00 69 00  6e 00 67 00 20 00 68 00  |a.l.l.i.n.g. .h.|
00000030  61 00 73 00 20 00 6e 00  6f 00 74 00 20 00 70 00  |a.s. .n.o.t. .p.|
00000040  61 00 73 00 73 00 65 00  64 00 20 00 57 00 69 00  |a.s.s.e.d. .W.i.|
00000050  6e 00 64 00 6f 00 77 00  73 00 20 00 4c 00 6f 00  |n.d.o.w.s. .L.o.|
00000060  67 00 6f 00 20 00 74 00  65 00 73 00 74 00 69 00  |g.o. .t.e.s.t.i.|
00000070  6e 00 67 00 20 00 74 00  6f 00 20 00 76 00 65 00  |n.g. .t.o. .v.e.|
00000080  72 00 69 00 66 00 79 00  20 00 69 00 74 00 73 00  |r.i.f.y. .i.t.s.|
00000090  20 00 63 00 6f 00 6d 00  70 00 61 00 74 00 69 00  | .c.o.m.p.a.t.i.|
000000a0  62 00 69 00 6c 00 69 00  74 00 79 00 20 00 77 00  |b.i.l.i.t.y. .w.|
000000b0  69 00 74 00 68 00 20 00  74 00 68 00 69 00 73 00  |i.t.h. .t.h.i.s.|
000000c0  20 00 76 00 65 00 72 00  73 00 69 00 6f 00 6e 00  | .v.e.r.s.i.o.n.|
000000d0  20 00 6f 00 66 00 20 00  57 00 69 00 6e 00 64 00  | .o.f. .W.i.n.d.|
000000e0  6f 00 77 00 73 00 2e 00  20 00 28 00 3c 00 41 00  |o.w.s... .(.<.A.|
000000f0  3e 00 54 00 65 00 6c 00  6c 00 20 00 6d 00 65 00  |>.T.e.l.l. .m.e.|
00000100  20 00 77 00 68 00 79 00  20 00 74 00 68 00 69 00  | .w.h.y. .t.h.i.|
00000110  73 00 20 00 74 00 65 00  73 00 74 00 69 00 6e 00  |s. .t.e.s.t.i.n.|
00000120  67 00 20 00 69 00 73 00  20 00 69 00 6d 00 70 00  |g. .i.s. .i.m.p.|
00000130  6f 00 72 00 74 00 61 00  6e 00 74 00 2e 00 3c 00  |o.r.t.a.n.t...<.|
00000140  2f 00 41 00 3e 00 29 00  00 00 00 00 00 00 02 50  |/.A.>.)........P|
00000150  00 00 00 00 2b 00 0f 00  d0 00 18 00 d1 10 ff ff  |....+...........|
00000160  82 00 68 00 61 00 73 00  20 00 6e 00 6f 00 74 00  |..h.a.s. .n.o.t.|
00000170  20 00 70 00 61 00 73 00  73 00 65 00 64 00 20 00  | .p.a.s.s.e.d. .|
00000180  57 00 69 00 6e 00 64 00  6f 00 77 00 73 00 20 00  |W.i.n.d.o.w.s. .|
00000190  4c 00 6f 00 67 00 6f 00  20 00 74 00 65 00 73 00  |L.o.g.o. .t.e.s.|
000001a0  74 00 69 00 6e 00 67 00  20 00 74 00 6f 00 20 00  |t.i.n.g. .t.o. .|
000001b0  76 00 65 00 72 00 69 00  66 00 79 00 20 00 80 fe  |v.e.r.i.f.y. ...|
000001c0  ff ff 07 fe ff ff fe c5  dd 01 90 19 14 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff 8e df  f1 04 35 a3 1a 0d 00 00  |..........5.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdg1

00000000  81 4f 1f 00 82 4f 1f 00  83 4f 1f 00 84 4f 1f 00  |.O...O...O...O..|
00000010  85 4f 1f 00 86 4f 1f 00  87 4f 1f 00 88 4f 1f 00  |.O...O...O...O..|
00000020  89 4f 1f 00 8a 4f 1f 00  8b 4f 1f 00 8c 4f 1f 00  |.O...O...O...O..|
00000030  8d 4f 1f 00 8e 4f 1f 00  8f 4f 1f 00 90 4f 1f 00  |.O...O...O...O..|
00000040  91 4f 1f 00 92 4f 1f 00  93 4f 1f 00 94 4f 1f 00  |.O...O...O...O..|
00000050  95 4f 1f 00 96 4f 1f 00  97 4f 1f 00 98 4f 1f 00  |.O...O...O...O..|
00000060  99 4f 1f 00 9a 4f 1f 00  9b 4f 1f 00 9c 4f 1f 00  |.O...O...O...O..|
00000070  9d 4f 1f 00 9e 4f 1f 00  9f 4f 1f 00 a0 4f 1f 00  |.O...O...O...O..|
00000080  a1 4f 1f 00 a2 4f 1f 00  a3 4f 1f 00 a4 4f 1f 00  |.O...O...O...O..|
00000090  a5 4f 1f 00 a6 4f 1f 00  a7 4f 1f 00 a8 4f 1f 00  |.O...O...O...O..|
000000a0  a9 4f 1f 00 aa 4f 1f 00  ab 4f 1f 00 ac 4f 1f 00  |.O...O...O...O..|
000000b0  ad 4f 1f 00 ae 4f 1f 00  af 4f 1f 00 b0 4f 1f 00  |.O...O...O...O..|
000000c0  b1 4f 1f 00 b2 4f 1f 00  b3 4f 1f 00 b4 4f 1f 00  |.O...O...O...O..|
000000d0  b5 4f 1f 00 b6 4f 1f 00  b7 4f 1f 00 b8 4f 1f 00  |.O...O...O...O..|
000000e0  b9 4f 1f 00 ba 4f 1f 00  bb 4f 1f 00 bc 4f 1f 00  |.O...O...O...O..|
000000f0  bd 4f 1f 00 be 4f 1f 00  bf 4f 1f 00 c0 4f 1f 00  |.O...O...O...O..|
00000100  c1 4f 1f 00 c2 4f 1f 00  c3 4f 1f 00 c4 4f 1f 00  |.O...O...O...O..|
00000110  c5 4f 1f 00 c6 4f 1f 00  c7 4f 1f 00 c8 4f 1f 00  |.O...O...O...O..|
00000120  c9 4f 1f 00 ca 4f 1f 00  cb 4f 1f 00 cc 4f 1f 00  |.O...O...O...O..|
00000130  cd 4f 1f 00 ce 4f 1f 00  cf 4f 1f 00 d0 4f 1f 00  |.O...O...O...O..|
00000140  d1 4f 1f 00 d2 4f 1f 00  d3 4f 1f 00 d4 4f 1f 00  |.O...O...O...O..|
00000150  d5 4f 1f 00 d6 4f 1f 00  d7 4f 1f 00 d8 4f 1f 00  |.O...O...O...O..|
00000160  d9 4f 1f 00 da 4f 1f 00  db 4f 1f 00 dc 4f 1f 00  |.O...O...O...O..|
00000170  dd 4f 1f 00 de 4f 1f 00  df 4f 1f 00 e0 4f 1f 00  |.O...O...O...O..|
00000180  e1 4f 1f 00 e2 4f 1f 00  e3 4f 1f 00 e4 4f 1f 00  |.O...O...O...O..|
00000190  e5 4f 1f 00 e6 4f 1f 00  e7 4f 1f 00 e8 4f 1f 00  |.O...O...O...O..|
000001a0  e9 4f 1f 00 ea 4f 1f 00  eb 4f 1f 00 ec 4f 1f 00  |.O...O...O...O..|
000001b0  ed 4f 1f 00 ee 4f 1f 00  ef 4f 1f 00 f0 4f 00 01  |.O...O...O...O..|
000001c0  01 01 0b fe ff ff 02 00  00 00 1f 5e dc 16 00 00  |...........^....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Quackers on 2011-01-24
Your Windows XP partition (sda5) has 2 problems.
Firstly, there are no XP boot files in it, and
secondly, XP is in a logical partition. Windows will not boot from a logical partition unless its boot files are in a primary partition.

The first problem can be fixed by running fixmbr from the command prompt in the Windows XP repair cd recovery console.
I'm really not sure how to advise you to fix the second problem.
Maybe some other users here have experience of changing logical partitions to primary partitions (if that's possible), but I'm afraid I don't :-(

Hopefully somebody else can clear this up for us :-)

---

### Post by jim78 on 2011-01-24
OK, thanks for your help. Would it be easier to do a fresh xp install after formatting the partition to primary? Or would i then run into problems booting into ubuntu?

---

### Post by Quackers on 2011-01-24
Well, sda5,6,7 & 8 are inside an extended partition (sda2) which makes things difficult. I would advise you to wait for somebody who has done something similar before, to post.
In the meantime you could google for how to change logical partitions to primary. The number of hits will give you an idea as to how possible it is.

---

### Post by oldfred on 2011-01-24
It is possible with many caveats to change a partition, but you still can only have 4 primary with one of those as extended. If your XP is in the middle it is just about impossible. Reinstall is one of the simple solutions. 

Other possibilities are to use gparted to copy the partition to a primary and repair it. While windows only lets its MBR boot loader boot primary partitions lilo will jump to any partition to boot and you can from Ubuntu do all the Windows XP repairs in a logical partition (except chkdsk).

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

Boot WinXP from extended partition - Herman
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)

---

### Post by jim78 on 2011-01-24
Thanks for the replies but I've decided to bite the bullet and just get rid of windows altogether. I can do a big chunk of photoshop stuff in gimp anyway, the rest I'll just have to find workarounds or beg to use someone's xp machine. It's probably the excuse I've been looking for.

---

### Post by Quackers on 2011-01-24
You're welcome, and good luck :-)

---

### Post by leclerc65 on 2011-01-24
> **jim78 said:**
> Thanks for the replies but I've decided to bite the bullet and just get rid of windows altogether. I can do a big chunk of photoshop stuff in gimp anyway, the rest I'll just have to find workarounds or beg to use someone's xp machine. It's probably the excuse I've been looking for.

VirtualBox is one workaround.

---

