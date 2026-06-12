---
title: "Grub installs on wrong disk and overwrites Win 7 mbr"
date: 2017-07-05
forum: Installation &amp; Upgrades
---

### Post by catplace on 2017-07-05
I have exactly the same problem as [this closed thread]("https://ubuntuforums.org/showthread.php?t=1489190"). I'd like to be able to try the solution given [here]("https://ubuntuforums.org/showthread.php?t=1489190&p=9336445#post9336445"); ie, 
```
sudo dpkg-reconfigure grub-pc
```
However, my system is UEFI not BIOS, and 64-bit, so I'm not sure how relevant that old advice is.

My tenuous understanding is that debconf-show should show me the options that I could change using dpkg-reconfigure, so I've used debconf-show to try to find out which of the many grub-related packages might be relevant. The results are:
```
debconf-show grub-pc
  grub-pc/partition_description:
  grub-pc/install_devices_empty: false
  grub-pc/hidden_timeout: true
  grub-pc/disk_description:
  grub2/linux_cmdline:
  grub-pc/chainload_from_menu.lst: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_disks_changed:
  grub2/linux_cmdline_default: quiet splash
  grub-pc/install_devices_failed: false
  grub2/device_map_regenerated:
  grub-pc/kopt_extracted: false
  grub2/force_efi_extra_removable: false
  grub-pc/install_devices:
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/timeout: 10
  grub2/kfreebsd_cmdline:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/postrm_purge_boot_grub: false

debconf-show grub-common

debconf-show grub2-common

debconf-show grub-efi-amd64-bin

debconf-show grub-efi-amd64
  grub2/linux_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline:
  grub2/force_efi_extra_removable: false
  grub2/linux_cmdline:
  grub2/device_map_regenerated:

debconf-show grub-efi-amd64-signed

debconf-show shim-signed
  shim/error/secureboot_key_mismatch:
  shim/secureboot_key:
  shim/secureboot_explanation:
  shim/secureboot_key_again:
  shim/error/bad_secureboot_key:
  shim/enable_secureboot: false
  shim/title/secureboot:
  shim/disable_secureboot: true

debconf-show grub-efi

```

Nothing here seems to indicate which package might need to be reconfigured to get grub to leave sda alone.

I would have attached the output from the boot info script, but I can't get the file attachment thing to work.

Some other possibly relevant info is [here]("https://forums.linuxmint.com/viewtopic.php?f=46&t=247711").

My question is: which package should I reconfigure to stop grub from installing itself onto sda whenever it upgrades?

Thanks!

---

### Post by yancek on 2017-07-05
The default for an EFI system for Ubuntu is to install to the EFI partition on the primary drive.  If both windows and Ubuntu are installed UEFI, that should not be a problem.  If you want Ubuntu UEFI and only on the second or non-primary drive, you need to create an EFI partition there and manually tell it you want it there during the install or move all the files from the other drive for Ubuntu.  Also, if you have an EFI install, you won't be using the MBR so more details on both systems would help someone to help you.

---

### Post by oldfred on 2017-07-05
If you have UEFI and both Widnows & Ubuntu are UEFI installs, then UEFI can directly boot either system from UEFI boot menu often f10 or f12.
And you can change boot order in UEFI to set any installed system as first in boot order. Or use efibootmgr in Ubuntu to change boot order.

But if using MBR then you have BIOS boot installs, not UEFI. Or perhaps a mixed install with one UEFI and other BIOS?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by catplace on 2017-07-07
Thanks to you both for your replies!

You're probably right about MBR; I'm easily confused about such things (and copied-and-pasted from an old thread). Both installations are EFI 64-bit. On my first attempt to install, linux indeed stuck its EFI and grub(?) stuff on sda1, which I didn't want. The vestige of this is now in ubuntu.hidden on sda; however, this may be insufficient obfuscation to prevent grub from finding it when it upgrades, resulting in it clagging sda1 again.

To get my system the way I want it (with only windows on sda and only linux on sdb), I reinstalled linux with sda physically disconnected. Thus, I now have a separate EFI partition on sdb. I select which OS to load by pressing F12 after starting the computer.

An outline of the two EFI partitions is:
```
sda EFI partition:
    EFI
       Boot
          bkpbootx64.efi.hidden
          bootx64.efi.hidden
      Microsoft
         (windows stuff)
      ubuntu.hidden
         (original linux/grub stuff, now not used?)

sdb EFI partition:
        EFI
      ubuntu
         (linux/grub stuff, now used?)
```

