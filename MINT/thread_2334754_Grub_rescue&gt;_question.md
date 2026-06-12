---
title: "Grub rescue&gt; question"
date: 2016-08-22
forum: MINT
---

### Post by georg5 on 2016-08-22
My linux Mint 17 Cinnamon has run into a grub rescue> situation after trying to play a video online.
  
The ls command produces the following:
 
(hd0), (hd0,msdos3), (hd0,msdos2), (hd0,msdos1), (hd1), (hd1,msdos2) and (hd1,msdos1)

I tested all 7 possibilities with the commands recommended online
set boot= (hdX,Y)/boot/grub
set prefix= (hdX,Y)/boot/grub
insmod normal
normal

6 of them resulted in "error: unknown filesystem" BUT the (hd0,msdos3) showed "error: file boot/grub/i386-pc/normal.mod not found".

After booting with the original Linux Mint 17 "Qiana" - Cinnamon (64-bit)
installation CD, Gparted shows this:

/dev/sda1 - unknown  - boot (about 28Gb)
/dev/sda2 - linux-swap       (about 9.5 Gb)
/dev/sda3 - ext4            (about 112 Gb)
and a message 'unable to detect file system" and listing possible reasons.
Personal data is all there.


Looking at this drive with Gparted on my other Mint 17 system, I get similar result,
only the the partitions are called /dev/sdb1 through 3.

QUESTION:
Which of the drive/partition names do I need to use in the commands 
set boot= (hdX,Y)/boot/grub and 
set prefix= (hdX,Y)/boot/grub  
etc....?


Bootinfoscript Results.txt:

```
 Boot Info Script 0.61      


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    13507584 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17 Qiana
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 46716928.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   234,441,647   234,441,647  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048    46,701,266    46,699,219 Data partition (Linux)
/dev/sda2      46,815,232   234,440,703   187,625,472 Data partition (Linux)
/dev/sda3      46,702,592    46,716,927        14,336 Swap partition (Linux)
/dev/sda4      46,716,928    46,815,231        98,304 EFI System partition

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    60,000,255    59,998,208  83 Linux
/dev/sdb2          60,000,256    80,001,023    20,000,768  82 Linux swap / Solaris
/dev/sdb3          80,001,024   312,580,095   232,579,072  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        63a6db40-aabd-456d-a595-e8ef75e68565   ext4       
/dev/sda2        7e4a63b3-b698-489f-9ee2-9c7a859be888   ext4       
/dev/sda3        2b9c8fff-9500-4c75-be8f-305b96bb4321   swap       
/dev/sda4        384E-FB82                              vfat       
/dev/sdb2        a34ef38f-846f-43a5-9ccf-d1f24c314c9a   swap       
/dev/sdb3        84ea9d51-ceb2-4cc0-9749-4662ea764fac   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/georgina/7e4a63b3-b698-489f-9ee2-9c7a859be888 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda4        /boot/efi                vfat       (rw)
/dev/sdb3        /media/georgina/84ea9d51-ceb2-4cc0-9749-4662ea764fac ext4       (rw,nosuid,nodev,uhelper=udisks2)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  63a6db40-aabd-456d-a595-e8ef75e68565
else
  search --no-floppy --fs-uuid --set=root 63a6db40-aabd-456d-a595-e8ef75e68565
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

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
menuentry 'Linux Mint 17 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda1)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  63a6db40-aabd-456d-a595-e8ef75e68565
    else
      search --no-floppy --fs-uuid --set=root 63a6db40-aabd-456d-a595-e8ef75e68565
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=63a6db40-aabd-456d-a595-e8ef75e68565 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
menuentry 'Linux Mint 17 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda1) -- recovery mode' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  63a6db40-aabd-456d-a595-e8ef75e68565
    else
      search --no-floppy --fs-uuid --set=root 63a6db40-aabd-456d-a595-e8ef75e68565
    fi
    echo    'Loading Linux 3.13.0-24-generic ...'
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=63a6db40-aabd-456d-a595-e8ef75e68565 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sde1 during installation
UUID=63a6db40-aabd-456d-a595-e8ef75e68565 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sde4 during installation
UUID=384E-FB82  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sde3 during installation
UUID=2b9c8fff-9500-4c75-be8f-305b96bb4321 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-wzcyeacp/Tmp_Log: No such file or directory
  No volume groups found
```

