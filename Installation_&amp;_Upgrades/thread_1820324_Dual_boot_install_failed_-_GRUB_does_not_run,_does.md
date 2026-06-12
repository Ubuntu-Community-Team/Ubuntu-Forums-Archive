---
title: "Dual boot install failed - GRUB does not run, does straight to Win7"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by ZaphodFJ on 2011-08-07
Hi All,

Can someone give me a nudge in the right direction?

Win 7 (64 bit) machine has 500 GB drive C and 500 GB that shows as drive H.  C holds the OS and data, H is there waiting for C to fill.

Doing a dual boot install of 11.04 (64 bit) from USB, I took the "Win 7 and Ubuntu" side-by-side option and told it to partition the 500GB drive in two equal halves.  It only showed one 500GB drive, which I presumed to be C:....

Install runs through, I reboot and it goes straight to Windows 7.  No sign of Grub or the Windows bootloader.

Windows now tells me I have 500GB on C: and 250 GB on H:  So the partition clearly worked. 

Any suggestions (before I do a total wipe on H: and redo the install, with H: disconnected?!)

TIA.

Zaphod

---

### Post by oldfred on 2011-08-07
Did you try booting from the other drive? Grub normally installs to sda, unless you selected some place else.

Post this to see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by ZaphodFJ on 2011-08-08
I boot as normal - direct to Windows.

So I boot from the USB stick I installed from: 

Windows C: mounts as /media/HardDisk1 (HardDisk1 was its volume name under Windows), shows as 500GB
This appears to be /dev/sda2

Windows H: mounts as /media/HardDisk2, 250GB - This appears to be /dev/sdb1 
I also see a mount to "/media/246 GB Filesystem", from a volume calling itself "/media/4f0535f6-1320-43c1-a93f-5d8cb8bfadab".  This is the other half of the physical volume H: is on.  This comes up as /dev/sdb5 

Full results of the script file are below.

TIA.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.

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

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 4734984 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   976,771,071   976,564,224   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   488,385,535   488,383,488   7 NTFS / exFAT / HPFS
/dev/sdb2         488,386,558   976,771,071   488,384,514   5 Extended
/dev/sdb5         488,386,560   968,562,687   480,176,128  83 Linux
/dev/sdb6         968,564,736   976,771,071     8,206,336  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4007 MB, 4007657472 bytes
183 heads, 16 sectors/track, 2673 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             16     7,827,454     7,827,439   b W95 FAT32


Drive: sde _____________________________________________________________________

Disk /dev/sde: 122 MB, 122814464 bytes
128 heads, 2 sectors/track, 937 cylinders, total 239872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *              2       239,871       239,870   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F60A25740A2532D3                       ntfs       System Reserved
/dev/sda2        C2B02942B0293E73                       ntfs       HardDisk1
/dev/sdb1        F084102D840FF53E                       ntfs       HardDisk2
/dev/sdb5        4f0535f6-1320-43c1-a93f-5d8cb8bfadab   ext4       
/dev/sdb6        835b10ea-6ac5-4e85-8e52-4581df3f85c2   swap       
/dev/sdd1        B8B2-89D4                              vfat       PENDRIVE
/dev/sde1        0DD1-0074                              vfat       DISGO

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/HardDisk1         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/HardDisk2         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/4f0535f6-1320-43c1-a93f-5d8cb8bfadab ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sde1        /media/DISGO            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 4f0535f6-1320-43c1-a93f-5d8cb8bfadab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 4f0535f6-1320-43c1-a93f-5d8cb8bfadab
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
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 4f0535f6-1320-43c1-a93f-5d8cb8bfadab
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=4f0535f6-1320-43c1-a93f-5d8cb8bfadab ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 4f0535f6-1320-43c1-a93f-5d8cb8bfadab
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=4f0535f6-1320-43c1-a93f-5d8cb8bfadab ro single 
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
    search --no-floppy --fs-uuid --set=root 4f0535f6-1320-43c1-a93f-5d8cb8bfadab
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 4f0535f6-1320-43c1-a93f-5d8cb8bfadab
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root F60A25740A2532D3
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
UUID=4f0535f6-1320-43c1-a93f-5d8cb8bfadab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=835b10ea-6ac5-4e85-8e52-4581df3f85c2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 441.064296722 = 473.589182464  boot/grub/grub.cfg                             1
 398.185546875 = 427.548475392  boot/initrd.img-2.6.38-8-generic               2
 369.013675690 = 396.225417216  boot/vmlinuz-2.6.38-8-generic                  1
 398.185546875 = 427.548475392  initrd.img                                     2
 369.013675690 = 396.225417216  vmlinuz                                        1

=========================== sdd1/boot/grub/grub.cfg: ===========================

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

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sde1

00000000  eb 3c 90 2b 51 7a 54 34  49 48 43 00 02 04 01 00  |.<.+QzT4IHC.....|
00000010  02 00 02 00 00 f8 ea 00  02 00 80 00 02 00 00 00  |................|
00000020  fe a8 03 00 80 00 29 74  00 d1 0d 00 00 00 00 00  |......)t........|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by YesWeCan on 2011-08-08
Grub is not installed to the MBR of anydisk. Since you have Ubuntu on sdb you probably want Grub on sdb too. This way you can either boot sdb to get the Grub bootloader or boot sda to get Windows bootloader. Grub will give you Windows on its menu.

