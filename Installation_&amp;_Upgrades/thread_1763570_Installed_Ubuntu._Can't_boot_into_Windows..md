---
title: "Installed Ubuntu. Can't boot into Windows."
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by anilkiral on 2011-05-20
I have a computer with a 160GB HDD. It was divided into two partitions (120GB and 40GB). 120GB partition had Windows XP installed on it and the 40GB partition had some music, images, etc.

I really wanted to try out Ubuntu so I deleted everything on the 40GB partition to install Ubuntu on it. I download Ubuntu 11.04 and burned it onto a DVD - booted from it.

When installing, it gave me the option of installing with windows side by side, wiping windows and installing just Ubuntu and an option saying something else. I chose the option to install it with windows side by side but It didn't give me the option to install ubuntu on the 40GB partition. It was going to install it on the same partition as windows. So I went back and chose 'something else'. I divided the 40GB partition into two partitions - 1GB for swap space and the rest for Ubuntu.

After installing Ubuntu, I had some problems with the GRUB loader. I was just getting a blank screen but solved that problem after some research. Now I can see the GRUB bootloader but Windows XP is not listed.

How can I put Windows XP onto the list so I can boot into it? Btw I'm new to linux.

---

### Post by Hedgehog1 on 2011-05-20
We need to get a look at your install to get an idea what is going on.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by linuxinstalledfromhdd on 2011-05-20
And you can try this walk-through..

