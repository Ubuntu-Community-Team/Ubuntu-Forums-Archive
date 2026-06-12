---
title: "Can't Boot into Fedora 23 After Installing Ubuntu MATE 15.10"
date: 2016-02-06
forum: Installation &amp; Upgrades
---

### Post by spython01 on 2016-02-06
Hi Everyone.  I originally posted this in the Fedora forums but realized it may be better to post it here given the nature of the problem.  I initially installed Fedora 23 on my laptop using only about half of my drive space.  Everything was working fine.  I then installed Ubuntu MATE 15.10 on the remaining, unallocated space of my drive.  Now when I boot the laptop, it goes straight to the Ubuntu login screen with no prompt or Grub options to select between Fedora or Ubuntu.  Therefore, I can no longer boot into Fedora.

How can I restore a Grub menu upon initial boot so that I can choose between Fedora and Ubuntu?

I've messed around with my Grub configuration files in the past but with disastrous results so I thought I would seek help here before doing something stupid.  Here are some relevant details:
- I boot using traditional BIOS as [FONT=courier new]/sys/firmware/efi[/FONT] does not exist on my Ubuntu partition.
- I installed Fedora 23 first with separate boot (unencrypted), root (encrypted), home (encrypted) and swap (encrypted) partitions.
- I then installed Ubuntu MATE 15.10 with separate root (unencrypted), home (encrypted) and swap (unencrypted) partitions using the "Something else" option on the "Installation Type" screen of the Installer.
- I *believe* (but could be wrong) that [FONT=courier new]/dev/sda1[/FONT], [FONT=courier new]2[/FONT] and [FONT=courier new]3[/FONT] belong to Fedora while [FONT=courier new]/dev/sd5[/FONT], [FONT=courier new]6[/FONT] and [FONT=courier new]7[/FONT] belong to Ubuntu.

