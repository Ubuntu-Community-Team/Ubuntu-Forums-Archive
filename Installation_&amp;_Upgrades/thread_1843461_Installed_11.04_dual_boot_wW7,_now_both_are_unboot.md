---
title: "Installed 11.04 dual boot w/W7, now both are unbootable"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by SavageFreedom on 2011-09-13
I have seen variations of this problem, but nothing seemed to be exactly the same, so forgive me if this is duplicate but until reading it entirely don't assume it's the same.

Preface:

3HDDS, sda, sdb, sdc. All are 500gb SATA drives

sda is labelled "media" and contained 3 partitions. sda1) a broken install of 9.04, sda2) a swap partition and sda3) a large ntfs partition used by Windows (which is on sdc)

sdb is labelled "backup" and was, prior to installation, an empty ntfs partition. This partition was deleted and in the free space I created a 15gb ext4 and an 8gb swap partition, the rest I left empty for now.

sdc is (was!) a bootable NTFS partition with Windows 7 installed.

I installed Ubuntu 11.04 onto the new 15gb ext4 on sdb using the Live CD. After install, the computer restarts and I am taken (after typical boot sequence) to a black screen with a blinking cursor. I made sure any USB devices were unplugged and that all optical drives were empty.

Here's where the big problem is... I cannot boot from CD or USB anymore (to use the Live CD to check anything) and I cannot access my BIOS or boot settings. I have to hit DEL to enter BIOS setup or ESC to enter boot settings. However, neither work anymore. They worked perfectly as of yesterday. So I am, as of right now, completely incapable of booting into either OS or to any recovery media.

GRUB never loads, just to make that clear. It goes directly from the Mobo splash screen and RAM check into a black screen with a cursor!

If anyone knows what I should be doing here, I am fairly desperate but will provide any further info I can. Understand that I cannot boot into anything right now, and thus cannot provide outputs of any files or commands.

---

### Post by SavageFreedom on 2011-09-13
UPDATE: I violently assaulted my keyboard and magically it started responding (no idea what went wrong there.) I forced a boot into the Live CD and I am now going through my partitions seeing what may have gone wrong. I would still appreciate any pointers. I've been using Ubuntu for a good 3 years now, so you think my noob days would be behind me, but when it comes to installing I always seem to revert back to a hopeless neanderthal.

---

### Post by sanderd17 on 2011-09-13
> **SavageFreedom said:**
> 

Here's where the big problem is... I cannot boot from CD or USB anymore (to use the Live CD to check anything) and I cannot access my BIOS or boot settings. I have to hit DEL to enter BIOS setup or ESC to enter boot settings. However, neither work anymore. They worked perfectly as of yesterday. So I am, as of right now, completely incapable of booting into either OS or to any recovery media.

Ubuntu doesn't change anything to your BIOS. Your BIOS is loaded before your harddisk starts, so before Ubuntu can do anything.

This means that your problem has nothing to do with the installation of Ubuntu.

This has to be a hardware problem, maybe due to overheating or so.

Try opening your computer, removing the hard drives (so you can boot from a CD), check the graphical card ...

There is not much I can do on such a distance.

EDIT:

Ok, it was a hardware problem, but less severe than I thought.

---

### Post by sanderd17 on 2011-09-13
Can you give us the output of the boot info script?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by SavageFreedom on 2011-09-13
UPDATE 2: In the Disk Utility, I am showing the following:

/dev/sda has 2 partitions (17GB of free space, this is where the old 9.04 install was that I deleted, and 483GB of NTFS (this is where my media files reside)

/dev/sdb has 2 partitions (a 16GB ext4 which is where I installed 11.04, an 8.1GB Swap, and the rest of the drive, 476GB worth, is free space. Under the ext4 partition it shows usage as Filesystem, type as ext4, and no mountpoint. It does not show it as being bootable, but I'm not sure if it normally would. When I mount it, I can browse it and verify that 11.04 is installed there as I expected. FYI, that partition was formatted as /

/dev/sdc (my windows drive) shows one 500GB NTFS partition, which is bootable.

So, my issues is that I cannot seem to reach GRUB at all if I reboot. I just get the black screen. I don't believe it's a graphics issue yet (which I'll probably run into later since I'm using ATI) because I can't even reach GRUB to try nomodeset or any of that jazz.

Any ideas?

---

### Post by SavageFreedom on 2011-09-13
> **sanderd17 said:**
> Can you give us the output of the boot info script?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Trying that now, have to jump through a couple hoops to get any files over to Ubuntu ATM due to internet issues, I will post the output as soon as I get it transferred.

---

### Post by SavageFreedom on 2011-09-13
Alright, here we go.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid db1c33ae-0394-4962-b50b-125dabf26665 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda3    *     33,126,400   976,771,071   943,644,672   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    31,250,431    31,248,384  83 Linux
/dev/sdb2          31,252,478    47,083,519    15,831,042   5 Extended
/dev/sdb5          31,252,480    47,083,519    15,831,040  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 8103 MB, 8103395328 bytes
256 heads, 21 sectors/track, 2944 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             32    15,826,943    15,826,912   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda3        108873DF8873C1B0                       ntfs       Media
/dev/sdb1        db1c33ae-0394-4962-b50b-125dabf26665   ext4       
/dev/sdb5        39a2a346-fe75-429d-9272-fcd70ca3b1f7   swap       
/dev/sdc1        BA88F93588F8F12D                       ntfs       
/dev/sdd1        24B6-1DF0                              vfat       USB20FD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/db1c33ae-0394-4962-b50b-125dabf26665 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/USB20FD           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root db1c33ae-0394-4962-b50b-125dabf26665
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root db1c33ae-0394-4962-b50b-125dabf26665
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root db1c33ae-0394-4962-b50b-125dabf26665
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=db1c33ae-0394-4962-b50b-125dabf26665 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root db1c33ae-0394-4962-b50b-125dabf26665
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=db1c33ae-0394-4962-b50b-125dabf26665 ro single 
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
	search --no-floppy --fs-uuid --set=root db1c33ae-0394-4962-b50b-125dabf26665
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root db1c33ae-0394-4962-b50b-125dabf26665
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root BA88F93588F8F12D
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=39a2a346-fe75-429d-9272-fcd70ca3b1f7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.210292816 = 8.815734784    boot/grub/core.img                             1
   4.364368439 = 4.686204928    boot/grub/grub.cfg                             1
   0.547851562 = 0.588251136    boot/initrd.img-2.6.38-8-generic               2
   8.208560944 = 8.813875200    boot/vmlinuz-2.6.38-8-generic                  1
   0.547851562 = 0.588251136    initrd.img                                     2
   8.208560944 = 8.813875200    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  0e 19 3a 03 dd e9 a2 01  bd b7 95 40 0c 02 46 0c  |..:........@..F.|
00000010  44 21 20 60 60 08 02 26  9d 6e d3 2b dc 1f 9f 83  |D! ``..&.n.+....|
00000020  1f a0 d4 46 7c 8b 7e ff  25 25 95 93 b6 eb 80 49  |...F|.~.%%.....I|
00000030  a5 dd 3a d0 30 a4 3d f8  79 7f 53 e0 fb 93 e1 19  |..:.0.=.y.S.....|
00000040  39 8a e5 f6 b1 67 f1 6c  84 61 53 67 c1 5b f0 fa  |9....g.l.aSg.[..|
00000050  75 9e 0d 9e 97 8f fe 78  32 28 bf 43 4d 9b 6f a2  |u......x2(.CM.o.|
00000060  0f 98 c9 e4 e7 72 32 f9  69 61 0e 4e 75 d0 11 e5  |.....r2.ia.Nu...|
00000070  7d e7 c9 3e 08 f9 ab 41  e3 a6 6c 0a 7b 8d b3 85  |}..>...A..l.{...|
00000080  6c e7 0a fd a6 1f 4b 6e  13 4c 21 52 a3 10 e1 98  |l.....Kn.L!R....|
00000090  db a4 e8 cf 33 27 a0 ea  fb 30 5a 0b b4 4c 80 c5  |....3'...0Z..L..|
000000a0  00 0a a5 31 64 4d 30 aa  1a f6 97 f9 2d ff 97 62  |...1dM0.....-..b|
000000b0  74 c4 76 d9 76 14 5d 80  96 81 80 33 6b f6 17 ab  |t.v.v.]....3k...|
000000c0  d3 51 70 f3 bf 79 12 0b  ed 24 3a e9 77 d2 45 46  |.Qp..y...$:.w.EF|
000000d0  a9 6c 50 6f d9 03 02 27  70 45 f0 59 c6 e0 fe 0b  |.lPo...'pE.Y....|
000000e0  24 98 b0 aa 41 cc 22 e0  b4 ac d7 ef dc 83 24 c5  |$...A.".......$.|
000000f0  3c 77 30 a5 0a 8b 52 85  19 7f f6 28 05 06 b4 3a  |<w0...R....(...:|
00000100  cc b3 c8 be ff 1b 30 33  92 c1 e7 bc 9b 38 ee 18  |......03.....8..|
00000110  4d 2f 0b d2 6b d6 54 f6  63 95 64 0a bd 80 d1 66  |M/..k.T.c.d....f|
00000120  73 44 b5 81 bf 89 6a 7a  34 c2 fc d7 09 76 86 df  |sD....jz4....v..|
00000130  f2 e3 54 82 0d 92 b9 6d  b3 aa 2f 4e 51 c8 d5 94  |..T....m../NQ...|
00000140  7e 03 7a 0d 10 bd 06 af  a7 d7 80 4a 2f bd 38 f4  |~.z........J/.8.|
00000150  b7 d1 4b be 9e 5e 67 88  5e f9 7f 03 bd c8 3f 87  |..K..^g.^.....?.|
00000160  8f 48 05 1a b3 d3 5c 54  ce 56 e1 c9 a3 86 97 68  |.H....\T.V.....h|
00000170  3b 13 7d a1 9b 1c fe 99  bf 93 14 e7 b9 69 2a 15  |;.}..........i*.|
00000180  78 a9 d8 0c 43 16 8f ac  01 b5 5e 7b 1c e5 11 6a  |x...C.....^{...j|
00000190  1e ca 9a 63 06 db f9 8e  82 ec 5b 88 ac de b2 17  |...c......[.....|
000001a0  80 03 28 bd ed 7a 9f 05  8f ae c0 9c bd ba 1b a4  |..(..z..........|
000001b0  32 fa bf 78 ef 66 36 bc  53 ec d7 b2 ed 04 00 fe  |2..x.f6.S.......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 f1 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by SavageFreedom on 2011-09-13
I see from this that Grub2 is installed onto both sda and sdb. sda is where 9.04 used to be installed, sdb is where 11.04 is now installed. My guess is that the grub on sda is trying to boot rather than on sdb, and since sda is a blank drive it just throws me a blank screen? An uneducated guess, but I'm assuming i need to get rid of the Grub2 on sda. I have no idea what sdd is, probably my thumb drive. sdc is Windows 7

---

### Post by Quackers on 2011-09-13
Which drive is set to boot first in your bios? Try setting sdb to be first and see what happens.

---

### Post by sanderd17 on 2011-09-13
You have four disks? Probably one of them is your USB disk, but I can't find it immediatly. sda has a windows partition and sdb a swap partition. So they are probably not your USB drive. And sdc and sdd contain Windows mbrs.

Do you have any idea why there are four disks shown?

For your problem, I would install grub to the mbr of sda, but I don't know in what partition your new ubuntu installation is.

You can follow this [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) to reinstall grub.

EDIT:

If you change to boot from sdb first, the names of your drives may change (sda and sdb might get switched). This can cause problems in your /etc/fstab file since you use those names. But it's a good test to see where your Grub is installed.

---

### Post by SavageFreedom on 2011-09-13
> **sanderd17 said:**
> You have four disks? Probably one of them is your USB disk, but I can't find it immediatly. sda has a windows partition and sdb a swap partition. So they are probably not your USB drive. And sdc and sdd contain Windows mbrs.

Do you have any idea why there are four disks shown?

For your problem, I would install grub to the mbr of sda, but I don't know in what partition your new ubuntu installation is.

You can follow this [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) to reinstall grub.

sda has a Windows partition, though no OS is installed to it. It also has Grub2 installed to its MBR because that drive used to be used for Ubuntu 9.04.

sdb is where Ubuntu is installed now, particularly sdb1 (I can verify this by mounting the drive from the LiveCD. sdb5 is the swap. The rest of the drive isn't partitioned currently.

sdc is, as you said, Windows. So, the problem seems to be sda.

sdd didn't exist until I plugged my thumb drive in to copy that bash file over. So I'm about 99% positive that's what it is.

I'll try what Quackers said and set sdb to be my first boot device, and see if Grub loads properly from it. Otherwise, the next step (I think) will be removing Grub from sda by wiping that drive's MBR

---

### Post by SavageFreedom on 2011-09-13
booting from my first drive, which I assume to be sda, brings up the black screen with the cursor.

booting from my second drive, which I assume is sdb (where I just installed 11.04 to) brings up this
```
error: the symbol 'grub_xputs' not found
grub rescue> 
```

booting from my third, sdc drive brings up Windows as expected.

---

### Post by Quackers on 2011-09-13
Ok thanks. It seems that grub has not fully installed and needs to be purged and re-installed.
The guide below explains how to do that from a live cd desktop. It is your choice where to install grub to (/dev/sda or /dev/sdb) but it should be installed to the drive your bios is set to boot from first.
The partition you need to mount first is /dev/sdb1.
As you do not have a separate Linux boot partition you can ignore that part of the guide.
Scroll down to the CHROOT section for details.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by SavageFreedom on 2011-09-13
UPDATE 3: From the grub rescue prompt, I typed ls. This brings up (hd0) (hd0,5) (hd0,1) (hd1) (hd1,1) (hd2) and (hd2,3)

running the following command on each
```
ls (hdx,x)/boot
```
I get the "error: unknown filesystem" on all of them other than (hd0,1) which returns:
```
./ ../ grub System.map-2.6.38-8-generic abi-2.6.38-8-generic config-2.6.38-8-generic memtest86+.bin memtest86+_multiboot.bin vmcoreinfo-2.6.38-8-generic vmlinuz-2.6.38-8-generic initrd.img-2.6.38-8-generic
```

---

### Post by SavageFreedom on 2011-09-13
> **Quackers said:**
> Ok thanks. It seems that grub has not fully installed and needs to be purged and re-installed.
The guide below explains how to do that from a live cd desktop. It is your choice where to install grub to (/dev/sda or /dev/sdb) but it should be installed to the drive your bios is set to boot from first.
The partition you need to mount first is /dev/sdb1.
As you do not have a separate Linux boot partition you can ignore that part of the guide.
Scroll down to the CHROOT section for details.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Alright, digging into this now. Will post further issues if they come up or mark it as solved hopefully.

---

### Post by Quackers on 2011-09-13
Take your time and if you're not sure about something, ask. It's a lot easier to answer a question than fix a resulting problem :-)
Good luck!

---

### Post by SavageFreedom on 2011-09-13
Well I'll be...

I rebooted again, after doing absolutely nothing other than what I mentioned at the grub rescue prompt, and it booted Grub, and successfully booted Ubuntu with no problems. Why, how, I have no idea. But there you have it... don't know if I should really marked this SOLVED because I didn't actually do anything to my knowledge...

Could typing "ls (hd0,1)/boot" really do anything? I assumed that was just asking grub whether or not there was a boot record on hd0,1, not actually passing a commands capable of fixing anything.

---

### Post by Quackers on 2011-09-13
Lol, me neither :-)

---

### Post by YesWeCan on 2011-09-13
> **SavageFreedom said:**
> Well I'll be...

I rebooted again, after doing absolutely nothing other than what I mentioned at the grub rescue prompt, and it booted Grub, and successfully booted Ubuntu with no problems. Why, how, I have no idea. But there you have it... don't know if I should really marked this SOLVED because I didn't actually do anything to my knowledge...

Could typing "ls (hd0,1)/boot" really do anything? I assumed that was just asking grub whether or not there was a boot record on hd0,1, not actually passing a commands capable of fixing anything.
Grub works in mysterious ways. You should always have rosary beads on hand and a plume of burning incense entering the PC's fan before you try to boot.

Also, you should run update-grub and grub-install to refresh Grub's files.

---