[http://cinderbox.net/2011/02/01/how-to-recovery-grub2-after-borking/](http://cinderbox.net/2011/02/01/how-to-recovery-grub2-after-borking/)

---

### Post by anilkiral on 2011-05-20
> **Hedgehog1 said:**
> We need to get a look at your install to get an idea what is going on.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

OK. I've run the script. Here are the results:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    80,523,263    80,521,216  83 Linux
/dev/sda2          80,525,310   312,560,639   232,035,330   f W95 Extended (LBA)
/dev/sda5          82,477,773   312,560,639   230,082,867   7 NTFS / exFAT / HPFS
/dev/sda6          80,525,312    82,477,055     1,951,744  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01bc553c-a653-4667-b7bf-cb67139e9af6   ext4       
/dev/sda5        F06C7F716C7F3188                       ntfs       
/dev/sda6        23bdc40e-2c98-4e11-83f4-963cc2f6bd2a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/F06C7F716C7F3188  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 01bc553c-a653-4667-b7bf-cb67139e9af6
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 01bc553c-a653-4667-b7bf-cb67139e9af6
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01bc553c-a653-4667-b7bf-cb67139e9af6
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=01bc553c-a653-4667-b7bf-cb67139e9af6 ro  vga=792 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01bc553c-a653-4667-b7bf-cb67139e9af6
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=01bc553c-a653-4667-b7bf-cb67139e9af6 ro single  vga=792 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01bc553c-a653-4667-b7bf-cb67139e9af6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01bc553c-a653-4667-b7bf-cb67139e9af6
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=23bdc40e-2c98-4e11-83f4-963cc2f6bd2a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.135009766 = 21.619802112   boot/grub/core.img                             1
   4.177791595 = 4.485869568    boot/grub/grub.cfg                             1
   5.630096436 = 6.045270016    boot/initrd.img-2.6.38-8-generic               2
  20.133281708 = 21.617946624   boot/vmlinuz-2.6.38-8-generic                  1
   5.630096436 = 6.045270016    initrd.img                                     2
  20.133281708 = 21.617946624   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  7c 34 ca d8 a4 50 a3 5b  44 db 9a 6c 9f fd b2 a5  ||4...P.[D..l....|
00000010  44 45 40 dc 1d 92 3e 25  8a 8b 66 7e 5a fb ea 27  |DE@...>%..f~Z..'|
00000020  18 dc df dd 3b cc 3c 30  7b 34 f5 a5 90 21 87 03  |....;.<0{4...!..|
00000030  9a 6e 04 e8 39 82 02 4c  46 ca c0 b4 41 15 78 28  |.n..9..LF...A.x(|
00000040  05 bb 5d 72 25 10 86 5e  46 c7 66 dc 1b 2a 0b 82  |..]r%..^F.f..*..|
00000050  62 8e 53 07 b4 3a 78 7a  05 9c 46 19 9b ae a3 a5  |b.S..:xz..F.....|
00000060  00 bb 2f 23 21 a1 94 7d  72 78 f2 59 4a b4 f0 cd  |../#!..}rx.YJ...|
00000070  50 80 42 32 15 07 a1 f2  e3 8f 5a ed a9 e4 72 ea  |P.B2......Z...r.|
00000080  86 df 72 31 b1 71 c7 8a  2d 47 29 ac bb 16 9a 39  |..r1.q..-G)....9|
00000090  ae 18 bd 2e 42 c5 60 e5  4b 95 c3 48 0e 58 d6 23  |....B.`.K..H.X.#|
000000a0  05 d7 3e 3b 32 f3 6d 6b  b9 3d ef 32 72 98 41 67  |..>;2.mk.=.2r.Ag|
000000b0  b3 3a 2c 54 8e 47 7f 65  13 aa e8 ce 97 76 45 5b  |.:,T.G.e.....vE[|
000000c0  92 b5 2b 85 0e 21 88 26  54 53 ba bb 89 9e 16 75  |..+..!.&TS.....u|
000000d0  74 26 e1 60 1d d2 0e b8  45 1a d7 ff fa b3 6c 6d  |t&.`....E.....lm|
000000e0  cf eb 0e e5 a9 5e 56 0b  2f 44 f4 80 2b 5b 03 3d  |.....^V./D..+[.=|
000000f0  28 98 13 29 75 5e 4c 30  b7 41 a9 ae ec 8c c3 16  |(..)u^L0.A......|
00000100  58 97 4b d4 31 7d b3 04  10 97 9f 80 fe 2b 5b 74  |X.K.1}.......+[t|
00000110  5c b9 c2 80 a6 30 06 51  97 d3 be 5d a3 f4 ae 68  |\....0.Q...]...h|
00000120  02 4a df 0e d6 18 75 a5  90 a8 88 3c 8f 43 23 94  |.J....u....<.C#.|
00000130  52 b2 72 d1 2e 83 de eb  42 20 db 86 96 ff f1 61  |R.r.....B .....a|
00000140  c2 43 1d c5 ed 5a d9 3f  ee ec 9c d3 22 ec 8a 73  |.C...Z.?...."..s|
00000150  0b 0e ab ab 38 50 e2 0f  18 35 46 4f 57 71 ae b3  |....8P...5FOWq..|
00000160  4b 46 ca 16 00 00 90 44  46 3d 06 58 20 50 68 97  |KF.....DF=.X Ph.|
00000170  51 30 e3 c7 bb 6d a3 6c  b5 c2 a0 ab e1 84 59 db  |Q0...m.l......Y.|
00000180  3c 63 89 c0 1c 4b 12 8f  b5 e7 61 5d c3 11 75 b6  |<c...K....a]..u.|
00000190  de 87 16 e2 97 b4 82 a4  83 24 0e 73 78 68 8b 4a  |.........$.sxh.J|
000001a0  1a d2 7f 97 10 ef 11 73  08 98 86 a8 9f ae 49 42  |.......s......IB|
000001b0  31 0c 38 61 21 ae 92 49  73 a9 5c a1 63 46 00 fe  |1.8a!..Is.\.cF..|
000001c0  ff ff 07 fe ff ff cf ca  1d 00 33 c9 b6 0d 00 fe  |..........3.....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 c8 1d 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by anilkiral on 2011-05-20
> **linuxinstalledfromhdd said:**
> And you can try this walk-through..

[http://cinderbox.net/2011/02/01/how-to-recovery-grub2-after-borking/](http://cinderbox.net/2011/02/01/how-to-recovery-grub2-after-borking/)

I have tried this but it isn't working. I think this is only for adding a drive that has Ubuntu on it?

---

### Post by Hedgehog1 on 2011-05-20
The reason that XP is not showing is that windows will not boot from a logical partition.

Right now your XP partition is in a logical partition of extended partition /decs/sda2:

```
sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        
```

Right now you have:

/dev/sda1 EXT4 '/' Root)
/dev/sda2 extended partiton
__/dev/sda5 NTFS XP install
__/dev/sda6 Swap

For long term reliability, Windows prefers to be first on the disk, and then followed by Ubuntu.

The better layout is to have XP, and then your Ubuntu partitions.

/dev/sda1 NTFS XP Install
/dev/sda2 NTFS Shared files (music, photos, movies)
/dev/sda3 Extended partition to end of disk
__/dev/sda5 EXT4 '/' (root)
__/dev/sda6 EXT4 '/home' partition 
__/dev/sda7 Swap (Size of ram + 10%)

Moving this partitions around is rather a large job.  Thankfully we have quite a few folks on the forum who are very good with this.

How comfortable are you with doing this?

***The Hedge***

:KS

---

### Post by oldfred on 2011-05-20
To understand how windows works.:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Windows boots from a primary partition and any additional installs move the boot files from the second partition to the first primary partition with the boot flag. You had another install of windows in a primary partition and the boot files for XP were in that partition. 

The official windows way is to create a primary NTFS boot partition and add the XP boot files to that. 

But some old timers here have a work around that boots XP from a logical if you want to try that. You will not be able to run windows repairs and may have other issues but you can make it bootable.

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by anilkiral on 2011-05-30
> **Hedgehog1 said:**
> The reason that XP is not showing is that windows will not boot from a logical partition.

Right now your XP partition is in a logical partition of extended partition /decs/sda2:

```
sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        
```

Right now you have:

/dev/sda1 EXT4 '/' Root)
/dev/sda2 extended partiton
__/dev/sda5 NTFS XP install
__/dev/sda6 Swap

