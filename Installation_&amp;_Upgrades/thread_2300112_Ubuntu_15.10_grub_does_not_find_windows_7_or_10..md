---
title: "Ubuntu 15.10 grub does not find windows 7 or 10."
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by Chase_Preuninger on 2015-10-23
I upgraded to ubuntu 15.10 yesterday.  After installing it I noticed there was no entry for my current windows 7 install on the boot manager.  I then tried running update-grub (did not find windows), and installing Ubuntu again to see if the installer found the windows installation and it did not.  Then I decided to try reinstalling windows (I wanted to upgrade from 7 to 10 anyway) and after this update-grub still could not find my windows install.  Ubuntu on Windows are installed on separate 250gb SSDs.  Right now if I want to switch operating systems I have to go into my bios and choose which drive to boot from.

Here is the output from running update-grub
> Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Adding boot menu entry for EFI firmware configuration
done


Also here is the output I got from running a bootinfoscript
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    268565976 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  The info in the boot sector on the starting sector of 
                       the MFT Mirror is wrong. According to the info in the 
                       boot sector, sdc1 has 1565562879 sectors, but 
                       according to the info from fdisk, it has 2639304703 
                       sectors.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb: ___________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624   454,961,151   453,910,528 Data partition (Linux)
/dev/sda3     454,961,152   488,396,799    33,435,648 Swap partition (Linux)

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1           2,048 2,639,306,751 2,639,304,704 Data partition (Windows/Linux)

Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048   488,396,799   488,394,752   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0727-9CFE                              vfat       
/dev/sda2        a864e3a6-025b-41a6-b28f-5dae179709f9   ext4       
/dev/sda3        91de152a-8765-43ad-ae12-9e2a49f946aa   swap       
/dev/sdb                                                           
/dev/sdc1        3161D67803D8C5BE                       ntfs       
/dev/sdd1        CA0A47FA0A47E255                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdd1        /media/chase/CA0A47FA0A47E255 fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)


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
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a864e3a6-025b-41a6-b28f-5dae179709f9
else
  search --no-floppy --fs-uuid --set=root a864e3a6-025b-41a6-b28f-5dae179709f9
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a864e3a6-025b-41a6-b28f-5dae179709f9' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a864e3a6-025b-41a6-b28f-5dae179709f9
    else
      search --no-floppy --fs-uuid --set=root a864e3a6-025b-41a6-b28f-5dae179709f9
    fi
    linux    /boot/vmlinuz-4.2.0-16-generic.efi.signed root=UUID=a864e3a6-025b-41a6-b28f-5dae179709f9 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.2.0-16-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a864e3a6-025b-41a6-b28f-5dae179709f9' {
    menuentry 'Ubuntu, with Linux 4.2.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-16-generic-advanced-a864e3a6-025b-41a6-b28f-5dae179709f9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a864e3a6-025b-41a6-b28f-5dae179709f9
        else
          search --no-floppy --fs-uuid --set=root a864e3a6-025b-41a6-b28f-5dae179709f9
        fi
        echo    'Loading Linux 4.2.0-16-generic ...'
        linux    /boot/vmlinuz-4.2.0-16-generic.efi.signed root=UUID=a864e3a6-025b-41a6-b28f-5dae179709f9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-16-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-16-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-16-generic-init-upstart-a864e3a6-025b-41a6-b28f-5dae179709f9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a864e3a6-025b-41a6-b28f-5dae179709f9
        else
          search --no-floppy --fs-uuid --set=root a864e3a6-025b-41a6-b28f-5dae179709f9
        fi
        echo    'Loading Linux 4.2.0-16-generic ...'
        linux    /boot/vmlinuz-4.2.0-16-generic.efi.signed root=UUID=a864e3a6-025b-41a6-b28f-5dae179709f9 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-16-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-16-generic-recovery-a864e3a6-025b-41a6-b28f-5dae179709f9' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a864e3a6-025b-41a6-b28f-5dae179709f9
        else
          search --no-floppy --fs-uuid --set=root a864e3a6-025b-41a6-b28f-5dae179709f9
        fi
        echo    'Loading Linux 4.2.0-16-generic ...'
        linux    /boot/vmlinuz-4.2.0-16-generic.efi.signed root=UUID=a864e3a6-025b-41a6-b28f-5dae179709f9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-16-generic
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=a864e3a6-025b-41a6-b28f-5dae179709f9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=0727-9CFE  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=91de152a-8765-43ad-ae12-9e2a49f946aa none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-vlBztUjk/Tmp_Log: No such file or directory

```

---

### Post by oldfred on 2015-10-23
Please use code tags not quotes for long text or terminal output. Easy to add with Forum's advanced editor and # icon.

You show Ubuntu installed in UEFI boot mode on a gpt partitioned drive and Windows installed in BIOS boot mode on a MBR(msdos) partitioned drive, sdd.

At one time you must have had Ubuntu in BIOS boot as you have grub still in gpt's protective MBR. But that is not configured now.

Drives over 2TiB must be gpt partitioned.
Windows only boots from gpt with UEFI.
Windows only boots with BIOS from MBR(msdos) partitioned drives.

You can have Ubuntu on a gpt drive and boot in either UEFI or BIOS mode if you have correct supporting partitions and then install correct version of grub2.
With UEFI you need the ESP - efi system partition and grub-efi-amd64.
With BIOS on gpt you need a tiny 1 or 2MB unformatted partition with the bios_grub flag and grub-pc.
Boot-Repair can convert an install from UEFI to BIOS (or vice-versa) if correct partitions are on drive.

UEFI & BIOS are not compatible. You can only boot from UEFI boot menu or possibly one time boot key, if system auto switches or know configuration. Some UEFI require you to turn on/off UEFI or CSM/Legacy/BIOS mode.
But best to have all systems UEFI/gpt or all systems BIOS boot.
But with Ubuntu on separate drive I still suggest gpt and have both ESP & bios_grub so you can change later if desired.

---

