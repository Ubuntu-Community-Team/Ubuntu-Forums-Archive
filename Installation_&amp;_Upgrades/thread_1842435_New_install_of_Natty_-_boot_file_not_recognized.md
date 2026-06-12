---
title: "New install of Natty - boot file not recognized"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by netwidget on 2011-09-11
I installed Natty on a second physical drive (500GB) on my system and have spent the last few days configuring the OS with the system. I removed the other HDD, changed the physical SATA socket that the Natty HDD was installed on to SATA port 0 (as shown in BIOS), and checked BIOS to make sure it was the only boot device.  I now get no boot filename found from the BIOS.  It can't find it.  

Loading Natty from live CD, and typing fdisk -l at terminal I get the following:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00071a67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60410   485241856   83  Linux
/dev/sda2           60411       60802     3141633    5  Extended
/dev/sda5           60411       60802     3141632   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

The fstab file reads:

```
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
UUID=a4f3a089-b8df-5ec0-5ebb-ab1b0bc6efa0 none            swap    sw              0       0

```

The contents of /etc/default/grub are:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

device.map  does not exist in /boot/grub/

I am new to Linux especially with grub.  Can anyone tell me what else I might check, or were to go to look.

system: 

Gateway s-5200s 
Pentium 4 2.8GHz
RAM: 3 GB DDR2 
Intel Board
HDD: WD 500 GB (new)
MSI ATI Radeon R5450 Graphics Card (1GB DDR3)

---

### Post by Basher101 on 2011-09-11
you must update your grub. If its not too big of a trouble simply reinstall it...thats the easiest way. To update your grub from the CD try the command in a terminal ```
sudo update-grub
``` and see if it spits out sth like ```
Ubuntu 2.38.something-generic
blah blah recovery
blah memory test
``` if it does try rebooting and see if your problem is solved

---

### Post by drs305 on 2011-09-11
You can get Grub2 back on the MBR by booting the LiveCD, mounting your Ubuntu partition and running the following commands. I'll assume your Ubuntu drive is sda1, but change it if not. Also do NOT use the partition number in the second command:


```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot. If it still doesn't work, please run the boot info script and post the contents of RESULTS.txt (click on the 'BIS' link in my signature line to get the script).

---

### Post by netwidget on 2011-09-11
@drs305

grub-install didn't work.  below is the contents of results.txt when I ran the BIS script:

 ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   970,485,759   970,483,712  83 Linux
/dev/sda2         970,487,806   976,771,071     6,283,266   5 Extended
/dev/sda5         970,487,808   976,771,071     6,283,264  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3880 MB, 3880452096 bytes
120 heads, 62 sectors/track, 1018 cylinders, total 7579008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/sdb1     ? 1,869,270,955 3,493,395,135 1,624,124,181  65 Novell Netware 386
/dev/sdb2     ? 2,995,680,026 4,190,351,312 1,194,671,287  44 GoBack
/dev/sdb3     ? 3,033,587,513 4,838,108,669 1,804,521,157  5e Unknown
/dev/sdb4     ? 2,941,202,223 6,708,484,492 3,767,282,270  39 Plan 9

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb1 overlaps with /dev/sdb4
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb2 overlaps with /dev/sdb4
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb3 overlaps with /dev/sdb4
/dev/sdb4 ends after the last sector of /dev/sdb

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        e97c56a9-01e2-495d-a509-645ceb19a421   ext4       
/dev/sda5        a4f3a089-b8df-5ec0-5ebb-ab1b0bc6efa0   linux_raid_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=e97c56a9-01e2-495d-a509-645ceb19a421 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=e97c56a9-01e2-495d-a509-645ceb19a421 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e97c56a9-01e2-495d-a509-645ceb19a421 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e97c56a9-01e2-495d-a509-645ceb19a421 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a4f3a089-b8df-5ec0-5ebb-ab1b0bc6efa0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 100.138130188 = 107.522498560  boot/grub/core.img                             1
  84.368434906 = 90.589917184   boot/grub/grub.cfg                             1
   3.755134583 = 4.032045056    boot/initrd.img-2.6.38-11-generic              2
   1.047515869 = 1.124761600    boot/initrd.img-2.6.38-8-generic               2
   3.294254303 = 3.537178624    boot/vmlinuz-2.6.38-11-generic                 2
 100.133281708 = 107.517292544  boot/vmlinuz-2.6.38-8-generic                  1
   3.755134583 = 4.032045056    initrd.img                                     2
   1.047515869 = 1.124761600    initrd.img.old                                 2
   3.294254303 = 3.537178624    vmlinuz                                        2
 100.133281708 = 107.517292544  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  1f 8b 08 00 00 00 00 00  02 03 ec dd 09 20 d4 db  |............. ..|
00000010  df 3f f0 19 c6 92 d4 70  d3 aa 50 74 4b 0b b9 29  |.?.....p..PtK..)|
00000020  2d a4 45 b9 dd 16 4a 7b  96 2b 11 2a 8a 19 ca 36  |-.E...J{.+.*...6|
00000030  4a 8b 21 b4 ef a5 52 69  df 53 88 21 4a 25 09 95  |J.!...Ri.S.!J%..|
00000040  2c 51 29 86 c9 92 9d 61  be ff f3 1d ba bf 7b 9f  |,Q)....a......{.|
00000050  e7 f9 fd 9f f5 ff 3c bf  ff 33 ef d7 ef 37 73 be  |......<..3...7s.|
00000060  cb 99 73 ce e7 7c cf f9  7e cf b8 29 91 29 e3 0f  |..s..|..~..).)..|
00000070  72 7f db 64 fc f4 e7 bd  7e da 2e ee 8c 45 d6 8a  |r..d....~....E..|
00000080  36 46 29 a1 75 d6 ee 6a  fc af c2 14 46 84 8b 5a  |6F).u..j....F..Z|
00000090  66 87 d1 f3 c8 d4 c8 82  c8 9c 47 8c 00 7e b9 80  |f.........G..~..|
000000a0  a1 24 79 d2 70 21 b9 26  30 b8 3d d8 6b 4c 1c 53  |.$y.p!.&0.=.kL.S|
000000b0  f8 3b 23 9e c9 48 be 12  19 c7 0c 0e 60 5d e0 2a  |.;#..H......`].*|
000000c0  95 0d 6c 66 05 73 35 42  9e aa 49 9e 06 4b 14 bc  |..lf.s5B..I..K..|
000000d0  2a e7 96 7d 4a 3e 17 28  9a 67 94 cb ef c7 e8 11  |*..}J>.(.g......|
000000e0  a7 26 34 60 24 32 f6 86  fb aa 30 4b 04 8c 94 78  |.&4`$2....0K...x|
000000f0  c6 0d fd ef 0d e7 db e7  72 34 be ac bd 24 c7 6d  |........r4...$.m|
00000100  b9 95 53 be 56 ba d5 7e  ab b4 fc 77 71 a5 75 9f  |..S.V..~...wq.u.|
00000110  c4 6f 7b c2 2d 94 c3 e7  ab f4 16 ae a2 bc 47 25  |.o{.-.........G%|
00000120  9f 0a 14 0e 66 24 c7 06  0a fb 31 c6 7d c9 ea 97  |....f$....1.}...|
00000130  a1 e8 c5 32 fe a9 8a c1  a0 a8 44 25 c6 bd de 59  |...2......D%...Y|
00000140  6a d7 76 a4 70 1b ef 31  db d2 0c 9a 15 6f 29 07  |j.v.p..1.....o).|
00000150  73 86 d1 6d 1d 92 78 65  e9 e2 7b 33 b2 fa ac f2  |s..m..xe..{3....|
00000160  fa 69 9b 78 e9 15 ae 6a  73 2a 93 a3 c4 af b9 37  |.i.x...js*.....7|
00000170  33 ab 4f da e2 7b ca 59  7d 42 9b 56 79 65 06 7f  |3.O..{.Y}B.Vye..|
00000180  32 e7 a4 b5 bb 84 cf 51  5e ec c2 8e 2b 70 31 ca  |2......Q^...+p1.|
00000190  75 69 69 08 15 85 be 9d  35 4e ba 95 bf ca c5 8c  |uii.....5N......|
000001a0  92 67 30 c4 be a7 76 a5  a7 3c 93 53 16 4e df 17  |.g0...v..<.S.N..|
000001b0  2a 19 f9 31 cc 45 6e d2  47 2f b9 5b 4c 81 02 23  |*..1.En.G/.[L..#|
000001c0  dd 9e 65 7d 4f 2e ab cf  6a 6f 15 2b ce 60 d2 c8  |..e}O...jo.+.`..|
000001d0  3e 07 44 22 76 5c 1a 73  8e b2 b7 3c 35 47 e5 75  |>.D"v\.s...<5G.u|
000001e0  19 c3 5e 61 e4 1c 39 df  d0 b4 c5 ce 8e 6b 19 33  |..^a..9......k.3|
000001f0  3d 3d 39 0c 1d 67 2f 2f  4f af 5e 2a 8c e0 bd 7f  |==9..g//O.^*....|
00000200

Unknown BootLoader on sdb1


Unknown BootLoader on sdb2


Unknown BootLoader on sdb3


Unknown BootLoader on sdb4



=============================== StdErr Messages: ===============================

unlzma: Decoder error
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory

```

Any other ideas, thanks for you help.

---

### Post by netwidget on 2011-09-11
I had a usb drive connected in the above results.txt.  Below is the BI script run usb drive disconnected:

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
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   970,485,759   970,483,712  83 Linux
/dev/sda2         970,487,806   976,771,071     6,283,266   5 Extended
/dev/sda5         970,487,808   976,771,071     6,283,264  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        e97c56a9-01e2-495d-a509-645ceb19a421   ext4       
/dev/sda5        a4f3a089-b8df-5ec0-5ebb-ab1b0bc6efa0   linux_raid_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=e97c56a9-01e2-495d-a509-645ceb19a421 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=e97c56a9-01e2-495d-a509-645ceb19a421 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e97c56a9-01e2-495d-a509-645ceb19a421 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e97c56a9-01e2-495d-a509-645ceb19a421 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root e97c56a9-01e2-495d-a509-645ceb19a421
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a4f3a089-b8df-5ec0-5ebb-ab1b0bc6efa0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 100.138130188 = 107.522498560  boot/grub/core.img                             1
  84.368434906 = 90.589917184   boot/grub/grub.cfg                             1
   3.755134583 = 4.032045056    boot/initrd.img-2.6.38-11-generic              2
   1.047515869 = 1.124761600    boot/initrd.img-2.6.38-8-generic               2
   3.294254303 = 3.537178624    boot/vmlinuz-2.6.38-11-generic                 2
 100.133281708 = 107.517292544  boot/vmlinuz-2.6.38-8-generic                  1
   3.755134583 = 4.032045056    initrd.img                                     2
   1.047515869 = 1.124761600    initrd.img.old                                 2
   3.294254303 = 3.537178624    vmlinuz                                        2
 100.133281708 = 107.517292544  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by drs305 on 2011-09-11
Thanks for reposting. I was about to offer some advice that probably wouldn't have applied ...

I don't know much about RAID setups but do note the sda5 RAID designation. I know of cases where RAID remnants can screw up things. Assuming you aren't really using RAID any longer, you can try to remove the traces with the following:
```
sudo dmraid -E -r /dev/sda
```

There are some other RAID related commands but I'm not in a position to offer advice about how or if they would work.

Other than that, we'll have to wait with someone more familiar with Grub and RAID to respond.

---

### Post by netwidget on 2011-09-11
@drs305

Tried dmraid - didn't work.  If there is no other ideas I may just have to re-install the system again and run the grub boot loader through its paces.  Was hoping not to have to do it again.

Thanks for your help, though.

---

### Post by drs305 on 2011-09-11
I really can't determine if your problem is hardware/BIOS related or something else. Other than the mention of RAID, the RESULTS.txt files look correct.

One option you could try is using the Boot Repair tool. Here is the link:
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
[http://ubuntuforums.org/showthread.php?t=1769482#post10976174]("http://ubuntuforums.org/showthread.php?t=1769482#post10976174")

I believe the boot repair app can lead you through a complete purge and reinstallation (as well as easier automated repairs). If nothing works and you have a lot of time invested in the current installation, you could try booting the LiveCD and manually chrooting to completely remove and reinstall Grub 2 (without uninstalling the entire system). Sometimes it is necessary to completely remove Grub2 rather than just reinstall if one of the files is corrupt. Use the 'Chroot' link in my signature line if Boot Repair doesn't work and you want to try the manual method. 

Best of luck. Let us know if any of these work.

---

