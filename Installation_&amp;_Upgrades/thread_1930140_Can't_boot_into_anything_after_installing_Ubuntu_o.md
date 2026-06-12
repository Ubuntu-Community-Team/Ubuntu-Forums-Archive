---
title: "Can't boot into anything after installing Ubuntu on Windows 7"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by zeiontic on 2012-02-23
Hi,

I installed Ubuntu 11.10 as a partition on the same HD as my Windows 7; after rebooting the HD would not boot into either OS. I've tried to set partition flags to 'boot' but it does nothing. Should there be some files I need in /boot ?

I'm able to mount and access the files on either partition but I can't boot into them. (Only able to boot from USB). 

Please help.

Thanks.

---

### Post by darkod on 2012-02-23
Boot into live mode and follow the link in my signature to run the boot info script. Post the results as explained there. They will show more details.

---

### Post by zeiontic on 2012-02-23
Thanks for replying; here's the result:
```

----------------------------------------------------------------------

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 37976 of /dev/sdb1 for its 
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

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1   1,534,093,312 1,550,093,312    16,000,001 Swap partition (Linux)
/dev/sda2   1,550,093,313 1,953,524,953   403,431,641 Data partition (Windows/Linux)
/dev/sda3         468,992 1,534,093,311 1,533,624,320 EFI System partition

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060927 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            128     8,060,799     8,060,672   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1fc11ecd-0735-4c85-bbf3-a6b2e1f94ce4   swap       
/dev/sda2        26d36caa-7d60-4f39-afd6-1c596a6552a3   ext4       
/dev/sda3        DCAA8516AA84EE78                       ntfs       
/dev/sdb1        7C9A-C58E                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/DCAA8516AA84EE78  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


=========================== sda2/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root 26d36caa-7d60-4f39-afd6-1c596a6552a3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root 26d36caa-7d60-4f39-afd6-1c596a6552a3
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 26d36caa-7d60-4f39-afd6-1c596a6552a3
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=26d36caa-7d60-4f39-afd6-1c596a6552a3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 26d36caa-7d60-4f39-afd6-1c596a6552a3
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=26d36caa-7d60-4f39-afd6-1c596a6552a3 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 26d36caa-7d60-4f39-afd6-1c596a6552a3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 26d36caa-7d60-4f39-afd6-1c596a6552a3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=26d36caa-7d60-4f39-afd6-1c596a6552a3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=1fc11ecd-0735-4c85-bbf3-a6b2e1f94ce4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

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

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

---

### Post by darkod on 2012-02-23
Wow, it looks quite messy right now. You seem to be using GPT table on the disk plus EFI boot (or the win7 partition was wrongly marked as EFI).

I haven't got much experience with both. Let me see if I can call some help.

---

### Post by zeiontic on 2012-02-23
:cry:

I use a EFI BIOS if that says anything...

---

### Post by darkod on 2012-02-23
And do you have a win7 dvd or you only had a restore partition?

---

### Post by zeiontic on 2012-02-23
I have a windows 7 DVD.
I tried installing ubuntu with wubi at first but there was some problems with it booting, so then I tried to used the liveUSB method to install it. When I tried to install using the live method ubuntu couldn't detect my windows 7 partition (only had options to wipe the disk or 'something else'), so then I partitioned my HD, made a swap partition thing with the liveUSB, and then installed a ubuntu partition (I picked '/' instead of '/boot').

---

### Post by oldfred on 2012-02-23
When you repartitioned, was the sda1 the efi partition? It is now swap which is unusual. 

Windows 7 will only work on gpt partitioning with UEFI. But UEFI has to have the first partition as the efi partition. Even systems with UEFI will look first for the efi partition and if not found boot in BIOS mode from the MBR.

Older Windows info on gpt - updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

> For UEFI systems, each bootable drive must contain an ESP, an MSR, and at least one basic data partition that contains the operating system. Each data drive must contain at least an MSR and one basic data partition.

Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

Gert has been updating boot info script to also parse efi partition and some other fixes. Could you please run the git version.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript


```

---

### Post by darkod on 2012-02-23
But with making the swap partition, sda1, you deleted the EFI system partition where parts of the bootloaders are stored.

Since ubuntu is new install, I guess you have no important data inside. Boot the ubuntu cd in live mode, open Gparted and delete sda1 and sda2. If sda1 has a keys symbol, it means it's mounted (live mode usually mounts swap) so you will need to do right-click on it in Gparted, and Swapoff. The keys symbol should go away. After that you can delete it.

oldfred, what is the best way to create the EFI system partition? parted? Gparted?

