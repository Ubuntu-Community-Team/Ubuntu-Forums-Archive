---
title: "Another 10.04 grub problem"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Shunt on 2010-05-11
Well, like so many others, I can't boot into my newly installed Ubuntu Lucid Lynx.

There's no problems with the installation, everything looks ok when I boot through the Live CD (or USB-stick in my case) and check things out.

But when I try to boot the system normally, I get the "no boot device - insert boot disk and press any key" message.

My system is a mini-itx, Intel D510MO w. a single 2TB HDD (WD Green). I've been reading up for the last 6-7hrs while trying different ways to install (partitioning etc). Found out there's issues with manually partitioning a 2TB HDD, so on my last few tries I've let the installer handle that.

I've also tried most of the "easy to find" solutions (which pretty much are the same, with variations) as:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)

Ubuntu partitions my HD (/dev/sda) as:
```

/dev/sda1	unknown					1.00MiB		bios_grub
/dev/sda2	ext4		/media/<serial>		1.81TiB
/dev/sda3	linux-swap				5.71GiB

```


boot_info_script055 gives me (I guess the first few lines about core.img is a big hint, hehe):
(oh, also ignore /dev/sdc ... 2:nd usb-stick)
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 2048 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048         4,095         2,048 Bios Boot Partition
/dev/sda2           4,096 3,895,052,287 3,895,048,192 Linux or Data
/dev/sda3   3,895,052,288 3,907,028,991    11,976,704 Linux Swap

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  52    31,283,909    31,283,858   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8053 MB, 8053063680 bytes
183 heads, 32 sectors/track, 2685 cylinders, total 15728640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32    15,728,639    15,728,608   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        4e8513ae-869e-438e-abb3-4e2d402be761   ext4                                     
/dev/sda3        20abe5d3-ff63-4b33-8cc3-7fc1eb0f3b1e   swap                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        382F-2E36                              vfat       Cruzer                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1498-55DF                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Cruzer            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 4e8513ae-869e-438e-abb3-4e2d402be761
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 4e8513ae-869e-438e-abb3-4e2d402be761
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 4e8513ae-869e-438e-abb3-4e2d402be761
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4e8513ae-869e-438e-abb3-4e2d402be761 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 4e8513ae-869e-438e-abb3-4e2d402be761
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4e8513ae-869e-438e-abb3-4e2d402be761 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 4e8513ae-869e-438e-abb3-4e2d402be761
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 4e8513ae-869e-438e-abb3-4e2d402be761
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=4e8513ae-869e-438e-abb3-4e2d402be761 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=20abe5d3-ff63-4b33-8cc3-7fc1eb0f3b1e none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 148.3GB: boot/grub/core.img
1430.3GB: boot/grub/grub.cfg
 148.3GB: boot/initrd.img-2.6.32-21-generic
 148.3GB: boot/vmlinuz-2.6.32-21-generic
 148.3GB: initrd.img
 148.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 2f 00 20 08  |............/. .|
00000200

```

Any help deeply appreciated.

Also, anyone know if this issue is in the Server Edition? All 10.04? 
I'm more or less building a NAS-system here, I just liked the idea of a desktop environment for coding (which I do a lot of).

---

### Post by kansasnoob on 2010-05-11
The error is obvious:

> File system:       **[COLOR="Red"]Bios Boot Partition[/COLOR]**

Since Ubuntu will be your only OS (it appears) you need to start over. (Regardless you need to start over.)

Boot a Live CD, go to Gparted and select the drive, then click on Device, and Create Partition Table.

As it is the whole drive is a BIOS boot partition :)

---

### Post by Shunt on 2010-05-11
> **kansasnoob said:**
> As it is the whole drive is a BIOS boot partition :)

Well, the /dev/sda1 is a BIOS Boot... and it's a 1mb partition.

From what I've read, grub2 need this to be able to boot at all on a single 2TB drive. Ubuntu resides on sda2.

These figures are from when I let the Ubuntu installer do all the work (ie. let it use the whole HDD as it chooses).
```

