---
title: "Grub on HDD doesn't see Win8 on SSD"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by padzikm on 2013-06-06
I've installed Ubuntu on second drive - HDD - when I start computer grub  is shown, ubuntu and windows8 are shown in grub, ubuntu starts  normally, but when I choose windows I get this message: "can't find  command 'drivemap', invalid efi file path". 
I tried boot repair, but it didn't work, this is my  boot_info_script_result:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 
    1446256904 of the same hard drive for core.img, but core.img can not be 
    found at this location.

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

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 256.1 GB, 256060514304 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 31130, w sumie sektorów: 500118192
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             718,848   450,203,240   449,484,393   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 91201, w sumie sektorów: 1465149168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 4096

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1     410,241,024 1,465,147,391 1,054,906,368 Data partition (Windows/Linux)
/dev/sdb2           2,048       194,559       192,512 EFI System partition
/dev/sdb3         194,560   393,545,727   393,351,168 Data partition (Windows/Linux)
/dev/sdb4     393,545,728   410,241,023    16,695,296 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        609693A1969375EE                       ntfs       Zastrze&#380;one przez system
/dev/sda2        1EBE9592BE956357                       ntfs       
/dev/sdb1        0357293E0CA0EA25                       ntfs       Data
/dev/sdb2        E40D-2243                              vfat       
/dev/sdb3        831ea632-2ea3-4478-9fd1-4442af36487a   ext4       
/dev/sdb4        8bf66a9e-d267-4b51-a79a-2334202f7485   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /boot/efi                vfat       (rw)
/dev/sdb3        /                        ext4       (rw,errors=remount-ro)


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
set default="0"

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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  831ea632-2ea3-4478-9fd1-4442af36487a
else
  search --no-floppy --fs-uuid --set=root 831ea632-2ea3-4478-9fd1-4442af36487a
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=pl_PL
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-831ea632-2ea3-4478-9fd1-4442af36487a' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  831ea632-2ea3-4478-9fd1-4442af36487a
    else
      search --no-floppy --fs-uuid --set=root 831ea632-2ea3-4478-9fd1-4442af36487a
    fi
    linux    /boot/vmlinuz-3.8.0-23-generic root=UUID=831ea632-2ea3-4478-9fd1-4442af36487a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-23-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-831ea632-2ea3-4478-9fd1-4442af36487a' {
    menuentry 'Ubuntu, with Linux 3.8.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-advanced-831ea632-2ea3-4478-9fd1-4442af36487a' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  831ea632-2ea3-4478-9fd1-4442af36487a
        else
          search --no-floppy --fs-uuid --set=root 831ea632-2ea3-4478-9fd1-4442af36487a
        fi
        echo    'Loading Linux 3.8.0-23-generic ...'
        linux    /boot/vmlinuz-3.8.0-23-generic root=UUID=831ea632-2ea3-4478-9fd1-4442af36487a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-recovery-831ea632-2ea3-4478-9fd1-4442af36487a' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  831ea632-2ea3-4478-9fd1-4442af36487a
        else
          search --no-floppy --fs-uuid --set=root 831ea632-2ea3-4478-9fd1-4442af36487a
        fi
        echo    'Loading Linux 3.8.0-23-generic ...'
        linux    /boot/vmlinuz-3.8.0-23-generic root=UUID=831ea632-2ea3-4478-9fd1-4442af36487a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-831ea632-2ea3-4478-9fd1-4442af36487a' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  831ea632-2ea3-4478-9fd1-4442af36487a
        else
          search --no-floppy --fs-uuid --set=root 831ea632-2ea3-4478-9fd1-4442af36487a
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=831ea632-2ea3-4478-9fd1-4442af36487a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-831ea632-2ea3-4478-9fd1-4442af36487a' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  831ea632-2ea3-4478-9fd1-4442af36487a
        else
          search --no-floppy --fs-uuid --set=root 831ea632-2ea3-4478-9fd1-4442af36487a
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=831ea632-2ea3-4478-9fd1-4442af36487a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-609693A1969375EE' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  609693A1969375EE
    else
      search --no-floppy --fs-uuid --set=root 609693A1969375EE
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
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

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb3 during installation
UUID=831ea632-2ea3-4478-9fd1-4442af36487a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
#UUID=E40D-2243  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdb4 during installation
UUID=8bf66a9e-d267-4b51-a79a-2334202f7485 none            swap    sw              0       0
UUID=E40D-2243    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  70.319740295 = 75.505246208   boot/grub/grub.cfg                             1
   1.818756104 = 1.952874496    boot/initrd.img-3.8.0-19-generic               1
   1.779693604 = 1.910931456    boot/initrd.img-3.8.0-23-generic               1
   0.796981812 = 0.855752704    boot/vmlinuz-3.8.0-19-generic                  1
   0.836044312 = 0.897695744    boot/vmlinuz-3.8.0-23-generic                  1
   1.779693604 = 1.910931456    initrd.img                                     1
   1.779693604 = 1.910931456    initrd.img.old                                 1
   0.836044312 = 0.897695744    vmlinuz                                        1
   0.836044312 = 0.897695744    vmlinuz.old                                    1


```

---

### Post by oldfred on 2013-06-06
You must have a newer computer that has both UEFI & BIOS/CSM/Legacy boot options. Windows is installed in BIOS mode and it looks like Ubuntu was installed in UEFI mode as you have efi partition. But you have grub installed to MBR and you can boot Ubuntu in BIOS mode from gpt partitioned drive. But for grub2 to install properly with gpt drives you need a tiny 1MB unformatted bios_grub partition on the drive. Use gparted from liveCD and create a new partition and right click manage flags and make it a bios_grub, be sure not to format it.

Then you should be able to use Boot-Repair to fix your Ubuntu install. Boot Repair can convert a UEFI install to BIOS and vice-versa by uninstalling grub-efi and installing grub-pc.

---