The output from [FONT=courier new]boot-repair[/FONT] can be found here:  [http://paste.ubuntu.com/14921156/](http://paste.ubuntu.com/14921156/)

I am also pasting it here if that helps.  Thanks in advance.

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub2/grub.cfg /grub2/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

fedora_new-host-3-00: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

fedora_new-host-3-01: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

fedora_new-host-3-02: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     2,099,199     2,097,152  83 Linux
/dev/sda2           2,099,200   499,156,991   497,057,792  8e Linux LVM
/dev/sda3         499,159,038   962,983,935   463,824,898   5 Extended
/dev/sda5         499,159,040   575,328,255    76,169,216  83 Linux
/dev/sda6         575,330,304   922,984,447   347,654,144  83 Linux
/dev/sda7         922,986,496   962,983,935    39,997,440  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 8b6bef0c-a414-4777-801c-9359f2f018bb   swap       
/dev/mapper/fedora_new--host--3-00 258fc2c7-3bfa-4bb0-ad69-4940632c7afe   crypto_LUKS 
/dev/mapper/fedora_new--host--3-01 996e89c2-1a7c-4a32-8352-4dad0f3f0f57   crypto_LUKS 
/dev/mapper/fedora_new--host--3-02 0a0d1cbf-3257-463b-9a74-af08ad9593e0   crypto_LUKS 
/dev/sda1        7de6123f-a492-4108-9fdc-a7619033b329   ext4       
/dev/sda2        TOXTdr-FBee-B5fB-rKrG-21pY-eQ7x-2ZkJP2 LVM2_member 
/dev/sda5        2b11c027-902d-4b23-8a25-3658e64ff41e   ext4       
/dev/sda6        3f5738db-d23b-4cd1-9439-627788056a02   ext4       
/dev/sda7        91653085-2329-469d-bdba-afbb84c5a383   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb  6 11:57 ata-SAMSUNG_MZ7LN512HCHP-000L1_S1ZKNXAGB02618 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  6 11:57 ata-SAMSUNG_MZ7LN512HCHP-000L1_S1ZKNXAGB02618-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  6 11:57 ata-SAMSUNG_MZ7LN512HCHP-000L1_S1ZKNXAGB02618-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  6 11:57 ata-SAMSUNG_MZ7LN512HCHP-000L1_S1ZKNXAGB02618-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb  6 11:57 ata-SAMSUNG_MZ7LN512HCHP-000L1_S1ZKNXAGB02618-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb  6 11:57 ata-SAMSUNG_MZ7LN512HCHP-000L1_S1ZKNXAGB02618-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Feb  6 11:57 ata-SAMSUNG_MZ7LN512HCHP-000L1_S1ZKNXAGB02618-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Feb  6 11:57 dm-name-cryptswap1 -> ../../dm-3
lrwxrwxrwx 1 root root 10 Feb  6 11:57 dm-name-fedora_new--host--3-00 -> ../../dm-2
lrwxrwxrwx 1 root root 10 Feb  6 11:57 dm-name-fedora_new--host--3-01 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Feb  6 11:57 dm-name-fedora_new--host--3-02 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Feb  6 11:57 dm-uuid-CRYPT-PLAIN-cryptswap1 -> ../../dm-3
lrwxrwxrwx 1 root root 10 Feb  6 11:57 dm-uuid-LVM-8oc19WvlIsVH3X2jwCOz1lLVUYw9swIpLd4kVmOVbCmvysB3473eb3wj3jxydUyJ -> ../../dm-0
lrwxrwxrwx 1 root root 10 Feb  6 11:57 dm-uuid-LVM-8oc19WvlIsVH3X2jwCOz1lLVUYw9swIpZP0MyPLh8xBrLizd1jEffeGvUSWn08Tx -> ../../dm-2
lrwxrwxrwx 1 root root 10 Feb  6 11:57 dm-uuid-LVM-8oc19WvlIsVH3X2jwCOz1lLVUYw9swIpjs2ULLdeKs4NvYLHe01P8N91eE5FQ8KE -> ../../dm-1
lrwxrwxrwx 1 root root 10 Feb  6 11:57 lvm-pv-uuid-TOXTdr-FBee-B5fB-rKrG-21pY-eQ7x-2ZkJP2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Feb  6 11:57 wwn-0x5002538d00000000 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  6 11:57 wwn-0x5002538d00000000-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  6 11:57 wwn-0x5002538d00000000-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  6 11:57 wwn-0x5002538d00000000-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb  6 11:57 wwn-0x5002538d00000000-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb  6 11:57 wwn-0x5002538d00000000-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Feb  6 11:57 wwn-0x5002538d00000000-part7 -> ../../sda7

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1
fedora_new--host--3-00
fedora_new--host--3-01
fedora_new--host--3-02

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda6        /home                    ext4       (rw,relatime,data=ordered)


============================= sda1/grub2/grub.cfg: =============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub2-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set pager=1

if [ -s $prefix/grubenv ]; then
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="${saved_entry}"
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

terminal_output console
if [ x$feature_timeout_style = xy ] ; then
  set timeout_style=menu
  set timeout=5
# Fallback normal timeout code in case the timeout_style feature is
# unavailable.
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/01_users ###
if [ -f ${prefix}/user.cfg ]; then
  source ${prefix}/user.cfg
  if [ -n ${GRUB2_PASSWORD} ]; then
    set superusers="root"
    export superusers
    password_pbkdf2 root ${GRUB2_PASSWORD}
  fi
fi
### END /etc/grub.d/01_users ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Fedora (4.2.3-300.fc23.x86_64) 23 (Workstation Edition)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-4.2.3-300.fc23.x86_64-advanced-b27d7fac-45e1-4cbc-85c7-76dab2a38562' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  7de6123f-a492-4108-9fdc-a7619033b329
    else
      search --no-floppy --fs-uuid --set=root 7de6123f-a492-4108-9fdc-a7619033b329
    fi
    linux16 /vmlinuz-4.2.3-300.fc23.x86_64 root=/dev/mapper/luks-258fc2c7-3bfa-4bb0-ad69-4940632c7afe ro rd.lvm.lv=fedora_new-host-3/00 rd.luks.uuid=luks-258fc2c7-3bfa-4bb0-ad69-4940632c7afe rd.lvm.lv=fedora_new-host-3/02 rd.luks.uuid=luks-0a0d1cbf-3257-463b-9a74-af08ad9593e0 rhgb quiet LANG=en_US.UTF-8
    initrd16 /initramfs-4.2.3-300.fc23.x86_64.img
}
menuentry 'Fedora (0-rescue-2b10e3724f624a13b04f2a7dafa43e68) 23 (Workstation Edition)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-0-rescue-2b10e3724f624a13b04f2a7dafa43e68-advanced-b27d7fac-45e1-4cbc-85c7-76dab2a38562' {
    load_video
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  7de6123f-a492-4108-9fdc-a7619033b329
    else
      search --no-floppy --fs-uuid --set=root 7de6123f-a492-4108-9fdc-a7619033b329
    fi
    linux16 /vmlinuz-0-rescue-2b10e3724f624a13b04f2a7dafa43e68 root=/dev/mapper/luks-258fc2c7-3bfa-4bb0-ad69-4940632c7afe ro rd.lvm.lv=fedora_new-host-3/00 rd.luks.uuid=luks-258fc2c7-3bfa-4bb0-ad69-4940632c7afe rd.lvm.lv=fedora_new-host-3/02 rd.luks.uuid=luks-0a0d1cbf-3257-463b-9a74-af08ad9593e0 rhgb quiet
    initrd16 /initramfs-0-rescue-2b10e3724f624a13b04f2a7dafa43e68.img
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_ppc_terminfo ###
### END /etc/grub.d/20_ppc_terminfo ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

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

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 extlinux/cat.c32                   :  not a COM32/COM32R module
 extlinux/chain.c32                 :  not a COM32/COM32R module
 extlinux/cmd.c32                   :  not a COM32/COM32R module
 extlinux/cmenu.c32                 :  not a COM32/COM32R module
 extlinux/config.c32                :  not a COM32/COM32R module
 extlinux/cptime.c32                :  not a COM32/COM32R module
 extlinux/cpu.c32                   :  not a COM32/COM32R module
 extlinux/cpuid.c32                 :  not a COM32/COM32R module
 extlinux/cpuidtest.c32             :  not a COM32/COM32R module
 extlinux/debug.c32                 :  not a COM32/COM32R module
 extlinux/dhcp.c32                  :  not a COM32/COM32R module
 extlinux/disk.c32                  :  not a COM32/COM32R module
 extlinux/dmi.c32                   :  not a COM32/COM32R module
 extlinux/dmitest.c32               :  not a COM32/COM32R module
 extlinux/elf.c32                   :  not a COM32/COM32R module
 extlinux/ethersel.c32              :  not a COM32/COM32R module
 extlinux/gfxboot.c32               :  not a COM32/COM32R module
 extlinux/gpxecmd.c32               :  not a COM32/COM32R module
 extlinux/hdt.c32                   :  not a COM32/COM32R module
 extlinux/hexdump.c32               :  not a COM32/COM32R module
 extlinux/host.c32                  :  not a COM32/COM32R module
 extlinux/ifcpu.c32                 :  not a COM32/COM32R module
 extlinux/ifcpu64.c32               :  not a COM32/COM32R module
 extlinux/ifmemdsk.c32              :  not a COM32/COM32R module
 extlinux/ifplop.c32                :  not a COM32/COM32R module
 extlinux/kbdmap.c32                :  not a COM32/COM32R module
 extlinux/kontron_wdt.c32           :  not a COM32/COM32R module
 extlinux/ldlinux.c32               :  not a COM32/COM32R module
 extlinux/lfs.c32                   :  not a COM32/COM32R module
 extlinux/libcom32.c32              :  not a COM32/COM32R module
 extlinux/libgpl.c32                :  not a COM32/COM32R module
 extlinux/liblua.c32                :  not a COM32/COM32R module
 extlinux/libmenu.c32               :  not a COM32/COM32R module
 extlinux/libutil.c32               :  not a COM32/COM32R module
 extlinux/linux.c32                 :  not a COM32/COM32R module
 extlinux/ls.c32                    :  not a COM32/COM32R module
 extlinux/lua.c32                   :  not a COM32/COM32R module
 extlinux/mboot.c32                 :  not a COM32/COM32R module
 extlinux/meminfo.c32               :  not a COM32/COM32R module
 extlinux/menu.c32                  :  not a COM32/COM32R module
 extlinux/pci.c32                   :  not a COM32/COM32R module
 extlinux/pcitest.c32               :  not a COM32/COM32R module
 extlinux/pmload.c32                :  not a COM32/COM32R module
 extlinux/poweroff.c32              :  not a COM32/COM32R module
 extlinux/prdhcp.c32                :  not a COM32/COM32R module
 extlinux/pwd.c32                   :  not a COM32/COM32R module
 extlinux/pxechn.c32                :  not a COM32/COM32R module
 extlinux/reboot.c32                :  not a COM32/COM32R module
 extlinux/rosh.c32                  :  not a COM32/COM32R module
 extlinux/sanboot.c32               :  not a COM32/COM32R module
 extlinux/sdi.c32                   :  not a COM32/COM32R module
 extlinux/sysdump.c32               :  not a COM32/COM32R module
 extlinux/syslinux.c32              :  not a COM32/COM32R module
 extlinux/vesa.c32                  :  not a COM32/COM32R module
 extlinux/vesainfo.c32              :  not a COM32/COM32R module
 extlinux/vesamenu.c32              :  not a COM32/COM32R module
 extlinux/vpdtest.c32               :  not a COM32/COM32R module
 extlinux/whichsys.c32              :  not a COM32/COM32R module
 extlinux/zzjson.c32                :  not a COM32/COM32R module

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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  2b11c027-902d-4b23-8a25-3658e64ff41e
else
  search --no-floppy --fs-uuid --set=root 2b11c027-902d-4b23-8a25-3658e64ff41e
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
if background_color 60,59,55; then
  clear
fi

color_normal=light-gray/black

if [ -e ${prefix}/themes/ubuntu-mate/theme.txt ]; then
  insmod png
  theme=${prefix}/themes/ubuntu-mate/theme.txt
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2b11c027-902d-4b23-8a25-3658e64ff41e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  2b11c027-902d-4b23-8a25-3658e64ff41e
    else
      search --no-floppy --fs-uuid --set=root 2b11c027-902d-4b23-8a25-3658e64ff41e
    fi
    linux    /boot/vmlinuz-4.2.0-27-generic root=UUID=2b11c027-902d-4b23-8a25-3658e64ff41e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.2.0-27-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2b11c027-902d-4b23-8a25-3658e64ff41e' {
    menuentry 'Ubuntu, with Linux 4.2.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-27-generic-advanced-2b11c027-902d-4b23-8a25-3658e64ff41e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  2b11c027-902d-4b23-8a25-3658e64ff41e
        else
          search --no-floppy --fs-uuid --set=root 2b11c027-902d-4b23-8a25-3658e64ff41e
        fi
        echo    'Loading Linux 4.2.0-27-generic ...'
        linux    /boot/vmlinuz-4.2.0-27-generic root=UUID=2b11c027-902d-4b23-8a25-3658e64ff41e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-27-generic-recovery-2b11c027-902d-4b23-8a25-3658e64ff41e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  2b11c027-902d-4b23-8a25-3658e64ff41e
        else
          search --no-floppy --fs-uuid --set=root 2b11c027-902d-4b23-8a25-3658e64ff41e
        fi
        echo    'Loading Linux 4.2.0-27-generic ...'
        linux    /boot/vmlinuz-4.2.0-27-generic root=UUID=2b11c027-902d-4b23-8a25-3658e64ff41e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-16-generic-advanced-2b11c027-902d-4b23-8a25-3658e64ff41e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  2b11c027-902d-4b23-8a25-3658e64ff41e
        else
          search --no-floppy --fs-uuid --set=root 2b11c027-902d-4b23-8a25-3658e64ff41e
        fi
        echo    'Loading Linux 4.2.0-16-generic ...'
        linux    /boot/vmlinuz-4.2.0-16-generic root=UUID=2b11c027-902d-4b23-8a25-3658e64ff41e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-16-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-16-generic-recovery-2b11c027-902d-4b23-8a25-3658e64ff41e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  2b11c027-902d-4b23-8a25-3658e64ff41e
        else
          search --no-floppy --fs-uuid --set=root 2b11c027-902d-4b23-8a25-3658e64ff41e
        fi
        echo    'Loading Linux 4.2.0-16-generic ...'
        linux    /boot/vmlinuz-4.2.0-16-generic root=UUID=2b11c027-902d-4b23-8a25-3658e64ff41e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-16-generic
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  2b11c027-902d-4b23-8a25-3658e64ff41e
    else
      search --no-floppy --fs-uuid --set=root 2b11c027-902d-4b23-8a25-3658e64ff41e
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  2b11c027-902d-4b23-8a25-3658e64ff41e
    else
      search --no-floppy --fs-uuid --set=root 2b11c027-902d-4b23-8a25-3658e64ff41e
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
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
UUID=2b11c027-902d-4b23-8a25-3658e64ff41e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=3f5738db-d23b-4cd1-9439-627788056a02 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
#UUID=91653085-2329-469d-bdba-afbb84c5a383 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on fedora_new-host-3-00


Unknown BootLoader on fedora_new-host-3-01


Unknown BootLoader on fedora_new-host-3-02



=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 9 (/proc/19656/mounts) leaked on lvs invocation. Parent PID 28998: bash
File descriptor 63 (pipe:[52021]) leaked on lvs invocation. Parent PID 28998: bash
File descriptor 9 (/proc/19656/mounts) leaked on lvchange invocation. Parent PID 30212: bash
File descriptor 63 (pipe:[52021]) leaked on lvchange invocation. Parent PID 30212: bash
  skip_dev_dir: Couldn't split up device name fedora_new-host-3-00.
  Volume group "fedora_new-host-3-00" not found
  Cannot process volume group fedora_new-host-3-00
hexdump: /dev/mapper/fedora_new-host-3-00: No such file or directory
hexdump: /dev/mapper/fedora_new-host-3-00: No such file or directory
File descriptor 9 (/proc/19656/mounts) leaked on lvchange invocation. Parent PID 30212: bash
File descriptor 63 (pipe:[52021]) leaked on lvchange invocation. Parent PID 30212: bash
  skip_dev_dir: Couldn't split up device name fedora_new-host-3-01.
  Volume group "fedora_new-host-3-01" not found
  Cannot process volume group fedora_new-host-3-01
hexdump: /dev/mapper/fedora_new-host-3-01: No such file or directory
hexdump: /dev/mapper/fedora_new-host-3-01: No such file or directory
File descriptor 9 (/proc/19656/mounts) leaked on lvchange invocation. Parent PID 30212: bash
File descriptor 63 (pipe:[52021]) leaked on lvchange invocation. Parent PID 30212: bash
  skip_dev_dir: Couldn't split up device name fedora_new-host-3-02.
  Volume group "fedora_new-host-3-02" not found
  Cannot process volume group fedora_new-host-3-02
hexdump: /dev/mapper/fedora_new-host-3-02: No such file or directory
hexdump: /dev/mapper/fedora_new-host-3-02: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-02-06__11h57 ===================
boot-repair version : 4ppa35
boot-sav version : 4ppa35
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa35
BLKID BEFORE LVM ACTIVATION:
/dev/sda1: UUID="7de6123f-a492-4108-9fdc-a7619033b329" TYPE="ext4" PARTUUID="ffb50088-01"
/dev/sda2: UUID="TOXTdr-FBee-B5fB-rKrG-21pY-eQ7x-2ZkJP2" TYPE="LVM2_member" PARTUUID="ffb50088-02"
/dev/sda5: UUID="2b11c027-902d-4b23-8a25-3658e64ff41e" TYPE="ext4" PARTUUID="ffb50088-05"
/dev/sda6: UUID="3f5738db-d23b-4cd1-9439-627788056a02" TYPE="ext4" PARTUUID="ffb50088-06"
/dev/sda7: UUID="91653085-2329-469d-bdba-afbb84c5a383" TYPE="swap" PARTUUID="ffb50088-07"
/dev/mapper/fedora_new--host--3-02: UUID="0a0d1cbf-3257-463b-9a74-af08ad9593e0" TYPE="crypto_LUKS"
/dev/mapper/fedora_new--host--3-01: UUID="996e89c2-1a7c-4a32-8352-4dad0f3f0f57" TYPE="crypto_LUKS"
/dev/mapper/fedora_new--host--3-00: UUID="258fc2c7-3bfa-4bb0-ad69-4940632c7afe" TYPE="crypto_LUKS"
/dev/mapper/cryptswap1: UUID="8b6bef0c-a414-4777-801c-9359f2f018bb" TYPE="swap"
MODPROBE
VGSCAN
File descriptor 9 (/proc/19656/mounts) leaked on vgscan invocation. Parent PID 19664: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "fedora_new-host-3" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/19656/mounts) leaked on vgchange invocation. Parent PID 19664: /bin/bash
3 logical volume(s) in volume group "fedora_new-host-3" now active
File descriptor 9 (/proc/19656/mounts) leaked on lvscan invocation. Parent PID 19664: /bin/bash
LVSCAN:
ACTIVE            '/dev/fedora_new-host-3/02' [20.00 GiB] inherit
ACTIVE            '/dev/fedora_new-host-3/01' [178.00 GiB] inherit
ACTIVE            '/dev/fedora_new-host-3/00' [39.00 GiB] inherit
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Is there RAID on this computer? no
File descriptor 9 (/proc/19656/mounts) leaked on lvs invocation. Parent PID 21455: /bin/sh
Error: /dev/mapper/fedora_new--host--3-00: unrecognised disk label
Error: /dev/mapper/fedora_new--host--3-01: unrecognised disk label
Error: /dev/mapper/fedora_new--host--3-02: unrecognised disk label
Error: /dev/mapper/fedora_new--host--3-00: unrecognised disk label
Error: /dev/mapper/fedora_new--host--3-01: unrecognised disk label
Error: /dev/mapper/fedora_new--host--3-02: unrecognised disk label
boot-repair is executed in installed-session (Ubuntu 15.10, wily, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.2.0-27-generic root=UUID=2b11c027-902d-4b23-8a25-3658e64ff41e ro quiet splash vt.handoff=7
Set sda as corresponding disk of mapper/fedora_new--host--3-02
Set sda as corresponding disk of mapper/fedora_new--host--3-01
Set sda as corresponding disk of mapper/fedora_new--host--3-00
Set sda as corresponding disk of mapper/fedora_new--host--3-02
Set sda as corresponding disk of mapper/fedora_new--host--3-01
Set sda as corresponding disk of mapper/fedora_new--host--3-00
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mapper/fedora_new--host--3-02 : Error code 32
mount -r /dev/mapper/fedora_new--host--3-02 /mnt/boot-sav/mapper/fedora_new--host--3-02
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mapper/fedora_new--host--3-02 : Error code 32
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mapper/fedora_new--host--3-01 : Error code 32
mount -r /dev/mapper/fedora_new--host--3-01 /mnt/boot-sav/mapper/fedora_new--host--3-01
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mapper/fedora_new--host--3-01 : Error code 32
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mapper/fedora_new--host--3-00 : Error code 32
mount -r /dev/mapper/fedora_new--host--3-00 /mnt/boot-sav/mapper/fedora_new--host--3-00
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mapper/fedora_new--host--3-00 : Error code 32

=================== os-prober:
/dev/sda5:The OS now in use - Ubuntu 15.10 CurrentSession:linux

=================== blkid:
/dev/sda1: UUID="7de6123f-a492-4108-9fdc-a7619033b329" TYPE="ext4" PARTUUID="ffb50088-01"
/dev/sda2: UUID="TOXTdr-FBee-B5fB-rKrG-21pY-eQ7x-2ZkJP2" TYPE="LVM2_member" PARTUUID="ffb50088-02"
/dev/sda5: UUID="2b11c027-902d-4b23-8a25-3658e64ff41e" TYPE="ext4" PARTUUID="ffb50088-05"
/dev/sda6: UUID="3f5738db-d23b-4cd1-9439-627788056a02" TYPE="ext4" PARTUUID="ffb50088-06"
/dev/sda7: UUID="91653085-2329-469d-bdba-afbb84c5a383" TYPE="swap" PARTUUID="ffb50088-07"
/dev/mapper/fedora_new--host--3-02: UUID="0a0d1cbf-3257-463b-9a74-af08ad9593e0" TYPE="crypto_LUKS"
/dev/mapper/fedora_new--host--3-01: UUID="996e89c2-1a7c-4a32-8352-4dad0f3f0f57" TYPE="crypto_LUKS"
/dev/mapper/fedora_new--host--3-00: UUID="258fc2c7-3bfa-4bb0-ad69-4940632c7afe" TYPE="crypto_LUKS"
/dev/mapper/cryptswap1: UUID="8b6bef0c-a414-4777-801c-9359f2f018bb" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mapper/fedora_new--host--3-02 : Error code 32
mount -r /dev/mapper/fedora_new--host--3-02 /mnt/boot-sav/mapper/fedora_new--host--3-02
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mapper/fedora_new--host--3-02 : Error code 32
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mapper/fedora_new--host--3-01 : Error code 32
mount -r /dev/mapper/fedora_new--host--3-01 /mnt/boot-sav/mapper/fedora_new--host--3-01
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mapper/fedora_new--host--3-01 : Error code 32
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mapper/fedora_new--host--3-00 : Error code 32
mount -r /dev/mapper/fedora_new--host--3-00 /mnt/boot-sav/mapper/fedora_new--host--3-00
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mapper/fedora_new--host--3-00 : Error code 32

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Feb  5 22:36 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Oct 14 12:36 00_header
-rwxr-xr-x 1 root root  6058 Sep  4 07:13 05_debian_theme
-rwxr-xr-x 1 root root 12261 Oct 14 12:36 10_linux
-rwxr-xr-x 1 root root 11082 Oct 14 12:36 20_linux_xen
-rwxr-xr-x 1 root root  1992 Aug 27 09:04 20_memtest86+
-rwxr-xr-x 1 root root 11692 Oct 14 12:36 30_os-prober
-rwxr-xr-x 1 root root  1418 Oct 14 12:36 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 14 12:36 40_custom
-rwxr-xr-x 1 root root   216 Oct 14 12:36 41_custom
-rw-r--r-- 1 root root   483 Oct 14 12:36 README




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




=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
EFI in dmesg.
[    0.000000] ACPI: UEFI 0x00000000BCDD7000 000042 (v01 LENOVO TP-JB    00001190 PTEC 00000002)
[    0.000000] ACPI: UEFI 0x00000000BCDD4000 0002E2 (v01 LENOVO TP-JB    00001190 PTEC 00000002)
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    is-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda6    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.
mapper/fedora_new--host--3-02    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mapper/fedora_new--host--3-02.
mapper/fedora_new--host--3-01    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mapper/fedora_new--host--3-01.
mapper/fedora_new--host--3-00    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mapper/fedora_new--host--3-00.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA SAMSUNG MZ7LN512 (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type      File system     Flags
1      1049kB  1075MB  1074MB  primary   ext4            boot
2      1075MB  256GB   254GB   primary                   lvm
3      256GB   493GB   237GB   extended
5      256GB   295GB   39.0GB  logical   ext4
6      295GB   473GB   178GB   logical   ext4
7      473GB   493GB   20.5GB  logical   linux-swap(v1)


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 20.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system     Flags
1      0.00B  20.5GB  20.5GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora_new--host--3-00: 41.9GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora_new--host--3-01: 191GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora_new--host--3-02: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

=================== parted -lm:

BYT;
/dev/sda:512GB:scsi:512:512:msdos:ATA SAMSUNG MZ7LN512:;
1:1049kB:1075MB:1074MB:ext4::boot;
2:1075MB:256GB:254GB:::lvm;
3:256GB:493GB:237GB:::;
5:256GB:295GB:39.0GB:ext4::;
6:295GB:473GB:178GB:ext4::;
7:473GB:493GB:20.5GB:linux-swap(v1)::;

BYT;
/dev/mapper/cryptswap1:20.5GB:dm:512:512:loop:Linux device-mapper (crypt):;
1:0.00B:20.5GB:20.5GB:linux-swap(v1)::;

BYT;
/dev/mapper/fedora_new--host--3-00:41.9GB:dm:512:512:unknown:Linux device-mapper (linear):;

BYT;
/dev/mapper/fedora_new--host--3-01:191GB:dm:512:512:unknown:Linux device-mapper (linear):;

BYT;
/dev/mapper/fedora_new--host--3-02:21.5GB:dm:512:512:unknown:Linux device-mapper (linear):;

=================== lsblk:
KNAME TYPE  FSTYPE        SIZE LABEL
sda   disk                477G
sda1  part  ext4            1G
sda2  part  LVM2_member   237G
dm-0  lvm   crypto_LUKS    20G
dm-1  lvm   crypto_LUKS   178G
dm-2  lvm   crypto_LUKS    39G
sda3  part                  1K
sda5  part  ext4         36.3G
sda6  part  ext4        165.8G
sda7  part  swap         19.1G
dm-3  crypt swap         19.1G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      0  0  0 running
sda1     0  0  0         /mnt/boot-sav/sda1
sda2     0  0  0
dm-0     0  0  0 running
dm-1     0  0  0 running
dm-2     0  0  0 running
sda3     0  0  0
sda5     0  0  0         /
sda6     0  0  0         /home
sda7     0  0  0
dm-3     0  0  0 running [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=10109456k,nr_inodes=2527364,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=2025444k,mode=755)
/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=22,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda6 on /home type ext4 (rw,relatime,data=ordered)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=2025444k,mode=700,uid=1000,gid=1000)
/home/.ecryptfs/samir/.Private on /home/samir type ecryptfs (rw,nosuid,nodev,relatime,ecryptfs_fnek_sig=e274c726cc4bd67e,ecryptfs_sig=d8f958606e8dc1a8,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw,relatime,data=ordered)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-2 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-3 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 dm-2 dm-3 dri ecryptfs fb0 fd fedora_new-host-3 full fuse hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 initctl input kmsg kvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue ndctl0 net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sda7 sg0 shm snapshot snd stderr stdin stdout tpm0 uhid uinput urandom v4l vfio vga_arbiter vhci vhost-net video0 watchdog watchdog0 xconsole zero
ls /dev/mapper:  control cryptswap1 fedora_new--host--3-00 fedora_new--host--3-01 fedora_new--host--3-02
ls: cannot access : No such file or directory

=================== df -Th:

Filesystem           Type      Size  Used Avail Use% Mounted on
udev                 devtmpfs  9.7G     0  9.7G   0% /dev
tmpfs                tmpfs     2.0G  9.4M  2.0G   1% /run
/dev/sda5            ext4       36G  4.0G   30G  12% /
tmpfs                tmpfs     9.7G  280K  9.7G   1% /dev/shm
tmpfs                tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                tmpfs     9.7G     0  9.7G   0% /sys/fs/cgroup
/dev/sda6            ext4      164G  118M  155G   1% /home
tmpfs                tmpfs     2.0G   32K  2.0G   1% /run/user/1000
/home/samir/.Private ecryptfs  164G  118M  155G   1% /home/samir
/dev/sda1            ext4      976M  108M  801M  12% /mnt/boot-sav/sda1

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


Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xffb50088

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048   2099199   2097152     1G 83 Linux
/dev/sda2         2099200 499156991 497057792   237G 8e Linux LVM
/dev/sda3       499159038 962983935 463824898 221.2G  5 Extended
/dev/sda5       499159040 575328255  76169216  36.3G 83 Linux
/dev/sda6       575330304 922984447 347654144 165.8G 83 Linux
/dev/sda7       922986496 962983935  39997440  19.1G 82 Linux swap / Solaris


Disk /dev/mapper/fedora_new--host--3-02: 20 GiB, 21479030784 bytes, 41951232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/fedora_new--host--3-01: 178 GiB, 191130238976 bytes, 373301248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/fedora_new--host--3-00: 39 GiB, 41875931136 bytes, 81788928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/cryptswap1: 19.1 GiB, 20478164992 bytes, 39996416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.


=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to enable-lvm) and reinstall the grub2 of sda5 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems


=================== Advice in case of suggested repair
You may want to retry after decrypting your partitions. (https://help.ubuntu.com/community/EncryptedPrivateDirectory)
Do you want to continue?


=================== Final advice in case of suggested repair


The boot files of [The OS now in use - Ubuntu 15.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)


=================== User settings
The settings chosen by the user will not act on the boot.

```

**UPDATE:**  See how to solve this in this [post]("http://ubuntuforums.org/showthread.php?t=2312703&page=2&p=13438949#post13438949").

---

### Post by oldfred on 2016-02-06
Is your Fedora encrypted also? It looks like it from Summary report.

Ubuntu uncrypted install does not have LVM nor encrypt drivers. You need to install those and mount the encrypted partition from Ubuntu, so os-prober can see the Fedora install.

       To get Ubuntu to see different encrypted install, but use your partition and encrypted partition name:
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sdb2 my-crypt
sudo os-prober
sudo update-grub

---

### Post by spython01 on 2016-02-06
> **oldfred said:**
> Is your Fedora encrypted also? It looks like it from Summary report.

Yes, you are correct -- my Fedora partitions (root, home and swap) are encrypted.  The boot partition is not.

> **oldfred said:**
> To get Ubuntu to see different encrypted install, but use your partition and encrypted partition name:
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sdb2 my-crypt
sudo os-prober
sudo update-grub

When running these commands, I got the following error message here:
```
$ sudo cryptsetup luksOpen /dev/sdb2 my-crypt
Device /dev/sdb2 doesn't exist or access denied.
```

Should the partition I use be [FONT=courier new]sda2[/FONT] instead of [FONT=courier new]sdb2[/FONT]?

Out of curiosity, what is this command doing?

Will this update my Grub to Grub2?

Thanks again for the quick reply!

---

### Post by oldfred on 2016-02-06
You need to mount & open your encrypted partition as grub has to see /boot & / partition.

Not sure of exact commands if those are not correct. But it looks like sda2 is correct. The post was just an example not your exact commands.

Afraid I do not know LVM nor encryption and am just trying to help by copying some commands posted elsewhere that supposedly worked.

 sudo pvs
sudo vgs
sudo lvs
ls -l /dev/mapper

---

### Post by spython01 on 2016-02-08
So here is what I got:
```
$ sudo cryptsetup luksOpen /dev/sda2 my-crypt
Device /dev/sda2 is not a valid LUKS device.

$ sudo pvs
  PV         VG                Fmt  Attr PSize   PFree
  /dev/sda2  fedora_new-host-3 lvm2 a--  237.01g 4.00m

$ sudo vgs
  VG                #PV #LV #SN Attr   VSize   VFree
  fedora_new-host-3   1   3   0 wz--n- 237.01g 4.00m

$ sudo lvs
  LV   VG                Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  00   fedora_new-host-3 -wi-a-----  39.00g                                                    
  01   fedora_new-host-3 -wi-a----- 178.00g                                                    
  02   fedora_new-host-3 -wi-a-----  20.00g

$ ls -l /dev/mapper
total 0
crw------- 1 root root 10, 236 Feb  8 20:17 control
lrwxrwxrwx 1 root root       7 Feb  8 20:17 cryptswap1 -> ../dm-3
lrwxrwxrwx 1 root root       7 Feb  8 20:17 fedora_new--host--3-00 -> ../dm-2
lrwxrwxrwx 1 root root       7 Feb  8 20:17 fedora_new--host--3-01 -> ../dm-1
lrwxrwxrwx 1 root root       7 Feb  8 20:17 fedora_new--host--3-02 -> ../dm-0
```

Any suggestions for next steps?

Thanks!

---

### Post by oldfred on 2016-02-09
I do not know LVM, but this maybe should be the VG name not the PV device?

sudo cryptsetup luksOpen /dev/sdb2 my-crypt
sudo cryptsetup luksOpen fedora_new-host-3 my-crypt

[http://www.linuxwave.info/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://www.linuxwave.info/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

---

### Post by spython01 on 2016-02-10
> **oldfred said:**
> I do not know LVM, but this maybe should be the VG name not the PV device?

sudo cryptsetup luksOpen /dev/sdb2 my-crypt
sudo cryptsetup luksOpen fedora_new-host-3 my-crypt

[http://www.linuxwave.info/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://www.linuxwave.info/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

I tried the following:
```
$ sudo cryptsetup luksOpen /dev/sda2 my-crypt
Device /dev/sda2 is not a valid LUKS device.
$ sudo cryptsetup luksOpen fedora_new-host-3 my-crypt
Device fedora_new-host-3 doesn't exist or access denied.

```
I then tried [FONT=courier new]sudo cryptsetup luksOpen /dev/fedora_new-host-3 my-crypt[/FONT] which didn't return any messages or output.  Based on [these]("http://ubuntuforums.org/showthread.php?t=611165") [pages]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html"), I thought I would be prompted for my passphase used to decrypt my Fedora partition.  I went ahead and followed the other directions listed there anyway and here is what I got:

```
$ sudo vgscan --mknodes
  Reading all physical volumes.  This may take a while...
  Found volume group "fedora_new-host-3" using metadata type lvm2
$ sudo vgchange -ay
  3 logical volume(s) in volume group "fedora_new-host-3" now active
$ sudo lvscan --all
  ACTIVE            '/dev/fedora_new-host-3/02' [20.00 GiB] inherit
  ACTIVE            '/dev/fedora_new-host-3/01' [178.00 GiB] inherit
  ACTIVE            '/dev/fedora_new-host-3/00' [39.00 GiB] inherit
$ sudo mount /dev/fedora_new-host-3/ /mnt
mount:  /dev/fedora_new-host-3 is not a block device

```

Please note that I am doing all of this from my Ubuntu partition, and not from a Live CD.  I even ran [FONT=courier new]sudo update-grub[/FONT] but don't think it did anything:
```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done 
```

I'm beginng to wonder if what I am trying to do -- dual boot both and encrypted Fedora and an encrypted Ubuntu parition -- is even possible.  :confused:

---

### Post by oldfred on 2016-02-10
Still do not know LVM.
But is not this the entire "drive"
fedora_new-host-3

And you want to mount the / partition? or:
/dev/mapper/fedora_new--host--3-01

But again, which is your encrypted partition? Or is entire "drive" encrypted. I do not know details.

---

### Post by spython01 on 2016-02-12
> **oldfred said:**
> Still do not know LVM.
But is not this the entire "drive"
fedora_new-host-3

And you want to mount the / partition? or:
/dev/mapper/fedora_new--host--3-01

But again, which is your encrypted partition? Or is entire "drive" encrypted. I do not know details.

Only certain partitions within my drive are encrypted.  Looking at this  GParted screenshot, /dev/sda1 and sda2 are for Fedora.  sda1 was the  boot partition and sda2 is the encrypted Fedora partition containing  everything else.  It looks like sd3-7 belong to Ubuntu.

[IMG]http://i.imgur.com/sctm8cw.png?1[/IMG]

I'm not trying to mount or access Fedora from Ubuntu.  I just want a  Grub menu to appear at boot that allows me to select between Fedora and  Ubuntu.

---

### Post by oldfred on 2016-02-12
While this discusses resizing, its first 4 steps are mounting.
Go thru steps 1 thru 4 which I thought I posted & you ran above.

[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)
You can now manage your encrypted partitions, mount them, copy them, or perform maintenance (fsck, backup, resize).

Older versions:
 HowTo: add Fedora 15 to Maverick Grub 2
[http://ubuntuforums.org/showthread.php?t=1714170](http://ubuntuforums.org/showthread.php?t=1714170)
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27 chainload
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)

Or can you look in Fedora's grub for its boot stanza and copy into Ubuntu's grub 40_custom?

---

### Post by spython01 on 2016-02-12
I think I finally figured it out!!!  I haven't completely solved it but I am much closer.  Here is what I did:

I copied lines 239 through 267 from my [[FONT=courier new]boot-repair[/FONT]]("http://paste.ubuntu.com/14921156/") output.  I believe these are the Fedora [FONT=courier new]menuentry[/FONT] items that originally existed in the [FONT=courier new]/etc/grub.d/10_linux[/FONT] file on sda1 (boot partition) when I first installed Fedora.

Because Ubuntu installs its own version of Grub, my laptop was no longer seeing these items on sda1.  (Perhaps my current Ubuntu Grub2 resides on [FONT=courier new]sda5[/FONT] but I'm not sure.)

I then pasted those lines into my [FONT=courier new]/etc/grub.d/40_custom[/FONT] file which I believe is on [FONT=courier new]sda5[/FONT] -- essentially where line 636 is in my [FONT=courier new]boot-repair[/FONT] output.

Finally, I ran [FONT=courier new]sudo update-grub2[/FONT].

Only 2 issues I have now:

(1) I have to press the right-shift key to get the Grub menu to appear upon bootup after which I can select between Fedora and Ubuntu.
(2) What happens if I update my kernel?

Anyway, huge thank you to oldfred for getting me this far!!  :p

---

### Post by spython01 on 2016-02-12
> **spython01 said:**
> (1) I have to press the right-shift key to get the Grub menu to appear upon bootup after which I can select between Fedora and Ubuntu.

I fixed this too.  I changed the line [FONT=courier new]GRUB_HIDDENT_TIMEOUT=0[/FONT] to [FONT=courier new]GRUB_HIDDENT_TIMEOUT= [FONT=arial]within my [FONT=courier new]/etc/default/grub[/FONT] file.[/FONT]
[/FONT]
(I just deleted the zero per the instructions posted [here]("https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries").)

---

### Post by Dennis N on 2016-02-12
> Only 2 issues I have now:

(1) I have to press the right-shift key to get the Grub menu to appear upon bootup after which I can select between Fedora and Ubuntu.
(2) What happens if I update my kernel?


#2:

I assume you have Ubuntu grub booting to Fedora (did not read your entire thread). Then, when Fedora has a kernel update (there will be lots of them) you need to update grub from Ubuntu each time that happens. That's because the exact Fedora kernel version is in the Ubuntu grub menu entry and it won't magically change when Fedora updates.

A new Fedora is released about every 6 mos. Any Fedora is supported until the second release after yours, giving you about a year of support. There is no LTS.

---

### Post by spython01 on 2016-02-12
> **Dennis N said:**
> #2:

I assume you have Ubuntu grub booting to Fedora (did not read your entire thread). Then, when Fedora has a kernel update (there will be lots of them) you need to update grub from Ubuntu each time that happens. That's because the exact Fedora kernel version is in the Ubuntu grub menu entry and it won't magically change when Fedora updates.

A new Fedora is released about every 6 mos. Any Fedora is supported until the second release after yours, giving you about a year of support. There is no LTS.

Is the update to Grub required just so that the menu item displays the current kernel version?  If so, I'd rather just remove it from the [FONT=courier new]menuentry[/FONT] altogether and just label the item as something generic, such as "Fedora".  That way, I don't have to bother updating it with every kernel upgrade.

Thanks!

---

### Post by Dennis N on 2016-02-12
> **spython01 said:**
> Is the update to Grub required just so that the menu item displays the current kernel version?  If so, I'd rather just remove it from the [FONT=courier new]menuentry[/FONT] altogether and just label the item as something generic, such as "Fedora".  That way, I don't have to bother updating it with every kernel upgrade.

Thanks!
If you don't update Ubuntu's grub menu to reflect the newer kernel, Fedora will continue to use the older kernel version instead of its latest one. It will still boot and run as usual.

---

### Post by spython01 on 2016-02-16
> **Dennis N said:**
> If you don't update Ubuntu's grub menu to reflect the newer kernel, Fedora will continue to use the older kernel version instead of its latest one. It will still boot and run as usual.

Got it.  Thanks!

---

