---
title: "Problem with Win7 boot"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by balaconaute on 2014-12-21
Hi,
I got a problem: After replacing my HDD on my laptop, I proceeded to the installation of Win 7 on sda1, and everything was perfect.
After that, I installed Ubuntu 14.04 on sda5, I can boot on that one, but impossible to boot on Win 7 from Grub.
I tried to do what I could with Win 7 installation DVD, but it seems it cant repair boot or MBR of Win 7.
I dont know what to do... :icon_frown:
Please help me!

Here is the result of the bootscript:
 ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda2         204,804,094 1,953,523,711 1,748,719,618   5 Extended
/dev/sda5         204,804,096   259,491,595    54,687,500  83 Linux
/dev/sda6         266,246,144 1,487,835,135 1,221,588,992   7 NTFS / exFAT / HPFS
/dev/sda7       1,487,837,184 1,747,677,183   259,840,000   7 NTFS / exFAT / HPFS
/dev/sda8       1,747,679,232 1,953,523,711   205,844,480   7 NTFS / exFAT / HPFS
/dev/sda9         259,491,840   266,244,095     6,752,256  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    37,457,919    37,455,872  73 Unknown
/dev/sdb2          37,457,920    46,895,103     9,437,184  84 OS/2 hidden C: drive


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        794E131854C3B740                       ntfs       Windows 7
/dev/sda5        f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1   ext3       
/dev/sda6        5689AA1230F18985                       ntfs       Gnafron
/dev/sda7        1FA130FC4EE4DE61                       ntfs       Joyeux
/dev/sda8        6A2F4B066E9694A0                       ntfs       Grincheux
/dev/sda9        022757ad-e1ba-4aa7-9b42-d7ac16ea08cf   swap       
/dev/sr0                                                iso9660    Ubuntu 14.04.1 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
else
  search --no-floppy --fs-uuid --set=root f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=fr_FR
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
    else
      search --no-floppy --fs-uuid --set=root f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
    fi
    linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-43-generic
}
submenu 'Options avancées pour Ubuntu' $menuentry_id_option 'gnulinux-advanced-f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1' {
    menuentry 'Ubuntu, avec Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
        else
          search --no-floppy --fs-uuid --set=root f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
        fi
        echo    'Chargement de Linux 3.13.0-43-generic…'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1 ro  quiet splash $vt_handoff
        echo    'Chargement du disque mémoire initial…'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
        else
          search --no-floppy --fs-uuid --set=root f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
        fi
        echo    'Chargement de Linux 3.13.0-43-generic…'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1 ro recovery nomodeset 
        echo    'Chargement du disque mémoire initial…'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, avec Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
        else
          search --no-floppy --fs-uuid --set=root f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
        fi
        echo    'Chargement de Linux 3.13.0-32-generic…'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1 ro  quiet splash $vt_handoff
        echo    'Chargement du disque mémoire initial…'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
        else
          search --no-floppy --fs-uuid --set=root f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
        fi
        echo    'Chargement de Linux 3.13.0-32-generic…'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1 ro recovery nomodeset 
        echo    'Chargement du disque mémoire initial…'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
    else
      search --no-floppy --fs-uuid --set=root f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
    else
      search --no-floppy --fs-uuid --set=root f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (sur /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-794E131854C3B740' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  794E131854C3B740
    else
      search --no-floppy --fs-uuid --set=root 794E131854C3B740
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
UUID=f8cf52b4-e1b4-4e90-b6b5-f888ef65eea1 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=022757ad-e1ba-4aa7-9b42-d7ac16ea08cf none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-lZsOZW4i/Tmp_Log: No such file or directory
  No volume groups found
```

---

### Post by UltimateCat on 2014-12-21
I'm not an expert but running [B]sudo os-prober might help. (if you don't have Ubuntu and Windows in your Grub Menu)

Than run sudo update grub and restart.

Os prober should find your Windows partition and add it it Grub.

I'm not good with boot repair, sorry.

Best to wait for a member with more experience with that.
[/B]

---

### Post by fantab on 2014-12-22
Post the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by oldfred on 2014-12-22
@fantab
All that info is in BootInfo report.

Please use code tags or in advanced editor the # icon in edit panel. Or use Boot-Repair and just post link it provides with its summary report. Boot-Repair has a slightly newer version of Bootinfoscript.

Is this an Ultrabook, you show sdb as a 24GB drive. That is typical of Ultrabooks that use Intel SRT and the small SSD is used a a boot cache. But it uses RAID for its configuration and grub does not boot that.

You may have to temporarily reinstall a Windows boot loader to MBR of sda and boot Windows or into Windows repair console to run Windows fixes. And turn off Intel SRT in BIOS. Then reinstall grub and see if it then boots Windows.

Some with the small SSD that use Ubuntu more than Windows just install / (root) to SSD and make a very fast Ubuntu install, but then Windows does not boot very quickly. Others have turned on SRT after installs and have it work.

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Ubuntu used to not even install when it saw the RAID, then it would install but not correctly install grub. So the older threads discussing install issues can be ignored. The Intel SRT seems to be standard across all vendors as it is Intel.

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

