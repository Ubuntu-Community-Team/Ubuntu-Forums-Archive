---
title: "Can't boot into Ubuntu (more problems)"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by griffsterb on 2011-05-26
Hey all, I finally decided to give in and come here after troubleshooting for like 5-6 hours on my own last night. 

I am a first-time linux user, and decided to try out Ubuntu just cause I thought it would be fun. However when installing I messed up a partition on my extra hard drive (windows 7 and ubuntu were installed on my main drive), so I got gparted, booted it up and then proceeded to delete the partitions on my extra hd and format them. (ubuntu was working fine at this point. i had the option to boot windows or ubuntu on startup and i was using apps/messing around on my new ubuntu install). 

Of course when i rebooted I got that 'no such file, grub rescue' message. I fixed windows 7 boot through my windows CD, but spent *hours* trying to fix linux with no luck. i think i might have even accidentally deleted the partition it was on, so i popped in my flash drive to just reinstall it. the new install went fine, 'installation successful' and all that jazz, except now when i boot up my computer it goes straight into windows with no option for ubuntu. 

halp! i am so frustrated... been dealing with problems all night long and now apparently today too. did some google searching and found some similar issues... but not quite the same and i don't have to motivation to try out a ton of stuff right now with the mentality that it probably won't work. 

any help is GREATLY appreciated

---

### Post by griffsterb on 2011-05-26
Found a way to get this, might help. Except looking at the FIRST paragraph it tells me grub2 and windows are both in the MBR of the same partition.

EDIT: actually i see that grub is installed on sda1. WTF? i told the installer to put linux alongside windows. how the heck could grub get on my backup hard drive?

so i guess the question now is how to move grub into the MBR of my main hard drive, sdb?

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid d21f7a01-42cc-4cf1-98da-ed786a4baa35 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /boot/grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM 
                       /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 32776 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,953,523,711 1,953,521,664   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   282,012,934   282,012,872   7 NTFS / exFAT / HPFS
/dev/sdb2         282,013,694   312,580,095    30,566,402   5 Extended
/dev/sdb5         282,013,696   304,195,583    22,181,888  83 Linux
/dev/sdb6         304,197,632   312,580,095     8,382,464  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             44    15,679,439    15,679,396   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1592DFE21B2DD2B8                       ntfs       DatDisk
/dev/sdb1        208CF3FB8CF3C8F4                       ntfs       
/dev/sdb5        d21f7a01-42cc-4cf1-98da-ed786a4baa35   ext4       
/dev/sdb6        5248001f-1fd5-422a-817f-773d39347f9d   swap       
/dev/sdc1        FC86-9741                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             2
            ?? = ??             boot/grub/grub.cfg                             1

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root d21f7a01-42cc-4cf1-98da-ed786a4baa35
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root d21f7a01-42cc-4cf1-98da-ed786a4baa35
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
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root d21f7a01-42cc-4cf1-98da-ed786a4baa35
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d21f7a01-42cc-4cf1-98da-ed786a4baa35 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root d21f7a01-42cc-4cf1-98da-ed786a4baa35
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d21f7a01-42cc-4cf1-98da-ed786a4baa35 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root d21f7a01-42cc-4cf1-98da-ed786a4baa35
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root d21f7a01-42cc-4cf1-98da-ed786a4baa35
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 208CF3FB8CF3C8F4
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=d21f7a01-42cc-4cf1-98da-ed786a4baa35 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5248001f-1fd5-422a-817f-773d39347f9d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 141.365840912 = 151.790415872  boot/grub/core.img                             1
 142.765754700 = 153.293561856  boot/grub/grub.cfg                             1
 138.885108948 = 149.126750208  boot/initrd.img-2.6.38-8-generic               2
 141.364555359 = 151.789035520  boot/vmlinuz-2.6.38-8-generic                  1
 138.885108948 = 149.126750208  initrd.img                                     2
 141.364555359 = 151.789035520  vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  39 04 12 6c b4 a1 52 0c  f9 f2 42 a4 14 3e 25 90  |9..l..R...B..>%.|
