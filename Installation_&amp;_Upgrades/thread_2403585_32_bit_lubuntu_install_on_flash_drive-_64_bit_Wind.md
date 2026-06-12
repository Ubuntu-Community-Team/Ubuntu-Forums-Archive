---
title: "32 bit lubuntu install on flash drive- 64 bit Windows7 OS stopped booting up"
date: 2018-10-13
forum: Installation &amp; Upgrades
---

### Post by kabe12 on 2018-10-13
I installed 32 bitlubuntu on a flashdrive(32G) using the install utility and the iso image saved on the 64bit PC.


During installation, I was asked to format the drive and chose F: where the flash drive was connected.
The installation appeared to proceed well.

I went to the BIOS setup, and changed then 1st Boot device to the sandisk/lubuntu, and it booted up.

I now cannot access the 64bit harddrive on the PC. despite changing the BIOS set up to boot HD642(where W7 was /is installed.


F12 gives following bios boot options...

SATA:SAMSUNG HD642JJ
HITACHI HDP725050gla36
USB:SanDisk(The sandisk has 32 bit lubuntu installed which boots up ok.) 
Diagnostics
Boot to utility partition.
Enter Setup


In the BIOS...
HARD DISK BOOT PRIORITY

1st device [SATA:Samsung HD642]
2nd device [SATA: HITACHI HDP72] (backup drive, no OS)
3RD DEVICE [USB:SanDisk]
4th Device  


When I choose  HD642, it does not boot my 64bit windows, but defaults to a Gnu grub VERSION dos SCREEN.
WITH LIST OF OPTIONS.. THE FIRST BEING *uBUNTU which loads from the Flash Drive.
with a log in screen.


If I remove the external 32bit lubuntu flash drive, and boot up, 

I still get the UBUNTU log in, (How is this possible?)
*ubuntu
Memory test
Memory test
windows7(on dev/sdb1) 


choosing windows windows7(on dev/sdb1) 

windows error recovery screen

launch repair
startwindows normally

launch repair
System Recovery Options.

IT does not show an operating system to choose for repair.

windows cannot find a system image on this computer


Where has my W7 gone, and can I recover the situation to boot W7 back up.

Feeling a bit desparate! Any help appreciated. Thanks.

---

### Post by TheFu on 2018-10-13
Is the system UEFI boot or Legacy boot?  Most computers made in the last 5 yrs are UEFI boot and Windows comes pre-installed that way.  Switching to legacy/BIOS boot will break it until you switch it back.

If that doesn't solve the issue, boot linux, install "boot-repair", run it, but only to use the last option (something about creating some boot-info), and post the URL it creates back here.  Don't tell boot repair to try and fix anything.  With a setup like yours, it could cause damage. It would be bad.

---

### Post by oldfred on 2018-10-13
If during install you used BIOS boot, which is most like if the 32bit version, you have to specify during install to install grub to flash drive. If you did not specify F:drive then grub defaulted to first internal drive.

Link to Boot-Repair.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kabe12 on 2018-10-14
The BIOS date showing is 

CMOS SETUP UTILITY 1985-2005 AMERICAN MEGATRENDS. v02.67

 I do not think UEFI is present., as the efi folder in sys/firmware/efi  is not present.


I do not know what installer I used to install lubuntu on the flash drive which was formatted during install, in 

F:drive socket.  Those install files are on the W7 desktop on HD642, (which is the problem drive/OS.)


I think the installer came from source forge, and the .iso file from the ubuntu site.


lubuntu is showing disk information in following images.
 

**My original W7 HD642,** 64 bit. With all my data and progs on it.(still?)

The original primary drive is HD642, and the partition type is known given as "Linux(Bootable)"

(presumably originally NTFS? Before corruption)

 
When Ubuntu running&#8230;
HD642 (original W7 64bit) does not get presented by Ubuntu File manager, but DOES get presented by the BIOS F12 
options as a bootable option.
File browser in Ubuntu does NOT detect HD642, but does detect HDP725

 
[ATTACH=CONFIG]281347[/ATTACH]
 

A  2nd drive 

HDP725  shows as a 'bootable device',  using F12, start options, but cannot boot.

This is  an old WXP/ 32 bit at root. Probably damaged boot but all files are readable.

HDP725  (originally running a 32bit windows OS) does get presented and is accessible for file browsing in Ubuntu, 

 
[ATTACH=CONFIG]281348[/ATTACH]
 

IN THE BIOS

 

Boot Settings:

Hard Disk Boot Priority.

1st device: HD642

2nd device: HDP72

3rd device USB JetFlash Trans.

 If I select to change any of these, I get presented just those options.

In SETUP, the selection of boot up options OFFERED is
SATA SAMSUNG HD642
CD/DVD:tsstcORP
REMOVEABLE dEV.
DISABLED

++++++++++++++++++++++++++++++++++++

[B]My current concern is that the system now boots into UBUNTU, but WITHOUT the external USB with Ubntu OS being 

plugged in.[/B]

That suggests the Ubuntu OS has also been dumped onto HD624. during installation to the F:drive?

ie. UBUNTU now runs from, presumably, the HD642?, whereas I installed it on the external flash drive.?

 During installation, I was asked to check single or dual boot, and chose single, expecting that to refer only to the 
flash drive UBUNTU  OS.

 ---------------

I now have downloaded 2 files. rufus3.3.exe, and boot-repair-disk-64bit.iso
I am advised to use boot-repair iso on a flash drive to examine the set up, by installing it onto an ext. usb drive 
using rufus3 and starting the system with the flashdrive.
 

Given that my last installation of an ISO on a flash drive went catastrophically wrong!!, I am reluctant to compound 
the mess further.


Is there enough info now to attempt a recovery? or  establish if that is possible?
If not, do I still need  to create boot-repair for further interrogation of the system?


Thanks..

---

### Post by oldfred on 2018-10-14
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kabe12 on 2018-10-14
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]