EDIT: We were typing at the same time. The idea is, delete sda1 and sda2, create new sda1 partition as EFI system, try to restore windows boot (because win7 boot files are also missing) with the win7 dvd. Will he need to change the type of the win7 partition to ntfs manually?

---

### Post by oldfred on 2012-02-23
The gpt printout does not seem to show format, just that it is a data partition. Elsewhere it does say NTFS, so I assume it is ok.

I do not know all the details of repairing a broken UEFI system. The main boot files have to be in the efi partition. Not sure if a standard Windows 7 repairCD/USB also repairs efi partitions??

Someone posted this before, but I think it was with refit from a Mac, so not exactly compariable.

```
find /boot/efi -name "*efi"
/boot/efi
[COLOR=DarkRed]/boot/efi/EFI/ubuntu/grubx64.efi[/COLOR]
/boot/efi/EFI/BOOT/refit.efi
/boot/efi/EFI/BOOT/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
[COLOR=DarkRed]/boot/efi/EFI/Microsoft/Boot/bootmgr.efi[/COLOR]
/boot/efi/EFI/Microsoft/Boot/memtest.efi
/boot/efi/EFI/grub/grub.efi
/boot/efi/EFI/BOOT-backup/bootx64.efi
/boot/efi/EFI/BOOT-backup/BOOT/refit/refit.efi
/boot/efi/EFI/BOOT-backup/BOOT/bootx64.efi

```

I think the required files are the one's I have highlighted.

---

### Post by zeiontic on 2012-02-23
I've deleted sda1 and sda2, now they are both unallocated.
How do I make sda1 as EFI?

edit: I will try to use the Windows restore DVD.
edit: I can't run the repair program from booting with DVD... it says it is not compatible with the version of windows I am trying to repair??

---

### Post by oldfred on 2012-02-23
You can use gparted and set the boot flag. But in gpt the boot flag is not the same as a boot flag in MBR. You can also use gdisk which is in the repository and on some Linux repairCD.

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

Grub also had (has) a bug. So backup your efi partition before trying to reinstall Ubuntu. Not sure if newest grub has this fixed.
UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)

---

### Post by zeiontic on 2012-02-23
Ok so, before I try to reinstall ubuntu I want to get my windows booting.

I made a new FAT32 partition with gparted and I set the flag to 'boot' (and nothing else).
What flags should my windows partition have?

edit: the FAT32 partition is sda1, the windows partition is sda3
edit: It doesn't boot still. I guess I'm missing the boot files in the EFI partition? (which I can't repair with the DVD?)

---

### Post by oldfred on 2012-02-23
You may be better in a Windows forum. 

I found this in google. But most of the results are just giving up on gpt & UEFI and reinstall in BIOS/MBR. I think that is only because few know about UEFI and they suggest what they know.

Initial Startup Phase for EFI Computers
[http://sourcedaddy.com/windows-7/initial-startup-phase-for-efi-computers.html](http://sourcedaddy.com/windows-7/initial-startup-phase-for-efi-computers.html)

---

### Post by zeiontic on 2012-02-23
Okay.. I think I will just reinstall Windows then Ubuntu again. And hopefully not mess it up this time.
Anyway thanks for all the help.

---

### Post by oldfred on 2012-02-23
With gpt every partition is primary and you can just add partitions.

Use Windows tools to shrink Windows partition, but not to create partitions. I think even in gpt Windows may want to convert to dynamic but with gpt that is not required.


Be sure to back up efi partition in case grub bug still overwrites it. And create partitions with gparted or gdisk before the install and use manual install or Something else.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)


Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

### Post by zeiontic on 2012-02-23
Okay so, actually I haven't reinstalled windows yet.
So is there still a solution to this situation?

edit: actually I wouldn't care that much about the dual boot with windows; would it be possible to use the liveUSB to install Ubuntu without formatting my HD?

---

### Post by oldfred on 2012-02-23
I thought you had already formatted drive?

In all cases it is better to decide on partitions and sizes and use manual install. It does require a bit of advance planning. If dual booting you have to allocate partitions for Windows as well and they like to be first.

Is there some data you want to save that is not backed up?

---

### Post by zeiontic on 2012-02-23
Okay I've backed-up all the files I need and now I'm going to use gparted to set up the partitions before I install Ubuntu.

So to summarize I need to have:

1. /dev/sda1 as a FAT32 with 250MB, (and I am also going to make /efi/grub on this partition)

.. and what else?

---

### Post by oldfred on 2012-02-23
If planning Windows you need to create those partitions. If not I suggest smaller system partitions and larger /home or data partition(s).

With gpt you do not have to worry about primary or logical.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