/dev/sda1	unknown					1.00MiB		bios_grub
/dev/sda2	ext4		/media/<serial>		1.81TiB
/dev/sda3	linux-swap				5.71GiB

```

I've tried to manually create partitions, but the installer always reserved a 1mb sda1 partition for bios_grub.

Will using parted (or gparted) to partition the hd before installation have any impact on my problems?

Re-installing is no problem, as this is a clean install, nothing on the HD except Ubuntu.

---

### Post by darkod on 2010-05-11
This is the core issue:

GUID Partition Table detected.

When disks started growing over 1TB they started to use GPT instead of the good old DOS partition table. And that uses the small bios boot partition.

What Kansas said, deleting all partitions and creating new partition table should work, because the new table would be DOS type. I'm not sure if it can be used on 2TB disk though, haven't worked with them. Google should help you out.

Just deleting the partitions doesn't help, the partition table needs to be recreated as DOS type, if you want to give it a shot.

Alternatively, this is a fix for Grub2 when used in a system with both DOS and GPT disks (but note that this is not your case). Maybe it can help.
[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)

---

### Post by Shunt on 2010-05-11
> **darkod said:**
> This is the core issue:
I'm not sure if it can be used on 2TB disk though, haven't worked with them. Google should help you out.

Just deleting the partitions doesn't help, the partition table needs to be recreated as DOS type, if you want to give it a shot.


Google is full of semi-worthless info about the 2TB drives. :)

I'll try to manually create the partition-table tomorrow (0.30 am, and off the bed soon I guess) and then reinstall. Hopefully it'll work, despite GPT. I'd like to mount / on a 80gb (or so) partition, and leave the rest 1.9-ish TB for a /nas partition.

---

### Post by kansasnoob on 2010-05-11
> **Shunt said:**
> Well, the /dev/sda1 is a BIOS Boot... and it's a 1mb partition.

From what I've read, grub2 need this to be able to boot at all on a single 2TB drive. Ubuntu resides on sda2.

These figures are from when I let the Ubuntu installer do all the work (ie. let it use the whole HDD as it chooses).
```

/dev/sda1	unknown					1.00MiB		bios_grub
/dev/sda2	ext4		/media/<serial>		1.81TiB
/dev/sda3	linux-swap				5.71GiB

