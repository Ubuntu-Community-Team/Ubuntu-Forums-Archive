---
title: "GRUB can't see Windows 7 - Boot Info Script Included"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by slimeph on 2013-04-25
Grub couldn't see my windows installation
update-grub couldn't find windows installation.

What I've tried so far:
* The suggestions in [http://ubuntuforums.org/showthread.php?t=1758396](http://ubuntuforums.org/showthread.php?t=1758396)

Please help.

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/mnt/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 1198. But according to the info from fdisk, 
                       sda6 starts at sector 237795328.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 31000 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    29,085,695    29,083,648  83 Linux
/dev/sda2          29,087,742   312,580,095   283,492,354   f W95 Extended (LBA)
/dev/sda5          32,994,031   237,794,129   204,800,099   7 NTFS / exFAT / HPFS
/dev/sda6         237,795,328   312,580,095    74,784,768   7 NTFS / exFAT / HPFS
/dev/sda7          29,087,744    32,993,279     3,905,536  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4075 MB, 4075290624 bytes
256 heads, 63 sectors/track, 493 cylinders, total 7959552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     7,959,551     7,957,504   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        87fa974e-d025-4151-b872-684e73513a6f   ext4       
/dev/sda5        ECF8BE60F8BE292A                       ntfs       data
/dev/sda6        2638128738125661                       ntfs       sys7
/dev/sda7        13bc54aa-7026-4802-a117-5a538759fdae   swap       
/dev/sdb1        1B11-1A61                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /mnt                     ext4       (rw)
/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /media/sys7              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 87fa974e-d025-4151-b872-684e73513a6f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 87fa974e-d025-4151-b872-684e73513a6f
  set locale_dir=($root)/boot/grub/locale
  set lang=en_PH
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 87fa974e-d025-4151-b872-684e73513a6f
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=87fa974e-d025-4151-b872-684e73513a6f ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 87fa974e-d025-4151-b872-684e73513a6f
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=87fa974e-d025-4151-b872-684e73513a6f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 87fa974e-d025-4151-b872-684e73513a6f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 87fa974e-d025-4151-b872-684e73513a6f
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=87fa974e-d025-4151-b872-684e73513a6f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=13bc54aa-7026-4802-a117-5a538759fdae none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  00 60 09 00 13 57 f3 00  a6 f5 7c 44 15 1f 00 00  |.`...W....|D....|
00000010  e9 8d 48 a2 e9 f8 7c 44  d5 7a 00 00 00 d6 3e c3  |..H...|D.z....>.|
00000020  a4 19 7d 44 45 81 01 00  dc 92 ff cc 46 1a 7d 44  |..}DE.......F.}D|
00000030  30 00 00 00 1c 23 75 ec  bb 1e 7d 44 05 1e 2e 01  |0....#u...}D....|
00000040  6a 50 e8 67 b1 29 7d 44  80 4d 00 00 07 33 d5 fb  |jP.g.)}D.M...3..|
00000050  dc 2b 7d 44 05 30 00 00  ad 6e 1a 97 57 31 7d 44  |.+}D.0...n..W1}D|
00000060  30 20 00 00 1e b0 43 20  57 31 7d 44 30 20 00 00  |0 ....C W1}D0 ..|
00000070  a6 d4 49 5c 57 31 7d 44  35 20 00 00 4c 88 ed 18  |..I\W1}D5 ..L...|
00000080  57 31 7d 44 35 20 00 00  f2 a9 32 45 57 31 7d 44  |W1}D5 ....2EW1}D|
00000090  35 20 00 00 a3 fa ac e6  57 31 7d 44 37 20 00 00  |5 ......W1}D7 ..|
000000a0  df d9 a3 64 62 33 7d 44  05 e0 0e 00 53 0f 28 1e  |...db3}D....S.(.|
000000b0  91 45 7d 44 05 30 00 00  6d 19 88 c7 3c 49 7d 44  |.E}D.0..m...<I}D|
000000c0  85 ae 04 00 61 54 57 d7  03 52 7d 44 00 bb 0e 00  |....aTW..R}D....|
000000d0  ce 06 84 73 d6 57 7d 44  d0 3f 00 00 45 77 e3 61  |...s.W}D.?..Ew.a|
000000e0  50 61 7d 44 85 9a 00 00  e0 a0 2f c3 7e 65 7d 44  |Pa}D....../.~e}D|
000000f0  00 ed 00 00 0a 39 6b c0  eb 6a 7d 44 05 30 00 00  |.....9k..j}D.0..|
00000100  24 05 3f c0 a6 6c 7d 44  00 c0 02 00 3b 65 08 57  |$.?..l}D....;e.W|
00000110  dd 6c 7d 44 90 1f 00 00  82 e4 40 b0 a7 71 7d 44  |.l}D......@..q}D|
00000120  45 53 23 00 20 a8 23 be  33 75 7d 44 85 e6 09 00  |ES#. .#.3u}D....|
00000130  7d 31 f2 14 aa 80 7d 44  c0 b4 01 00 5c 6d 8b 7b  |}1....}D....\m.{|
00000140  b6 88 7d 44 15 76 00 00  20 a5 cf d8 05 91 7d 44  |..}D.v.. .....}D|
00000150  04 37 00 00 22 d9 d7 93  7c 95 7d 44 05 03 00 00  |.7.."...|.}D....|
00000160  ea 51 22 dc 85 97 7d 44  12 10 00 00 5e a1 58 c3  |.Q"...}D....^.X.|
00000170  ea 99 7d 44 d5 70 00 00  1a 32 de e9 be 9a 7d 44  |..}D.p...2....}D|
00000180  05 a0 1a 00 f7 56 88 6d  4d b0 7d 44 00 40 12 00  |.....V.mM.}D.@..|
00000190  99 5e 2a f8 08 b4 7d 44  83 20 01 00 94 3d c3 aa  |.^*...}D. ...=..|
000001a0  24 b5 7d 44 55 1b 00 00  5f f7 a5 6b 8e bf 7d 44  |$.}DU..._..k..}D|
000001b0  95 0b 00 00 07 17 63 5a  9a c0 7d 44 00 30 00 fe  |......cZ..}D.0..|
000001c0  ff ff 07 fe ff ff f1 9a  3b 00 63 00 35 0c 00 fe  |........;.c.5...|
000001d0  ff ff 05 fe ff ff 54 9b  70 0c ae 24 75 04 00 00  |......T.p..$u...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2013-04-25
Did you have XP or Vista on sda1 and just install Ubuntu over the top of that?

Windows only boots from primary partitions, your Windows 7 install is now in a logical partition sda and only has one of three required boot files. Typically Windows installs those other two in a boot partition or in another install in a primary partition. 

 Vista and win7 boot files - missing files in Red.
  Boot files/dirs:   [COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe

How Windows boots with BIOS and MBR(msdos) partitioning. Show Vista but 7 is the same except it often has a separate boot partition with the files you have missing.
      
 Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you cannot totally reinstall with Windows first as it prefers, you may be able to convert your sda6 to a primary partition, but will have to do it in multiple steps. You can only have 4 primary partitions and only one of the primary partition can be the extended. All logical partitions must be in the extended.

Windows often does not like to have logical partitions before it on the drive, but you can try to use this to convert sda6 to primary.
You need to back up all your data and the existing partition table so you can restore it, if everything goes South.
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Then you need to put boot flag on the Windows 7 partition and use a Windows repairCD to repair the Windows install. It should add your missing files.

---

