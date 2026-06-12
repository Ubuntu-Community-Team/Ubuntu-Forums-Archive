---
title: "Installed Ubuntu 11.04 -&gt; windows 7 broke"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by maltorius on 2011-08-05
Hello

Ive been running windows 7/Ubuntu dualboot for some years now and never had any problems.
Some months ago I got a new Patriot Inferno ssd. Ofc the first thing I did was to installl windows 7, it had no problems, ran fast and smooth.
Then when I reinstalled grub I started to get error when trying to start windows, the logo never apeared and all I got was the message "Windows failed to start. A recent hardware or software....." "Status: 0x00...00F"
"Info: The boot selection failed because a required device was inaccessible.".

It does not matter what order I install windows and ubuntu in, or how many times Ive tried to reinstall grub.
Windows 7 will not work while I have grub/windows installed.

Right now Ive got them installed on separate drives, ubuntu on the ssd and windows on a partition on a 1tb hdd. 
Unfortunately I need to have windows for .net programing and gaming..

I saw this requested in another post so Ill just put it here:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 7bda77a7-29fa-4c0d-9e18-bc3c45880bba root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => No known boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,131,538,431 1,131,536,384   7 NTFS / exFAT / HPFS
/dev/sda2       1,131,538,432 1,336,338,431   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda3       1,336,338,432 1,953,523,711   617,185,280  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1         109,418,496   117,229,567     7,811,072  82 Linux swap / Solaris
/dev/sdb2    *          2,048    29,296,639    29,294,592  83 Linux
/dev/sdb3          29,296,640   109,418,495    80,121,856  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/sdc1     ? 3,283,468,842 4,458,661,525 1,175,192,684  2d Unknown
/dev/sdc2     ? 1,315,454,913 5,384,320,371 4,068,865,459  1b Hidden W95 FAT32
/dev/sdc3     ? 3,916,089,230 4,675,495,360   759,406,131  f2 DOS secondary
/dev/sdc4     ?   738,208,454 2,374,774,176 1,636,565,723  37 Unknown

/dev/sdc1 ends after the last sector of /dev/sdc
/dev/sdc1 overlaps with /dev/sdc2
/dev/sdc1 overlaps with /dev/sdc3
/dev/sdc2 ends after the last sector of /dev/sdc
/dev/sdc2 overlaps with /dev/sdc3
/dev/sdc2 overlaps with /dev/sdc4
/dev/sdc3 ends after the last sector of /dev/sdc
/dev/sdc4 ends after the last sector of /dev/sdc

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 1e5515f4-23fb-4bb4-a216-af531b696de4   swap       
/dev/sda1        6ED44FB238CF1A06                       ntfs       workspace
/dev/sda2        7C06CFAB06CF652C                       ntfs       
/dev/sda3        c204904b-4467-4b77-8429-14fee87209d0   ext4       
/dev/sdb2        96b91028-3eae-42e6-9029-ed370f7aa782   ext4       
/dev/sdb3        36767e24-032d-4073-8cc6-f1647e6574d0   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb3        /home                    ext4       (rw,commit=0)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root 96b91028-3eae-42e6-9029-ed370f7aa782
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root 96b91028-3eae-42e6-9029-ed370f7aa782
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
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 96b91028-3eae-42e6-9029-ed370f7aa782
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=96b91028-3eae-42e6-9029-ed370f7aa782 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 96b91028-3eae-42e6-9029-ed370f7aa782
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=96b91028-3eae-42e6-9029-ed370f7aa782 ro single 
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
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 96b91028-3eae-42e6-9029-ed370f7aa782
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 96b91028-3eae-42e6-9029-ed370f7aa782
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6ED44FB238CF1A06
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

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=96b91028-3eae-42e6-9029-ed370f7aa782 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=36767e24-032d-4073-8cc6-f1647e6574d0 /home           ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
#UUID=5b88a040-be6c-4778-8942-abf43b51d70d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.606494904 = 2.798702592    boot/grub/core.img                             1
   2.719749451 = 2.920308736    boot/grub/grub.cfg                             1
   1.004508972 = 1.078583296    boot/initrd.img-2.6.38-8-generic               2
   2.667301178 = 2.863992832    boot/vmlinuz-2.6.38-8-generic                  1
   1.004508972 = 1.078583296    initrd.img                                     2
   2.667301178 = 2.863992832    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdc

00000000  42 fd a5 b6 45 23 88 4f  d7 d7 36 88 b6 b4 31 c0  |B...E#.O..6...1.|
00000010  2d ef 3c da ba 91 52 f5  50 59 a3 c2 b1 b7 3b 27  |-.<...R.PY....;'|
00000020  5b 6e 9b 93 b2 8d c5 95  84 5c c4 bd 6c 92 a6 61  |[n.......\..l..a|
00000030  fd e9 35 cc ee fc 60 10  5d 9f 6f 70 de 80 cc 06  |..5...`.].op....|
00000040  df d4 c1 60 55 98 85 da  0c 9d 12 00 e1 db 1e 71  |...`U..........q|
00000050  34 3b f1 5f ea 77 cf 6f  d9 63 19 ed ef 1c df 0d  |4;._.w.o.c......|
00000060  5b df 16 8e ca 72 8f bd  3a f6 0a 26 a7 e4 b7 33  |[....r..:..&...3|
00000070  55 9f d6 7b d6 f9 b8 1c  60 61 c1 c5 04 08 55 82  |U..{....`a....U.|
00000080  63 17 76 b1 0e 6f da db  27 0f 10 ab 09 49 e0 d4  |c.v..o..'....I..|
00000090  2b 34 22 43 fe fe f8 d3  c8 24 38 b9 23 4d 4a e8  |+4"C.....$8.#MJ.|
000000a0  76 e5 af f1 60 ac 28 f3  dd b9 ba 02 ea 76 59 0d  |v...`.(......vY.|
000000b0  b9 eb 7a 15 5e c0 31 1a  76 d4 c4 44 14 43 3b ed  |..z.^.1.v..D.C;.|
000000c0  56 2d 7d fe d0 38 e1 aa  2f ba c2 98 72 99 51 28  |V-}..8../...r.Q(|
000000d0  b3 65 9b 60 9c d9 37 a4  0a eb 72 2c 21 85 a3 f5  |.e.`..7...r,!...|
000000e0  6d ca 1c 71 5f e6 41 a1  18 41 27 f9 55 e8 ce b7  |m..q_.A..A'.U...|
000000f0  94 bc a1 7e ba 3f 9b 98  56 a8 21 a9 32 55 13 c7  |...~.?..V.!.2U..|
00000100  ae 0d f7 16 2a ca f7 6c  a2 97 f4 b8 ce cc fd 39  |....*..l.......9|
00000110  7c 2a 32 9f 23 ad b4 c8  26 d8 0c 55 ab 37 11 1f  ||*2.#...&..U.7..|
00000120  a5 cf c2 3b 82 50 d0 4c  21 09 53 d2 02 26 8f d4  |...;.P.L!.S..&..|
00000130  5e 24 a8 63 c1 63 84 44  c5 2b f2 52 ef e5 22 37  |^$.c.c.D.+.R.."7|
00000140  37 ba 9f fd cd 83 dc 5a  c6 2e a2 ee ed 5a 69 1c  |7......Z.....Zi.|
00000150  2c 94 14 5b f1 80 95 3b  a8 66 78 23 6d 3a 4e c2  |,..[...;.fx#m:N.|
00000160  bc ed 2a b8 94 2a 20 ec  4c 2a 0e dd e9 9e da 2d  |..*..* .L*.....-|
00000170  aa 9d e2 41 09 1b 11 ff  0b 82 2d f4 1b 68 71 f2  |...A......-..hq.|
00000180  bb 9d bc 7b 77 67 31 2c  fd 92 0a a3 2c 31 73 04  |...{wg1,....,1s.|
00000190  00 b3 88 9f c5 0f f7 ef  cf 8b 9a 1e 0f b6 de 72  |...............r|
000001a0  a3 4e e9 9d 3b df 14 5f  6b f0 3f b9 25 9e 8e 57  |.N..;.._k.?.%..W|
000001b0  b3 b2 33 3c be a9 77 ab  48 85 6a 80 58 01 1c 7c  |..3<..w.H.j.X..||
000001c0  15 a1 2d 9f 0a 25 2a c2  b5 c3 6c 04 0c 46 3b 0a  |..-..%*...l..F;.|
000001d0  e8 31 1b 48 16 47 c1 3f  68 4e b3 f5 85 f2 e6 54  |.1.H.G.?hN.....T|
000001e0  c9 4a f2 44 c1 38 8e c7  6a e9 33 9e 43 2d da 82  |.J.D.8..j.3.C-..|
000001f0  2f 21 37 ad 76 1d c6 2a  00 2c db 02 8c 61 ec 1c  |/!7.v..*.,...a..|
00000200

Unknown BootLoader on sdc1


Unknown BootLoader on sdc2


Unknown BootLoader on sdc3


Unknown BootLoader on sdc4



=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory

```

---

### Post by YesWeCan on 2011-08-05
Repair you Windows boot: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Dont install grub to your Windows disk, not needed.

---