```

I've tried to manually create partitions, but the installer always reserved a 1mb sda1 partition for bios_grub.

Will using parted (or gparted) to partition the hd before installation have any impact on my problems?

Re-installing is no problem, as this is a clean install, nothing on the HD except Ubuntu.

I have a bit of a problem even taking you seriously :confused:

You have a new 2TB drive and you know nothing about partitioning! Do you really plan on just tossing everything together in two or three partitions?

Look:

[ATTACH]156537[/ATTACH]

That drive is 1/4th the size of yours!

---

### Post by darkod on 2010-05-11
It seems you can use DOS MBR on 2TB disk:
[http://www.tomshardware.co.uk/forum/233291-14-what-difference](http://www.tomshardware.co.uk/forum/233291-14-what-difference)

Creating the new parttion table will replace the GPT partition table so your disk will not be GPT any more, which is what you want. It should work fine after that.

And Kansas really has a point about making some kind of partitioning plan, not just a single ~2TB partition. You have plenty of space, leave yourself options to install or test another OS later, organize your data not only in separate folders but on separate partitions, etc.

Also you could have one partition for storing regular backups in a quick way. If you have single partition and it gets corrupted, goodbye.

Of course having backups on the same hdd is not enough, but you could copy them from time to time on external disks too, etc.

I'm just thinking aloud here, of course it depends how you need and want to use your computer. :)

---

### Post by Shunt on 2010-05-11
> **kansasnoob said:**
> You have a new 2TB drive and you know nothing about partitioning! Do you really plan on just tossing everything together in two or three partitions?


Yeah, I do... 

Thought I'd mentioned it, but... seems I didn't.
This system is intended for a low-energy NAS-server and a small internal LAMP/print server. And Squeezebox Server (but that's beside the point).

I've had a Slackware server running for about 10yrs, but it's grown old & beyond upgrading, so... hence the new system.

I've run Ubuntu on my laptop for a few years, so... choose it for my NAS server. I could go for the Server Edition, but.. I'd kind of like the idea of (for once) coding in a nice KDE/Gnome environment instead of a boring remote session.

---

### Post by Shunt on 2010-05-11
> **darkod said:**
> It seems you can use DOS MBR on 2TB disk:
[http://www.tomshardware.co.uk/forum/233291-14-what-difference](http://www.tomshardware.co.uk/forum/233291-14-what-difference)

Thanks v. much, I'll look into that tomorrow. 

> 
Also you could have one partition for storing regular backups in a quick way. If you have single partition and it gets corrupted, goodbye.


Well, like I said in my reply to Kansas; this system's gonna be a NAS, pretty much. And I've always done my backups to an always-mounted USB-stick, which I empty to a DVD when needed.

This is not meant to be a system where I store sensitive data at all. It's pretty much gonna be photos, music and videos. And all photos & music are backed up on 2 other systems, and if some videos gets fried, I can live with that.

---

### Post by frantid on 2010-05-11
If you want to stay with gpt, here's a good site:

[http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)

this deals with booting:
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)

I suppose since bluray rips are 25gig, and who knows how big a 3d clip will be.  All movie collectors will end up with at least 1 large GPT disk.  At least we aren't required to run OS X to get it up and running.

---

### Post by Shunt on 2010-05-11
> **frantid said:**
> If you want to stay with gpt, here's a good site:

[http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)

this deals with booting:
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)


Thanks... will read when sleep restores brain from mush. :)

The fun thing is, my mobo; Intel D510MO supports EFI, so I should have an in there, but... updated to latest BIOS to no avail. Not found anything about it in BIOS either.

Currently setting up the HD manually. If it works; great. Looking for the easiest way out. I should be in bed by now, but... can't sleep when I'm working on something. :p

---

### Post by Shunt on 2010-05-11
No luck so far... manually created partitions with (g)parted.
/dev/sda1 ... 80 gb for /
/dev/sda2 ... 2  gb for swap
/dev/sda3 ... the rest of 2tb /nas

Installed nicely, but no boot. It's still recognized as "GUID Partition Table detected." ... 

(again with 2 USB-sticks inserted)...
```

Noot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 151298690 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34   163,846,934   163,846,901 Linux or Data
/dev/sda2     163,846,935   167,943,509     4,096,575 Linux Swap
/dev/sda3     167,943,510 3,907,024,064 3,739,080,555 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8053 MB, 8053063680 bytes
183 heads, 32 sectors/track, 2685 cylinders, total 15728640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    15,728,639    15,728,608   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  52    31,283,909    31,283,858   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4a1af4f0-3508-4d85-bfb5-748889c942cb   ext4                                     
/dev/sda2        5cb3a9ab-b897-4ddf-b1a8-f67982e3f3f9   swap                                     
/dev/sda3        be2a1df9-9330-4f8c-8644-5a626b523c4d   ext4                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        A495-026D                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        382F-2E36                              vfat       Cruzer                        
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdc1        /media/Cruzer            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 4a1af4f0-3508-4d85-bfb5-748889c942cb
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
search --no-floppy --fs-uuid --set 4a1af4f0-3508-4d85-bfb5-748889c942cb
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4a1af4f0-3508-4d85-bfb5-748889c942cb
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4a1af4f0-3508-4d85-bfb5-748889c942cb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4a1af4f0-3508-4d85-bfb5-748889c942cb
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4a1af4f0-3508-4d85-bfb5-748889c942cb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4a1af4f0-3508-4d85-bfb5-748889c942cb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4a1af4f0-3508-4d85-bfb5-748889c942cb
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
UUID=4a1af4f0-3508-4d85-bfb5-748889c942cb /               ext4    errors=remount-ro 0       1
# /nas was on /dev/sda3 during installation
UUID=be2a1df9-9330-4f8c-8644-5a626b523c4d /nas            ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=5cb3a9ab-b897-4ddf-b1a8-f67982e3f3f9 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/core.img
  71.1GB: boot/grub/grub.cfg
  77.4GB: boot/initrd.img-2.6.32-21-generic
  77.4GB: boot/vmlinuz-2.6.32-21-generic
  77.4GB: initrd.img
  77.4GB: vmlinuz

