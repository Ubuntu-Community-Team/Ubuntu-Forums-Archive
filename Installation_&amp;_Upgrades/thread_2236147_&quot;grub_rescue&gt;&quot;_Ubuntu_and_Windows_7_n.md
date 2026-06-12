---
title: "&quot;grub rescue&gt;&quot; Ubuntu and Windows 7 not booting"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by Bikerman114 on 2014-07-24
Hi, I just got a used Dell Latitude E6410. It came with Windows on it, of course, I want to dual boot and yesterday I installed Ubuntu 12.04 from a live CD image I had from a couple years ago. After installing it wanted to reboot and upon turning back on all I got was text at the top of the screeen:

File not found:
grub rescue>

I used gparted to delete the entire extended partition that held Ubuntu but Windows still didn't boot. I was able to use the CD to make a live USB of version of 14.04. the installer couldn't see Windows being on my harddrive so I manually set up the partition and installed it. I'm still having the same problem and through Google found the Boot Info Script, here is the RESULTS.txt printout

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 268133592 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for .
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       257,039       256,977   7 NTFS / exFAT / HPFS
/dev/sda2             257,040   125,222,911   124,965,872   7 NTFS / exFAT / HPFS
/dev/sda3         125,224,958   488,396,799   363,171,842   5 Extended
/dev/sda5         125,224,960   477,910,506   352,685,547  83 Linux
/dev/sda6         477,913,088   488,396,799    10,483,712  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  32    15,633,407    15,633,376   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7AC698F8C698B5BB                       ntfs       System Reserved
/dev/sda2        B6E89B9AE89B5787                       ntfs       
/dev/sda5        94e0abc4-84db-45d4-860c-205acc10a874   ext4       
/dev/sdb1                                               iso9660    Ubuntu 14.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   iso9660    (ro,noatime)
/dev/sr0         /media/ubuntu/Ubuntu 12.04 LTS amd64 iso9660    (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  94e0abc4-84db-45d4-860c-205acc10a874
else
  search --no-floppy --fs-uuid --set=root 94e0abc4-84db-45d4-860c-205acc10a874
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-94e0abc4-84db-45d4-860c-205acc10a874' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  94e0abc4-84db-45d4-860c-205acc10a874
    else
      search --no-floppy --fs-uuid --set=root 94e0abc4-84db-45d4-860c-205acc10a874
    fi
    linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=94e0abc4-84db-45d4-860c-205acc10a874 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-94e0abc4-84db-45d4-860c-205acc10a874' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-94e0abc4-84db-45d4-860c-205acc10a874' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  94e0abc4-84db-45d4-860c-205acc10a874
        else
          search --no-floppy --fs-uuid --set=root 94e0abc4-84db-45d4-860c-205acc10a874
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=94e0abc4-84db-45d4-860c-205acc10a874 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-94e0abc4-84db-45d4-860c-205acc10a874' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  94e0abc4-84db-45d4-860c-205acc10a874
        else
          search --no-floppy --fs-uuid --set=root 94e0abc4-84db-45d4-860c-205acc10a874
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=94e0abc4-84db-45d4-860c-205acc10a874 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-94e0abc4-84db-45d4-860c-205acc10a874' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  94e0abc4-84db-45d4-860c-205acc10a874
        else
          search --no-floppy --fs-uuid --set=root 94e0abc4-84db-45d4-860c-205acc10a874
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=94e0abc4-84db-45d4-860c-205acc10a874 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-94e0abc4-84db-45d4-860c-205acc10a874' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  94e0abc4-84db-45d4-860c-205acc10a874
        else
          search --no-floppy --fs-uuid --set=root 94e0abc4-84db-45d4-860c-205acc10a874
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=94e0abc4-84db-45d4-860c-205acc10a874 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
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
UUID=94e0abc4-84db-45d4-860c-205acc10a874 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=b87c01b0-8cb7-4020-b9b0-ca9bd316a6a9 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  b4 35 00 00 00 00 00 00  d6 46 4a 09 00 00 80 00  |.5.......FJ.....|
000001c0  01 00 00 3f e0 c3 00 00  00 00 00 20 1e 00 00 fe  |...?....... ....|
000001d0  ff ff ef fe ff ff 0c d2  1d 00 40 12 00 00 00 00  |..........@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
cat: /tmp/BootInfo-hsSsHrYo/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-hsSsHrYo/Tmp_Log: No such file or directory
  No volume groups found


```

Can anyone please tell me what the next step is atleast. Thanks.

---

### Post by yancek on 2014-07-24
Does still having the same problem mean you are just getting 'grub rescue' or that you cannot boot windows?
If you can boot Ubuntu but not windows, boot Ubuntu and open a terminal and run:  sudo update-grub
Watch the output to see if windows is detected.  If it is reboot and select it from the menu.  If you are just getting 'grub rescue' post back.  I don't see any obvious problems with the bootinfoscript output.

---

### Post by Bikerman114 on 2014-07-24
When I try to boot it shows the start up screen where I can F12 to BIOS and then goes black for a few seconds  before hitting the grub rescue screen. I'm using my USB now to boot and try to figure out what is wrong.

---

### Post by oldfred on 2014-07-25
You also show an install of grub to the Linux partition. That almost never is correct. If that is the newer grub from your 14.04 install and the grub in the MBR is from the old install that would be the reason for the error.

You can manually boot, use Boot-Repair to reinstall the correct version of grub to MBR, or use Supergrub to boot and from inside your install reinstall grub to MBR.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
First part of Boot-Repair's BootInfo report is just the bootinfoscript.

---

### Post by Bikerman114 on 2014-07-25
BIOS vs UEFI

This is going to be a total newby question but: When I booted into my USB 14.04 it only worked in UEFI. So does that mean that my Ubuntu is UEFI? And would it necessarily mean that my Windoze 7 is also UEFI? Would there be an easy way to check before I do the wrong thing? Also might it work to just delete my Grub2 and reinstall it or might that break things worse then they already are.

---

### Post by oldfred on 2014-07-25
If you booted Ubuntu in UEFI mode then your hardware is newer & UEFI capable.
But most systems have this which is another chip:
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Your BootInfoScript showed BIOS installs. 
With BIOS Windows 7 or later has a 100MB hidden NTFS partition and the main install. Drive must be MBR(msdos) formatted.
With UEFI Windows must use gpt partitioned drive and requires several extra partitions including efi & system reserved.
Ubuntu only installs in BIOS mode to MBR drives. But if you force a UEFI install it may erase drive. 

And how you boot installer is how it installs for both Windows & Ubuntu as UEFI & BIOS are not really compatible.

From flash drive you should see both UEFI and non UEFI or BIOS boot. Most clearly label UEFI entry, but BIOS may just be name of flash drive or something not UEFI.

Some UEFI screens.

---

### Post by Bikerman114 on 2014-07-25
I think my computer has BIOS by default, here is an image of the screen when I F12 at start up:

When the USB is plugged in it gives me the option to choose it under the top BIOS or the UEFI. However, it only boots under the UEFI, when I choose it under the top menu it goes the a black screen with a blinking curser at the top and doesn't een get as far as the grub rescue. 

I also attached a picture of gparted's view of my hardrive. The sda2 is my main Windoze partition and idk why it has it listed as ubuntu. Also the sda6 was formated as a Linux-swap. I put those partitions in manually since the ubuntu installer didn't see the Windoze as being there. 

Is is a good idea for me to change my USB to the boot-rescue.iso and see if that helps or might that break it more? The main thing is I'de be okay just wiping windoze off if I could get the key to if first. I don't have recovery CD but figure that would be easy to get. Is there a program I could use from live sesion to obtain that and how would I start over without carrying this problem through another install?

---

### Post by oldfred on 2014-07-25
In BIOS mode you may need boot options. 
Press any key at tiny icons keyboard & person at bottom of accessibility screen and then f6. Often nomodeset, but may be others depending on your system.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Bikerman114 on 2014-07-26
So I decided to change back to 12.04 for keeping normal BIOS with a live image that works. It installed properly and is now duel booting like it should have from the start. I guess third times the charm. Thanks for all the help this has been a good learning experience for me ;)

---