Here's the results from bootinfoscript (done in line because the pastebin option created a text file instead and I can't upload files because of ioerror!):
```

 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows Vista is installed in the MBR of /dev/sdc.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi.hidden
                       /EFI/Boot/bootx64.efi.hidden
                       /EFI/ubuntu.hidden/fwupx64.efi
                       /EFI/ubuntu.hidden/grubx64.efi
                       /EFI/Microsoft/Boot/bootmgfw.efi
                       /EFI/Microsoft/Boot/bootmgr.efi
                       /EFI/Microsoft/Boot/memtest.efi
                       /boot-sav/log/2016-10-26__17h20boot-repair33/sda1/bootx
                       64.efi

sda2: __________________________________________________________________________

    File system:      
    Boot sector type:  -
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 has
                       1565095935 sectors, but according to the info from
                       fdisk, it has 5860063231 sectors.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/fbx64.efi /EFI/ubuntu/fwupx64.efi
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi
                       /EFI/ubuntu/shimx64.efi

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Linux Mint 18.1
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048       206,847       204,800 EFI System partition
/dev/sda2   +           206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3               468,992 5,860,532,223 5,860,063,232 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                 2,048       585,727       583,680 EFI System partition
/dev/sdb2               585,728    64,585,727    64,000,000 Swap partition (Linux)
/dev/sdb3            64,585,728 1,041,147,903   976,562,176 Data partition (Linux)
/dev/sdb4         1,041,147,904 3,907,026,943 2,865,879,040 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048   234,438,655   234,436,608   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        488B-14F3                              vfat       SYSTEM
/dev/sda2                                                          
/dev/sda3        443017B93017B0C2                       ntfs       HDD1
/dev/sdb1        BA63-45D9                              vfat      
/dev/sdb2        a91475fe-af0b-4a2f-8ec7-464c9de34c17   swap      
/dev/sdb3        bb9d478b-9b65-4ba1-a48e-20dd95cce7c7   ext4      
/dev/sdb4        B240154A40151727                       ntfs       HDD2
/dev/sdc1        185EFBB35EFB8830                       ntfs       Patches
/dev/sdd1        365EF3F15EF3A7AF                       ntfs       FSX

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul  8 08:56 ata-ATAPI_iHAS324_B_3743524219_3H8021513 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul  8 09:57 ata-OCZ-VERTEX2_OCZ-6ZOMPS2KIO2595BA -> ../../sdd
lrwxrwxrwx 1 root root 10 Jul  8 09:57 ata-OCZ-VERTEX2_OCZ-6ZOMPS2KIO2595BA-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Jul  8 09:57 ata-SAMSUNG_HD501LJ_S0MUJDWPC12019 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jul  8 09:57 ata-SAMSUNG_HD501LJ_S0MUJDWPC12019-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jul  8 09:57 ata-WDC_WD2001FASS-00W2B0_WD-WMAY00630919 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul  8 09:57 ata-WDC_WD2001FASS-00W2B0_WD-WMAY00630919-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jul  8 09:57 ata-WDC_WD2001FASS-00W2B0_WD-WMAY00630919-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jul  8 09:57 ata-WDC_WD2001FASS-00W2B0_WD-WMAY00630919-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jul  8 09:57 ata-WDC_WD2001FASS-00W2B0_WD-WMAY00630919-part4 -> ../../sdb4
lrwxrwxrwx 1 root root  9 Jul  8 09:57 ata-WDC_WD3003FZEX-00Z4SA0_WD-WCC132HX3ZPE -> ../../sda
lrwxrwxrwx 1 root root 10 Jul  8 09:57 ata-WDC_WD3003FZEX-00Z4SA0_WD-WCC132HX3ZPE-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul  8 09:57 ata-WDC_WD3003FZEX-00Z4SA0_WD-WCC132HX3ZPE-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul  8 09:57 ata-WDC_WD3003FZEX-00Z4SA0_WD-WCC132HX3ZPE-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Jul  8 09:57 wwn-0x50000f00dbc12019 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jul  8 09:57 wwn-0x50000f00dbc12019-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jul  8 09:57 wwn-0x50014ee057d9583c -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul  8 09:57 wwn-0x50014ee057d9583c-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jul  8 09:57 wwn-0x50014ee057d9583c-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jul  8 09:57 wwn-0x50014ee057d9583c-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jul  8 09:57 wwn-0x50014ee057d9583c-part4 -> ../../sdb4
lrwxrwxrwx 1 root root  9 Jul  8 09:57 wwn-0x50014ee2b5ffa2f6 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul  8 09:57 wwn-0x50014ee2b5ffa2f6-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul  8 09:57 wwn-0x50014ee2b5ffa2f6-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul  8 09:57 wwn-0x50014ee2b5ffa2f6-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Jul  8 09:57 wwn-0x5e83a97fbea2f92b -> ../../sdd
lrwxrwxrwx 1 root root 10 Jul  8 09:57 wwn-0x5e83a97fbea2f92b-part1 -> ../../sdd1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/peter/SYSTEM      vfat       (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
/dev/sda3        /mnt/c                   fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb3        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdc1        /media/peter/Patches     fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdd1        /media/peter/FSX         fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='hd1,gpt3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
else
  search --no-floppy --fs-uuid --set=root bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

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
menuentry 'Linux Mint 18.1 Cinnamon 64-bit' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bb9d478b-9b65-4ba1-a48e-20dd95cce7c7' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
    else
      search --no-floppy --fs-uuid --set=root bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
    fi
    linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=bb9d478b-9b65-4ba1-a48e-20dd95cce7c7 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-21-generic
}
submenu 'Advanced options for Linux Mint 18.1 Cinnamon 64-bit' $menuentry_id_option 'gnulinux-advanced-bb9d478b-9b65-4ba1-a48e-20dd95cce7c7' {
    menuentry 'Linux Mint 18.1 Cinnamon 64-bit, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-bb9d478b-9b65-4ba1-a48e-20dd95cce7c7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
        else
          search --no-floppy --fs-uuid --set=root bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=bb9d478b-9b65-4ba1-a48e-20dd95cce7c7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Linux Mint 18.1 Cinnamon 64-bit, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-bb9d478b-9b65-4ba1-a48e-20dd95cce7c7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
        else
          search --no-floppy --fs-uuid --set=root bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=bb9d478b-9b65-4ba1-a48e-20dd95cce7c7 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Linux Mint 18.1 Cinnamon 64-bit, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-bb9d478b-9b65-4ba1-a48e-20dd95cce7c7' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
        else
          search --no-floppy --fs-uuid --set=root bb9d478b-9b65-4ba1-a48e-20dd95cce7c7
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=bb9d478b-9b65-4ba1-a48e-20dd95cce7c7 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-efi-488B-14F3' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  488B-14F3
    else
      search --no-floppy --fs-uuid --set=root 488B-14F3
    fi
    chainloader /efi/Microsoft/Boot/bootmgfw.efi
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

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=bb9d478b-9b65-4ba1-a48e-20dd95cce7c7 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=BA63-45D9  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda2 during installation
UUID=a91475fe-af0b-4a2f-8ec7-464c9de34c17 none            swap    sw              0       0
/dev/disk/by-uuid/443017B93017B0C2 /mnt/c auto nosuid,nodev,nofail,x-gvfs-show 0 0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 165.848861694 = 178.078859264  boot/grub/grub.cfg                             1
  58.976463318 = 63.325495296   boot/vmlinuz-4.4.0-21-generic                  1
  58.976463318 = 63.325495296   vmlinuz                                        1
  60.177089691 = 64.614658048   boot/initrd.img-4.4.0-21-generic               2
  60.177089691 = 64.614658048   initrd.img                                     2

======================== Unknown MBRs/Boot Sectors/etc: ========================


/dev/sda2: unknown GPT attributes
8000000000000000

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/22999/mounts) leaked on lvs invocation. Parent PID 1994: bash
File descriptor 63 (pipe:[103506]) leaked on lvs invocation. Parent PID 1994: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 2017-07-08__09h57 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version :
File descriptor 9 (/proc/22999/mounts) leaked on lvs invocation. Parent PID 24613: /bin/sh
boot-info is executed in installed-session (Linux Mint 18.1 Serena, serena, LinuxMint, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.4.0-21-generic root=UUID=bb9d478b-9b65-4ba1-a48e-20dd95cce7c7 ro quiet splash vt.handoff=7

=================== os-prober:
/dev/sdb3:The OS now in use - Linux Mint 18.1 Serena CurrentSession:linux
/dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi

=================== blkid:
/dev/sda1: LABEL="SYSTEM" UUID="488B-14F3" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="96e85dba-3984-4318-be99-c7a3ba717110"
/dev/sda3: LABEL="HDD1" UUID="443017B93017B0C2" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="4e15dcce-d900-49b2-8294-c5e79a3f1dae"
/dev/sdb1: UUID="BA63-45D9" TYPE="vfat" PARTUUID="30a8613f-bfb3-408f-97ec-d700509e6e76"
/dev/sdb2: UUID="a91475fe-af0b-4a2f-8ec7-464c9de34c17" TYPE="swap" PARTUUID="8d59b435-ff36-41e8-9fa8-938cbf85d011"
/dev/sdb3: UUID="bb9d478b-9b65-4ba1-a48e-20dd95cce7c7" TYPE="ext4" PARTUUID="81d82277-8dbb-48b0-95d3-4f4557737a21"
/dev/sdb4: LABEL="HDD2" UUID="B240154A40151727" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="7c42fcf6-6984-4608-bd78-29d3b6548618"
/dev/sdc1: LABEL="Patches" UUID="185EFBB35EFB8830" TYPE="ntfs" PARTUUID="75a0e68d-01"
/dev/sdd1: LABEL="FSX" UUID="365EF3F15EF3A7AF" TYPE="ntfs" PARTUUID="45f9db74-01"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="4f62faae-c760-4066-ba33-4e1f42761f36"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda3.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Jul  8 08:56 grub.d
total 108
-rwxr-xr-x 1 root root  9791 Apr 16  2016 00_header
-rwxr-xr-x 1 root root  6258 Mar 16  2016 05_debian_theme
-rwxr-xr-x 1 root root  1180 Oct 25  2014 06_mint_theme
-rwxr-xr-x 1 root root 12273 Jul  8 08:56 10_linux
-rwxr-xr-x 1 root root 12512 Mar 24 17:32 10_linux.dpkg-dist
-rwxr-xr-x 1 root root 10634 Oct  1  2012 10_lupin
-rwxr-xr-x 1 root root 11082 Apr 16  2016 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 16  2016 30_os-prober
-rwxr-xr-x 1 root root  1418 Apr 16  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 16  2016 40_custom
-rwxr-xr-x 1 root root   216 Apr 16  2016 41_custom
-rw-r--r-- 1 root root   483 Apr 16  2016 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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



/boot/efi detected in the fstab of sdb3: UUID=BA63-45D9   (sdb1)
Presence of EFI/Microsoft file detected: /media/peter/SYSTEM/EFI/Microsoft/Boot/bootmgfw.efi

=================== efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0001,0000,0004,0005,0006,000C,000F,0010
Boot0000* ubuntu    HD(1,GPT,30a8613f-bfb3-408f-97ec-d700509e6e76,0x800,0x8e800)/File(EFIUBUNTUSHIMX64.EFI)
Boot0001* Windows Boot Manager    HD(1,GPT,96e85dba-3984-4318-be99-c7a3ba717110,0x800,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004  ATAPI   iHAS324   B    BBS(CDROM,,0x0)AMBO
Boot0005  SAMSUNG HD501LJ    BBS(HD,,0x0)AMBO
Boot0006  OCZ-VERTEX2    BBS(HD,,0x0)AMBO
Boot000C  WDC WD2001FASS-00W2B0    BBS(HD,,0x0)AMBO
Boot000F  WDC WD3003FZEX-00Z4SA0    BBS(HD,,0x0)AMBO
Boot0010  ubuntu    HD(1,GPT,30a8613f-bfb3-408f-97ec-d700509e6e76,0x800,0x8e800)/File(EFIUBUNTUGRUBX64.EFI)

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sdb3    : sdb,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/peter/SYSTEM.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/c.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot/efi.
sdb4    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb4.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/peter/Patches.
sdd1    : sdd,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/peter/FSX.

sdb    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdd    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD3003FZEX-0 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                          Flags
1      1049kB  106MB   105MB   fat32        EFI system partition          boot, esp
2      106MB   240MB   134MB                Microsoft reserved partition  msftres
3      240MB   3001GB  3000GB  ntfs         Basic data partition          msftdata


Model: ATA WDC WD2001FASS-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name                  Flags
1      1049kB  300MB   299MB   fat32                                 boot, esp
2      300MB   33.1GB  32.8GB  linux-swap(v1)
3      33.1GB  533GB   500GB   ext4
4      533GB   2000GB  1467GB  ntfs            Basic data partition  msftdata


Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type     File system  Flags
1      1049kB  500GB  500GB  primary  ntfs


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sdd: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type     File system  Flags
1      1049kB  120GB  120GB  primary  ntfs

=================== parted -lm:

BYT;
/dev/sda:3001GB:scsi:512:4096:gpt:ATA WDC WD3003FZEX-0:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:240MB:134MB::Microsoft reserved partition:msftres;
3:240MB:3001GB:3000GB:ntfs:Basic data partition:msftdata;

BYT;
/dev/sdb:2000GB:scsi:512:512:gpt:ATA WDC WD2001FASS-0:;
1:1049kB:300MB:299MB:fat32::boot, esp;
2:300MB:33.1GB:32.8GB:linux-swap(v1)::;
3:33.1GB:533GB:500GB:ext4::;
4:533GB:2000GB:1467GB:ntfs:Basic data partition:msftdata;

BYT;
/dev/sdc:500GB:scsi:512:512:msdos:ATA SAMSUNG HD501LJ:;
1:1049kB:500GB:500GB:ntfs::;

BYT;
/dev/sdd:120GB:scsi:512:512:msdos:ATA OCZ-VERTEX2:;
1:1049kB:120GB:120GB:ntfs::;

=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL
sda   disk          2.7T
sda1  part vfat     100M SYSTEM
sda2  part          128M
sda3  part ntfs     2.7T HDD1
sdb   disk          1.8T
sdb1  part vfat     285M
sdb2  part swap    30.5G
sdb3  part ext4   465.7G
sdb4  part ntfs     1.3T HDD2
sdc   disk        465.8G
sdc1  part ntfs   465.8G Patches
sdd   disk        111.8G
sdd1  part ntfs   111.8G FSX
sr0   rom          1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /media/peter/SYSTEM
sda2     1  0  0
sda3     1  0  0         /mnt/c
sdb      1  0  0 running
sdb1     1  0  0         /boot/efi
sdb2     1  0  0         [SWAP]
sdb3     1  0  0         /
sdb4     1  0  0         /mnt/boot-sav/sdb4
sdc      1  0  1 running
sdc1     1  0  1         /media/peter/Patches
sdd      0  0  1 running
sdd1     0  0  1         /media/peter/FSX
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8150436k,nr_inodes=2037609,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1634264k,mode=755)
/dev/sdb3 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd,nsroot=/)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct,nsroot=/)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children,nsroot=/)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids,nsroot=/)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer,nsroot=/)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio,nsroot=/)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory,nsroot=/)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices,nsroot=/)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio,nsroot=/)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb,nsroot=/)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event,nsroot=/)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
/dev/sda3 on /mnt/c type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1634264k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdd1 on /media/peter/FSX type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc1 on /media/peter/Patches type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda1 on /media/peter/SYSTEM type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
gvfsd-fuse on /home/peter/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=0,group_id=0)
/dev/sdb4 on /mnt/boot-sav/sdb4 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb2 sdb3 sdb4 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvb dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hidraw6 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kmsg kvm lightnvm lirc0 lirc1 log mapper mcelog media0 media1 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null nvidia0 nvidiactl nvidia-modeset nvidia-uvm port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdb3 sdb4 sdc sdc1 sdd sdd1 sg0 sg1 sg2 sg3 sg4 shm snapshot snd sr0 stderr stdin stdout swradio0 swradio1 uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control
ls: cannot access '': No such file or directory

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 f3 14 8b 48 4e  4f 20 4e 41 4d 45 20 20  |..)...HNO NAME  |
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

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 07 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 77 49 5d 01 00 00 00  |.........wI]....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  c2 b0 17 30 b9 17 30 44  |...........0..0D|
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

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 e8 08 00 39 02 00 00  00 00 00 00 02 00 00 00  |....9...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 d9 45 63 ba 4e  4f 20 4e 41 4d 45 20 20  |..).Ec.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 0e 3e  |........?......>|
00000020  00 00 00 00 80 00 80 00  ff d7 d1 aa 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  27 17 15 40 4a 15 40 b2  |........'..@J.@.|
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

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 4f 38 3a 00 00 00 00  |.........O8:....|
00000030  00 00 0c 00 00 00 00 00  ff 84 a3 03 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  30 88 fb 5e b3 fb 5e 18  |........0..^..^.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdd1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 37 f9 0d 00 00 00 00  |.........7......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  af a7 f3 5e f1 f3 5e 36  |...........^..^6|
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
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  9.7M  1.6G   1% /run
/dev/sdb3      ext4      459G  9.5G  426G   3% /
tmpfs          tmpfs     7.8G   35M  7.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda3      fuseblk   2.8T  2.0T  752G  74% /mnt/c
/dev/sdb1      vfat      285M  3.5M  281M   2% /boot/efi
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     1.6G   40K  1.6G   1% /run/user/1000
/dev/sdd1      fuseblk   112G   93G   20G  83% /media/peter/FSX
/dev/sdc1      fuseblk   466G  135G  332G  29% /media/peter/Patches
/dev/sda1      vfat       96M   50M   47M  52% /media/peter/SYSTEM
/dev/sdb4      fuseblk   1.4T  129M  1.4T   1% /mnt/boot-sav/sdb4

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 003B887B-9DB0-4F84-8140-68122866115C

Device      Start        End    Sectors  Size Type
/dev/sda1    2048     206847     204800  100M EFI System
/dev/sda2  206848     468991     262144  128M Microsoft reserved
/dev/sda3  468992 5860532223 5860063232  2.7T Microsoft basic data




Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C0DBB3ED-1272-4BBB-82CB-EAED00B1D36A

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048     585727     583680   285M EFI System
/dev/sdb2      585728   64585727   64000000  30.5G Linux swap
/dev/sdb3    64585728 1041147903  976562176 465.7G Linux filesystem
/dev/sdb4  1041147904 3907026943 2865879040   1.3T Microsoft basic data


Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x75a0e68d

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdc1        2048 976771071 976769024 465.8G  7 HPFS/NTFS/exFAT


Disk /dev/sdd: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x45f9db74

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdd1        2048 234438655 234436608 111.8G  7 HPFS/NTFS/exFAT




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sdb3, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb (2000GB) disk!

The boot files of [The OS now in use - Linux Mint 18.1 Serena] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot-Repair]. (https://help.ubuntu.com/community/BootPartition)

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi


=================== User settings
The settings chosen by the user will not act on the boot.

```

