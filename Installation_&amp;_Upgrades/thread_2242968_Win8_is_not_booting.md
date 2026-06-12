---
title: "Win8 is not booting"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by priyesh2 on 2014-09-05
Can anyone help me...


1 week ago i tried to install Ubuntu 12.10 and 13.10, but members here suggested me to install Ubuntu 14.04, so i did.

Now my win8 is not booting, Ubuntu is directly boots without showing to option select windows.

Windows boot loader is peresnt on my HDD 

Output of sudo parted -l

```
priyesh@priyesh-HP-Pavilion-15-Notebook-PC:~$ sudo parted -l
Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  10.7GB  10.7GB  primary   fat32           hidden, lba
 2      10.7GB  63.2GB  52.4GB  primary   ntfs            boot
 4      63.2GB  116GB   52.4GB  extended
 5      63.2GB  106GB   42.4GB  logical   ext4
 6      106GB   116GB   9999MB  logical   linux-swap(v1)
 3      116GB   500GB   385GB   primary   ntfs


```


i tried several things
1 : [http://askubuntu.com/questions/210914/grub-does-not-show-a-windows-8-option-after-dual-boot](http://askubuntu.com/questions/210914/grub-does-not-show-a-windows-8-option-after-dual-boot)
 /etc/grub.d/40_custom         could not edit and save 40_custom file because i root is the owner (i m admin, i don't know how to save i).

2: [http://ubuntuforums.org/showthread.php?t=2233142](http://ubuntuforums.org/showthread.php?t=2233142)
 Didn't work for me,  anyone please

My laptop is HP pavilion 15 n204tx pre-installed with Ubuntu, legacy mode.

---

### Post by priyesh2 on 2014-09-05
my [B]bootinfoscript output: 
[/B]
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 12735888 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos1)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    20,973,567    20,971,520  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,973,568   123,373,567   102,400,000   7 NTFS / exFAT / HPFS
/dev/sda3         225,773,568   976,771,071   750,997,504   7 NTFS / exFAT / HPFS
/dev/sda4         123,375,614   225,773,567   102,397,954   5 Extended
/dev/sda5         123,375,616   206,241,791    82,866,176  83 Linux
/dev/sda6         206,243,840   225,773,567    19,529,728  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B26B-0339                              vfat       HP_TOOLS
/dev/sda2        E0C87500C874D66E                       ntfs       Win 8
/dev/sda3        042EE56F2EE55A66                       ntfs       My files
/dev/sda5        30bfe694-009d-4d10-a8e8-3129403cd200   ext4       
/dev/sda6        5b3d1599-6342-46ba-8633-a71cfd2ca4f1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/priyesh/Win 8     fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /media/priyesh/My files  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#########################################################
#                                                       #
# Grub2 configuration file for recovery partitions #
# By: Mario Limonciello <Mario_Limonciello@Dell.com>    #
#                                                       #
#########################################################

#
# Try to load the grub environment. We may have set a failure bit here.
#  If the failure bit is set, then we don't default to automatic install
#
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
  set default=0
else
  set timeout=0
  set default=4
fi

#
# Load other misc defaults
#

#First check our current directory for additional options
if [ -s /boot/grub/common.cfg ]; then
    source /boot/grub/common.cfg
fi

#Now set the root partition that has our OS installer
search --no-floppy --hint '(hd0,1)' --set --fs-uuid B26B-0339

#If we still don't have options, they are on the the RP too, look there
#If missing, load a nice basic default set
if [ -z "${options}" ]; then
    if [ -s /cdrom/boot/grub/common.cfg ]; then
        source /cdrom/boot/grub/common.cfg
    else
        set options="boot=casper automatic-ubiquity noprompt quiet splash --"
    fi
fi

#adding default kernel options in bootstrap
set options="$options vga=791 i915.modeset=1"

#Support starting from a loopback mount (Only support ubuntu.iso for filename)
if [ -f /ubuntu.iso ]; then
    loopback loop /ubuntu.iso
    set root=(loop)
    set loop_options="iso-scan/filename=/ubuntu.iso"
fi

if loadfont ${prefix}/unicode.pf2 ; then
  set gfxmode=auto
  if [ -e ${prefix}/efi ]; then
    insmod efi_gop
    insmod efi_uga
  else
    insmod vbe
    insmod vga
  fi
  insmod video_bochs
  insmod video_cirrus
  insmod gfxterm
fi
terminal_output gfxterm

#
# Show the menu if we press shift
#
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

set menu_color_normal=white/red
set menu_color_highlight=red/white
if background_color 44,0,30; then
  clear
fi

set gfxpayload=keep

if hwmatch ${prefix}/cedartraillist.txt 3; then
  if [ ${match} = 1 ]; then
    set options="$options mem=4GB"
  fi
fi

if hwmatch ${prefix}/nomodesetlist.txt 3; then
  if [ ${match} != 0 ]; then
    set options="nomodeset $options"
  fi
fi

#
# Debugging information and options
#
menuentry "If you are seeing this menu, your installation has failed." {
  chainloader +1
}
menuentry "Choose from the following options for debugging purposes:" {
  chainloader +1
}
menuentry "" {
  chainloader +1
}

menuentry "Single User Mode" {
  linux /casper/vmlinuz boot=casper noprompt single $loop_options --
  initrd /casper/initrd.lz
}

#
# Default option
#
set title="Automated Installation of  (Default)"

if [ "${recordfail}" != 1 ]; then
    if [ "${rectype}" == 'hdd' ]; then
        set title="Restore  to factory state"
        # set local
        if [ -n "${lang}" ]; then
            set options="$options locale=$lang"
        else
            set options="$options locale=en"
        fi
        # set installer run in recovery-hdd mode
        set options="ubuntu-recovery/recovery_type=hdd $options"
    fi
fi

menuentry "${title}" {
  linux /casper/vmlinuz $options $loop_options
  initrd /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  30bfe694-009d-4d10-a8e8-3129403cd200
else
  search --no-floppy --fs-uuid --set=root 30bfe694-009d-4d10-a8e8-3129403cd200
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_IN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-30bfe694-009d-4d10-a8e8-3129403cd200' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  30bfe694-009d-4d10-a8e8-3129403cd200
    else
      search --no-floppy --fs-uuid --set=root 30bfe694-009d-4d10-a8e8-3129403cd200
    fi
    linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=30bfe694-009d-4d10-a8e8-3129403cd200 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-30bfe694-009d-4d10-a8e8-3129403cd200' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-30bfe694-009d-4d10-a8e8-3129403cd200' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  30bfe694-009d-4d10-a8e8-3129403cd200
        else
          search --no-floppy --fs-uuid --set=root 30bfe694-009d-4d10-a8e8-3129403cd200
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=30bfe694-009d-4d10-a8e8-3129403cd200 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-30bfe694-009d-4d10-a8e8-3129403cd200' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  30bfe694-009d-4d10-a8e8-3129403cd200
        else
          search --no-floppy --fs-uuid --set=root 30bfe694-009d-4d10-a8e8-3129403cd200
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=30bfe694-009d-4d10-a8e8-3129403cd200 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=30bfe694-009d-4d10-a8e8-3129403cd200 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5b3d1599-6342-46ba-8633-a71cfd2ca4f1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  8b 4d 39 6e b6 98 a6 96  e3 58 63 63 9b 6d 98 99  |.M9n.....Xcc.m..|
00000010  58 9a 03 d8 63 73 9b f8  9c 9c c8 c9 f4 3c 3d 76  |X...cs.......<=v|
00000020  a0 19 e8 a2 33 1c 65 c9  5d 7c d2 8e 65 4c 9b dc  |....3.e.]|..eL..|
00000030  ab 91 f2 a8 db 0e 66 97  a9 77 71 58 87 1d cd 32  |......f..wqX...2|
00000040  73 ef e2 c3 4e 36 e3 5a  76 1e 67 90 e7 dd ce c6  |s...N6.Zv.g.....|
00000050  a7 ed 78 ce b4 df bd 03  fc 77 8e 90 17 cf c5 d6  |..x......w......|
00000060  9d 07 da b7 53 ef 24 13  1a 68 be 9c 98 c0 a3 cf  |....S.$..h......|
00000070  68 a4 09 72 62 12 cf 8f  e9 4d 1b 8e 2b c3 dc f8  |h..rb....M..+...|
00000080  c8 9e d3 9a 56 b9 87 e3  e4 98 b7 9e d4 54 73 f3  |....V........Ts.|
00000090  e2 47 cf 1c f7 53 e7 59  4d 35 e9 76 8c 1e e8 dd  |.G...S.YM5.v....|
000000a0  a6 13 17 7a 5c 5a d7 9d  c6 d8 23 d8 74 af ed ad  |...z\Z....#.t...|
000000b0  3d 0e b6 54 27 2f f7 8b  51 3d b2 b1 e9 3a 71 c1  |=..T'/..Q=...:q.|
000000c0  e7 0c 7b 99 5d 4d f1 89  a3 3e da d9 4b ed 62 9a  |..{.]M...>..K.b.|
000000d0  8f 5c 6d d9 4e 5e f4 17  e3 7d 6e 70 53 77 e2 b2  |.\m.N^...}npSw..|
000000e0  8f 58 f7 a3 bb 9b ee a7  97 0b 91 37 f8 e9 87 fd  |.X.........7....|
000000f0  19 7f 77 df 97 8f ee cf  a8 be eb 66 1f c5 f5 0f  |..w........f....|
00000100  f2 80 c3 4d 3f 8b fb 1f  e5 8e cf ff 08 c2 69 bf  |...M?.........i.|
00000110  7b 18 fe b4 23 32 02 27  8e 80 10 e1 b6 3c bd 58  |{...#2.'.....<.X|
00000120  8a 4f 13 8b 4b 20 c6 15  67 f5 c4 43 10 41 90 3b  |.O..K ..g..C.A.;|
00000130  4e d6 13 9f 41 92 1c d3  0e ea 94 f6 76 83 10 42  |N...A.......v..B|
00000140  96 63 4e da 13 8e 42 0b  69 cc 39 71 4f 39 0c 34  |.cN...B.i.9qO9.4|
00000150  e4 31 e8 e4 3d e8 38 f3  90 c4 a4 11 f8 a6 03 4e  |.1..=.8........N|
00000160  44 13 a3 44 e2 1d 9f 26  62 aa d3 3c f7 76 9e 46  |D..D...&b..<.v.F|
00000170  8a 51 5e 9a 3a 08 76 d7  a9 b7 63 8b d0 fa 36 d3  |.Q^.:.v...c...6.|
00000180  b8 45 b4 cb ce ee 17 1b  46 9d 7d 3b 4d 64 84 b1  |.E......F.};Md..|
00000190  ed f0 db 9b 46 92 7e 69  55 23 de 75 67 fb 8a 8d  |....F.~iU#.ug...|
000001a0  23 4e 9f 9e a6 3a 02 d8  77 fc ec cd 23 ae 9f 84  |#N...:..w...#...|
000001b0  27 af 8f 8a 89 24 ff fe  08 3c 71 85 84 6c 00 fe  |'....$...<q..l..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 70 f0 04 00 fe  |...........p....|
000001d0  ff ff 05 fe ff ff a8 72  f0 04 5a 05 2a 01 00 00  |.......r..Z.*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Unexpected end of input
cat: /tmp/BootInfo-1zmPeUla/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-1zmPeUla/Tmp_Log: No such file or directory


```


anyone please help

---

### Post by yancek on 2014-09-05
You are using the standard MBR boot with Grub installed to the master boot record of the drive.  You don't have any entry for windows in the boot menu (the grub.cfg file) so it can't be selected from the menu.  Have you tried running sudo update-grub?  Did you install windows 8 on your own or was it pre-installed?

The links you posted is in reference to GPT/EFI partitioning and there is no indication in your bootinfoscript that you are using that, at least you have no separate EFI partition.

---

### Post by priyesh2 on 2014-09-05
Thanks for reply 
i installed Win 8, it was preinstalled with ubuntu, 
sudo update-grub gives windows 2 loader found on /dev/sda2
What next????

---

### Post by yancek on 2014-09-05
> sudo update-grub gives windows 2 loader found on /dev/sda2

Then it should have created an entry in the grub.cfg file for windows on sda2.  You can either take a look at the /boot/grub/grub.cfg file to verify it or reboot and see if the windows option appears in the menu, highlight it to select it and hit the Enter key to see if it boots.

---

### Post by priyesh2 on 2014-09-05
> **yancek said:**
> Then it should have created an entry in the grub.cfg file for windows on sda2.  You can either take a look at the /boot/grub/grub.cfg file to verify it or reboot and see if the windows option appears in the menu, highlight it to select it and hit the Enter key to see if it boots.


Thanks!!!! [SIZE=5]Its Working[/SIZE]

---