Boot from live CD
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-partition=/mnt /dev/sdb

Then reboot off sdb and run
sudo update-grub
to add Windows to the Grub menu

---

### Post by ZaphodFJ on 2011-08-08
*Boot from live CD*
- works
[I]
sudo mount /dev/sdb5 /mnt[/I]
- says
[I] Unrecognized option `--root-partition=/mnt'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.  [/I]

You went on to say I should reboot off SDB - is there an easy way to do that, without messing round with hardware?  The BIOS is only showing one hard disk.

TIA.

---

### Post by oldfred on 2011-08-08
Did you copy YesWeCan's commands. Sometimes in hand typing them a space or character is not entered correctly. But if now the system is not seeing sdb then the commands will not work.

BIOS did see second drive when you ran boot script as it could not have shown the second drive in script otherwise. Did something change since you ran script?

BIOS should show two drives, usually by model number/size. It looks like yours are identical. I have two identical 160GB SATA drives and at first had to guess which to boot from in BIOS. Then I learned the order seems to be consistent in BIOS and sda, sdb order. If one drive is IDE and the other SATA that can confuse drive order.

---

### Post by ZaphodFJ on 2011-08-08
Hi,

YesWeCan's Commands were C&P'ed directly...

Re. BIOS - my mistake.  The GUI front-end to the BIOS only shows bootable devices.  It lists one hard drive, CD, USB and some 'Generic Device'.  It doesn't show non-bootable USB devices (so, I'm guessing the second hard-drive is not seen here because it is non-bootable?)

On closer inspection- and through the textual boot options that list all devices, I do see two hard drives (with the same model number - this could get confusing).

The only device that boots into Linux is the USB drive I installed from, running as a live disk.

Is this likely to be an easy fix, or might wiping the partitions on sdb and reinstalling be quicker, now I have a better idea of what I am looking at.  Somewhere in the setup I probably confused sda/sdb and the identical model numbers.

BTW, OldFred - do you have one OS per hard-drive, or do you dual boot using one disk for both OSes (maybe you don't dual boot at all!).

Zaphod

---

### Post by oldfred on 2011-08-08
I have XP on sda and Ubuntu on sdb. But I have a newer sdc that is larger and I have all but my first Ubuntu still installed, puppy, Oneiric  and an empty partition or two to experiment with.:)

I suggest an operating system fully on each drive and the boot loader on the same drive. This is more for reliability than any other reason, so if a drive fails you can boot the other.

while root is supposed to also still work, with 11.04 they changed it to boot.

This is exactly the same command as before by YesWeCan except using boot.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb5 and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdb5 if not correct:
sudo fdisk -l
#confirm that linux is sdb5
[COLOR=Red]sudo mount /dev/sdb5 /mnt[/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If grub 1.99 with Natty uses boot not root
[COLOR=Red]sudo grub-install --boot-directory=/mnt/ /dev/sdb

[/COLOR]

---

### Post by YesWeCan on 2011-08-08
Something strange going on here. That grub-install command should definitely work ok provided the preceding mount command worked.
You may want to post another bootinfoscript output if the grub install commands fail to work.

You may also want to make the first partition on sdb bootable just so it shows up properly in your bios boot list.

sudo sfdisk /dev/sdb -A1

---

### Post by ZaphodFJ on 2011-08-10
Good news:

I ran the following commands.  Output id described - though I am having to do this from memory as I forgot to save the file I was noting everything in (duh!)

**From oldfred**

[I]sudo fdisk -l
#confirm that linux is sdb5
[/I]
- output confirms sdb5 is Linux

[I]sudo mount /dev/sdb5 /mnt
[/I]- works

[I]sudo grub-install --root-directory=/mnt/ /dev/sdb
[/I]- says installation was successful.  No other comments

[I]#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sdb
[/I]- didn't do this, as it should have been Grub 2 (was I right to ignore this step?)

[I]sudo sfdisk /dev/sdb -A1 
[/I]
**From YesWeCan**

[I]sudo sfdisk /dev/sdb -A1 
[/I]- did it, the error was a complaint about the partition not coinciding with the end of a cylinder, and possible differences in behaviour with Linux/DOS.  It went ahead and ran anyway, without giving me an option to cancel or confirm.

Then I rebooted: straight to Windows 7, no bootloaders seen.

Then I rebooted via BIOS boot options.  The second hard disk (sdb) is now higher in the list, I told the BIOS to use it and GRUB appeared, asking me if I wanted Ubuntu or Windows.  I accepted Ubuntu and all appears to work.

As I type this, updates are downloading.  The update manager complained of a failed update from earlier - maybe something went wrong in the install, hence my current woes.

I will see if it does anything re. boot options by itself.  If it doesn't, I will see if the BIOS will let me promote sdb above sda permanently.

---

### Post by ZaphodFJ on 2011-08-10
After the updates, Grub 1.99 appears.

Ubuntu boots by default.
Windows will boot if asked to.

So, problem solved.

Now I'm off to sort out data sharing between the two, but that's well documented.

Thanks again!

---

### Post by YesWeCan on 2011-08-10
Good stuff. Dont forget to mark this as solved in [COLOR="Red"]Thread Tools[/COLOR].

---