For long term reliability, Windows prefers to be first on the disk, and then followed by Ubuntu.

The better layout is to have XP, and then your Ubuntu partitions.

/dev/sda1 NTFS XP Install
/dev/sda2 NTFS Shared files (music, photos, movies)
/dev/sda3 Extended partition to end of disk
__/dev/sda5 EXT4 '/' (root)
__/dev/sda6 EXT4 '/home' partition 
__/dev/sda7 Swap (Size of ram + 10%)

Moving this partitions around is rather a large job.  Thankfully we have quite a few folks on the forum who are very good with this.

How comfortable are you with doing this?

***The Hedge***

:KS

Thank you very much. I think I can now see what the problem is. I don't know how to do this myself but I can do it if I can get some help/directions. I don't mind loosing Ubuntu as there is nothing important on it and I can reinstall it if I have to. But I don't want to loose anything on the Windows partition.

---

### Post by anilkiral on 2011-06-01
Anyone? I really need help with this.

---

### Post by oldfred on 2011-06-01
See post #7. You can make it work. Otherwise you will have to back up and reinstall.

There also are some tools that can convert partitions from logical to primary but you have to only 4 partitions. But these are more risky, better have really good backups.

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo sfdisk -d /dev/sdc > parts.txt


Use sfdisk to edit partitions and links to how to convert primary/logical
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

Whatever changes you make will require windows repairs and depending on what you do to Ubuntu reinstall of grub.

---

### Post by Pumalite on 2011-06-01
Erase the drive after saving your data. Install Windows in sda. After that make a partition for Ubuntu and install it

---

### Post by anilkiral on 2011-06-01
Problem solved. Thanks to oldfred and everyone who helped.

Followed instruction 1-5 on this thread and it worked:
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
(Booted XP from logical partition)

---

