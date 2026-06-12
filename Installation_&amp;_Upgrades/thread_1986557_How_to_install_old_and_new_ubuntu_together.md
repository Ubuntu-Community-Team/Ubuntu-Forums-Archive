---
title: "How to install old and new ubuntu together"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by peter12345 on 2012-05-25
I have old ubuntu installed, then on another partition installed in the cpu - i put the latest ubuntu. But when i click the old ubuntu i always go to the new ubuntu. Tried clicking old linux ver. At the boot prompt but always go to the new ubuntu. Do i have to delete the new ubuntu to get the boot for the old ubuntu to work.

I am guessing other people may want to keep both the old and new versions of ubuntu on their cpu as new cpu's have so much storage!

---

### Post by wilee-nilee on 2012-05-25
> **peter12345 said:**
> I have old ubuntu installed, then on another partition installed in the cpu - i put the latest ubuntu. But when i click the old ubuntu i always go to the new ubuntu. Tried clicking old linux ver. At the boot prompt but always go to the new ubuntu. Do i have to delete the new ubuntu to get the boot for the old ubuntu to work.

I am guessing other people may want to keep both the old and new versions of ubuntu on their cpu as new cpu's have so much storage!

Strange try in the new Ubuntu install, running in the terminal.

```
sudo update-grub
```If that version has the grub control it should fix this.

If nothing changes, download the link, extract it to your desktop, and run the command. You will see a result.txt appear, copy all the text from it and open a reply and in its panel click the # then paste the text between the code tags.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by peter12345 on 2012-05-26
Thank you, for helping me. I am sure that many Ubuntu users will want to keep their old version of Ubuntu, when they update.   I want to rely more on Ubuntu, I even have worked out how to play 24bit 96000 flac on Ubuntu. I hope that the below info is helpful - kind regards:        


                                    ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

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
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda6/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda8/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden NTFS (Recovery Environment)
/dev/sda2             821,248   121,403,204   120,581,957   7 NTFS / exFAT / HPFS
/dev/sda3         121,403,205   976,768,064   855,364,860   f W95 Extended (LBA)
/dev/sda5         121,403,268   467,218,394   345,815,127   7 NTFS / exFAT / HPFS
/dev/sda6         467,218,458   490,641,164    23,422,707   7 NTFS / exFAT / HPFS
/dev/sda7         490,649,600   951,546,014   460,896,415   7 NTFS / exFAT / HPFS
/dev/sda8         951,546,078   976,768,064    25,221,987   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       8ac4120c-95a3-4956-9feb-b1631b890529   ext4       
/dev/sda1        3A76C59F76C55BEF                       ntfs       SYSTEM
/dev/sda2        D63ED04F3ED029EF                       ntfs       Internet
/dev/sda5        01CC85C9A8793C20                       ntfs       Music
/dev/sda6        01CCF6031142B160                       ntfs       Ubuntu
/dev/sda7        4432D97032D96806                       ntfs       Data
/dev/sda8        01CD277A2CD06280                       ntfs       Ubuntu New

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /tmp/BootInfo-rmVCTqA7/sda6 fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda6/Wubi/boot/grub/grub.cfg: =========================

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

insmod part_msdos
insmod ntfs
set root='(hd0,msdos'
search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=01CD277A2CD06280 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=01CD277A2CD06280 loop=/ubuntu/disks/root.disk ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=01CD277A2CD06280 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=01CD277A2CD06280 loop=/ubuntu/disks/root.disk ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

============================= sda6/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda6/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== sda8/Wubi/boot/grub/grub.cfg: =========================

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

insmod part_msdos
insmod ntfs
set root='(hd0,msdos'
search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos'
  search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=01CD277A2CD06280 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=01CD277A2CD06280 loop=/ubuntu/disks/root.disk ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=01CD277A2CD06280 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 01CD277A2CD06280
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=01CD277A2CD06280 loop=/ubuntu/disks/root.disk ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

============================= sda8/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda8/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 57 b8 9c 14 00 fe  |......?...W.....|
000001d0  ff ff 05 fe ff ff 96 b8  9c 14 32 67 65 01 00 00  |..........2ge...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
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

### Post by bcbc on 2012-05-26
You can't just copy a Wubi install and hope to get a multiboot. The old linux versions in Grub refer to the old kernels, not another install.

The way Wubi works is that the FIRST /ubuntu/disks/root.disk it finds will be used. So when you copied that from /dev/sda8 to /dev/sda6 (?) it just loads the one on /dev/sda6 (however the grub on that is pointing to /dev/sda8 ) so likely that will boot.

There are other ways to do it. Like adding a custom entry in grub.cfg to boot a root.disk located somewhere else or with a different name. I described a bit about this here: [http://ubuntu-with-wubi.blogspot.ca/2012/05/how-to-run-development-release-with.html](http://ubuntu-with-wubi.blogspot.ca/2012/05/how-to-run-development-release-with.html) (ignore the bits about the dev release - there is a description of booting a different virtual disk).

---

### Post by oldfred on 2012-05-26
Added code tags to make results.txt easier to reveiw.

One of the advantages of wubi is that you do not have to partition and it then is easy to uninstall if you do not like Ubuntu.

But even the developer of wubi assumes you will convert to a partitioned install if you like Ubuntu. It may be time to convert?

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by peter12345 on 2012-05-28
The full installation was not a success as I tried with the previous  Ubuntu disc burnt with imageburn at low speed as it could not find W7, and I have 2 of them installed.

Though the problems of the Wubi install are small - 1- cannot fix a NTFS error within Ubuntu, just takes a second to defrag from W7 - 2- cannot use hibernation - i never use it; and i cannot understand people that use it - 3 - cannot dual boot 2 versions of Ubuntu. but I have a back up of the previous Ubuntu if the new Ubuntu goes wrong. I just uninstall the new one.

I was only able to give this answer because of the 2 well constructed  answers to my question.  So thanks to the 2 administrators.

---

