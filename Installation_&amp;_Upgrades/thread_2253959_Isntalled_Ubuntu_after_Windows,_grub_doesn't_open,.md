---
title: "Isntalled Ubuntu after Windows, grub doesn't open, boots windows immidiately"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by Yuriy_Zaynulin on 2014-11-23
So I have an issue where Grub won't load and therefore I can't choose to boot Ubuntu. 
I've done a lot of manipulations that may or may not be important for my problem. 
I'm posting the output of bootinforscript. If you have additional questions I will tell what exacatly happened in details. 
Thank you
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/MokManager.efi /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 122236 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   250,069,679   250,069,679  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       264,191       262,144 EFI System partition
/dev/sda2         264,192   190,068,735   189,804,544 Data partition (Windows/Linux)
/dev/sda3     190,068,736   250,068,991    60,000,256 Data partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1       1,083,392 1,905,524,735 1,904,441,344 Data partition (Windows/Linux)
/dev/sdb2   1,905,524,736 1,953,523,711    47,998,976 Swap partition (Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 128.0 GB, 128035674112 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069676 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   250,068,991   250,066,944   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8BF5-2D0F                              vfat       
/dev/sda2        D8F658E0F658C104                       ntfs       
/dev/sda3        dfbd7d42-3df3-47ff-9ccd-ec8a652fda18   ext4       
/dev/sdb1        AE9CC49C9CC46087                       ntfs       
/dev/sdb2        c25301cf-3a6d-417a-ba38-4b7f795186ce   swap       
/dev/sdc1        07E9-243A                              vfat       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
else
  search --no-floppy --fs-uuid --set=root dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-dfbd7d42-3df3-47ff-9ccd-ec8a652fda18' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
    else
      search --no-floppy --fs-uuid --set=root dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
    fi
    linux    /boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=dfbd7d42-3df3-47ff-9ccd-ec8a652fda18 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-39-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-dfbd7d42-3df3-47ff-9ccd-ec8a652fda18' {
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-dfbd7d42-3df3-47ff-9ccd-ec8a652fda18' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
        else
          search --no-floppy --fs-uuid --set=root dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=dfbd7d42-3df3-47ff-9ccd-ec8a652fda18 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-dfbd7d42-3df3-47ff-9ccd-ec8a652fda18' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
        else
          search --no-floppy --fs-uuid --set=root dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=dfbd7d42-3df3-47ff-9ccd-ec8a652fda18 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-dfbd7d42-3df3-47ff-9ccd-ec8a652fda18' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
        else
          search --no-floppy --fs-uuid --set=root dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=dfbd7d42-3df3-47ff-9ccd-ec8a652fda18 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-dfbd7d42-3df3-47ff-9ccd-ec8a652fda18' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
        else
          search --no-floppy --fs-uuid --set=root dfbd7d42-3df3-47ff-9ccd-ec8a652fda18
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=dfbd7d42-3df3-47ff-9ccd-ec8a652fda18 ro recovery nomodeset 
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=dfbd7d42-3df3-47ff-9ccd-ec8a652fda18 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=8BF5-2D0F  /boot/efi       vfat    defaults        0       1
# /windows-C was on /dev/sda2 during installation
UUID=D8F658E0F658C104 /windows-C      ntfs    defaults,umask=007,gid=46 0       0
# /windows-D was on /dev/sdb1 during installation
UUID=AE9CC49C9CC46087 /windows-D      ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sdb2 during installation
UUID=c25301cf-3a6d-417a-ba38-4b7f795186ce none            swap    sw              0       0
UUID=8BF5-2D0F    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-owPisD8z/Tmp_Log: No such file or directory
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-owPisD8z/Tmp_Log: No such file or directory
  No volume groups found


```

---

### Post by oldfred on 2014-11-23
I do not see how your system can boot Windows at all.

Both drives are now gpt partitioned and Windows only boots from gpt partitioned drives with UEFI. 
And the efi partition in sda1 only has Ubuntu efi boot files, no Windows boot files.
Windows install looks more like a MBR(msdos) type install, but boot partition is not shown. And script is not showing the BCD which is one of the required Windows configuration for booting.

Was this originally a Windows 8 system?
Did you turn off secure boot and fast boot?

Since os-prober did not find a complete Windows set of boot files, it did not add a boot stanza. With only one system found it does not show grub menu as it assumes you only want to boot the one install.
With UEFI you click escape key to get to grub menu right after UEFI. If BIOS you hold shift key from BIOS until menu appears.

What brand/model system and what video card?

Ubuntu looks complete and should just boot. But perhaps you need boot parameters. Often video needs boot parameter to configure it to work until you install proprietary video driver.
Grub menu also remembers key presses. Right after UEFI one down arrow should get you into recovery mode.

---

### Post by Yuriy_Zaynulin on 2014-11-24
I actually managed to make it work fine by reinstalling Ubuntu on sda1  and EFI partition on sda3 - I don't really know if that's the reason it  works but that is the only change I made.

Now I'll explain what happened to the system and why is it that way. 
So first it was OEM windows 8.1 from MSI with small partition for windows bootloader separately on sda and the large sdb with extra 15GB partition for, as far as i think, the image of windows with drivers and w/e for recovery.
I installed ubuntu on sda along with windows and it worked fine. 
Then after some time I had to reinstall ubuntu and that is when i decided to clean up some partitions like the 15GB one and other small ones on sdb, because I thought they dont affect Windows anyways.
Which I did and then isntalled ubuntu on it's previous partition. 
The problem now was that it didnt load grub and went straight to ubuntu. 
I spent a day trying to fix that and might have made some manipulations that i don't recall preciselly now, but at the end I had to run windows recovery and fix it's bootloader. 
After that windows was running and grub didn't show up. After another set of manipulations I ended up in the situation presented above. 

Again my system works fine now, strangely bootinfoscript still doesnt show Microsoft folder in EFI, but I see it when it's  mounted. The output of the script and the EFI folder:


```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/MokManager.efi /efi/ubuntu/shimx64.efi

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   250,069,679   250,069,679  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1     190,068,736   250,068,991    60,000,256 Data partition (Linux)
/dev/sda2         264,192   190,068,735   189,804,544 Data partition (Windows/Linux)
/dev/sda3           2,048       264,191       262,144 EFI System partition

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1       1,083,392 1,905,524,735 1,904,441,344 Data partition (Windows/Linux)
/dev/sdb2   1,905,524,736 1,953,523,711    47,998,976 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4dd15a52-b34a-49c0-88f8-93fecfa09c32   ext4       
/dev/sda2        D8F658E0F658C104                       ntfs       
/dev/sda3        8BF5-2D0F                              vfat       
/dev/sdb1        AE9CC49C9CC46087                       ntfs       
/dev/sdb2        c25301cf-3a6d-417a-ba38-4b7f795186ce   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /windows-C               fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /boot/efi                vfat       (rw)
/dev/sdb1        /windows-D               fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
insmod part_gpt
insmod ext2
set root='hd0,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  4dd15a52-b34a-49c0-88f8-93fecfa09c32
else
  search --no-floppy --fs-uuid --set=root 4dd15a52-b34a-49c0-88f8-93fecfa09c32
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-4dd15a52-b34a-49c0-88f8-93fecfa09c32' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  4dd15a52-b34a-49c0-88f8-93fecfa09c32
    else
      search --no-floppy --fs-uuid --set=root 4dd15a52-b34a-49c0-88f8-93fecfa09c32
    fi
    linux    /boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=4dd15a52-b34a-49c0-88f8-93fecfa09c32 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-39-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-4dd15a52-b34a-49c0-88f8-93fecfa09c32' {
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-4dd15a52-b34a-49c0-88f8-93fecfa09c32' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  4dd15a52-b34a-49c0-88f8-93fecfa09c32
        else
          search --no-floppy --fs-uuid --set=root 4dd15a52-b34a-49c0-88f8-93fecfa09c32
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=4dd15a52-b34a-49c0-88f8-93fecfa09c32 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-4dd15a52-b34a-49c0-88f8-93fecfa09c32' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  4dd15a52-b34a-49c0-88f8-93fecfa09c32
        else
          search --no-floppy --fs-uuid --set=root 4dd15a52-b34a-49c0-88f8-93fecfa09c32
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=4dd15a52-b34a-49c0-88f8-93fecfa09c32 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-4dd15a52-b34a-49c0-88f8-93fecfa09c32' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  4dd15a52-b34a-49c0-88f8-93fecfa09c32
        else
          search --no-floppy --fs-uuid --set=root 4dd15a52-b34a-49c0-88f8-93fecfa09c32
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=4dd15a52-b34a-49c0-88f8-93fecfa09c32 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-4dd15a52-b34a-49c0-88f8-93fecfa09c32' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  4dd15a52-b34a-49c0-88f8-93fecfa09c32
        else
          search --no-floppy --fs-uuid --set=root 4dd15a52-b34a-49c0-88f8-93fecfa09c32
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=4dd15a52-b34a-49c0-88f8-93fecfa09c32 ro recovery nomodeset 
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
menuentry 'Windows Boot Manager (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-efi-8BF5-2D0F' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  8BF5-2D0F
    else
      search --no-floppy --fs-uuid --set=root 8BF5-2D0F
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
UUID=4dd15a52-b34a-49c0-88f8-93fecfa09c32 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
UUID=8BF5-2D0F  /boot/efi       vfat    defaults        0       1
# /windows-C was on /dev/sda2 during installation
UUID=D8F658E0F658C104 /windows-C      ntfs    defaults,umask=007,gid=46 0       0
# /windows-D was on /dev/sdb1 during installation
UUID=AE9CC49C9CC46087 /windows-D      ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sdb2 during installation
UUID=c25301cf-3a6d-417a-ba38-4b7f795186ce none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-pTzdPrn0/Tmp_Log: No such file or directory


```

```

total 3
drwxr-xr-x 5 root root 512 Nov 23 04:30 .
drwxr-xr-x 4 root root 512 Dec 31  1969 ..
drwxr-xr-x 2 root root 512 Nov 23 04:30 Boot
drwxr-xr-x 3 root root 512 Nov 23 04:30 Microsoft
drwxr-xr-x 2 root root 512 Nov 23 04:30 ubuntu

```

---

### Post by oldfred on 2014-11-24
I am surprised script is not showing Microsoft efi folder. I have seen where it does. But script has not been maintained for a while so does need some updates.

You also are supposed to have a 128MB unformated Microsoft reserved partition just before the main NTFS partition. I gather it is not required, but I usually see it and with both efi files missing and no MSR partition could not tell it is an UEFI boot install.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[URL="http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx"]http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx
[/URL]
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

[URL="http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx"]
[/URL]

---