```

---

### Post by mbrennwa on 2010-05-17
I have the same problem, with the same motherboard (I have a Tranquil PC Barebones Server, see here: [http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVER_Series_2.html](http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVER_Series_2.html) )

However, I believe the problem is not directly related to Ubuntu or GRUB etc. I think it's the motherboard, which does not like to boot hard disks with GPT partition tables, see here:
   [http://tranquilpc-support.co.uk/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=259](http://tranquilpc-support.co.uk/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=259)

According to the following post, it seems to be possible to convince the motherboard to boot GPT disks:
   [http://communities.intel.com/message/79431](http://communities.intel.com/message/79431)

However, I do not understand what the author of this post meant by "The trick was to set the partition in the protective mbr as active", or how to achieve this.

I'd really appreaciate any clues or hints on how to make this work.

Also, do you guys think that we could convince Intel to fix their BIOS or firmware or something so that GPT disks would boot without problems?

Matthias

---

### Post by Shunt on 2010-05-17
I've meant to post an update for a few days now, but been busy with work and such...

I gave up on the whole GPT issue, killed the partition table and replaced with a good old MBR.

I didn't need GPT at all, and after spending some long nights trying many variations of the same few solutions which didn't work... well, it just wasn't worth it.

Also, I'd never heard of GPT before, didn't feel like reading up on it either. My hard disk experience before this have been; buy, install, partition and format, hehe.

Did a quick read [http://communities.intel.com/message/79431](http://communities.intel.com/message/79431) (at work, and clocking out in 10 so... :p) but if I understand it correctly, they created a small MBR-partition, set it to active without installing an OS on it. Which, for some reason, made it possible to install & boot Ubuntu on the rest of GPT-disk.


Pretty much have my installation complete, so not really in a mood to start experimenting again. :)

---

### Post by darkod on 2010-05-17
> **Shunt said:**
> I've meant to post an update for a few days now, but been busy with work and such...

I gave up on the whole GPT issue, killed the partition table and replaced with a good old MBR.

I didn't need GPT at all, and after spending some long nights trying many variations of the same few solutions which didn't work... well, it just wasn't worth it.

Also, I'd never heard of GPT before, didn't feel like reading up on it either. My hard disk experience before this have been; buy, install, partition and format, hehe.

Did a quick read [http://communities.intel.com/message/79431](http://communities.intel.com/message/79431) (at work, and clocking out in 10 so... :p) but if I understand it correctly, they created a small MBR-partition, set it to active without installing an OS on it. Which, for some reason, made it possible to install & boot Ubuntu on the rest of GPT-disk.


Pretty much have my installation complete, so not really in a mood to start experimenting again. :)

Yeap, you made the right choice. :) Good old DOS/MBR disks. :)

As for that small partition + GPT system, they call it BIOS Boot partition or similar. The point is probably that BIOS will know and call it, when it's there. The problem is, as we can see in most threads here, it's NEVER there. :)

The GPT system is still not needed right now I guess. But very soon, when disks are 10TB, we'll have to start learning new things it seems...

---

### Post by Shunt on 2010-05-17
> **darkod said:**
> As for that small partition + GPT system, they call it BIOS Boot partition or similar. The point is probably that BIOS will know and call it, when it's there. The problem is, as we can see in most threads here, it's NEVER there. :)

Well, I had the BIOS boot partition (Ubuntu even created it for me during disk setup if I hadn't created it manually) but it didn't help. Maybe because my system hates GPT.
And, as I'm no hard disk guru, I have no idea if you can create a MBR and a GPT partition table on the same drive (without creating a hybrid which I read was not a good idea). If you can, I guess the solution might be to create the BIOS BP on the MBR-part.

But, I guess it all ads up to the same reason I never buy the first edition of any new "toy" (iPod, PSP etc) that comes out on the market. There's bound to be bugs left in the system. :p

As far at GPT goes, the only good thing about it is if you need many, many partitions, or partitions bigger than 2TB. Not something many'll need.

---

### Post by srs5694 on 2010-05-17
Sorry I've overlooked this thread. As the author of GPT fdisk, I think I can dispel some of the fog, even if it's a bit late for some....

> **Shunt said:**
> ```

