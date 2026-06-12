---
title: "Installed Ubuntu 11.04 but cannot boot into it or windows 7"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by lumale on 2011-10-06
Hi, 

I was originally running Windows 7 on a 240GB SSD and I had another 1.5TB hard drive in my computer which I kept video files etc on. I just installed (or tried to) Ubuntu 11.04 on a partition of the 1.5 TB hard drive and now cannot boot into Windows or Ubuntu, except for the "try it" version of Ubuntu. I have tried using the Windows 7 recovery disk and running the bootrec.exe file with /FixMbr and /FixBoot and /RebuildBcd but to no avail. Additionally, when running the DISKPART command in the Windows System Recovery Tool it lists what used to be my C:/ (240GB) as now being my D:/ and what used to be my F:/ (1.5TB) as my C:/. 

Here's my RESULTS.txt from the boot info script:


```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/core.img

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

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 60956 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 240.1 GB, 240057409536 bytes
256 heads, 63 sectors/track, 29071 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   468,860,927   468,391,936 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 2,315,873,071 2,315,873,009   7 NTFS / exFAT / HPFS
/dev/sdb2       2,315,874,302 2,930,274,303   614,400,002   5 Extended
/dev/sdb5       2,315,874,304 2,316,376,063       501,760  83 Linux
/dev/sdb6       2,316,378,112 2,320,281,599     3,903,488  82 Linux swap / Solaris
/dev/sdb7       2,320,283,648 2,378,874,879    58,591,232  83 Linux
/dev/sdb8       2,378,876,928 2,930,274,303   551,397,376  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16003694592 bytes
19 heads, 19 sectors/track, 86585 cylinders, total 31257216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064    31,257,215    31,249,152   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5240-D17F                              vfat       
/dev/sda3        A0E069C6E069A370                       ntfs       
/dev/sdb1        269E73B19E73785F                       ntfs       LUKE2
/dev/sdb5        db597153-75f1-4bf9-9ccb-3749ed7d4335   ext2       
/dev/sdb6        dc641794-b1b6-495c-b488-0207c7f720e1   swap       
/dev/sdb7        fd85b602-a80c-4df9-be8d-14e05e6f9d42   ext4       
/dev/sdb8        66994941-2f42-4efd-b04d-ffa638b866db   ext4       
/dev/sdc1        18E3-0A17                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     vfat       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

============================= sdb5/grub/grub.cfg: ==============================

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
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root fd85b602-a80c-4df9-be8d-14e05e6f9d42
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root db597153-75f1-4bf9-9ccb-3749ed7d4335
set locale_dir=($root)/grub/locale
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
    search --no-floppy --fs-uuid --set=root db597153-75f1-4bf9-9ccb-3749ed7d4335
    linux    /vmlinuz-2.6.38-8-generic root=UUID=fd85b602-a80c-4df9-be8d-14e05e6f9d42 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root db597153-75f1-4bf9-9ccb-3749ed7d4335
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=fd85b602-a80c-4df9-be8d-14e05e6f9d42 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root db597153-75f1-4bf9-9ccb-3749ed7d4335
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root db597153-75f1-4bf9-9ccb-3749ed7d4335
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1104.334715843 = 1185.770372096 grub/grub.cfg                                  1
1104.317959785 = 1185.752380416 initrd.img-2.6.38-8-generic                   54
1104.305191994 = 1185.738671104 vmlinuz-2.6.38-8-generic                      20

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=fd85b602-a80c-4df9-be8d-14e05e6f9d42 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb5 during installation
UUID=db597153-75f1-4bf9-9ccb-3749ed7d4335 /boot           ext2    defaults        0       2
# /home was on /dev/sdb8 during installation
UUID=66994941-2f42-4efd-b04d-ffa638b866db /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=dc641794-b1b6-495c-b488-0207c7f720e1 none            swap    sw              0       0
--------------------------------------------------------------------------------

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
            ?? = ??             syslinux/syslinux.cfg                          1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 7f d1 40 52 4e  4f 20 4e 41 4d 45 20 20  |..)..@RNO NAME  |
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

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```Please tell me how I can fix this, as it would be a real pain to reinstall Windows and all the programs. Also, I was a little too trusting in the install process and did not back up my files.

Also, when I say I cannot boot into Ubuntu I mean there is no option at bootup for me to boot into Ubuntu. I am using Asus' UEFI Bios and the only options are my DVD drive, Windows Boot Manager, which just attempts to load the windows files then gives up, and my SSD.

I would very much appreciate any help.

Also, note: LUKE2 is the name of my 1.5TB drive.

---

### Post by lumale on 2011-10-06
bump (sorry, it's a pretty urgent request as I cannot get to any OSs and am forced to view this on my phone)

---

### Post by dino99 on 2011-10-06
how i'm doing installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by lumale on 2011-10-06
> **dino99 said:**
> how i'm doing installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Unfortunately, that doesn't help me at this stage - I'm just trying to get Windows back.

---

### Post by dino99 on 2011-10-06
so use the windoz cd to repair it :)

---

### Post by lumale on 2011-10-06
> **dino99 said:**
> so use the windoz cd to repair it :)


I already tried that - bootrec didn't work and windows couldn't find any automatic repair options.

---

### Post by oldfred on 2011-10-07
You are booting with UEFI which is a lot different than the old style BIOS/MBR boot. That you have Windows in the MBR does not matter as it is not used. The boot script does not parse the efi partition but it has to have Windows files in it. Some have reported that grub overwrites the efi partition files or reformats before installing without checking that the efi partition already has files in it. This should be reported as a bug to the grub efi installation procedure.

Windows also has another boot partition sda2 that the script does not show.

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ in case of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.
Post #76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
efi\Microsoft\Boot\bootmgfw.efi
Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)

bug reports info on how to do:
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
Check bugs
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

---