To reiterate, I like the way my computer boots now; I just don't want it to change (again) if I allow grub and shim to upgrade. Ergo, I need to prevent grub and shim from messing with sda on upgrade (I think).

Thanks again for your help!

---

### Post by oldfred on 2017-07-09
While it says grub installed to sda1, the UUID is for sdb1.

# /boot/efi was on /dev/sda1 during installation
UUID=[COLOR=#ff0000]BA63-45D9[/COLOR]  /boot/efi       vfat    umask=0077      0       1
/dev/sdb1: UUID="[COLOR=#ff0000]BA63-45D9[/COLOR]" TYPE="vfat" PARTUUID="[COLOR=#0000ff]30a8613f-bfb3-408f-97ec-d700509e6e76[/COLOR]"

So it looks like you did not have sda drive connected when you installed Ubuntu. Grub does default to install to ESP - efi system partition on sda.

And this says UEFI is looking for GUID that is now sdb1.
Boot0000* ubuntu    HD(1,GPT,[COLOR=#0000ff]30a8613f-bfb3-408f-97ec-d700509e6e76[/COLOR],0x800,0x8e800)/File(EFIUBUNTUSHIMX64.EFI)

Part UUID, is the gpt GUID it assigns, that is different than an UUID.

---

### Post by catplace on 2017-07-09
Oh! That's very credible; I did indeed remove the Windows drive when installing Linux (after the first botched attempt).

If this is what's causing grub to worm its way back onto the Windows drive when it upgrades, some adaptation of the suggestion [here]("https://ubuntuforums.org/showthread.php?t=1489190&p=9336445#post9336445") might still seem appropriate; ie,
```
sudo dpkg-reconfigure grub-pc
```...but probably not grub-pc on a 64-bit UEFI system.

How safe would it be for me to go messing with dpkg-reconfigure to look for options? Will it warn me before actually making any changes?

Or is this totally the wrong solution, and I need to mess around with a config file of some sort?

I've heard that there's a grub reconfiguration utility. Would that work?

Apologies for my questions and ignorance; your help is greatly appreciated!

---

### Post by oldfred on 2017-07-09
I think with UEFI, it is the entry in your fstab as I posted above. 
And since that is the UUID of sdb, grub should not update into sda's ESP. 

But if you do a new install of grub with Windows drive connected, it will probably install into Windows sda's ESP. And then UEFI will not boot as GUID does not match, until you update UEFI entry. 
And updates from a Live installer like with Boot-Repair would see the Windows sda as it does not use fstab of your install.

---

### Post by catplace on 2017-07-09
Thanks again. I can verify that grub updates onto the Windows drive; it did last time I allowed it to update.

It sounds like there's no way to keep linux bits off the Windows drive, so I'll just avoid updating grub.

---

### Post by oldfred on 2017-07-10
If your fstab says to use sdb drive by UUID and UEFI says to use ESP on sdb by GUID as I posted above, and it still is updating into Windows ESP on sda, you need to file a bug. That is just wrong.

I have filed bugs on letting grub install to an ESP on sdb, and other distributions seem to allow that. But Ubuntu's does not. 

This is an install bug to sdb not working in UEFI mode, so not exactly the same issue.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1414124](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1414124)

But your issue is an install already in sdb, and still updating sda. But you can link to above bug as issue would still apply if they ever fix the install bug.

---

### Post by catplace on 2017-07-10
Thanks for persevering with me, oldfred!

Could not the grub folks could argue that grub is working as intended if my system contains conflicting info? Is it possible for me to hand-edit fstab to put the correct UUIDs in there? And how can I get grub (or whatever) to forget this: "# /boot/efi was on /dev/sda1 during installation" (or change it to sdb1)?

It occurs to me that I could probably upgrade grub/shim safely by physically disconnecting my Windows drive again, but it would be a pain to have to disassemble my computer whenever such an upgrade is available.

---

### Post by oldfred on 2017-07-10
The # line is just a comment, it means nothing to actual re-install or where system looks for files.
It just is saying when installed it was sda1.

But Ubuntu/grub system works on UUIDs, and UEFI works on GUIDs.

---

### Post by catplace on 2017-07-12
Ta yet again. I did suspect that # indicated a comment line, but wasn't sure whether grub might have made use of it regardless. It seems like an unusual comment to retain if it is not useful.

Based on your info, I checked out my fstab, blkid, etc. Everything seems to be pointing to the correct partition UUIDs. The only mentions of sda1 and its UUID are in the context of booting Windows (which makes sense).

I did note that the system was still seeing the original linux EFI and grub files on sda1 (in ubuntu-hidden). I bravely moved that folder out of the EFI partition and reran the BootInfo script; unsurprisingly, it no longer reports them. It would be nice to think that their existence was sufficient to cause grub to update sda1, and that their removal would solve my problem. However, I see from that bug report that grub-install remains willing to mess with sda even when told not to (especially when it had been previously installed there).

Alas, I'm still not confident enough to see whether the grub update would work properly now. I don't have the ability to recover the system when it goes wrong. This precludes me from possibly contributing to that bug report.

---

### Post by Dennis N on 2017-07-12
With ubiquity (ubuntu's installer package) running in UEFI mode, grub installs to an sda EFI system partition - probably the first one it finds. You could later move those files to a new partition and create a new EFI boot menu entry, but not a novice's task. To prevent all grub packages from being upgraded and new ones installed, you could use: 
```
sudo apt-mark hold grub* 
```
This is not the same as what happens with the update-grub command, which takes place after a new kernel gets installed. update-grub only regenerates the boot menu - no grub packages are installed.

---

### Post by catplace on 2017-07-15
Thanks Dennis. I'll do that.

 Should I also do
```
sudo apt-mark hold shim*
```...or is the shim safe to upgrade (in terms of not invading sda and not requiring a specific grub version)?

I gather that I must be being a bit obtuse in my desire to keep all linux stuff on its own drive. It isn't supposed to be like that, I now assume.

---

### Post by Dennis N on 2017-07-15
> **catplace said:**
> Thanks Dennis. I'll do that.

 Should I also do
```
sudo apt-mark hold shim*
```...or is the shim safe to upgrade (in terms of not invading sda and not requiring a specific grub version)?

I gather that I must be being a bit obtuse in my desire to keep all linux stuff on its own drive. It isn't supposed to be like that, I now assume.

Yes, I would hold that package too if it is present. It's for use with the secure boot check if secure boot is enabled.

---

### Post by catplace on 2017-07-15
Thanks again, Dennis. While I'm not using secure boot (I think), I can see some shim-related files on sdb in the same EFI directory as the grub files, hence my concern. I'll hold them too.

---

