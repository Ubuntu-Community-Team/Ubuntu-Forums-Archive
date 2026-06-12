---
title: "Lenovo q190 with Window 10 suddenly grub disappeared"
date: 2016-01-25
forum: Installation &amp; Upgrades
---

### Post by bigfootnmd2 on 2016-01-25
Hi,  My Lenovo q190 originally had WIndow 8.1.  Some months ago I upgraded to Windows 10 and at that time had to boot off a boot repair usb flash to repair grub.  All was well until last week.  I booted into windows, downloaded updates.  Then a few days later GRUB did not appear at start up. On the q190 F12 brings up the boot menu so I chose Unbuntu and Ubuntu 13.04 LTS booted fine. So, I downloaded Boot repair, used unetbootin to put in a bootable USB and it didnt work.  I can only get to Ubuntu by hitting F12.  Also now my boot menu shows WIndows,Ubuntu,  Windows, Ubuntu.  Like there are too many entries in the MBR.  It is not possible with BIOS on the q190 to set boot order.  UEFI is enabled in the BIOS.
So, I am at a loss.  I will run boot repair again and post the link.  Any help will be appreciated.  Hitting F1 for setup or F12 at startup is a pain.

---

### Post by yancek on 2016-01-25
I don't think you will get much help without posting the boot repair output.  Too many unknowns.  13.04 hasn't been supported for two years so you might think about upgrading to a supported version.

---

### Post by Nuno_Abreu on 2016-01-26
Please turn off UEFI and try again - UEFI is such a pain!

---

### Post by bigfootnmd2 on 2016-01-29
Hi

I have 14.04 Trusty not 13.04.

---

### Post by bigfootnmd2 on 2016-01-29
Ok


The BIOS on the LENOVO IdeaCentre q190 does not allow you to set the boot order.  What do you mean turn off UEFI.  On most recent computers UEFI is mandatory.  PLEASE NOTE
that if I hit F12 at start up and the BOOT order menu comes up it has Windows, Ubuntu, WIndows Ubuntu.  That is 4 choices not two.  Again this PC was originally windows 8.1 I added Ubutnu and dual booted with no issues. Then I upgraded to Windows 10 and for about 6 months no problem at all.  When I choose the first instance of Ubuntu from the F12 boot menu GRUB then appears.   I have no clue what to do