---

### Post by howefield on 2016-08-22
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2016-08-22
I don't see how playing a video online would affect the booting of the system, illogical.

If you look at the bootinfoscript output at the top, it shows Grub code in the MBR of sda but also states that the core.img file cannot be found.  Without it, it won't boot.
sda4 shows as an efi partition which is not needed with an MBR boot and mixing the two results in problems. 
You show Grub code in the MBR of sdb and the core.img file is present.  Are you able to boot that drive?  The bootinfoscript does not show the standard output for that drive for some reason.  Can you boot the system on the 160GB drive?

---

### Post by oldfred on 2016-08-22
Your fstab shows the mount of the ESP, so your install is really UEFI, even though you have a grub in the MBR.

Did you change the boot mode from UEFI to BIOS?

And if some application crashes you may have file corruption. Then system will not boot whether UEFI or BIOS and you probably need fsck to resolve corruption. Since not sure which partition, run fsck on every Linux formatted partition.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by georg5 on 2016-08-22
> **yancek said:**
> I don't see how playing a video online would affect the booting of the system, illogical.

If you look at the bootinfoscript output at the top, it shows Grub code in the MBR of sda but also states that the core.img file cannot be found.  Without it, it won't boot.
sda4 shows as an efi partition which is not needed with an MBR boot and mixing the two results in problems. 
You show Grub code in the MBR of sdb and the core.img file is present.  Are you able to boot that drive?  The bootinfoscript does not show the standard output for that drive for some reason.  Can you
 boot the system on the 160GB drive?

No, I cannot boot the system on the 160GB drive.
 OK - Reading a news page, there was a video I clicked to play and the  screen went black. On restart, only the grub rescue>  showed on the  160GB drive.
The system had run for a long time with no problems. I made NO changes to it whatsoever prior to this.
After researching online, I used the original Linux Mint 17 "Qiana" - Cinnamon (64-bit)
installation CD, and its Gparted showed this about the 160GB drive:

/dev/sda1 - unknown  - boot (about 28Gb)
/dev/sda2 - linux-swap       (about 9.5 Gb)
/dev/sda3 - ext4            (about 112 Gb)
(There was no sda4 shown on this drive.)

I  also did a check of this 160GB drive by looking at it with the GParted  of my other Mint 17 system installed on a 120GB SSD drive. That produced  the /dev/sdb1 through 3 values, which I figured are the very same as the dev/sda ones. So  the 160GB contains only those 3.

I do not remember how I did the  Bootinfoscript. It could be I used this other system (on the 120GB  drive) to run bootinfoscript on the 160GB drive.

---

### Post by georg5 on 2016-08-22
Thanks, oldfred, I just need time to digest what you are suggesting. But NO, did no mode changes at all.

---

### Post by georg5 on 2016-08-23
> **georg5 said:**
> Thanks, oldfred, I just need time to digest what you are suggesting. But NO, did no mode changes at all.

OK, I am pretty new at thes kid of stuff, but I have looked at things more carefully. 
I would not presume to question anyone on this, really, but does the mount of ESP, which you mention, not pertain to the sda drive? Because that is the boot ing drive I used to run bootinfoscript to examine the problem drive sdb.

To simplify, I have revised that script result:  

The below pertains mostly to the corrupted drive and has been extracted from the original bootinfoscript.txt report
which included both the booting drive (sda here) and the unmounted drive in question (sdf), which I am trying to fix.
The 120GB booting drive sda is not relevant to me.