Noot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 151298690 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
```

Clearly the boot info script was getting confused, since it's provided three mutually exclusive diagnoses of the MBR. FWIW, both GRUB 2 and patched versions of GRUB Legacy can boot GPT disks, but they must have their stage 1 loaders installed in the MBR for this to work, at least on BIOS-based systems.

> **mbrennwa]According to the following post, it seems to be possible to convince the  motherboard to boot GPT disks:
   [http://communities.intel.com/message/79431](http://communities.intel.com/message/79431)

However, I do not understand what the author of this post meant by "The  trick was to set the partition in the protective mbr as active", or how  to achieve this.[/quote]

GPT includes what's known as a "protective MBR" -- a (more-or-less) legal MBR partition table that serves the purpose of telling GPT-unaware partitioning tools that the whole disk is in use, as in:

```

$ **sudo fdisk -l /dev/sda**

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488386583+  ee  GPT
```

It's possible to use fdisk to mark the single partition contained therein as active (aka bootable). Use the 'a' option in Linux fdisk to do this.

FWIW, I've got an [entire Web page](http://www.rodsbooks.com/gdisk/bios.html) devoted to BIOS/GPT incompatibilities. For the most part, the fixes to these problems are simple -- *if* you know about them. These problems also seem to be pretty rare, which makes it hard for me to investigate them. I "lucked out" by discovering that I've got a computer with an afflicted BIOS. That one's problem would have been hellish for most people to debug. The other big problem I know of is this refusal to boot unless an MBR partition is marked as active. That one's relatively well documented, too. Unfortunately, neither problem will be quickly discovered in a Web search if you're having problems booting.

[quote=mbrennwa]Also, do you guys think that we could convince Intel to fix their BIOS  or firmware or something so that GPT disks would boot without problems?[/quote]

I've got one Intel board that has no problems along these lines, so they've probably already fixed their BIOSes said:**
> As for that small partition + GPT system, they call it BIOS Boot  partition or similar. The point is probably that BIOS will know and call  it, when it's there. The problem is, as we can see in most threads  here, it's NEVER there.

Actually, you're confusing two very different things:


[list]
[*]A [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) is a type of partition on GPT disks in which boot loaders (GRUB 2, in particular) can store some of their boot code. This partition takes the place of the unallocated partitions immediately following the MBR on MBR disks, in which boot loaders have traditionally stored "extra" code that doesn't fit in the MBR's code area. GRUB 2 will work without a BIOS Boot Partition, but as the link explains, it's less reliable without a BIOS Boot Partition.
[*]A [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) is a GPT protective MBR that's been modified to include up to three ordinary primary MBR partitions. This is a flaky and dangerous hack that is nonetheless sometimes useful in coaxing Windows to boot on otherwise GPT-centric systems (such as Macs using Boot Camp). On a Linux-only system, there's no need for a hybrid MBR, except as a last-resort option to work around buggy BIOS implementations. If it's not absolutely necessary, it's like planting a land mine in your back yard: Unwise.
[/list]


> **darkod]The GPT system is still not needed right now I guess. But very soon,  when disks are 10TB, we'll have to start learning new things it seems... 	[/quote]

With 512-byte sectors, the limit is 2TiB. [Seagate has recently announced plans for a 3TiB drive,](http://www.thinq.co.uk/news/2010/5/17/exclusive-seagate-confirms-3tb-drive/) to be released later this year, so MBR just won't cut it for this up-and-coming drive. (Well, you could stretch MBR out to 4TiB by putting everything starting at slightly before the 2TiB mark in one partition, but that's awkward, ugly, and incompatible with many OSes, so I don't recommend it.) There are also hardware RAID arrays today that require GPT.

[quote=Shunt]And, as I'm no hard disk guru, I have no idea if you can create a MBR  and a GPT partition table on the same drive (without creating a hybrid  which I read was not a good idea). If you can, I guess the solution  might be to create the BIOS BP on the MBR-part.[/quote]

There are two ways to put both MBR and GPT data on one disk. One is a hybrid MBR, which as I say is a bad idea unless it's absolutely required. The other is to create a GPT setup and then use fdisk or some other GPT-unaware tool to create a separate MBR. The result is that most OSes will view the disk as an MBR disk said:**
> As far at GPT goes, the only good thing about it is if you need many,  many partitions, or partitions bigger than 2TB. Not something many'll  need.

Actually, GPT has several other minor advantages over MBR:


[list]
[*]No distinction between primary, extended, and logical partitions. This primary/extended/logical distinction has caused untold grief over the years, so I'm glad to see it'll be joining the dodo before too long....
[*]GPT includes backups of all its important data structures: One copy goes at the start of the disk, the other at its end. This should theoretically improve reliability.
[*]CRC32 checksums of all the important data structures are stored on the disk, which enables detection of corrupt data structures, again theoretically improving reliability.
[*]Partitions can be named, enabling easier identification of partitions in partition editing tools. (These names are independent of the names assigned to the filesystems contained in the partitions.)
[*]Partition type codes are 128-bit UUIDs rather than 8-bit bytes, which theoretically means less chance of collision. In practice, though, there's already one huge collision, since both Windows and Linux use the same UUID type code for their data partitions.
[*]GPT is clearly defined in a standards document. MBR, by contrast, just sort of grew haphazardly, and differing interpretations have caused problems over the year. Of course, in practice this may not be much of an advantage. The two best-documented BIOS incompatibilities are actually cured by deviating from the GPT standard.
[/list]


Anyhow, I hope this helps clear up some questions.

---

### Post by Shunt on 2010-05-18
> **srs5694 said:**
> 
I've got one Intel board that has no problems along these lines, so they've probably already fixed their BIOSes; however, that said, it's conceivable (maybe even likely) that they'll never release fixes for older motherboards.


Well, my first action after the first fail was to install the newest bios firmware, 4/14/2010, still no go.

And I read all the pages you linked to, including your own, and while they were very informative they didn't really get me anywhere.
Probably because I tried to get my server up & running when I didn't really have the time to do get into it. Real life always intrudes. :p

I usually have the OS on a smallish separate disk, but it wasn't doable on this system so... at least it's up & running.

---

### Post by bluesound on 2010-08-02
i had got same problem.
(d510mo + WD 2TB green)

but...you guys helped me to solve this problem.

this is what i did.

1. usb boot (server ed.) with (installed) HDD.

2. sudo activate /dev/sda 1  (after this... #1 partition of /dev/sda is set to active partition)

thank you all...

o my god...my poor english....

---

### Post by linutx on 2010-08-02
uhm, you have the latest bios? see if [this]("http://communities.intel.co.jp/thread/9779;jsessionid=229170E33C4600F927A879B384B5DC2C.node5COMS") helps

---