```

============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Windows 7/8/2012 is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,250,263,039 1,250,260,992  83 Linux


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        41c75b74-e7d8-4211-aa24-4403ca55b4dc   ext4       
/dev/sdb1        BA360D7A360D38C1                       ntfs       DellHD

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct 14 23:26 ata-Hitachi_HDP725050GLA360_GEA554RF34E5LG -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 14 23:26 ata-Hitachi_HDP725050GLA360_GEA554RF34E5LG-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Oct 14 23:26 ata-SAMSUNG_HD642JJ_S1JNJ90S802079 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 14 23:26 ata-SAMSUNG_HD642JJ_S1JNJ90S802079-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Oct 15  2018 ata-TSSTcorp_DVD+_-RW_TS-H653G_R4606GBS93591300 -> ../../sr0
lrwxrwxrwx 1 root root  9 Oct 15  2018 usb-Generic-_Compact_Flash_18E391066476-0:1 -> ../../sdd
lrwxrwxrwx 1 root root  9 Oct 15  2018 usb-Generic-_MS_MS-Pro_18E391066476-0:3 -> ../../sdf
lrwxrwxrwx 1 root root  9 Oct 15  2018 usb-Generic-_SD_MMC_18E391066476-0:0 -> ../../sdc
lrwxrwxrwx 1 root root  9 Oct 15  2018 usb-Generic-_SM_xD-Picture_18E391066476-0:2 -> ../../sde
lrwxrwxrwx 1 root root  9 Oct 14 23:26 wwn-0x5000cca34dec4979 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 14 23:26 wwn-0x5000cca34dec4979-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Oct 14 23:26 wwn-0x50024e9200dc4153 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 14 23:26 wwn-0x50024e9200dc4153-part1 -> ../../sda1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb1        /media/ka/DellHD         fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)


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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  41c75b74-e7d8-4211-aa24-4403ca55b4dc
else
  search --no-floppy --fs-uuid --set=root 41c75b74-e7d8-4211-aa24-4403ca55b4dc
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=1
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-41c75b74-e7d8-4211-aa24-4403ca55b4dc' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  41c75b74-e7d8-4211-aa24-4403ca55b4dc
    else
      search --no-floppy --fs-uuid --set=root 41c75b74-e7d8-4211-aa24-4403ca55b4dc
    fi
        linux    /boot/vmlinuz-4.15.0-20-generic root=UUID=41c75b74-e7d8-4211-aa24-4403ca55b4dc ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.15.0-20-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-41c75b74-e7d8-4211-aa24-4403ca55b4dc' {
    menuentry 'Ubuntu, with Linux 4.15.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-20-generic-advanced-41c75b74-e7d8-4211-aa24-4403ca55b4dc' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  41c75b74-e7d8-4211-aa24-4403ca55b4dc
        else
          search --no-floppy --fs-uuid --set=root 41c75b74-e7d8-4211-aa24-4403ca55b4dc
        fi
        echo    'Loading Linux 4.15.0-20-generic ...'
            linux    /boot/vmlinuz-4.15.0-20-generic root=UUID=41c75b74-e7d8-4211-aa24-4403ca55b4dc ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 4.15.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-20-generic-recovery-41c75b74-e7d8-4211-aa24-4403ca55b4dc' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  41c75b74-e7d8-4211-aa24-4403ca55b4dc
        else
          search --no-floppy --fs-uuid --set=root 41c75b74-e7d8-4211-aa24-4403ca55b4dc
        fi
        echo    'Loading Linux 4.15.0-20-generic ...'
            linux    /boot/vmlinuz-4.15.0-20-generic root=UUID=41c75b74-e7d8-4211-aa24-4403ca55b4dc ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-20-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  41c75b74-e7d8-4211-aa24-4403ca55b4dc
    else
      search --no-floppy --fs-uuid --set=root 41c75b74-e7d8-4211-aa24-4403ca55b4dc
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  41c75b74-e7d8-4211-aa24-4403ca55b4dc
    else
      search --no-floppy --fs-uuid --set=root 41c75b74-e7d8-4211-aa24-4403ca55b4dc
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-BA360D7A360D38C1' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  BA360D7A360D38C1
    else
      search --no-floppy --fs-uuid --set=root BA360D7A360D38C1
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
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
# / was on /dev/sda1 during installation
UUID=41c75b74-e7d8-4211-aa24-4403ca55b4dc /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 130.129386902 = 139.725365248  boot/grub/grub.cfg                             1
 186.179801941 = 199.909040128  boot/grub/i386-pc/core.img                     1
 186.177883148 = 199.906979840  boot/vmlinuz-4.15.0-20-generic                 1
 186.177883148 = 199.906979840  vmlinuz                                        1
   3.727298737 = 4.002156544    boot/initrd.img-4.15.0-20-generic              3
   3.727298737 = 4.002156544    initrd.img                                     3
   3.727298737 = 4.002156544    initrd.img.old                                 3

========================== sdb1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 


ADDITIONAL INFORMATION :
=================== log of boot-repair 20181014_2326 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-repair is executed in installed-session (Ubuntu 18.04 LTS, bionic, Ubuntu, i686)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.15.0-20-generic root=UUID=41c75b74-e7d8-4211-aa24-4403ca55b4dc ro quiet splash vt.handoff=1

=================== os-prober:
/dev/sda1:The OS now in use - Ubuntu 18.04 LTS CurrentSession:linux
/dev/sdb1:Windows 7:Windows:chain

=================== blkid:
/dev/sda1: UUID="41c75b74-e7d8-4211-aa24-4403ca55b4dc" TYPE="ext4" PARTUUID="669b7aaa-01"
/dev/sdb1: LABEL="DellHD" UUID="BA360D7A360D38C1" TYPE="ntfs" PARTUUID="8928c6fe-01"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Apr 26 19:25 grub.d
total 80
-rwxr-xr-x 1 root root  9783 Mar  4  2018 00_header
-rwxr-xr-x 1 root root  6258 Mar  4  2018 05_debian_theme
-rwxr-xr-x 1 root root 12693 Mar  4  2018 10_linux
-rwxr-xr-x 1 root root 11298 Mar  4  2018 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Mar  4  2018 30_os-prober
-rwxr-xr-x 1 root root  1418 Mar  4  2018 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Mar  4  2018 40_custom
-rwxr-xr-x 1 root root   216 Mar  4  2018 41_custom
-rw-r--r-- 1 root root   483 Mar  4  2018 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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




=================== UEFI/Legacy mode:
This installed-session is not EFI-compatible.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    notbiosboot, .
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /media/ka/DellHD.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:640GB:scsi:512:512:msdos:ATA SAMSUNG HD642JJ:;
1:1049kB:640GB:640GB:ext4::boot;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA Hitachi HDP72505:;
1:1049kB:500GB:500GB:ntfs::boot;

=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL
sda   disk        596.2G
sda1  part ext4   596.2G
sdb   disk        465.8G
sdb1  part ntfs   465.8G DellHD
sr0   rom          1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /
sdb      1  0  0 running
sdb1     1  0  0         /media/ka/DellHD
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4115448k,nr_inodes=190074,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=828092k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=35,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=16720)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=828088k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdb1 on /media/ka/DellHD type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 gpiochip0 gpiochip1 hidraw0 hidraw1 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 initctl input kmsg kvm lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdc sdd sde sdf sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 4f 38 3a 00 00 00 00  |.........O8:....|
00000030  00 00 0c 00 00 00 00 00  ff 84 a3 03 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  c1 38 0d 36 7a 0d 36 ba  |.........8.6z.6.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  4.0G     0  4.0G   0% /dev
tmpfs          tmpfs     809M  1.3M  808M   1% /run
/dev/sda1      ext4      586G  5.8G  551G   2% /
tmpfs          tmpfs     4.0G   31M  4.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     4.0G     0  4.0G   0% /sys/fs/cgroup
tmpfs          tmpfs     809M   20K  809M   1% /run/user/1000
/dev/sdb1      fuseblk   466G  334G  133G  72% /media/ka/DellHD

=================== fdisk -l:
Disk /dev/sda: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x669b7aaa

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1  *     2048 1250263039 1250260992 596.2G 83 Linux


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x8928c6fe

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1  *     2048 976771071 976769024 465.8G  7 HPFS/NTFS/exFAT



(zenity:15229): dbind-WARNING **: 23:26:53.618: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: 23:26:53.699: GtkDialog mapped without a transient parent. This is discouraged.
User choice: Is sda (ATA SAMSUNG HD642JJ) a removable disk? no




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBRs of all disks (except live-disks and removable disks without OS).
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (ATA SAMSUNG HD642JJ) disk!

The boot files of [The OS now in use - Ubuntu 18.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by TheFu on 2018-10-14
The URL would have been easier to read.
Lacking that, please wrap all the output using "code tags" so things line up. Please.  Go Advanced (#).

---

### Post by oldfred on 2018-10-14
Your first post said you installed to a flash drive. 
But you installed to sda, with Windows on sdb drive.
Was Windows always sdb?
If you switched drives that could be part of issue.

---

### Post by kabe12 on 2018-10-15
Thanks for your reply oldfred.

I did not install to sda. 
That was my W7 62bit system, the thing I was anxious to keep clean, hence choice and intention to have Linux system on a flash drive.

When expressly asked which drive, I expressly chose F:, and the Ubuntu OS has definitely been installed on F:, as I have booted from  the usb on another machine.

sdb has resided with an old windows system (32  bit) still on it, but was a storage, never used for booting this PC.

It reports as windows boot option , I presume, because it still has the file system on it.?

At no time do I recall being asked about the C: drive.
 I was asked about dual or single boot, and chose single  FOR THE FLASH DRIVE, I presumed, although the distinction did not appear during set up.

So I now have a 32 bit Linux system on my 640HD?  and a vast 640 GB drive ready to do 32 bit things? Is that the conclusion.?
If I now save ANYthing on the machine while it is running linux,  like rufus3, or boot-repair file of 800mb, as suggested above,  and as I have, has that now OVERWRITTEN whatever was on the sda?
Does anything I now do on the sda trash and overwrite existing files?
Is the sda now a 32 bit drive?
Can anything now even READ all my data or is it lost forever.?

I am increasingly alarmed by the warnings, but no nearer a solution. 
Correct that. I actually feel physically sick.   At what may be lost, and what I will need to do to get my life back in order.

(I cannot  say how steaming I am about the install instructions, and what has ensued.
.this should really not be possible IMHO.)

So am I in an impossible position or is anything recoverable?

---

### Post by TheFu on 2018-10-15
There are no drive letters in Ubuntu - or any Linux.  Every OS, except perhaps Windows, works using device names.  To avoid doing anything unwanted, it is important to understand which device name goes with which physical device.

I suspect there was confusion with what Rufus does and what installations do.  Rufus copies an ISO file onto the media you specify. It isn't really "installing", but it makes flash media capable of being used to install the OS.  If the next step is to boot from the flash drive and perform an install, the choices for what that does is pretty clear. There are warnings, but those help only if we read and understand them.  Yesterday, someone came to our LUG - Linux Users Group - and wanted to wipe Windows and install Ubuntu.  We helped him do exactly that using a flash drive. I would guess, and it is only a guess, that you made the same choices to wipe the first disk, sda, and install ubuntu that our new friend made yesterday.

I've felt that sinking feeling you feel now.  sda has been written with about 6G of data. Any data under that is gone unless you have backups.  The data areas that haven't been overwritten might be accessible, but getting it back without using backups will probably be painful.   [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) has some ideas.  So does [https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

I would strongly suggest the first step is to buy some new storage and mirror the original disk, sda, over to it, using ddrescue. Then only use the new disk for all data recovery attempts.

From the data above, it appears that 
/dev/sda1 is Linux - it is EXT4 - the "1" means this is the first primary partition on the physical disk.
/dev/sdb1 is Windows - it is NTFS  - the "1" means this is the first primary partition on the physical disk.

sda - the first SATA connection - it is  the device name for the entire disk.
sdb - the second SATA connection - it is  the device name for the entire disk.

Please make a bit-for-bit backup before doing anything else with the original disk.

If the data is very important, there are professional data recovery services which can do amazing things, but they aren't cheap.  $500-$4000. They use specialized tools, specialized knowledge, and have specialized hardware to ensure they do no more damage to the original data.

Not really helpful, but I lost 80% of my data in 2002 because I did something that really shouldn't be allowed, IMHO.  I knew what I was doing at the time, but even with all the warnings NOT to do it, I continued.  I never recovered that data.

---

### Post by oldfred on 2018-10-15
STOP using Ubuntu system. All use is overwriting more data.
Only use live installer or other flash drive based repair tools.

I have used photorec.
It scans drive for anything looking like a file. It does not recover full filename, but just extension. 
Since install of Ubuntu is 6GB and normally scattered all over drive where Windows typically if defragged is all data at front of drive, some data may be recoverable. 
In my case I was looking for .txt files. It found many and many duplicates as deleted files were also restored. I had an older backup and had to compare those files with my backup. Took many hours.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
If testdisk deeper search shows files, immediately copy those as you get full file name.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[URL="http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"]http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step
      [/URL]
Some that use Windows have said Windows tools may work better on NTFS, not sure if now ext4 they would see the old NTFS partition(s).

As mentioned by TheFu best to work on an image copy so you still have original in case recovery damages more.
[URL="http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"]
[/URL]

---

### Post by kabe12 on 2018-10-15
Thanks The Fu for your analysis. I fear the worst, given the evidence.

I attribute the failure to lack of clarity in the installation process, and am dismayed that this should have been so easy.

A friend has suggested ....
When I was given options I believed to be referencing the usb drive, which offer
**Install ubuntu alongside and existing system** (not selected, I want it alone on the flash drive)
**Erase disk and install Ubuntu **(no, the diskm was blank already)
**Something else** (I decided I wanted a 4GB partition on the 16GB usbdrive, which is what I believed I was dealing with.)

I proceeded without it being obvious that I was totally trashing the existing system.

Something like...
"You are about to overwrite OS W7 62 bit and 450GB of data on 624HD, .....are you sure you want to proceed" ....would have been nice.

I cannot now recall the branch decisions, and the GRUB screen was a confusing novelty.

I have some trusted help on offer outside the forum from an experienced programmer, who may be able to help with some data recovery, following steps you have also outlined.

It will be a few days before I can do a drive copy, so I am on hold till then.

Thanks to all who have tried to help.

---

### Post by kabe12 on 2018-10-15
Thank you Thefu.

I am getting an external drive to do a drive copy, and see if anything remains on the shredded disk.

I can't help feeling somewhere the warnings were absent, semantics unclear.
It should be crystal clear what action will affect what system, considering the consequences.

Nothing more to say really.

---

### Post by TheFu on 2018-10-15
Nobody here works for Canonical or can modify the installer.  Sorry.

This complaint has been around since the 1990s by everyone new to Unix. Longtime users expect the OS to do what we tell it and not ask "are you sure?"  If we weren't sure, we wouldn't have said to do it. That is part of the Unix philosophy. Do what I say, and don't ask for confirmation.

There are 2 warnings are already in the installer about wiping the disk, but those have to be read and understood. I just looked at them and they are accurate.  The "Warning" is actually in red, bold, text.

BTW, I can't count how many times software from Microsoft has broken or wiped my Linux installations the last 20+ yrs without **any** warning at all. Everyone that dual-boots with Windows has seen Windows break their Linux boot a few times a year.  The Windows installer has probably wiped millions of existing Linux installations too. Millions.

Anyways, I wish you well and hope the most important data can be recovered.

---

### Post by yancek on 2018-10-15
> When expressly asked which drive, I expressly chose F:, and the Ubuntu  OS has definitely been installed on F:, as I have booted from  the usb  on another machine.


I'm trying to understand where during an attempted install of a Linux system you would have seen a reference to a F: (or C:, D: or other) drive.  Drives and partitions are not and have never been shown in that manner in Linux.  As pointed out above, that is a windows naming convention which is a carryover from 1970's operating systems which usually had 2 floppy drives (A,B) and one hard drive (C).There is a massive amount of documentation on installing the various Ubuntu's and I'm afraid your problems are attributable primarily to a lack of research which resulted in a lack of understanding of what was happening during the install.  If you continue with Ubuntu, I would suggest that you post here before doing something you do not fully understand, saves a lot of trouble as many members here are very knowledgeable about Ubuntu.  Good luck recovering your data.

---

### Post by kabe12 on 2018-10-16
> **yancek said:**
>  I'm trying to understand where during an attempted install of a Linux system you would have seen a reference to a F: (or C:, D: or other) drive. Drives and partitions are not and have never been shown in that manner in Linux. As pointed out above, that is a windows naming convention which is a carryover from 1970's operating systems which usually had 2 floppy drives (A,B) and one hard drive (C). 
 
I do not have access now to discover which installer I downloaded, since the file and internet history have been &#8216;trashed&#8217;.
 
I used an installer to install Ubuntu onto the F: USB, in order to make the OS available for use.
 
Before I could put Ubuntu onto a USB drive, I had an installer on my W7 desktop, and an iso file.
The installer asked me for the drive name from the windows  environment, so I presume that is the point at which F: was identifiable as such.
A little research would have made this evident.
 
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#5](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#5)
 
 
> **yancek said:**
> 
There is a massive amount of documentation on installing the various Ubuntu's and I'm afraid your problems are attributable primarily to a lack of research which resulted in a lack of understanding of what was happening during the install.
 
Meaning  lack of &#8216;sufficient&#8217; research, since in my defense, I managed to install the OS on the USB. and I have used it in another machine to verify.
How much is enough, and when do you know you have sufficient?
 
--------------------
TLDR.
I read, and am told&#8230; &#8220;Install Ubuntu on a Flash Drive.
I follow instructions.
At the next stage I am presented with a menu that invites me to
 
 either
NOT install, but &#8220;TRY&#8221; Ubuntu
OR
Install Ubuntu.
 
Oh&#8230;.. this must be the final step to  &#8220;Install Ubuntu on a Flash Drive.&#8221;
 
Whoops.. Ive wiped my entire hard drive.
 
-------------------------
POST MORTEM
I believe the problem developed the next time I rebooted, and after my assumption that UBUNTU is now &#8216;available for use/installed&#8217; on the USB,  
I did not get a sophisticated GRUB, explaining the differences between Try and Install.

I am presented with a novel (to me) screen which leads me to assume I am already on the USB., and offers&#8230;
 
1. Try Linux without installing it.
2. Install Linux
3. Check Disk for defects
4. Test Memory
5. Boot from first hard disk
6. Advanced options
7. Help
 
1. I do not want to &#8216;try it&#8217;. I am committed to using it. So next option?
 
Now..as far as I am concerned, the environment I am in now is the USB OS Ubuntu, otherwise I would not see this screen.
So whatever I do from this root starting point, will only be able to address the next level up, the USB.
 
2. What does &#8220;install&#8221; mean?
 (Cambridge Dic.def:&#8221; to make available for use&#8221;&#8230;.specialized computing : **to put a [computer]("https://dictionary.cambridge.org/dictionary/english/computer") [program]("https://dictionary.cambridge.org/dictionary/english/program") onto a [computer]("https://dictionary.cambridge.org/dictionary/english/computer") so that the [computer]("https://dictionary.cambridge.org/dictionary/english/computer") can use it:)**
 
LOGIC
I need to install the program before I can use it. Until I do that it is NOT AVAILABLE.
I guess the process  is now asking me to fix, secure, commit to the installation on the USB stick.?
 
Since &#8216;I am on the UBUNTU platform&#8217;, any commands will only affect the USB.?
Wrong of course, since at this point, as I now understand,  I have already installed  ubuntu on the USB,  and I am not yet inside the OS.
 
To make it available, ie install  it,  I should have chosen &#8220;Try&#8221; it.
Choosing &#8220;Try&#8230;&#8221;  does &#8216;install&#8217; it, and stating &#8220;without installing it.&#8221; is surely to propose the impossible, and very misleading.

So I want it installed, not tried and it is saying at option 1., it is &#8216;not installed&#8217;.
 
Leading, logically,  back to option 2&#8230;.Install.
(Although I assumed I had already done so, maybe to boot up, I need this step a gain?.
Not serious, I assumed, Ubuntu is on the USB, and I am safely isolated from harming the PC.
Select install, at worst, can only overwrite the USB?
So the options whatever I choose will only result in needing to go round yet again if there is a problem.
 
Wrong of course. Badly wrong. I cannot replicate this, to confirm where I strayed after that. Probably not understanding novel drive references, and trusting that I could only act upon the USB,
because the USB was promoted as an installed copy of Ubuntu, not an installer.  ie&#8220;How to run Ubuntu from a flash drive&#8221; , should say  &#8220;Use the demo Ubuntu on the installer  as a system OS.&#8221;
There is no sandbox.
 
 &#8216;Try&#8217; should say &#8216;run&#8217;, since it&#8217;s already installed on the USB.
&#8216;Install&#8217; means install, but not over itself, since that is already an installation.
Install means the USB can overwrite any discovered drive, and the targets offered will not be familiar to the windows user being invited to try or install.
 
So the primary design objective of  this USB is to have a portable installer, rather than a portable &#8216;permanent&#8217; Ubuntu OS,
because the designers appear to consider TRY to be a precursor to &#8216;Install&#8217;.
 
So yes &#8220;lack of understanding of what was happening during the install&#8221; &#8230;.compounded by lack of clarity in the instructions.
 
Ironically, seeking help here, &#8220;suggest that you post here before doing something you do not fully understand &#8220; to prevent further harm has probably resulted in further harm.
Downloading a  large  boot-info file and installer, following advice, I have probably overwritten even more on the PC C: drive, and lost what the file overwrote.?
 
I appreciate that forum contributors are not Canonical staff, and that canonical business model is selling &#8216;support&#8217; for Linux, which explains a lot.
 
I appreciate  all the input.
 
Ps.. can someone tell me how or if I can delete a post?
Sometimes It does not appear, I post again, and it appears twice after an interval for instance, I need to delete one to avoid being jailed.

---

### Post by oldfred on 2018-10-16
Ubuntu on flash drive is called the live installer. You use a tool to extract ISO to flash drive or DVD and make it bootable. That is just to create the live installer.
Or when you boot live installer, you have a choice to do a full install to drive & partition you specify (or entire drive) or use as is to test if it works well with your system. It will not be as fast as a full install to a hard drive as flash drives on USB ports are not as fast as internal drives.

Even if on flash drive it it not updateable, it is just like the DVD and cannot be written to, to keep it consistent as the live installer.
You can add persistence and save some data.

       Persistent  install
[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)
[https://askubuntu.com/questions/1025847/usb-live-pen-persistent-boot-disk-in-uefi](https://askubuntu.com/questions/1025847/usb-live-pen-persistent-boot-disk-in-uefi)
[https://askubuntu.com/questions/1012717/what-is-a-cheap-simple-way-to-try-out-new-os-releases-without-committing-to-it/1012752#1012752](https://askubuntu.com/questions/1012717/what-is-a-cheap-simple-way-to-try-out-new-os-releases-without-committing-to-it/1012752#1012752)

You can also do a full install to a flash drive, but that cannot be same flash drive or DVD as live installer.
       
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

