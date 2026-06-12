---
title: "Cannot boot into Ubuntu after installing"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by chaquito on 2012-08-06
Hi,
I have just installed Ubuntu in a new laptop with Windows 7. I created a partition for Ubuntu and the installation went fine. However after rebooting (at the end of the installation) there was only a message from Windows 7 complaining that the MBR was corrupt, ignoring the message take me to a regular Windows 7 boot up, but there is no way to boot into Ubuntu.
Could anybody please help me to solve this?
I am including a file obtained after running the script from  [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

```
sudo bash ~/Desktop/bootinfoscript
``````
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    1307858944 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       411,647       409,600 EFI System partition
/dev/sda2         411,648       673,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         673,792 1,307,858,943 1,307,185,152 Data partition (Windows/Linux)
/dev/sda4   1,412,718,592 1,465,147,391    52,428,800 Windows Recovery Environment (Windows)
/dev/sda5   1,307,858,944 1,307,860,897         1,954 BIOS Boot partition
/dev/sda6   1,307,860,898 1,396,175,351    88,314,454 Data partition (Windows/Linux)
/dev/sda7   1,396,175,352 1,412,718,591    16,543,240 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B211-28C8                              vfat       SYSTEM
/dev/sda3        8AF24081F240738B                       ntfs       OS
/dev/sda4        AC7A43BA7A438056                       ntfs       Recovery
/dev/sda6        69cde522-8cf1-4852-94e6-14b216a6c065   ext4       
/dev/sda7        8441fedb-0703-41b7-80a2-f5ea9bd3092a   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt6)'
search --no-floppy --fs-uuid --set=root 69cde522-8cf1-4852-94e6-14b216a6c065
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt6)'
  search --no-floppy --fs-uuid --set=root 69cde522-8cf1-4852-94e6-14b216a6c065
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
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
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt6)'
    search --no-floppy --fs-uuid --set=root 69cde522-8cf1-4852-94e6-14b216a6c065
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=69cde522-8cf1-4852-94e6-14b216a6c065 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt6)'
    search --no-floppy --fs-uuid --set=root 69cde522-8cf1-4852-94e6-14b216a6c065
    echo    'Loading Linux 3.2.0-27-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=69cde522-8cf1-4852-94e6-14b216a6c065 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt6)'
    search --no-floppy --fs-uuid --set=root 69cde522-8cf1-4852-94e6-14b216a6c065
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=69cde522-8cf1-4852-94e6-14b216a6c065 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt6)'
    search --no-floppy --fs-uuid --set=root 69cde522-8cf1-4852-94e6-14b216a6c065
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=69cde522-8cf1-4852-94e6-14b216a6c065 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt6)'
    search --no-floppy --fs-uuid --set=root 69cde522-8cf1-4852-94e6-14b216a6c065
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt6)'
    search --no-floppy --fs-uuid --set=root 69cde522-8cf1-4852-94e6-14b216a6c065
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 8AF24081F240738B
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root AC7A43BA7A438056
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=69cde522-8cf1-4852-94e6-14b216a6c065 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8441fedb-0703-41b7-80a2-f5ea9bd3092a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           1
               =                boot/initrd.img-3.2.0-27-generic-pae           1
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-27-generic-pae              1
               =                initrd.img                                     1
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by Alex de Borba on 2012-08-08
I had the same issue and what I did was to reinstall Ubuntu again, and reboot a couple times until the option to login with Ubuntu shown up.

---

### Post by drmrgd on 2012-08-08
The issue here is that you have Windows installed in UEFI mode, and have installed Ubuntu in MBR mode.  The two are not compatible, and you'll have to reinstall Ubuntu as UEFI in order to get the bootloader working correctly.  For a little more info on how to do this, please see these links:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

It should be as simple as booting the Ubuntu .iso installer in UEFI mode (this is important!) rather than MBR mode, pointing the Grub to the /boot_efi parition, and chain loading Windows from there. 

Here's a nice post from a Forum user that has put a lot of effort into this, creating the Boot Info Script as well as the Boot Repair utility that I've heard is doing quite well to sort out even UEFI boot problems these days:

[http://ubuntuforums.org/showpost.php?p=12036059&postcount=17](http://ubuntuforums.org/showpost.php?p=12036059&postcount=17)

Hope that helps get you started.  There are a number of people here with successful UEFI dual boot knowledge that can help you get this sorted out.  So, definitely post back and let us know how it's going.

---

### Post by chaquito on 2012-08-10
Thank you very much!
Everything works fine now. For the record, the key was to re-install Ubuntu with the installer CD booted in UEFI mode. I had initially tried with Ubuntu 32-bit and couldn't do that but then I realized that for UEFI the 64-bit version is needed. I downloaded the 64-bit Ubuntu, burned it into a CD and booted in UEFI mode to do the installation. After that I could boot into Ubuntu from the grub boot menu without problems. Windows 7 however could not be loaded from the grub menu, but that was fixed after I run Boot-Repair.

---