```
Boot Info 
=> Grub2 (v1.99) is installed in the MBR of /dev/sdf and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
sdf1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdf2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdf3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

Drive/Partition Info:
Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *          2,048    60,000,255    59,998,208  83 Linux
/dev/sdf2          60,000,256    80,001,023    20,000,768  82 Linux swap / Solaris
/dev/sdf3          80,001,024   312,580,095   232,579,072  83 Linux

"blkid" output: ________________________________________________________________

Nothing for this drive. 

The report continues:
=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  63a6db40-aabd-456d-a595-e8ef75e68565
else
  search --no-floppy --fs-uuid --set=root 63a6db40-aabd-456d-a595-e8ef75e68565
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

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
menuentry 'Linux Mint 17 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda1)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  63a6db40-aabd-456d-a595-e8ef75e68565
    else
      search --no-floppy --fs-uuid --set=root 63a6db40-aabd-456d-a595-e8ef75e68565
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=63a6db40-aabd-456d-a595-e8ef75e68565 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
menuentry 'Linux Mint 17 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda1) -- recovery mode' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  63a6db40-aabd-456d-a595-e8ef75e68565
    else
      search --no-floppy --fs-uuid --set=root 63a6db40-aabd-456d-a595-e8ef75e68565
    fi
    echo    'Loading Linux 3.13.0-24-generic ...'
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=63a6db40-aabd-456d-a595-e8ef75e68565 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sde1 during installation
UUID=63a6db40-aabd-456d-a595-e8ef75e68565 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sde4 during installation
UUID=384E-FB82  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sde3 during installation
UUID=2b9c8fff-9500-4c75-be8f-305b96bb4321 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-vglBVSHg/Tmp_Log: No such file or directory
  No volume groups found
```

---

### Post by yancek on 2016-08-23
You should start by running a filesystem check as suggested above by oldfred as it appears that the filesystem on at least one partition is corrupt. 

Also, after that is done, you need to use either EFI or MBR and not mix the two.
Generally if you are watching a video online and it stalls, you can close the browser.  It might take some time but generally you will get a pop up windows telling you the program isn't running correctly and asking you to terminate.  Of course, that doesn't always happen?

---

### Post by georg5 on 2016-08-23
> **yancek said:**
> You should start by running a filesystem check as suggested above by oldfred as it appears that the filesystem on at least one partition is corrupt. 

Also, after that is done, you need to use either EFI or MBR and not mix the two.
Generally if you are watching a video online and it stalls, you can close the browser.  It might take some time but generally you will get a pop up windows telling you the program isn't running correctly and asking you to terminate.  Of course, that doesn't always happen?

Thank you, yancek, will do as you suggest. I t will take a while as I have to figure out how to do this - all too new to me.
Thanks also for the tip on video problems. In my case, it never played, the screen blanked out immediately upon clicking it.

---

### Post by oldfred on 2016-08-23
I have installed Ubuntu in UEFI mode many times to second drives, sdb or flash. And every time it installs the .efi boot files into sda.

If you want UEFI boot on an external drive, you have to gpt partition in advance and include an ESP - efi system partition. And after install manually copy files from ESP on sda. And copy & rename shim to /EFI/Boot/bootx64.efi as that is the only file UEFI uses to boot external devices (used by installer also). But different configurations have a different bootx64.efi.

Your sdf drive is also MBR partitioned, so it really should be BIOS boot with grub installed to MBR of sdb. But you used an old copy of bootinfoscript and it shows partition 112. Better to use Boot-Repair's summary report or the fork of bootinfoscript.

But if UEFI system, you have to make sure it is set to boot in BIOS mode to boot external. If install in sda is UEFI, you also then have to go into UEFI and change boot modes depending on which system you are booting.

       Updated fork  as original bootinfoscript does not seem to be maintained
[URL="https://github.com/arvidjaar/bootinfoscript"]https://github.com/arvidjaar/bootinfoscript
[/URL]
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
    [URL="https://github.com/arvidjaar/bootinfoscript"]
[/URL]

---

### Post by georg5 on 2016-08-23
Thank you both gentlemen oldfred and yancek for your kind advice and tips. 
I have now done the filesystem check fsck on the /dev/sdb1 partition. After letting it fix a bunch of stuff, the system boots and is back to normal.
I am going to further check and investigate both of the drives following the above  links' info.
As a note, I always use these drives solo and used them in tandem this time only, because one would not boot and it was an easy way to examine it.
Once again - thank you for the education!

---

