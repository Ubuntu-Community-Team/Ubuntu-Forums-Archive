---
title: "Boot problem &quot;Minimal BASH-like line editing...&quot;."
date: 2018-01-25
forum: Installation &amp; Upgrades
---

### Post by g0t0wasd on 2018-01-25
I ran sudo apt-get autoremove and apparently has broken something, since right now I get "Minimal BASH-like line ending..." message after system load. I'm able to type "exit" and system succesfully exits to BIOS settings, where I simply choose HDD and system loads properly. First I tried solution with boot-repair application, it created few entries in grub list, but hasn't solved the issue. Then I found bootinfoscript. Here is output of RESULT.TXT:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/shimx64.efi 
                       /efi/ubuntu/fbx64.efi /efi/ubuntu/fwupx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/Boot/bootx64.efi 
                       /efi/ubuntu/shimx64.efi

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,026,047     1,024,000 EFI System partition
/dev/sda2       1,026,048     7,317,503     6,291,456 Data partition (Windows/Linux)
/dev/sda3       7,317,504 1,922,238,463 1,914,920,960 Data partition (Linux)
/dev/sda4   1,922,238,464 1,953,523,711    31,285,248 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/sda1        A488-6DF3                              vfat       ESP
/dev/sda2        3610-7D86                              vfat       OS
/dev/sda3        4ccf2f6a-0f38-4801-bb6f-67311101fea1   ext4       UBUNTU
/dev/sda4        b61356c9-f06e-4d36-b2df-00624c1dce32   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda3        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda3        /var/lib/docker/overlay2 ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda3        /var/lib/docker/plugins  ext4       (rw,relatime,errors=remount-ro,data=ordered)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#########################################################
#                                                       #
# Dell Grub2 configuration file for ISO Images          #
# By: Mario Limonciello <Mario_Limonciello@Dell.com>    #
#                                                       #
#########################################################

# First check for additional options on ISO image
if [ -s /factory/common.cfg ]; then
    source /factory/common.cfg
fi

#Post RTS deliverables
if [ -s /factory/post-rts-gfx.cfg ]; then
    source /factory/post-rts-gfx.cfg
fi
if [ -s /factory/post-rts-wlan.cfg ]; then
    source /factory/post-rts-wlan.cfg
fi

# If missing, load a nice basic default set
if [ -z "${options}" ]; then
    set options="boot=casper automatic-ubiquity noprompt quiet splash nomodeset --"
fi

# Setup theme
set timeout=10
set gfxmode=auto
insmod gfxterm
terminal_output gfxterm
loadfont /boot/grub/dejavu-sans-12.pf2
loadfont /boot/grub/dejavu-sans-bold-14.pf2
insmod gfxmenu
insmod png
set theme=/boot/grub/dell/theme.txt

# Search for the RP (which contains grubenv in /factory)
search --file --set=new_root /factory/grubenv
if [ -s ($new_root)/factory/grubenv ]; then
    set have_grubenv=true
    load_env -f ($new_root)/factory/grubenv
    if [ "x${install_in_progress}" = "x1" ]; then
        set root=$new_root
        configfile ($new_root)/factory/grub.cfg
    else
        set timeout=10
        menuentry "Install Complete, remove media and reboot." {
        chainloader +1
        }
    fi
fi

#Default behavior
menuentry "Dell Recovery" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi $options
    initrd    /casper/initrd.lz
}

