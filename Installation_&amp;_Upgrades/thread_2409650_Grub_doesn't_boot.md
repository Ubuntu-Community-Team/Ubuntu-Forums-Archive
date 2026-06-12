---
title: "Grub doesn't boot"
date: 2019-01-04
forum: Installation &amp; Upgrades
---

### Post by jeeba on 2019-01-04
I have Windows 10 installed in my PC and today I wanted to install Ubuntu in a Logical Partition. Here is the Boot Info Screen result:

I want Grub to appear an also change the default option to windows and change the time to select the partition.

```


     Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

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
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/ubuntu/fwupx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048 1,366,614,758 1,365,588,711   7 NTFS / exFAT / HPFS
/dev/sda3       1,366,616,064 1,367,580,671       964,608  27 Hidden NTFS (Recovery Environment)
/dev/sda4       1,367,582,718 1,953,523,711   585,940,994   5 Extended
/dev/sda5       1,369,540,608 1,953,523,711   583,983,104  83 Linux
/dev/sda6    *  1,367,582,720 1,369,540,607     1,957,888  ef EFI (FAT-12/16/32)


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/sda1        20CCDD8BCCDD5B9A                       ntfs       Reservado para el sistema
/dev/sda2        808EE2D48EE2C1B0                       ntfs       
/dev/sda3        F80293060292C950                       ntfs       
/dev/sda5        693b306e-16e5-49a7-af51-b9e3e03d4db9   ext4       
/dev/sda6        FD40-C3C7                              vfat       
/dev/sdb1        24FA1857FA182816                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda6        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  693b306e-16e5-49a7-af51-b9e3e03d4db9
else
  search --no-floppy --fs-uuid --set=root 693b306e-16e5-49a7-af51-b9e3e03d4db9
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
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-693b306e-16e5-49a7-af51-b9e3e03d4db9' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  693b306e-16e5-49a7-af51-b9e3e03d4db9
    else
      search --no-floppy --fs-uuid --set=root 693b306e-16e5-49a7-af51-b9e3e03d4db9
    fi
        linux    /boot/vmlinuz-4.15.0-43-generic root=UUID=693b306e-16e5-49a7-af51-b9e3e03d4db9 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.15.0-43-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-693b306e-16e5-49a7-af51-b9e3e03d4db9' {
    menuentry 'Ubuntu, with Linux 4.15.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-43-generic-advanced-693b306e-16e5-49a7-af51-b9e3e03d4db9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  693b306e-16e5-49a7-af51-b9e3e03d4db9
        else
          search --no-floppy --fs-uuid --set=root 693b306e-16e5-49a7-af51-b9e3e03d4db9
        fi
        echo    'Loading Linux 4.15.0-43-generic ...'
            linux    /boot/vmlinuz-4.15.0-43-generic root=UUID=693b306e-16e5-49a7-af51-b9e3e03d4db9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 4.15.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-43-generic-recovery-693b306e-16e5-49a7-af51-b9e3e03d4db9' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  693b306e-16e5-49a7-af51-b9e3e03d4db9
        else
          search --no-floppy --fs-uuid --set=root 693b306e-16e5-49a7-af51-b9e3e03d4db9
        fi
        echo    'Loading Linux 4.15.0-43-generic ...'
            linux    /boot/vmlinuz-4.15.0-43-generic root=UUID=693b306e-16e5-49a7-af51-b9e3e03d4db9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 4.15.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-29-generic-advanced-693b306e-16e5-49a7-af51-b9e3e03d4db9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  693b306e-16e5-49a7-af51-b9e3e03d4db9
        else
          search --no-floppy --fs-uuid --set=root 693b306e-16e5-49a7-af51-b9e3e03d4db9
        fi
        echo    'Loading Linux 4.15.0-29-generic ...'
            linux    /boot/vmlinuz-4.15.0-29-generic root=UUID=693b306e-16e5-49a7-af51-b9e3e03d4db9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 4.15.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-29-generic-recovery-693b306e-16e5-49a7-af51-b9e3e03d4db9' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  693b306e-16e5-49a7-af51-b9e3e03d4db9
        else
          search --no-floppy --fs-uuid --set=root 693b306e-16e5-49a7-af51-b9e3e03d4db9
        fi
        echo    'Loading Linux 4.15.0-29-generic ...'
            linux    /boot/vmlinuz-4.15.0-29-generic root=UUID=693b306e-16e5-49a7-af51-b9e3e03d4db9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-29-generic
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
UUID=693b306e-16e5-49a7-af51-b9e3e03d4db9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda6 during installation
UUID=FD40-C3C7  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-lolThQ4q/Tmp_Log: No such file or directory
```

---

### Post by QIII on 2019-01-05
Hello!

I have enclosed your output in code tags to restore formatting and make your post easier to read.

When posting the results of the boot info script, it is best to save the results in plain text to [https://pastebin.ubuntu.com](https://pastebin.ubuntu.com), which I believe is given in the instructions for that script.

Cheers!

---

### Post by yancek on 2019-01-05
Both windows 10 and Ubuntu are installed in Legacy mode but you have an EFI partition which only has Ubuntu files on it (sda6).    Also, you have windows code in the MBR of both drives so you won't be able to boot from Grub until you install it  to the MBR which is the default in an Ubuntu installation.  You need to install Grub to the MBR of sda, reboot into Ubuntu and run:  sudo update-grub.

---

### Post by oldfred on 2019-01-05
You cannot have Windows in BIOS mode and Ubuntu in UEFI mode on same disk.
UEFI requires an  ESP, FAT32 with boot flag.
But Windows in BIOS mode requires boot flag on the NTFS partition with Windows boot files, your sda1.
And you can only have one boot flag per device/drive.

Use gparted to move boot flag back to sda1.  Then Windows should boot.
Make sure Windows fast start up is off. Note that Windows will turn it back on with updates, which you may not even see. Then grub will not boot system as grub only boots working Windows and if hibernation flag is set with the fast start up, then grub will not boot it. Use Windows repair disk to reset MBR to directly boot Windows and turn off fast start up or perhaps other repairs. Then use Boot-Repair to restore grub to MBR and dual boot will work.

After making sure fast start up is off, you can use Boot-Repair booted in BIOS mode to install the BIOS version of grub to MBR. 

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