Here is the BOOT repair summary  Any help will be appreciated

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /boot-sav/log/2016-01-19__15h58boot-repair40/sda2/bootx
                       64.efi 
                       /boot-sav/log/2016-01-19__15h58boot-repair40/sda3/bootx
                       64.efi 
                       /boot-sav/log/2016-01-19__15h58boot-repair40/sda9/bootx
                       64.efi

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/LrsBootMgr.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 1366592 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,050,047     2,048,000 Windows Recovery Environment (Windows)
/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     3,606,527     1,024,000 -
/dev/sda4       3,606,528     3,868,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5       3,868,672   954,712,063   950,843,392 Data partition (Windows/Linux)
/dev/sda6     954,712,064   955,428,863       716,800 Windows Recovery Environment (Windows)
/dev/sda7     955,428,864 1,894,146,047   938,717,184 Data partition (Windows/Linux)
/dev/sda8   1,894,146,048 1,902,323,711     8,177,664 Swap partition (Linux)
/dev/sda9   1,902,323,712 1,953,523,711    51,200,000 Windows Recovery Environment (Windows)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 32.2 GB, 32224837632 bytes
255 heads, 63 sectors/track, 3917 cylinders, total 62939136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    62,939,135    62,937,088   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2072147D721459BC                       ntfs       WINRE_DRV
/dev/sda2        4814-C9A2                              vfat       SYSTEM_DRV
/dev/sda3        6AF5-87F4                              vfat       LRS_ESP
/dev/sda5        8C78165C781644FC                       ntfs       Windows8_OS
/dev/sda6        F690D51290D4DA67                       ntfs       
/dev/sda7        0b5f5074-b1e7-43f4-bbf9-d31a348ee90d   ext4       
/dev/sda8        f8ca531b-6389-42af-a597-8d081adedb4b   swap       
/dev/sda9        FAACEE6EACEE253B                       ntfs       PBR_DRV
/dev/sdb1        5E22-413D                              vfat       ESD-USB
/dev/zram0       d76f7dac-f21c-4c60-8b44-9d7569388e15   swap       
/dev/zram1       026d4226-aa1a-46df-8651-848a872b7074   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jan 29 21:48 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8 -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 29 21:47 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 29 16:47 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 29 16:47 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jan 29 16:47 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jan 29 21:49 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan 29 21:47 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jan 29 16:47 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Jan 29 16:47 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Jan 29 21:47 ata-WDC_WD10JPVT-24A1YT0_WD-WXF1E32REXC8-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Jan 29 21:47 usb-JetFlash_Transcend_32GB_O39HUP2X-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jan 29 16:47 usb-JetFlash_Transcend_32GB_O39HUP2X-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jan 29 21:48 wwn-0x50014ee6ad7b449e -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 29 21:47 wwn-0x50014ee6ad7b449e-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 29 16:47 wwn-0x50014ee6ad7b449e-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 29 16:47 wwn-0x50014ee6ad7b449e-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jan 29 16:47 wwn-0x50014ee6ad7b449e-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jan 29 21:49 wwn-0x50014ee6ad7b449e-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan 29 21:47 wwn-0x50014ee6ad7b449e-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jan 29 16:47 wwn-0x50014ee6ad7b449e-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Jan 29 16:47 wwn-0x50014ee6ad7b449e-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Jan 29 21:47 wwn-0x50014ee6ad7b449e-part9 -> ../../sda9

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
insmod part_gpt
insmod ext2
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
else
  search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
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
  set timeout=10
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
if background_color 44,0,30,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
    else
      search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
    fi
    linux    /boot/vmlinuz-3.13.0-76-generic.efi.signed root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-76-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
    menuentry 'Ubuntu, with Linux 3.13.0-76-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-76-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-76-generic ...'
        linux    /boot/vmlinuz-3.13.0-76-generic.efi.signed root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-76-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-76-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-76-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-76-generic ...'
        linux    /boot/vmlinuz-3.13.0-76-generic.efi.signed root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-76-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-74-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-74-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-74-generic ...'
        linux    /boot/vmlinuz-3.13.0-74-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-74-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-74-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-74-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-74-generic ...'
        linux    /boot/vmlinuz-3.13.0-74-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-74-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-73-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-73-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-73-generic ...'
        linux    /boot/vmlinuz-3.13.0-73-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-73-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-73-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-73-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-73-generic ...'
        linux    /boot/vmlinuz-3.13.0-73-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-73-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-71-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-71-generic ...'
        linux    /boot/vmlinuz-3.13.0-71-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-71-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-71-generic ...'
        linux    /boot/vmlinuz-3.13.0-71-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-71-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-70-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-70-generic ...'
        linux    /boot/vmlinuz-3.13.0-70-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-70-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-70-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-70-generic ...'
        linux    /boot/vmlinuz-3.13.0-70-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-70-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-68-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-68-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-68-generic ...'
        linux    /boot/vmlinuz-3.13.0-68-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-68-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-68-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-68-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-68-generic ...'
        linux    /boot/vmlinuz-3.13.0-68-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-68-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-67-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-67-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-67-generic ...'
        linux    /boot/vmlinuz-3.13.0-67-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-67-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-67-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-67-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-67-generic ...'
        linux    /boot/vmlinuz-3.13.0-67-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-67-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-66-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-66-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-66-generic ...'
        linux    /boot/vmlinuz-3.13.0-66-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-66-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-66-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-66-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-66-generic ...'
        linux    /boot/vmlinuz-3.13.0-66-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-66-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-65-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-65-generic ...'
        linux    /boot/vmlinuz-3.13.0-65-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-65-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-65-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-65-generic ...'
        linux    /boot/vmlinuz-3.13.0-65-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-65-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-63-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-63-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-63-generic ...'
        linux    /boot/vmlinuz-3.13.0-63-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-63-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-63-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-63-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-63-generic ...'
        linux    /boot/vmlinuz-3.13.0-63-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-63-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-62-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-62-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-62-generic ...'
        linux    /boot/vmlinuz-3.13.0-62-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-62-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-62-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-62-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-62-generic ...'
        linux    /boot/vmlinuz-3.13.0-62-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-62-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-61-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-61-generic ...'
        linux    /boot/vmlinuz-3.13.0-61-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-61-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-61-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-61-generic ...'
        linux    /boot/vmlinuz-3.13.0-61-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-61-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-59-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-59-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-59-generic ...'
        linux    /boot/vmlinuz-3.13.0-59-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-59-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-59-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-59-generic ...'
        linux    /boot/vmlinuz-3.13.0-59-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-58-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-58-generic ...'
        linux    /boot/vmlinuz-3.13.0-58-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-58-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-58-generic ...'
        linux    /boot/vmlinuz-3.13.0-58-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-57-generic ...'
        linux    /boot/vmlinuz-3.13.0-57-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-57-generic ...'
        linux    /boot/vmlinuz-3.13.0-57-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-55-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-55-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-55-generic ...'
        linux    /boot/vmlinuz-3.13.0-55-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-55-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-55-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-55-generic ...'
        linux    /boot/vmlinuz-3.13.0-55-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-54-generic ...'
        linux    /boot/vmlinuz-3.13.0-54-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-54-generic ...'
        linux    /boot/vmlinuz-3.13.0-54-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /boot/vmlinuz-3.13.0-53-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /boot/vmlinuz-3.13.0-53-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-51-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-51-generic ...'
        linux    /boot/vmlinuz-3.13.0-51-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-51-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-51-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-51-generic ...'
        linux    /boot/vmlinuz-3.13.0-51-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-51-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-49-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-49-generic ...'
        linux    /boot/vmlinuz-3.13.0-49-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-49-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-49-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-49-generic ...'
        linux    /boot/vmlinuz-3.13.0-49-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-49-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-46-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-46-generic ...'
        linux    /boot/vmlinuz-3.13.0-46-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-46-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-46-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-46-generic ...'
        linux    /boot/vmlinuz-3.13.0-46-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-46-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /boot/vmlinuz-3.13.0-45-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /boot/vmlinuz-3.13.0-45-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-35-generic ...'
        linux    /boot/vmlinuz-3.13.0-35-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-35-generic ...'
        linux    /boot/vmlinuz-3.13.0-35-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-34-generic ...'
        linux    /boot/vmlinuz-3.13.0-34-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-34-generic ...'
        linux    /boot/vmlinuz-3.13.0-34-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-33-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-33-generic ...'
        linux    /boot/vmlinuz-3.13.0-33-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-33-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-33-generic ...'
        linux    /boot/vmlinuz-3.13.0-33-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /boot/vmlinuz-3.13.0-30-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /boot/vmlinuz-3.13.0-30-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /boot/vmlinuz-3.13.0-29-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /boot/vmlinuz-3.13.0-29-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-27-generic ...'
        linux    /boot/vmlinuz-3.13.0-27-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-27-generic ...'
        linux    /boot/vmlinuz-3.13.0-27-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-20-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.11.0-20-generic ...'
        linux    /boot/vmlinuz-3.11.0-20-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-20-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.11.0-20-generic ...'
        linux    /boot/vmlinuz-3.11.0-20-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 3.10.0-031000-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.10.0-031000-generic-advanced-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.10.0-031000-generic ...'
        linux    /boot/vmlinuz-3.10.0-031000-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.10.0-031000-generic
    }
    menuentry 'Ubuntu, with Linux 3.10.0-031000-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.10.0-031000-generic-recovery-0b5f5074-b1e7-43f4-bbf9-d31a348ee90d' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        else
          search --no-floppy --fs-uuid --set=root 0b5f5074-b1e7-43f4-bbf9-d31a348ee90d
        fi
        echo    'Loading Linux 3.10.0-031000-generic ...'
        linux    /boot/vmlinuz-3.10.0-031000-generic root=UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.10.0-031000-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 4814-C9A2
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 4814-C9A2
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root 4814-C9A2
chainloader (${root})/EFI/ubuntu/MokManager.efi
}