00000010  32 14 04 2e 42 25 55 1b  1d 72 71 e0 00 00 01 20  |2...B%U..rq.... |
00000020  10 0a 71 ad 25 55 c0 7a  c4 4a 79 81 e4 0b a2 36  |..q.%U.z.Jy....6|
00000030  54 32 86 a2 8f 22 b0 f8  59 1c 25 02 56 41 01 88  |T2..."..Y.%.VA..|
00000040  3c 88 83 66 c0 78 fb 2e  85 86 1e 0d a8 d8 28 a7  |<..f.x........(.|
00000050  af 47 b8 a9 8b e5 16 f6  f6 68 fc 6d 71 56 8d 6d  |.G.......h.mqV.m|
00000060  f5 f7 34 8f d8 ce 2f 99  37 d7 81 b7 db f5 2b c3  |..4.../.7.....+.|
00000070  ec 37 dd 29 27 aa 8f 81  1e 61 98 f7 58 38 f7 12  |.7.)'....a..X8..|
00000080  30 f9 a8 24 d1 ea 30 a5  2c 8e bc 00 04 09 4a 4d  |0..$..0.,.....JM|
00000090  f8 0b f1 df 28 b2 0e c3  c0 65 48 86 bc a9 4c 15  |....(....eH...L.|
000000a0  59 0e 0e 7e 80 b5 1b 34  0b 84 f9 e4 91 b2 26 55  |Y..~...4......&U|
000000b0  e7 81 9b d6 20 29 ce a4  aa b7 09 3d 7a 63 27 37  |.... ).....=zc'7|
000000c0  cc 78 bb 39 a1 91 83 68  c3 3e e6 39 b7 8f b8 de  |.x.9...h.>.9....|
000000d0  9b a7 08 6a f1 38 26 b7  9c de c8 7d 68 2e ed 29  |...j.8&....}h..)|
000000e0  d4 85 66 98 89 ba 41 ff  fb a2 00 9a 80 03 4a 55  |..f...A.......JU|
000000f0  d4 d1 e9 1c 44 6f 4a ba  9d 61 88 23 8d dd 2b 53  |....DoJ..a.#..+S|
00000100  47 b0 c7 19 f7 2b 2a 75  87 99 76 33 8f f0 61 23  |G....+*u..v3..a#|
00000110  6b 12 6b 63 c0 76 02 5f  32 ec 72 52 a0 30 00 19  |k.kc.v._2.rR.0..|
00000120  00 20 c9 29 b8 c6 f0 17  1c 74 bf 01 09 97 df 7c  |. .).....t.....||
00000130  b1 b4 25 b8 55 8b ea d4  78 71 ad 86 2d 35 e6 d7  |..%.U...xq..-5..|
00000140  78 78 79 db 23 6b 4f 7e  4e e5 12 3c 11 93 ad 30  |xxy.#kO~N..<...0|
00000150  da a9 10 2c 8a 53 74 72  58 da 51 4e 5a b3 32 74  |...,.StrX.QNZ.2t|
00000160  0c 8d e6 37 7f 93 1f 7c  6b fb 98 f9 98 df 33 b9  |...7...|k.....3.|
00000170  98 69 4f ba 2e f9 32 ad  67 20 7f 5f 2f 0f 5b cb  |.iO...2.g ._/.[.|
00000180  f4 6f 31 a9 ba 9b 58 a6  6c ad cd 77 2f b1 d4 61  |.o1...X.l..w/..a|
00000190  9d ec 9f d7 76 9b f9 cc  de 9f cc 80 80 00 10 24  |....v..........$|
000001a0  9c bb 82 aa 98 64 49 88  96 16 89 09 dd 07 50 cf  |.....dI.......P.|
000001b0  07 af d2 ee 07 d8 7c f5  c5 75 47 1b 47 cc 00 fe  |......|..uG.G...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 78 52 01 00 fe  |...........xR...|
000001d0  ff ff 05 fe ff ff 02 78  52 01 00 f0 7f 00 00 00  |.......xR.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by griffsterb on 2011-05-26
amg... i'm dying here. this makes absolutely no sense. grub.cfg and winload.exe are in the MBR. WTF is going on here?

---

### Post by oldfred on 2011-05-26
If you are directly booting windows you have BIOS set to boot sdb (160GB drive). You have grub2's boot loader in sda (1TB drive). Change BIOS or test with one time boot key (f12 only my system) to see if booting from sda works.

You also have grub files installed to your windows and it will cause problems. Your boot partition has the boot files for both XP & win7 which is normal for windows as it combines boots.

    Boot files:       [COLOR=Red] /boot/grub/grub.cfg[/COLOR] /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM 
                     [COLOR=Red]  /boot/grub/core.img[/COLOR]

You cannot in windows have /boot & /Boot as windows is not case sensitive and it gets confused and will not work. Delete /boot but do not delete /Boot as it has the essential windows BCD file.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by ILoveYorkies on 2011-05-26
[SIZE=3]Hello,
I'm new to Linux too. But I might have a couple of suggestions that could help. But I have a few questions first such as:

 What version of linux did you install? I've installed Ubuntu 11.04.
What kind of install did you do? Install within Windows (WUBI) or automatic dual boot? Or a manual install? That is use Gparted from the liveusb drive to partition the hard drive that you wanted to boot linux from? Last option (manual, advanced or other) instead of 1st option (automatic)?

Did you install the 32 bit or 64 bit version of Ubuntu?
One last question: does your computer tell you that you can push a certain function key to boot other drives. I.E. on mine during post but before the Win XP splash screen it says in the lower left corner press F2 to enter bios but it also says in the right side corner press F12 to enter quick boot menu. I press the quick boot menu and a list of drives shows up. I choose the drive that I have Ubuntu's bootloader (Grub) installed on which in my case is my Sandisk Cruzer thumbdrive. I have to do this each time I want to boot into Ubuntu 11.04 (nickname Natty) but I don't mind that because that's the way I wanted it. Would it bother you to have to press a function key to boot into linux each time?
[/SIZE]

---

### Post by griffsterb on 2011-05-26
I was actually able to get the boot option menu to come up when I made the 1TB drive the highest priority boot device. Haven't gone into ubuntu yet, came to windows so I could delete the boot file that oldfred told me to delete. One thing that's weird is that the boot option menu on startup lists my Win 7 as Windows 2000/XP/NT. Before I reinstalled ubuntu it did correctly list it as Win 7. Should I be worried about that?

Also I did not use Wubi, I downloaded the iso from here:
[http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download")

And just ran it off a usb.

---

### Post by oldfred on 2011-05-26
I do not know if you can delete the /boot in windows as it will not see it different from /Boot. Linux is case sensitive, so I would do it from a liveCD.

---

### Post by griffsterb on 2011-05-26
> **oldfred said:**
> I do not know if you can delete the /boot in windows as it will not see it different from /Boot. Linux is case sensitive, so I would do it from a liveCD.

thanks oldfred. i got into my linux install by booting from the 1TB hd, so i'll just leave that as the top boot priority. also deleted the boot folder from my windows partition. everything appears to be running smoothly... anything else you noticed in my text file that is worrisome?

---

### Post by oldfred on 2011-05-26
The real test is can you boot both Ubuntu & windows from grub.

Have you run this and does it still list Windows incorrectly?
sudo update-grub

You still have XP boot files in the win7 boot partition. Do you still have an XP install?

You have a huge 1TB NTFS partition. Do you have good ways to back that up. Just because drives have become large does not mean we should not have ways to back them up.

---

