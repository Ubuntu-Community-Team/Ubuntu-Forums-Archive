---
title: "Natty dual boot on separate hard drives"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by Cammer Pants on 2011-05-29
I've been trying to properly install grub for the past 3 days and failing every time.

I recently bought a new computer and would like to dual boot Windows 7 64 and Natty. On my previous machines, ubuntu installer has automatically detected windows. It does not do so on this machine.

I have three hard drives: 2 ssd's and a single 3 tb drive for storage.

I would like one ssd for windows 7 and one for natty.

Currently, I am able to boot into both OS's but only by altering the boot sequence of the drives from the bios. 

I am hesitant to install grub to the windows drive for fear I will lose the ability to boot into windows. I did this early in the discovery process and ended up having to reinstall windows. 

The results of the boot info script are as follows: 

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
256 heads, 63 sectors/track, 7268 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   117,229,567   116,760,576 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    23,480,319    23,478,272  83 Linux
/dev/sdb2          23,482,366   117,229,567    93,747,202   5 Extended
/dev/sdb5          23,482,368    97,699,839    74,217,472  83 Linux
/dev/sdb6          97,701,888   117,229,567    19,527,680  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 4,090,652,671 4,090,650,624  83 Linux
/dev/sdc2       4,090,652,672 5,860,532,223 1,769,879,552   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        06CB-AA3D                              vfat       
/dev/sda3        26ACD18EACD158BF                       ntfs       
/dev/sdb1        28199f42-c6b0-4814-a9c3-ffdd76225a17   ext4       
/dev/sdb5        2f0179a9-5cd3-4412-8c89-1644072f9c52   ext4       
/dev/sdb6        0a554dab-03a2-4914-9cf8-1b05c79f32d9   swap       
/dev/sdc1        88e87cec-795d-4b1d-955d-1a143daf9723   ext4       
/dev/sdc2        5A394D8C18309FF9                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/26ACD18EACD158BF  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb5        /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/88e87cec-795d-4b1d-955d-1a143daf9723 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_msdos
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="2"
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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 28199f42-c6b0-4814-a9c3-ffdd76225a17
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 28199f42-c6b0-4814-a9c3-ffdd76225a17
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 28199f42-c6b0-4814-a9c3-ffdd76225a17
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=28199f42-c6b0-4814-a9c3-ffdd76225a17 ro  splash vga=796  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 28199f42-c6b0-4814-a9c3-ffdd76225a17
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=28199f42-c6b0-4814-a9c3-ffdd76225a17 ro single  splash vga=796
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 28199f42-c6b0-4814-a9c3-ffdd76225a17
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 28199f42-c6b0-4814-a9c3-ffdd76225a17
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=28199f42-c6b0-4814-a9c3-ffdd76225a17 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=2f0179a9-5cd3-4412-8c89-1644072f9c52 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=0a554dab-03a2-4914-9cf8-1b05c79f32d9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.489166260 = 9.115172864    boot/grub/core.img                             1
   4.642700195 = 4.985061376    boot/grub/grub.cfg                             1
   2.336914062 = 2.509242368    boot/initrd.img-2.6.38-8-generic               2
   8.487438202 = 9.113317376    boot/vmlinuz-2.6.38-8-generic                  1
   2.336914062 = 2.509242368    initrd.img                                     2
   8.487438202 = 9.113317376    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 3d aa cb 06 4e  4f 20 4e 41 4d 45 20 20  |..)=...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```


I've tried manually telling grub to add windows to the list via adding an 11_Windows file to /grub.d but this didn't work. I tried doing this with various combinations of files and hard drive listings, along with combinations using drivemap -s . The contents of the file were based on instructions found here: [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/) . Currently, I have deleted this file in the interest of starting afresh.

I've also edited   /etc/default/grub to include GRUB_PRELOAD_MODULES="part_msdos"

Any help would be greatly, greatly appreciated.

---

### Post by Hedgehog1 on 2011-05-30
**EDIT:** FIXMBR info was the wrong info as MBR is not being used on your PC's SSD. (Thanks **srs5694**!)


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-30
Grub is failing to find windows on it's own because of a partition method that is cofusing it:

```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
256 heads, 63 sectors/track, 7268 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  **ee GPT**

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 **EFI System partition**
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   117,229,567   116,760,576 Data partition (Windows/Linux)
```

Others who know partition maps better may be able to tell you more of the details on what this means.

Selecting the drives from BIOS to boot has you working for now, so that give us time to figure out what your options are.

Right now, I am thinking that:

1) Have your Ubuntu SSD be the first to boot and **load GRUB from it only**.

2) Have a manual entry from the GRUB that chain-loads windows on it's own SSD.

As to how to do this, I will need to ask a few Ubuer-Ubuntu-Geeks.


Lastly, as a point of conversation, you appear to have split the 3 gig drive into EXT4 and NTFS.  Unless you really need EXT4 on this drive, making it all NTFS will make all data accessible by both Ubuntu and Windows.  I use a 1TB this way; just a thought.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-30
Until the calvary arrives, I think that if you setup your system to boot from the Ubuntu SSD, you may be able to chainload to the Windows SSD by using this in grub:


```
menuentry "Windows" {
        drivemap -s (hd0) (hd1)
	set root=(hd0,1)
	chainloader +1
}
```

However: *This comes with no warranty, expressed or implied. Your mileage may vary. No options are included in the Base sticker price. License, fees and dealer excise tax are not included.*

***The Hedge***

:KS

More mind-numbing GRUB data: [http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows]("http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows")

---

### Post by Cammer Pants on 2011-05-30
Thank you for your responses, Hedge.  Unfortunately, I get the same "invalid signature" error when I try to boot into windows from grub. I added the entry you suggested into 40_custom and it produced the same results as when I made the 11_Windows file. 

This grub is on my ubuntu ssd. I can only imagine that the efi on the Windows ssd is what is borking my system.

While we are on the topic, I also can't seem to set the timeout length for grub. I can only get the menu to appear at all by holding down shift while the machine starts. I haven't tried to edit this manually, but have only attempted to do so through a gui -- startup manager, I believe. 


I will be making up a backup disk as per your instructions as soon as I have the media to do so and am no longer exhausted. I spent the past few hours attempting to add blu-ray playback support (and failing at that too). :)

...Foiled all day long by newfangled technology ....

---

### Post by srs5694 on 2011-05-30
I'm 99% sure that Hedgehog1 is working under a mistaken assumption that renders his advice completely incorrect. This mistaken assumption is that you've got a BIOS-based computer. The fact that Windows installed to and boots from (sometimes) /dev/sda, which uses the GUID Partition Table (GPT), is a pretty clear indication that the computer uses a Unified Extensible Firmware Interface (UEFI) rather than a BIOS. To verify this, you could check the computer's or motherboard's specifications, or post the make and model here. (Most computers based on Intel's new Sandy Bridge chips, and some new AMD boards, use UEFI.)

UEFI computers boot in an entirely different way than do BIOS-based computers. Specifically, they don't use the MBR. Instead, they place files with .efi extensions in the EFI System Partition (your /dev/sda1). GRUB for EFI can chainload to one of these, but I don't know if GRUB for BIOS can do so.

Many UEFI computers have a BIOS compatibility mode, and my suspicion is that you've installed Linux in such a way that it's using this mode. The result is a computer with a sort of multiple personality disorder when it comes to booting.

The best solution is probably to re-install Linux using UEFI mode. I'm not sure exactly what steps you took to install Linux in the first place or what you might need to do to ensure that it installs in UEFI mode. Some of the answers may be specific to your motherboard.

Another option, which might or might not work, is to install [rEFIt](http://refit.sourceforge.net) in the EFI System Partition of /dev/sda. This is a boot loader that was originally built for Macs (which have used EFI since Apple's switch to Intel CPUs in 2006 or 2007). On Macs, it can boot OS X in EFI mode or Linux in BIOS compatibility mode. There's a chance it could do much the same for you, but launch Windows in UEFI mode and Linux in BIOS mode. OTOH, firmware and OS differences might make this solution not work. (Macs use the older EFI 1.x, whereas new PCs use 2.x, aka UEFI.) If you install rEFIt, you'll need to adjust your firmware to launch it rather than the Windows loader from the EFI System Partition. There should be a menu somewhere to let you do that.

Good luck.

---

### Post by Hedgehog1 on 2011-05-30
> **srs5694 said:**
> I'm 99% sure that Hedgehog1 is working under a mistaken assumption that renders his advice completely incorrect. 

If I had a nickel for every time somebody said that (and is usually right).  :D

If it weren't for bad ideas...


***The 'Not entirely UEFI compatible' Hedge***

:KS

---

### Post by Cammer Pants on 2011-05-30
> **srs5694 said:**
> I'm 99% sure that Hedgehog1 is working under a mistaken assumption that renders his advice completely incorrect. This mistaken assumption is that you've got a BIOS-based computer. The fact that Windows installed to and boots from (sometimes) /dev/sda, which uses the GUID Partition Table (GPT), is a pretty clear indication that the computer uses a Unified Extensible Firmware Interface (UEFI) rather than a BIOS. To verify this, you could check the computer's or motherboard's specifications, or post the make and model here. (Most computers based on Intel's new Sandy Bridge chips, and some new AMD boards, use UEFI.)

UEFI computers boot in an entirely different way than do BIOS-based computers. Specifically, they don't use the MBR. Instead, they place files with .efi extensions in the EFI System Partition (your /dev/sda1). GRUB for EFI can chainload to one of these, but I don't know if GRUB for BIOS can do so.

Many UEFI computers have a BIOS compatibility mode, and my suspicion is that you've installed Linux in such a way that it's using this mode. The result is a computer with a sort of multiple personality disorder when it comes to booting.

The best solution is probably to re-install Linux using UEFI mode. I'm not sure exactly what steps you took to install Linux in the first place or what you might need to do to ensure that it installs in UEFI mode. Some of the answers may be specific to your motherboard.

Another option, which might or might not work, is to install [rEFIt](http://refit.sourceforge.net) in the EFI System Partition of /dev/sda. This is a boot loader that was originally built for Macs (which have used EFI since Apple's switch to Intel CPUs in 2006 or 2007). On Macs, it can boot OS X in EFI mode or Linux in BIOS compatibility mode. There's a chance it could do much the same for you, but launch Windows in UEFI mode and Linux in BIOS mode. OTOH, firmware and OS differences might make this solution not work. (Macs use the older EFI 1.x, whereas new PCs use 2.x, aka UEFI.) If you install rEFIt, you'll need to adjust your firmware to launch it rather than the Windows loader from the EFI System Partition. There should be a menu somewhere to let you do that.

Good luck.

Thank you for the reply, srs5694. 

I don't have the time to implement some of your suggestions right now, but can tell you that my motherboard is a Gigabyte GA-870A-USB3 . 

Again, thank you very much. I will report back when I have more information.

---

### Post by srs5694 on 2011-05-30
I just did some Web searches, and the downloads section of the [manufacturer's Web page for the board](http://www.gigabyte.com/products/product-page.aspx?pid=3788#bios) does mention EFI support in the firmware, at least for the F4 revision. This makes my hypothesis about the cause of the problem a little more likely. Unfortunately, the manual I downloaded from the Web site doesn't say a word about EFI or UEFI features, and is pretty thin on boot options.

One other thought for a solution occurred to me: Instead of re-installing Ubuntu, it should be possible to convert your existing installation to boot using UEFI rather than BIOS. This would require installing a UEFI-capable boot loader, such as grub-efi or elilo. (I recommend the latter; in my limited experience, ELILO is more reliable than the current generation of GRUB for EFI. OTOH, ELILO can't boot Windows, so you'd need rEFIt in the picture to choose your OS, and use ELILO just to load Linux.) If you use ELILO, you'll need to copy your kernel and initial RAM disk to the EFI System Partition (but the elilo installer script should do this automatically).

It might also be necessary to remove the GRUB code from the MBR. This is easily done with dd:

```