menuentry "Windows UEFI recovery bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 6AF5-87F4
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows UEFI recovery sda3" {
search --fs-uuid --no-floppy --set=root 6AF5-87F4
chainloader (${root})/EFI/Microsoft/Boot/bootx64.efi
}

menuentry "Windows UEFI recovery LrsBootMgr.efi" {
search --fs-uuid --no-floppy --set=root 6AF5-87F4
chainloader (${root})/EFI/Microsoft/Boot/LrsBootMgr.efi
}

menuentry "Windows Boot UEFI recovery bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root 6AF5-87F4
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "Windows Boot UEFI recovery bootx64.efi" {
search --fs-uuid --no-floppy --set=root FAACEE6EACEE253B
chainloader (${root})/EFI/Boot/bootx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-4814-C9A2' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  4814-C9A2
    else
      search --no-floppy --fs-uuid --set=root 4814-C9A2
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=0b5f5074-b1e7-43f4-bbf9-d31a348ee90d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=4814-C9A2  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda8 during installation
UUID=f8ca531b-6389-42af-a597-8d081adedb4b none            swap    sw              0       0
UUID=4814-C9A2    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

====================== sda7/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

============== sda7: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

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

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^64bit session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^64bit session (failsafe)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --

label ubnentry3
menu label Boot-Repair-Disk session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
e7afbfbf4fa38a449a5b6213eb736c22

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/2045/mounts) leaked on lvs invocation. Parent PID 28729: bash
File descriptor 63 (pipe:[29741]) leaked on lvs invocation. Parent PID 28729: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-01-29__16h47 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2045/mounts) leaked on lvs invocation. Parent PID 4621: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda1 : Error code 14
mount -r /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda5 /mnt/boot-sav/sda5
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda5 : Error code 14
mount -r /dev/sda5 /mnt/boot-sav/sda5
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda6 /mnt/boot-sav/sda6
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda6 : Error code 14
mount -r /dev/sda6 /mnt/boot-sav/sda6
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda9': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda9 /mnt/boot-sav/sda9
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda9': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda9 : Error code 14
mount -r /dev/sda9 /mnt/boot-sav/sda9

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sda7:Ubuntu 14.04.3 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="WINRE_DRV" UUID="2072147D721459BC" TYPE="ntfs"
/dev/sda2: LABEL="SYSTEM_DRV" UUID="4814-C9A2" TYPE="vfat"
/dev/sda3: LABEL="LRS_ESP" UUID="6AF5-87F4" TYPE="vfat"
/dev/sda5: LABEL="Windows8_OS" UUID="8C78165C781644FC" TYPE="ntfs"
/dev/sda6: UUID="F690D51290D4DA67" TYPE="ntfs"
/dev/sda7: UUID="0b5f5074-b1e7-43f4-bbf9-d31a348ee90d" TYPE="ext4"
/dev/sda8: UUID="f8ca531b-6389-42af-a597-8d081adedb4b" TYPE="swap"
/dev/sda9: LABEL="PBR_DRV" UUID="FAACEE6EACEE253B" TYPE="ntfs"
/dev/sdb1: LABEL="ESD-USB" UUID="5E22-413D" TYPE="vfat"
/dev/zram0: UUID="d76f7dac-f21c-4c60-8b44-9d7569388e15" TYPE="swap"
/dev/zram1: UUID="026d4226-aa1a-46df-8651-848a872b7074" TYPE="swap"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda5.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

