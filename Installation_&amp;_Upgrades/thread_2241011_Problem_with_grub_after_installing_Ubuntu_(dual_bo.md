---
title: "Problem with grub after installing Ubuntu (dual boot)"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by dennis31 on 2014-08-23
Hello everyone,

Today I decided to upgrade my very outdated version of Fedora to the  newest version of Ubuntu. (I'm new to Ubuntu.) I have (or had until today) a dual-boot system  with Windows 8.1 and Fedora 17. They are located on the same physical  harddrive, but in different partitions. I have two for my Windows  (normal+backup/restore) and two for Fedora (/ and /boot). My /home is  located on another harddrive.

When installing Ubuntu I chose the "something else" option and let the  installer format my former Fedora partitions and install Ubuntu where my  Fedora used to be. So far, so good. Or so I thought. After restarting I  got an error in the grub menu, saying it cannot find the file  "/grub2/i386-pc/normal.mod" and I got into the grub rescue mode. I don't  know enough about Linux to be able to work with that. Now neither  Windows nor Ubuntu will boot. In retrospect I didn't really think about  where the bootloader should be and I guess I installed in the wrong  place. 

After this I kind of panicked, thinking I made a very big mistake. I put  in a gparted Live CD to check my partitions and maybe salvage what I  could. From there everything seemed relatively fine. I thought of simply  deleting all my former Fedora/Ubuntu partitions and starting over, but I  got an error while trying to do so. If I remember correctly it said  something about a logical volume. Now I'm glad it didn't work because  maybe I would have made things worse still.

I don't know if this is relevant, but I found it odd that both Ubuntu  (when installing) and gparted did nog recognize that any operating  systems were installed. Usually you can see if there are any (other)  OSes installed when setting up a multi-boot system.

So now I'm here on my laptop (with Windows), trying to figure out how I  can get my computer to boot again. I did a quick search and saw there is  a utility available ("Boot-Repair") for solving booting problems. Do I need this or is  there any other way I can fix this? Any advice would be greatly  appreciated. Thank in advance.

Dennis

ETA: I found this: [http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found). It seems like I'm having the same problem except I already have grub2. 

Extra info: I installed Ubuntu via USB and I forgot about my swap partition which is also located on the same harddrive as / and /boot. I'm quite sure my Ubuntu /boot is on the same partition as my Fedora /boot was.

---

### Post by yancek on 2014-08-23
The normal.mod file is one of about a hundred different file in either the grub or i386-pc directory and this error is fairly common.  The correct place to install Grub would have been /dev/sda if you only have one hard drive.  That is also the default so if you did not make a change, it should have gone there.  You could try, assuming only one drive again, installing Grub again from the installation medium.  Boot it and open a terminal and run:  sudo grub-install /dev/sda.  If it is a different drive, you will need to change it.  If that fails, you may need to google 'bootinfoscript' and go to its site and download and run it and post the output, a results.txt file.  It needs to be run from Linux.

---

### Post by dennis31 on 2014-08-24
Thank you for your reply. I think I put Grub in the same partition as /boot, which is /dev/mapper/pdc_hicaefeecp6. (Not sure about this, but quite sure I did NOT put it in /dev/sda). Since you stress the part of having only one hard drive, I think I should clarify that I actually have four; two for my OSes and two for my data. My OS HDDs are configured as RAID 0, my data HDDs as RAID 1. Everything except my /home directory is (was) located on the OS HDDs.

Does your suggestion still apply when it's technically not a single hard drive? If so I will try reinstalling Grub where it should have gone. I have googled and bookmarked the home of Boot Info Script just in case. (I don't really understand how one could download and open a file when booting from a live CD, but I guess that's a problem for later.)

I still do not understand the names Linux assigns to my drives, which is part of my problem. (I'm used to seeing C: and D: etc.) I think I have about 6 or 8 different partitions on the HDD(s) where my OSes are located (3 for Windows, rest for Linux). If necessary I can post a list of these, but I'll have to check to see how many I have exactly.

So, considering the multiple hard drives and partitions, should I still try to reinstall Grub like you told me? (I want to try anyway, just want to make sure I'm not going to make thing worse.) Thank you for your advice.

Dennis

ETA: Okay, so I just booted from Ubuntu Live USB and found out that from there I have access to my Windows partitions, which is awesome. I downloaded and ran Boot Info Script and here are the results. In the instructions it said to click on the code tags (#) before posting them but I could not find those so I justed pasted it normally.

Edit: quote tags

                 ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 99 for .
 => Windows is installed in the MBR of /dev/sde.
 => Windows is installed in the MBR of /dev/mapper/pdc_ieijfhgji.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/pdc_hicaefeec and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 99 for .

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi

pdc_ieijfhgji1: ________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

pdc_hicaefeec1: ________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

pdc_hicaefeec2: ________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

pdc_hicaefeec3: ________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

pdc_hicaefeec4: ________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

pdc_hicaefeec5: ________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

pdc_hicaefeec6: ________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of 
                       pdc_hicaefeec6 and looks at sector 1259311170 of the 
                       same hard drive for core.img. core.img is at this 
                       location and looks in partition 112 for .
    Operating System:  
    Boot files:        /grub/grub.cfg

System-lv_swap': _______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

System-lv_root': _______________________________________________________________

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

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             718,848   629,864,447   629,145,600   7 NTFS / exFAT / HPFS
/dev/sda3         629,864,448 1,259,010,047   629,145,600   7 NTFS / exFAT / HPFS
/dev/sda4       1,259,010,048 2,343,749,887 1,084,739,840   5 Extended
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.

/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sde _____________________________________________________________________

Disk /dev/sde: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders, total 7905279 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             32     7,905,278     7,905,247   b W95 FAT32


Drive: pdc_ieijfhgji _____________________________________________________________________

Disk /dev/mapper/pdc_ieijfhgji: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders, total 3906249984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_ieijfhgji1              2,048 3,906,248,703 3,906,246,656  83 Linux


Drive: pdc_hicaefeec _____________________________________________________________________

Disk /dev/mapper/pdc_hicaefeec: 1200.0 GB, 1199999942656 bytes
255 heads, 63 sectors/track, 145891 cylinders, total 2343749888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_hicaefeec1   *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_hicaefeec2            718,848   629,864,447   629,145,600   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_hicaefeec3        629,864,448 1,259,010,047   629,145,600   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_hicaefeec4      1,259,010,048 2,343,749,887 1,084,739,840   5 Extended
/dev/mapper/pdc_hicaefeec5      1,260,038,144 2,343,749,631 1,083,711,488  8e Linux LVM
/dev/mapper/pdc_hicaefeec6      1,259,014,144 1,260,038,143     1,024,000  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/pdc_hicaefeec1 48D43256D432468A                       ntfs       System Reserved
/dev/mapper/pdc_hicaefeec2 389A33DB9A33947A                       ntfs       Win8Pro
/dev/mapper/pdc_hicaefeec3 64D2F3C0D2F39510                       ntfs       WinBackup
/dev/mapper/pdc_hicaefeec5 bTEUce-YRmg-9jDY-mGWU-BYqM-1nqh-Iynv2a LVM2_member 
/dev/mapper/pdc_hicaefeec6 f6082afc-4a46-45af-8673-abe0e4de0995   ext4       
/dev/mapper/pdc_ieijfhgji1 e1cce577-dedd-4f28-8642-a9742d8e7c9c   ext4       
/dev/mapper/System-lv_root 3d6ef303-ed92-4a91-8ae4-50a7057ccc58   ext4       
/dev/mapper/System-lv_swap c538c75f-10bc-423a-92db-d218e02cfbb1   swap       
/dev/sda                                                promise_fasttrack_raid_member 
/dev/sdb                                                promise_fasttrack_raid_member 
/dev/sdc                                                promise_fasttrack_raid_member 
/dev/sdd                                                promise_fasttrack_raid_member 
/dev/sde1        8423-CED3                              vfat       S0406538

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
pdc_hicaefeec
pdc_hicaefeec1
pdc_hicaefeec2
pdc_hicaefeec3
pdc_hicaefeec4
pdc_hicaefeec5
pdc_hicaefeec6
pdc_ieijfhgji
pdc_ieijfhgji1
System-lv_root
System-lv_swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/pdc_hicaefeec2 /media/ubuntu/Win8Pro    fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sde1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sde1/boot/grub/grub.cfg: ===========================

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

=================== sde1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== pdc_hicaefeec6/grub/grub.cfg: =========================

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
insmod lvm
insmod ext2
set root='lvmid/Fa0ZDs-MhEF-pEe1-671z-0g4e-yWqD-J4VPcJ/CmiL5b-gPZO-BOcN-tCMt-y6Di-6G5L-xURwYh'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='lvmid/Fa0ZDs-MhEF-pEe1-671z-0g4e-yWqD-J4VPcJ/CmiL5b-gPZO-BOcN-tCMt-y6Di-6G5L-xURwYh'  3d6ef303-ed92-4a91-8ae4-50a7057ccc58
else
  search --no-floppy --fs-uuid --set=root 3d6ef303-ed92-4a91-8ae4-50a7057ccc58
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-3d6ef303-ed92-4a91-8ae4-50a7057ccc58' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  f6082afc-4a46-45af-8673-abe0e4de0995
    else
      search --no-floppy --fs-uuid --set=root f6082afc-4a46-45af-8673-abe0e4de0995
    fi
    linux    /vmlinuz-3.13.0-34-generic.efi.signed root=/dev/mapper/System-lv_root ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.13.0-34-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-3d6ef303-ed92-4a91-8ae4-50a7057ccc58' {
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-advanced-3d6ef303-ed92-4a91-8ae4-50a7057ccc58' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  f6082afc-4a46-45af-8673-abe0e4de0995
        else
          search --no-floppy --fs-uuid --set=root f6082afc-4a46-45af-8673-abe0e4de0995
        fi
        echo    'Loading Linux 3.13.0-34-generic ...'
        linux    /vmlinuz-3.13.0-34-generic.efi.signed root=/dev/mapper/System-lv_root ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-recovery-3d6ef303-ed92-4a91-8ae4-50a7057ccc58' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  f6082afc-4a46-45af-8673-abe0e4de0995
        else
          search --no-floppy --fs-uuid --set=root f6082afc-4a46-45af-8673-abe0e4de0995
        fi
        echo    'Loading Linux 3.13.0-34-generic ...'
        linux    /vmlinuz-3.13.0-34-generic.efi.signed root=/dev/mapper/System-lv_root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-3d6ef303-ed92-4a91-8ae4-50a7057ccc58' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  f6082afc-4a46-45af-8673-abe0e4de0995
        else
          search --no-floppy --fs-uuid --set=root f6082afc-4a46-45af-8673-abe0e4de0995
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /vmlinuz-3.13.0-24-generic root=/dev/mapper/System-lv_root ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-3d6ef303-ed92-4a91-8ae4-50a7057ccc58' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  f6082afc-4a46-45af-8673-abe0e4de0995
        else
          search --no-floppy --fs-uuid --set=root f6082afc-4a46-45af-8673-abe0e4de0995
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /vmlinuz-3.13.0-24-generic root=/dev/mapper/System-lv_root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-24-generic
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

============== pdc_hicaefeec6: Location of files loaded by Grub: ===============

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4


Unknown BootLoader on System-lv_swap'


Unknown BootLoader on System-lv_root'



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
cat: /tmp/BootInfo-WNXvSNeq/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-WNXvSNeq/Tmp_Log: No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/System-lv_swap': No such file or directory
hexdump: /dev/mapper/System-lv_swap': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/System-lv_root': No such file or directory
hexdump: /dev/mapper/System-lv_root': No such file or directory
```

---

### Post by grahammechanical on 2014-08-24
Please wrap quote tags around that text. 

Here is what I think is the problem. You have two hard disks. By default Grub is installed into the MBR of sda. Which disk is /home on? Which disk has boot priority? If Grub is on sda and sda does not have boot priority then the Grub that is controlling the boot menu and boot process is the Grub from Fedora and it looking for a folder in Fedora for its configuration files So, Grub is broken because Fedora no longer exists .

Regards.

---

### Post by dennis31 on 2014-08-24
Added the quote tags. Normally my OS HDD has boot priority, followed by my data HDD. Currently I have set my USB port to boot first, followed by my OS HDD. All parts of all my operating systems are/were located on this OS HDD, except for my /home directory. That is located on the data HDD, which always boots after everything else. That disk does not contain anything except /home. (Currently that is empty because I have backed up all my data to my Windows partitions to solve another problem.) 

I reckon I now have two versions or copies of Grub installed, which are on different partitions on my OS HDD. I think I found some other unusual things (that need fixing) in my results report as well, but I do not understand everything I read. For example, unknown file system type for sda1, 2, and 3. Hope this helps. Thanks.

Dennis

Edit: Thanks for fixing it for me.

---

### Post by fantab on 2014-08-24
Fedora, by default, uses LVM partitions... to install Ubuntu on LVM partitions [Read Here]("https://help.ubuntu.com/community/UbuntuDesktopLVM").
Ubuntu and most of the other distros use Ext4 file system as default.

You can also re-install after reformating the partitions as Ext4.

---

### Post by dennis31 on 2014-08-24
I've read that tutorial and I think I do not have to do the first part -install lvm2 and create partitions- because I have already created those when installing Fedora. 
When I first installed Ubuntu I pointed it to my locations of /, /boot and /home and told it to format those partitions as ext4 and install Ubuntu from there. At least that is what I intended, I don't know if that is how it turned out. Also during this process I seem to have misplaced Grub, pointing it to /boot. 

I have no problem deleting and/or formatting all my Linux partitions and starting over, but I do want to save what's on my Windows partitions. I get confused when I have to allocate drive space for Ubuntu because I see so many partitions and I only know what some of them are. I think I must have done something wrong there.

Dennis

ETA: Or should I still install lvm2 to be able to install Ubuntu in the partitions I already have? Thanks for the advice.
EDIT2: I just found this at the end of that tutorial:

> If you see this during your installation of lvm2, this means, in a  nutshell, your initrd image will now be able to use LVM based partitions  at startup. If lvm2 was not installed on your computer and you started  to start it up, you computer would complain about not being able to find  /dev/mapper/sysvg-lvroot and so on... Your computer is now set up with Ubuntu and logical volumes by using the Ubuntu Desktop image.

So I suppose I will still have to install lvm2, even though it's a different file which cannot be found. Did I put everything else where it should be? I'll see if I can make a screenshot or list of all the partitions I see when I have to allocate drive space for Ubuntu.

---

### Post by fantab on 2014-08-24
> I seem to have misplaced Grub, pointing it to /boot

That could be the issue. Grub must be installed to the HDD an not /boot. You can try Boot-Repair. However I don't use LVM so I can't really help you with that.
If you want to back your data on Windows and other partitions, you can use the Ubuntu live DVD/USB to do so...

---

### Post by dennis31 on 2014-08-24
This is what I see when I have to allocate drive space. I have added comments in between brackets.

> 
[The first two are my root and swap partitions. I had the same when using Fedora but formatted /root when installing Ubuntu.]

/dev/mapper/System-lv_root
      /dev/mapper/System-lv_root              ext4            size: 53687 MB                  used: unknown                  system: Linux device-mapper (linear)
/dev/mapper/System-lv_swap
      /dev/mapper/System-lv_swap            swap            size: 18924 MB                  used: unknown

[The following must be my OS HDD. I don't really know why some of the partitions are nested and others arent. The NTFS partitions are for Windows, I recognize those. I don't know why they seem to be duplicated.]

/dev/mapper/pdc_hicaefeec
      /dev/mapper/pdc_hicaefeec1             NTFS        size: 367 MB                      used: unknown
      /dev/mapper/pdc_hicaefeec2             NTFS           size: 322122 MB                 used: unknown
      /dev/mapper/pdc_hicaefeec3             NTFS           size: 322122 MB                 used: unknown
      /dev/mapper/pdc_hicaefeec6             ext4         size: 524 MB                      used: unknown
      /dev/mapper/pdc_hicaefeec5                                size: 554860 MB                 used: unknown
/dev/mapper/pdc_hicaefeec1
      /dev/mapper/pdc_hicaefeec1             NTFS           size: 367 MB                      used: unknown
/dev/mapper/pdc_hicaefeec2
      /dev/mapper/pdc_hicaefeec2          NTFS           size: 322122 MB                 used: unknown
/dev/mapper/pdc_hicaefeec3
      /dev/mapper/pdc_hicaefeec3             NTFS           size: 322122 MB          used: unknown
/dev/mapper/pdc_hicaefeec4
/dev/mapper/pdc_hicaefeec5
/dev/mapper/pdc_hicaefeec6

[Don't know where the following free space comes from.]

free space                    size: 524 MB

[The below must be my data HDD with my /home directory. Don't know why this seems to be duplicated as well. I guess it might have something to do with my RAID].

/dev/mapper/pdc_ieijfhgjj
      /dev/mapper/pdc_ieijfhgjj1                ext4            size: 1999998 MB            used: unknown
/dev/mapper/pdc_ieijfhgjj1
      /dev/mapper/pdc_ieijfhgjj                  ext4         size: 1999998 MB            used: unknown


The above is all I see in the window and it seems like a terrible mess to me. In the drop-down menu to choose the device for boat loader installations I have some other options as well, including /dev/sda (which I've learned is the default and where I should've put Grub). The others are the same as above except with Linux device-mapper behind it with some qualification (linear, striped or mirror). I suppose this has something to do with RAID but have no clue what I should do. Also there a column called "Mount point" which is completely empty. Shouldn't there certain directories there, such as / and /boot?

Thanks for the advice.

Dennis

EDIT: Hm, I had formatted my post (again) when I pasted it from Notepad into this box, but upon posting the formatting seems to have been lost again. I don't know how to fix this.
EDIT2: fixed grammar

---

### Post by oldfred on 2014-08-24
I do not know RAID nor LVM.

But with RAID you do not install grub to a drive like sda, but to the root of the RAID. 
When looking at a system without the RAID mounted, it will show both drives which are then seen separately as the same thing as the RAID makes it seem like one.

Often RAID 0 is not recommended as if either drive fails you lose all data on both drives.
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
 [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

I do not know if these are your RAID or LVM as both use /mapper/...

 /dev/mapper/pdc_hicaefeec
/dev/mapper/pdc_ieijfhgjj
Then the numbers at the end are the partitions within the RAID or LVM.
But it looks like the one ending in 5 or partition 5 has the LVM inside it only.

---

### Post by dennis31 on 2014-08-24
Under normal circumstances my OS HDD does not contain any really important data. I use Windows only for gaming and some software I cannot get to work with WINE. I have chosen to use RAID 0 in order to improve speed for gaming. All my important data was stored in /home, but I had to transfer that data to my Windows partitions for the moment. (/home was encrypted with Fedora and I wasn't sure if I could get to my data after replacing Fedora with Ubuntu.)

At this time all my Linux partitions are pretty much empty (I think), although the Ubuntu installer recognized Ubuntu already being installed when I ran the installer again. So something must have gone right. I still think I have two copies of Grub located in different partitions. I thought about simply reinstalling Ubuntu again and then choosing the correct place for Grub (meaning /dev/sda) but after this talk of LVM and RAID I do not know whether that is the right thing to do. It doesn't seem so to me.

Am I correct in thinking that the root of the RAID is the System Reserved partition of my Windows? How can I distinguish between drives in LVM or in RAID?

Dennis

---

### Post by oldfred on 2014-08-24
The system partition in Windows is just the Windows boot partition, typically 100MB. Not used by Linux except to chainload to boot Windows. If system reserved partition that is UEFI/gpt and something else.
It shows as this and since it has a 1 at end it is the first partition in that RAID volume.
pdc_hicaefeec1

Those that want speed usually convert to SSD, although a few have used RAID with SSDs, but not sure that rest of system really supports that much speed in most cases.

These look like typical LVM volumes which are just in one partition of your RAID:
/dev/mapper/System-lv_root 3d6ef303-ed92-4a91-8ae4-50a7057ccc58   ext4       
 /dev/mapper/System-lv_swap c538c75f-10bc-423a-92db-d218e02cfbb1   swap

---

### Post by dennis31 on 2014-08-24
> **oldfred said:**
>  If system reserved partition that is UEFI/gpt and something else.
It shows as this and since it has a 1 at end it is the first partition in that RAID volume.


I don't understand what you said here. Could you please explain? I know what UEFI stands for, but not much else. I don't think I've ever seen "gpt" before.

Yes I thought about getting SSDs when buying the parts for my system but in the end I decided against it. I now have two 600GB Western Digital Raptors on which my Windows + games and Linux partitions are located. 

Dennis


EDIT: So it's apparently possible to have two LVMs within the same partition?! I worked under the assumption that a LVM was a kind of partition. Like in Windows you have extended partitions and logical partitions. I thought LVM was the same as a logical partition. I'll have to read up on partitions and RAID again it seems.

---

### Post by dennis31 on 2014-08-24
I've learned that a HDD _or a partition thereof_ is (still) a physical volume. Logical volumes (LVs) are like another layer on top of this if I understand correctly. LVM is the management part, not the actual volume(s). So I now need to identity the correct logical volume for me to install Grub in. When reinstalling Ubuntu I will format all my Linux LVs anyway just to be sure. Am I getting somewhere with this? 

Thanks for the help.

Dennis

EDIT: Found out that GPT stands for GUID Partition Table. I have relatively new hardware so I assume it's UEFI-enabled. As far as I know I still have and use a BIOS. I still don't get the relevance of this to logical volumes.

If in a RAID such as mine /dev/sda is not the correct place to install Grub, how do I find the root of my RAID? (If that is where I should put it instead?)

---

### Post by oldfred on 2014-08-24
Back in post #10 I think I showed the two RAID root folders. BIOS boots those and during install that should be an install option for grub.

But with 12.04 you only could install to RAID with server or alternative installers, not desktop. They then obsoleted the alternative installer and said to use server version or upgrade from 12.04. And later they would have LVM & RAID to desktop installer. With 14.04 they show LVM as a full drive (erases everything) install option, and at least one or two posts say they were able to install with RAID. Have not seen any comments whether it is fully working with Desktop installer or not.

I never have used LVM, it is a logical overlay over the physical partitions. Was a way to work around the 4 primary partitions and has some advantages, but really only if full drive as its default with Ubuntu.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
Issues on very large 19TB LVM ext4 64 bit partition
[http://ubuntuforums.org/showthread.php?t=2213785](http://ubuntuforums.org/showthread.php?t=2213785)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by dennis31 on 2014-08-24
Thank you for the information/clarification. I still do not understand completely but I'll spend some time going through the links you provided. I looked at the link from your signature earlier but I'll have to look deeper into that as well. If I could I guess I would get rid of the logical volumes but I suppose I cannot do that without losing my current Windows partitions. So at this time I'm stuck with having logical volumes. Yet all I really want right now is for my computer to boot again, even if only Windows. Now I know what I'll be doing tomorrow.

Dennis

EDIT: spelling
ETA: I already found some useful info in those links, like

>  I know that since Ubuntu 12.10 we can install in LVM with the standard 'Desktop' Live installation CD, or a USB containg the 'Live' operating system made from the same .iso file as the CD.

and

> That's all for now, I hope this will be enough to get you started using the Logical Volume Management GUI, and I know it will revolutionise they way many of us set up for multiple booting.
LVM is just what we need for multiple booting, and now that we have GRUB2, LVM is quite a bit more practical and attractive than it used to be. 


Especially that last one made me hopeful. Both are from here: [http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html) 
Now I'm off to do some more reading.

---

### Post by oldfred on 2014-08-24
The Ubuntu default with LVM is entire drive as that is when LVM works better. But you already have other partitions that you want to keep, so you can only use Something Else and control which partitions are used for which install.

I think part of the advantage of LVM was you did not have to get into the primary, extended and logical partition issues. But your LVM is inside an extended partition 4 as partition 5.

 /dev/mapper/pdc_hicaefeec[COLOR=#ff0000]4[/COLOR]      1,259,010,048 2,343,749,887 1,084,739,840   5 Extended
/dev/mapper/pdc_hicaefeec[COLOR=#ff0000]5[/COLOR]      1,260,038,144 2,343,749,631 1,083,711,488  8e Linux LVM
/dev/mapper/pdc_hicaefeec6      1,259,014,144 1,260,038,143     1,024,000  83 Linux

---

### Post by dennis31 on 2014-08-25
Yes, I've seen the warning in the thread linked in your signature to only reinstall Ubuntu using the "Something else" option. I think I'm going to install lvm2 and/or system-config-lvm via Live USB and see what Ubuntu thinks about my partitions and logical volumes then. I reckon that after this I only have to choose the right logical volumes to format and reinstall Ubuntu in. I still need to figure out where I should put Grub so that everything functions properly as a RAID. I'm not yet clear on which partition is the root of my RAID.

Dennis

EDIT: Installed system-config-lvm. In the physical view I have /dev/mapper/pdc_hicaefeec5, in the logical view lv_root and lv_swap. As you have pointed out to me those two are my logical volumes. I also got a few unitialized entities (perhaps because I have disabled my data HDD for now in the boot sequence). One is dev/mapper/pdc_ieijfgji containing a single ext 4 partition, which is my data HDD. The other is /dev/sde, also containing a single partition, which is almost 4GB FAT32. I don't know what that last one is. I thought I had a logical volume lv_boot at one time as well, but that seems gone now. Maybe that's where the unexplained free space I found earlier comes from. I must have deleted it when using gparted. Can't think of any other reason it has disappeared.

Anyway, now I need to find out what /dev/sda, /dev/sdb and /dev/sde etc. are. Sometimes I see these, sometimes they have a number behind them.
Also I do not seem to have any mount points configured, which I assume would lead to problems later on. I have a lot more reading to do.

EDIT2: HA, I have found the Grub and the normal.mod I had misplaced. They are now on a 524 MB volume, which I assume used to be my lv_boot. I only see this volume and my Windows volumes in the left sidebar of Ubuntu, not in the window of system-config-lvm.
Also, while having the system-config-lvm open I get a lot of errors in the terminal of various sources not being found. No idea what that is about.

Still have a lot more reading and such to do, but I feel like I'm getting somewhere now.

---

### Post by dennis31 on 2014-08-27
After installing system-config-lvm and running the Ubuntu installer again from USB I did not see any changes in the contents of the window where I have to allocate drive space for Ubuntu, which was contrary to my expectations.

Meanwhile I have learned the following: 

- What device files are and the Linux naming conventions for those files. ([https://en.wikipedia.org/wiki/Device_file](https://en.wikipedia.org/wiki/Device_file)) In that article I found the following:

> On disks using the typical PC master boot record, the device numbers of primary and the optional extended partition are numbered 1 through 4, while the indexes of any logical partitions are 5 and onwards, regardless of the layout of the former partitions (their parent extended partition does not need to be the fourth partition on the disk, nor do all four primary partitions have to exist).

- That GUID Partion Table is a replacement for MBR, yet they can coexist. I'll have to find out which of these I have, I guess probably both.

- That there are different implementations of RAID ([https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid))
I'm hoping that I have Software RAID but it seems likely that I have so-called FakeRAID instead. I'll have to look deeper into this.

- There exists a possible bug in Grub which might be related to my problem ([http://savannah.gnu.org/bugs/?40935](http://savannah.gnu.org/bugs/?40935))

- There is a Live CD available called SystemRescueCD which might be useful to me. ([http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage))
This site has info on disk partitioning and LVM management which I still have to read.

- There is another one called Ultimate Boot CD. ([http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/))

- There are many things about this which I do not understand yet.

I have decided I'm going to start with deciphering the results I got from Boot Info Script. After I understand those I hope to have a better grasp of what the issue(s) is/are.

Dennis

---

### Post by dennis31 on 2014-08-31
I've tried reinstalling Ubuntu again with Grub in /dev/sda, knowing that this probably wouldn't work. It didn't. The installer crashed when it tried to install Grub.
Also found out that system-config-lvm does not recognize RAID, which was the reason for the uninitialized entries.

I figure at this time the easiest way to get everything working again is starting over. I'll buy an external HDD to properly back up my data and do a complete reinstall of Windows and subsequently Ubuntu. I'm still determined to make it work with RAID and maybe even logical volumes as well.

Dennis

EDIT: grammar

---

### Post by dennis31 on 2014-09-02
I've backed up my data on an external HDD so I'm almost ready to reinstall Windows. At the moment I'm still struggling with my partitioning scheme. (Seeing how much trouble I'm currently having with this I'm starting to wonder how I ever got my RAID-LVM-dual boot system working at all.)

Though I have my motherboard manual here I still haven't determined which kind of RAID I have exactly. (My motherboard is an ASUS Crosshair V Formula.) The manual says "*The motherboard comes with the AMD SB950 chipset that allows you to configure Serial ATA hard disk drives as RAID sets.*" So it seems to me that I have hardware RAID, although the Ubuntu RAID wiki ([https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)) states it is very rare. I've looked at my RAID configuration options and both my RAID sets seem to be working fine. My two 600 GB Western Digital Raptors in a RAID 0 configuration show up as a 1,09 TB drive, and my two 2 TB Western Digital Black HDDs in RAID 1 show up as an 1,82 TB drive. So far so good.

Before going on to install Windows I decided to clean up my partitions using Gparted. This is where I got confused again. I have the Gparted manual ([http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)) open in another tab but I still don't understand. Hopefully someone here can clear things up for me. 

First of all, in the top right corner there is a list with all the hard disks found on the system. I have two /dev/mapper/* entries, one 1,09 TB in size, the other 1,82 TB. These must be my RAID sets. Yet I have also five /dev/sd* entries (sda - sde). Both /dev/sda and /dev/sdc are 558, 91 GB in size, so I guess those must be my two Raptors. Both /dev/sdb and dev/sdd are 1,82 TB in size, so I guess those must be my data HDDs. (Yes, I am aware that these do not appear in order. When I go to RAID configuration in my BIOS I see Raptor 1, Black 1, Raptor 2, Black 2.) Finally there is /dev/sde, which is 59,65 GB in size. As I'm typing this I realize this must be the USB stick from which I'm running Gparted. What I don't understand is why so much entries show up, instead of only my RAID sets (and USB stick). Is this normal or something unusual?

Secondly, when using Gparted none of my partitions seem to have any flags associated with it. I'm also not sure whether this is normal or unusual. I reckon I should flag my Windows System Reserved partition as boot, but I'm not sure about this. I'm also wondering whether I should flag my partitions as RAID or not.

Thirdly, I still have no clue which kind(s) of partition table I am using. I've found that when creating a new partition table in Gparted you can choose the type, but I haven't found the type(s) I'm currently using. (As of yet I have not made any changes to my partitions.)

Also I have found that when changing boot order to boot from USB I can (sometimes?) choose between "UEFI: [usbname]" and just "[usbname]". Yet when booting my BIOS tells me to press Delete to enter _EFI_ BIOS settings. I still do not understand the relation (and differences) between BIOS, EFI and UEFI and which option I should choose when booting from USB.

I'm still considering deleting all my current partitions and starting completely anew (hoping everything such as flags and mount points will sort itself out during the process), but I'd like to understand what I'm doing. Does anyone here have any tips or insights to share on how to proceed? Thanks in advance.

Dennis

---