sudo dd if=/dev/zero of=/dev/sdb bs=440 count=1

```

This command wipes the first 440 bytes of /dev/sdb clean, thus eliminating the BIOS version of GRUB from the MBR. You should only do this after you've installed an EFI-capable boot loader, though. You might also want to have a copy of [Super GRUB 2 Disk](http://www.supergrubdisk.org/) handy; it should enable you to boot into your regular installation if the EFI boot loader doesn't work.

---

### Post by Cammer Pants on 2011-06-01
Again thank you.

I am currently traveling and am away from my desktop but I think I am going to try to give grub-efi a go when I arrive home, then elilo if that doesn't work.

I bought this computer with the idea of creating something that can double as a work computer and as a media center that I share with my girlfriend. While a text boot list would certainly be superior to going into the bios every time, it does kind of break the polished appearance I was striving for. I was hoping to eventually get a graphical bootloader installed--like burg, maybe. I haven't yet researched whether burg is yet possible in this situation, but something like it is the eventual goal. 

It is rather embarrassing at the moment to require a trip to the bios when one desires a television viewing. (Assuming, of course, that someone had been previously using the Windows 7 OS on it).

Anyhow, thank for the suggestions and I will let you know how it goes when I return home.

---

### Post by srs5694 on 2011-06-01
FWIW, rEFIt is primarily a GUI boot loader (see the [screen shot on its Web page](http://refit.sourceforge.net/screen.html)). It tends to pick up video glitches (text-mode error messages over the GUI) when run on UEFI-based machines (vs. EFI-based Macs), though -- or maybe that's the version that's distributed with Ubuntu. Thus, you can use rEFIt in conjunction with a short timeout period on GRUB or ELILO to boot into Linux with minimal text-mode displays. The rEFIt glitches could be an issue, though.

---

### Post by ClickHeRe on 2011-08-12
Just for the record, I also have the same issue (stumbled upon this thread a few days after mad searching)

[http://ubuntuforums.org/showthread.php?p=10883112](http://ubuntuforums.org/showthread.php?p=10883112)

My setup is identical to this one and everything boots in EFI mode whether Xubuntu (grub-efi installed) or Windows (both installed in GPT partitions). Like the OP I can boot from one another by selecting the boot option at system start (F8).

I just can't seem to figure out how to tell grub-efi what to load on the Windows SSD (few new suggestions that I haven't tried yet)

I'll let you know if I ever figure it out.

---