=================== No kernel in /mnt/boot-sav/sda2/boot:
boot.sdi


Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda3/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda3/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda3/EFI/Microsoft/Boot/LrsBootMgr.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda3/EFI/Boot/bootx64.efi

=================== sda7/etc/grub.d/ :
drwxr-xr-x  2 root root         4096 Jan 25 20:51 grub.d
drwxr-xr-x  2 root root         4096 Apr 16  2014 grub.d.bak
total 76
-rwxr-xr-x 1 root root  9791 Dec 17 15:00 00_header
-rwxr-xr-x 1 root root  6058 May 13  2015 05_debian_theme
-rwxr-xr-x 1 root root 11608 Dec 17 15:00 10_linux
-rwxr-xr-x 1 root root 10412 Dec 17 15:00 20_linux_xen
-rwxr-xr-x 1 root root  1225 Jan 25 20:51 25_custom
-rwxr-xr-x 1 root root 11692 Dec 17 15:00 30_os-prober
-rwxr-xr-x 1 root root  1416 Dec 17 15:00 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 17 15:00 40_custom
-rwxr-xr-x 1 root root   216 Dec 17 15:00 41_custom
-rw-r--r-- 1 root root   483 Dec 17 15:00 README




=================== sda7/etc/default/grub :

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



/boot/efi detected in the fstab of sda7: UUID=4814-C9A2     (sda2)
Presence of EFI/Boot file detected: /mnt/boot-sav/sda9/EFI/Boot/bootx64.efi

efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 2001,0001,0002,0003,0004,2002,2003
Boot0000* UEFI Generic Boot    ACPI(a0341d0,0)PCI(14,0)USB(0,0)HD(1,800,3c05800,00000000)File(EFIBOOTBOOTX64.EFI)RC
Boot0001* Windows Boot Manager    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0002* Ubuntu    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIubuntugrubx64.efi)RC
Boot0003* Windows Boot Manager    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0004* Ubuntu    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIubuntugrubx64.efi)RC
Boot0005* UEFI Generic Boot    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIBOOTBOOTX64.EFI)RC
Boot0006* Windows Boot Manager    HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIubuntushimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-maybe-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
sda7    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.
sda9    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda9.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD10JPVT-24A (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  1050MB  1049MB  ntfs                                          hidden, diag
2      1050MB  1322MB  273MB   fat32           EFI system partition          boot
3      1322MB  1847MB  524MB   fat32                                         hidden
4      1847MB  1981MB  134MB                   Microsoft reserved partition  msftres
5      1981MB  489GB   487GB   ntfs            Basic data partition          msftdata
6      489GB   489GB   367MB   ntfs                                          hidden, diag
7      489GB   970GB   481GB   ext4                                          msftdata
8      970GB   974GB   4187MB  linux-swap(v1)
9      974GB   1000GB  26.2GB  ntfs                                          hidden, diag


Model: JetFlash Transcend 32GB (scsi)
Disk /dev/sdb: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  32.2GB  32.2GB  primary  fat32        boot, lba



                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA WDC WD10JPVT-24A;
1:1049kB:1050MB:1049MB:ntfs::hidden, diag;
2:1050MB:1322MB:273MB:fat32:EFI system partition:boot;
3:1322MB:1847MB:524MB:fat32::hidden;
4:1847MB:1981MB:134MB::Microsoft reserved partition:msftres;
5:1981MB:489GB:487GB:ntfs:Basic data partition:msftdata;
6:489GB:489GB:367MB:ntfs::hidden, diag;
7:489GB:970GB:481GB:ext4::msftdata;
8:970GB:974GB:4187MB:linux-swap(v1)::;
9:974GB:1000GB:26.2GB:ntfs::hidden, diag;

BYT;
/dev/sdb:32.2GB:scsi:512:512:msdos:JetFlash Transcend 32GB;
1:1049kB:32.2GB:32.2GB:fat32::boot, lba;


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type vfat (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)
/dev/sda9 on /mnt/boot-sav/sda9 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 3f 1f 00 00 00 00 00  |.........?......|
00000030  55 4d 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |UM..............|
00000040  f6 00 00 00 01 00 00 00  bc 59 14 72 7d 14 72 20  |.........Y.r}.r |
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
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 1f 00  |........?....H..|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 a2 c9 14 48 4e  4f 20 4e 41 4d 45 20 20  |..)...HNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200
ls /mnt/boot-sav/sda3/1:
ls /mnt/boot-sav/sda3: Boot
bootmgr
bootmgr.efi
EFI
onekey  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== hexdump -n512 -C /dev/sda3
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 3e 18  |.X.MSDOS5.0...>.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 27 00  |........?....h'.|
00000020  00 a0 0f 00 e1 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 f4 87 f5 6a 4e  4f 20 4e 41 4d 45 20 20  |..)...jNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 3b 00  |........?.....;.|
00000020  00 00 00 00 80 00 80 00  ff b7 ac 38 00 00 00 00  |...........8....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  fc 44 16 78 5c 16 78 8c  |.........D.x.x.|
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
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 c0 e7 38  |........?......8|
00000020  00 00 00 00 80 00 80 00  ff ef 0a 00 00 00 00 00  |................|
00000030  aa 74 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.t..............|
00000040  f6 00 00 00 01 00 00 00  67 da d4 90 12 d5 90 f6  |........g.......|
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
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200
ls /mnt/boot-sav/sda9/1:
ls /mnt/boot-sav/sda9: EFI
H1100356.CRI
H1100356.IMZ
H1100358.CRI
H1100358.IMZ
H1100382.CRI
H1100382.IMZ
H1100391.CRI
H1100391.IMZ
H1100409.CRI
H1100409.IMZ
H1100420.CRI
H1100420.IMZ
H1100421.CRI
H1100421.IMZ
H1100468.CRI
H1100468.IMZ
H1200456.CRI
H1200456.IMZ
H1200480.CRI
H1200480.IMZ
H1200486.CRI
H1200486.IMZ
H1200507.CRI
H1200507.IMZ
H1200509.CRI
H1200509.IMZ
H9800012.CRI
H9800012.IMZ
LRSBootTmpT12.log
MFGPROC.INI
OKRBackup
onekey
pagefile.sys
Recovery
System Volume Information  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== hexdump -n512 -C /dev/sda9
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 63 71  |........?....(cq|
00000020  00 00 00 00 80 00 80 00  ff 3f 0d 03 00 00 00 00  |.........?......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  3b 25 ee ac 6e ee ac fa  |........;%..n...|
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
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.9G  6.2M  1.9G   1% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      385M  1.1M  384M   1% /run
/dev/sdb1      vfat        30G  653M   30G   3% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.9G  8.0K  1.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.9G     0  1.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk   1000M  467M  534M  47% /mnt/boot-sav/sda1
/dev/sda2      vfat       256M   44M  213M  18% /mnt/boot-sav/sda2
/dev/sda3      vfat       496M  265M  232M  54% /mnt/boot-sav/sda3
/dev/sda5      fuseblk    454G   49G  406G  11% /mnt/boot-sav/sda5
/dev/sda6      fuseblk    350M   26M  325M   8% /mnt/boot-sav/sda6
/dev/sda7      ext4       441G   92G  327G  22% /mnt/boot-sav/sda7
/dev/sda9      fuseblk     25G  9.6G   15G  40% /mnt/boot-sav/sda9

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb9033ebc

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 32.2 GB, 32224837632 bytes
255 heads, 63 sectors/track, 3917 cylinders, total 62939136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    62939135    31468544    c  W95 FAT32 (LBA)




=================== Default settings of Boot Repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda7, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda2/efi/.../grub*.efi file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi


=================== User settings
The settings chosen by the user will reinstall the grub-efi-amd64-signed of sda7, using the following options:        sda2/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    use-standard-efi-file


Mount sda2 on /mnt/boot-sav/sda7/boot/efi
ls /mnt/boot-sav/sda7/boot/efi/1:
ls /mnt/boot-sav/sda7/boot/efi: BOOT
boot-sav
BOOTSECT.BAK
EFI
FSCK0000.REC  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
Subsystem: Lenovo Device [17aa:366b]
Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

chroot /mnt/boot-sav/sda7 efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 2001,0001,0002,0003,0004,2002,2003
Boot0000* UEFI Generic Boot    ACPI(a0341d0,0)PCI(14,0)USB(0,0)HD(1,800,3c05800,00000000)File(EFIBOOTBOOTX64.EFI)RC
Boot0001* Windows Boot Manager    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0002* Ubuntu    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIubuntugrubx64.efi)RC
Boot0003* Windows Boot Manager    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0004* Ubuntu    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIubuntugrubx64.efi)RC
Boot0005* UEFI Generic Boot    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIBOOTBOOTX64.EFI)RC
Boot0006* Windows Boot Manager    HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIubuntushimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................

