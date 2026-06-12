---
title: "grub/os-prober can't find Windows 7 installation"
date: 2015-11-29
forum: Installation &amp; Upgrades
---

### Post by sgfallows on 2015-11-29
I'm trying to figure out why neither update-grup nor os-prober can find the Windows 7 installation on my system. This system was functioning fine for three years with a single hard drive and Windows 7 installed in a standard MBR/BIOS setup.

I've added another hard disk, installed Ubuntu 14.04 to that hard disk in a GPT/UEFI configuration. Both OSes boot and run fine, if I select the appropriate hard disk in the BIOS. (ASUS UEFI BIOS).

Now I want to use grub to select OS at boot, but can't get it to configure that. Based on read the many other posts here on the topic, I have run a chkdsk /F on the Windows install, been careful to shut is down cleanly (not hibernate) and used gparted to verify the boot flag is on the Windows partition.

Here are the results of bootinfoscript:

```
                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda2: __________________________________________________________________________


    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg


sda3: __________________________________________________________________________


    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sdb2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe


ubuntu-vg-root': _______________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


ubuntu-vg-swap_1': _____________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624     1,550,335       499,712 Data partition (Linux)
/dev/sda3       1,550,336 1,953,523,711 1,951,973,376 Logical Volume Manager (LVM) partition (Linux)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848 1,465,143,295 1,464,936,448   7 NTFS / exFAT / HPFS




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/mapper/ubuntu--vg-root 8dd3eb20-2e64-461c-95b8-3091700774db   ext4       
/dev/mapper/ubuntu--vg-swap_1 33910369-8e39-4a2f-adda-eccf5257511c   swap       
/dev/sda1        D839-4ECB                              vfat       
/dev/sda2        8506e4f0-d1dc-4d7c-8273-79364f7b1825   ext2       
/dev/sda3        vxCrMI-FK4A-HClR-wRvl-kS77-b20z-RTqM44 LVM2_member 
/dev/sdb1        AE18F3B318F378A3                       ntfs       System Reserved
/dev/sdb2        9442F4A042F487EE                       ntfs       


========================= "ls -R /dev/mapper/" output: =========================


/dev/mapper:
control
ubuntu--vg-root
ubuntu--vg-swap_1


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/mapper/ubuntu--vg-root /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda2        /boot                    ext2       (rw)
/dev/sdb2        /media/sgfallows/9442F4A042F487EE fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)




============================= sda2/grub/grub.cfg: ==============================


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
insmod lvm
insmod ext2
set root='lvmid/eayxQH-Rgxf-O5zo-J3VX-al8c-x8dT-UfotQn/6PkO1o-641f-6aHx-AwaC-1xS2-CCfu-Qfiv6T'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='lvmid/eayxQH-Rgxf-O5zo-J3VX-al8c-x8dT-UfotQn/6PkO1o-641f-6aHx-AwaC-1xS2-CCfu-Qfiv6T'  8dd3eb20-2e64-461c-95b8-3091700774db
else
  search --no-floppy --fs-uuid --set=root 8dd3eb20-2e64-461c-95b8-3091700774db
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8dd3eb20-2e64-461c-95b8-3091700774db' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  8506e4f0-d1dc-4d7c-8273-79364f7b1825
    else
      search --no-floppy --fs-uuid --set=root 8506e4f0-d1dc-4d7c-8273-79364f7b1825
    fi
    linux    /vmlinuz-3.19.0-33-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.19.0-33-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8dd3eb20-2e64-461c-95b8-3091700774db' {
    menuentry 'Ubuntu, with Linux 3.19.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-advanced-8dd3eb20-2e64-461c-95b8-3091700774db' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  8506e4f0-d1dc-4d7c-8273-79364f7b1825
        else
          search --no-floppy --fs-uuid --set=root 8506e4f0-d1dc-4d7c-8273-79364f7b1825
        fi
        echo    'Loading Linux 3.19.0-33-generic ...'
        linux    /vmlinuz-3.19.0-33-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-recovery-8dd3eb20-2e64-461c-95b8-3091700774db' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  8506e4f0-d1dc-4d7c-8273-79364f7b1825
        else
          search --no-floppy --fs-uuid --set=root 8506e4f0-d1dc-4d7c-8273-79364f7b1825
        fi
        echo    'Loading Linux 3.19.0-33-generic ...'
        linux    /vmlinuz-3.19.0-33-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-advanced-8dd3eb20-2e64-461c-95b8-3091700774db' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  8506e4f0-d1dc-4d7c-8273-79364f7b1825
        else
          search --no-floppy --fs-uuid --set=root 8506e4f0-d1dc-4d7c-8273-79364f7b1825
        fi
        echo    'Loading Linux 3.19.0-25-generic ...'
        linux    /vmlinuz-3.19.0-25-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-recovery-8dd3eb20-2e64-461c-95b8-3091700774db' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  8506e4f0-d1dc-4d7c-8273-79364f7b1825
        else
          search --no-floppy --fs-uuid --set=root 8506e4f0-d1dc-4d7c-8273-79364f7b1825
        fi
        echo    'Loading Linux 3.19.0-25-generic ...'
        linux    /vmlinuz-3.19.0-25-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-25-generic
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


=================== sda2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on ubuntu-vg-root'




Unknown BootLoader on ubuntu-vg-swap_1'






=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-R8I7k0ER/Tmp_Log: No such file or directory
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'
  Volume group name ubuntu-vg-root' has invalid characters
  Skipping volume group ubuntu-vg-root'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'
  Volume group name ubuntu-vg-root' has invalid characters
  Skipping volume group ubuntu-vg-root'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'
  Volume group name ubuntu-vg-root' has invalid characters
  Skipping volume group ubuntu-vg-root'
hexdump: /dev/mapper/ubuntu-vg-root': No such file or directory
hexdump: /dev/mapper/ubuntu-vg-root': No such file or directory
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'
  Volume group name ubuntu-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-vg-swap_1'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'
  Volume group name ubuntu-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-vg-swap_1'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'
  Volume group name ubuntu-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-vg-swap_1'
hexdump: /dev/mapper/ubuntu-vg-swap_1': No such file or directory
hexdump: /dev/mapper/ubuntu-vg-swap_1': No such file or directory



```

Is it possible the problem is using LVM?

---

### Post by oldfred on 2015-11-29
UEFI & BIOS are not compatible.
You have to reboot to switch boot modes, so from grub menu booted in UEFI mode, you cannot another install in BIOS whether Windows or another Ubuntu.

You can either convert Ubuntu to BIOS boot mode or reinstall Windows in UEFI boot mode. 
Boot-Repair can convert a UEFI install to BIOS if on gpt partitioned drive and you add a 1 or 2MB unformatted partition with the bios_grub flag, so grub can install in BIOS mode. Grub may default to installing to sda, but you want to be sure to select the Ubuntu drive and keep Windows BIOS boot loader on Windows drive. 

Was Windows originally sda? When directly booting it may be seen as first drive or sda, so it may not like being second drive. If it has issues you may need to change drive order on SATA ports so Windows is in first SATA port or SATA0.

---

### Post by sgfallows on 2015-12-20
Yes that was the problem. I was able to convert my MBR installation of Windows 7 to UEFI by following this:

[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)

One problem to note for anyone else doing this: the bcdboot command in step #17 uses the /f UEFI option. My WIndows 7 version of bcdboot does not support that option.

I happened to have a recovery USB stick handy from my Windows 8 laptop. I was able to boot from that just to perform step #17.

---