menuentry "Dell Recovery (safe graphics mode)" {
    set gfxpayload=keep
    linux   /casper/vmlinuz.efi $options ubiquity/force_failsafe_graphics=true
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
else
  search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
    else
      search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
    fi
    linux    /boot/vmlinuz-4.4.0-112-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-112-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
    menuentry 'Ubuntu, with Linux 4.4.0-112-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-112-generic-advanced-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
        else
          search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
        fi
        echo    'Loading Linux 4.4.0-112-generic ...'
        linux    /boot/vmlinuz-4.4.0-112-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-112-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-112-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-112-generic-init-upstart-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
        else
          search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
        fi
        echo    'Loading Linux 4.4.0-112-generic ...'
        linux    /boot/vmlinuz-4.4.0-112-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-112-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-112-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-112-generic-recovery-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
        else
          search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
        fi
        echo    'Loading Linux 4.4.0-112-generic ...'
        linux    /boot/vmlinuz-4.4.0-112-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-112-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-109-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-109-generic-advanced-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
        else
          search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
        fi
        echo    'Loading Linux 4.4.0-109-generic ...'
        linux    /boot/vmlinuz-4.4.0-109-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-109-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-109-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-109-generic-init-upstart-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
        else
          search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
        fi
        echo    'Loading Linux 4.4.0-109-generic ...'
        linux    /boot/vmlinuz-4.4.0-109-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-109-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-109-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-109-generic-recovery-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
        else
          search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
        fi
        echo    'Loading Linux 4.4.0-109-generic ...'
        linux    /boot/vmlinuz-4.4.0-109-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-109-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-36-generic-advanced-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
        else
          search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
        fi
        echo    'Loading Linux 4.4.0-36-generic ...'
        linux    /boot/vmlinuz-4.4.0-36-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-36-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-36-generic-init-upstart-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
        else
          search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
        fi
        echo    'Loading Linux 4.4.0-36-generic ...'
        linux    /boot/vmlinuz-4.4.0-36-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-36-generic-recovery-4ccf2f6a-0f38-4801-bb6f-67311101fea1' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  4ccf2f6a-0f38-4801-bb6f-67311101fea1
        else
          search --no-floppy --fs-uuid --set=root 4ccf2f6a-0f38-4801-bb6f-67311101fea1
        fi
        echo    'Loading Linux 4.4.0-36-generic ...'
        linux    /boot/vmlinuz-4.4.0-36-generic.efi.signed root=UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-36-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "EFI/ubuntu/fbx64.efi" {
search --fs-uuid --no-floppy --set=root A488-6DF3
chainloader (${root})/EFI/ubuntu/fbx64.efi
}

menuentry "EFI/ubuntu/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root A488-6DF3
chainloader (${root})/EFI/ubuntu/fwupx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root A488-6DF3
chainloader (${root})/EFI/ubuntu/mmx64.efi
}
### END /etc/grub.d/25_custom ###

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

### BEGIN /etc/grub.d/99_dell_recovery ###
menuentry "Restore Ubuntu 16.04 to factory state" {
        search --no-floppy --hint '(hd0,gpt2)' --set --fs-uuid 3610-7D86
        set uuid_options="uuid=3610-7D86"
        if [ -s /factory/common.cfg ]; then
            source /factory/common.cfg
        else
            set options="boot=casper automatic-ubiquity noprompt quiet splash nomodeset"
        fi
        if [ -s /factory/post-rts-gfx.cfg ]; then
            source /factory/post-rts-gfx.cfg
        fi
        if [ -s /factory/post-rts-wlan.cfg ]; then
            source /factory/post-rts-wlan.cfg
        fi
        #Support starting from a loopback mount (Only support ubuntu.iso for filename)
        if [ -f /ubuntu.iso ]; then
            loopback loop /ubuntu.iso
            set root=(loop)
            set options="$options iso-scan/filename=/ubuntu.iso"
        fi
        if [ -n "${lang}" ]; then
            set options="$options locale=$lang"
        fi
        if [ -s /factory/dual_enable ]; then
            set options="$options dell-recovery/dual_boot=true"
        fi 

        linux   /casper/vmlinuz.efi dell-recovery/recovery_type=hdd $uuid_options $options
    initrd    /casper/initrd.lz
}
### END /etc/grub.d/99_dell_recovery ###
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
UUID=4ccf2f6a-0f38-4801-bb6f-67311101fea1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=A488-6DF3  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda4 during installation
UUID=b61356c9-f06e-4d36-b2df-00624c1dce32 none            swap    sw              0       0
UUID=A488-6DF3    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 3e 18  |.X.MSDOS5.0...>.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 a0 0f 00 e1 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 f3 6d 88 a4 4e  4f 20 4e 41 4d 45 20 20  |..).m..NO NAME  |
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

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 1e 10  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 0f 00  |........?.......|
00000020  00 00 60 00 f1 17 00 00  00 00 00 00 02 00 00 00  |..`.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 86 7d 10 36 4e  4f 20 4e 41 4d 45 20 20  |..).}.6NO NAME  |
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


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-GokpvS1g/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-GokpvS1g/Tmp_Log: No such file or directory


```

Could you, please, help me fix it?

---