chroot /mnt/boot-sav/sda7 uname -r
Kernel: 3.13.0-32-generic

Reinstall the grub-efi-amd64-signed of sda7
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0
mv 25_custom
ls /mnt/boot-sav/sda7/boot/efi/1:
ls /mnt/boot-sav/sda7/boot/efi: BOOT
boot-sav
BOOTSECT.BAK
EFI
FSCK0000.REC  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
ls /mnt/boot-sav/sda3/1:
ls /mnt/boot-sav/sda3: Boot
bootmgr
bootmgr.efi
EFI
onekey  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
df /dev/sda2
Save and rename /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bootx64.efi (/mnt/boot-sav/sda7/boot/efi/EFI/Boot/bkpbootx64.efi)
cp /mnt/boot-sav/sda7/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bootx64.efi
ls /mnt/boot-sav/sda7/boot/efi/1:
ls /mnt/boot-sav/sda7/boot/efi: BOOT
boot-sav
BOOTSECT.BAK
EFI
FSCK0000.REC  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Add /mnt/boot-sav/sda7/boot/efi efi entries in /mnt/boot-sav/sda7/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda7/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bkpbootx64.efi
sda2/bkpbootx64.efi already added
Adding custom /mnt/boot-sav/sda7/boot/efi/EFI/ubuntu/MokManager.efi
sda2/bootmgfw.efi already added
df /dev/sda3
Save and rename /mnt/boot-sav/sda3/EFI/Boot/bootx64.efi (/mnt/boot-sav/sda3/EFI/Boot/bkpbootx64.efi)
cp /mnt/boot-sav/sda7/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda3/EFI/Boot/bootx64.efi
ls /mnt/boot-sav/sda3/1:
ls /mnt/boot-sav/sda3: Boot
bootmgr
bootmgr.efi
EFI
onekey  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Add /mnt/boot-sav/sda3 efi entries in /mnt/boot-sav/sda7/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda3/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /mnt/boot-sav/sda3/EFI/Microsoft/Boot/bootx64.efi
Adding custom /mnt/boot-sav/sda3/EFI/Microsoft/Boot/LrsBootMgr.efi
Adding custom /mnt/boot-sav/sda3/EFI/Boot/bkpbootx64.efi
sda3/bkpbootx64.efi already added
sda3/bootmgfw.efi already added
sda3/bootx64.efi already added
sda3/LrsBootMgr.efi already added
df /dev/sda9
Save and rename /mnt/boot-sav/sda9/EFI/Boot/bootx64.efi (/mnt/boot-sav/sda9/EFI/Boot/bkpbootx64.efi)
mv: cannot move â&#8364;&#732;/mnt/boot-sav/sda9/EFI/Boot/bootx64.efiâ&#8364;&#8482; to â&#8364;&#732;/mnt/boot-sav/sda9/EFI/Boot/bkpbootx64.efiâ&#8364;&#8482;: Read-only file system
Error: /mnt/boot-sav/sda9/EFI/Boot/bootx64.efi still pr. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
ls /mnt/boot-sav/sda9/1:
ls /mnt/boot-sav/sda9: EFI
H1100356.CRI
H1100356.IMZ
H1100358.CRI
H1100358.IMZ
H1100382.CRI
H1100382.IMZ
H1100391.CRI
H1100391.IMZ
H1100409.CRI
H1100409.IMZ
H1100420.CRI
H1100420.IMZ
H1100421.CRI
H1100421.IMZ
H1100468.CRI
H1100468.IMZ
H1200456.CRI
H1200456.IMZ
H1200480.CRI
H1200480.IMZ
H1200486.CRI
H1200486.IMZ
H1200507.CRI
H1200507.IMZ
H1200509.CRI
H1200509.IMZ
H9800012.CRI
H9800012.IMZ
LRSBootTmpT12.log
MFGPROC.INI
OKRBackup
onekey
pagefile.sys
Recovery
System Volume Information  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Add /mnt/boot-sav/sda9 efi entries in /mnt/boot-sav/sda7/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda9/EFI/Boot/bootx64.efi
sda9/bootx64.efi already added
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0

efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0002,2001,0001,0003,2002,2003
Boot0000* UEFI Generic Boot    ACPI(a0341d0,0)PCI(14,0)USB(0,0)HD(1,800,3c05800,00000000)File(EFIBOOTBOOTX64.EFI)RC
Boot0001* Windows Boot Manager    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0002* ubuntu    HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIubuntushimx64.efi)
Boot0003* Windows Boot Manager    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0005* UEFI Generic Boot    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIBOOTBOOTX64.EFI)RC
Boot0006* Windows Boot Manager    HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIubuntushimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................

chroot /mnt/boot-sav/sda7 efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0002,2001,0001,0003,2002,2003
Boot0000* UEFI Generic Boot    ACPI(a0341d0,0)PCI(14,0)USB(0,0)HD(1,800,3c05800,00000000)File(EFIBOOTBOOTX64.EFI)RC
Boot0001* Windows Boot Manager    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0002* ubuntu    HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIubuntushimx64.efi)
Boot0003* Windows Boot Manager    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0005* UEFI Generic Boot    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(3,276800,fa000,bbd0f084-281a-4c1d-a8c3-33a29aa743e3)File(EFIBOOTBOOTX64.EFI)RC
Boot0006* Windows Boot Manager    HD(2,1f4800,82000,7a949a0a-6a5f-4e2e-9ddd-ca36286f67c9)File(EFIubuntushimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................

chroot /mnt/boot-sav/sda7 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-73-generic
Found initrd image: /boot/initrd.img-3.13.0-73-generic
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-70-generic
Found initrd image: /boot/initrd.img-3.13.0-70-generic
Found linux image: /boot/vmlinuz-3.13.0-68-generic
Found initrd image: /boot/initrd.img-3.13.0-68-generic
Found linux image: /boot/vmlinuz-3.13.0-67-generic
Found initrd image: /boot/initrd.img-3.13.0-67-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.10.0-031000-generic
Found initrd image: /boot/initrd.img-3.10.0-031000-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda5 /mnt/boot-sav/sda5
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda5 : Error code 14
mount -r /dev/sda5 /mnt/boot-sav/sda5
Unhide GRUB boot menu in sda7/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.


If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

---

