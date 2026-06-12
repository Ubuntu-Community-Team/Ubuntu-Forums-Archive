---
title: "windows recovery partition no longer showing in boot loader"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by whitemagicwoman on 2013-03-15
Hello all, 

I am dual booting Ubuntu 12.04 and Windows 7 on a Lenovo ThinkPad T410.  The computer is new but it is my fourth dual-boot project.  First time doing it with 7 though.

I use the Lifehacker guide to dual booting when I'm getting started with a new installation: 
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

Sooo, I followed those steps to set up my dual boot.  Everything worked okay starting out, but the Windows partition was too small - apparently the real estate quoted in the article was a little sparse.  I booted into Ubuntu, fired up GParted, resized the partition.  Then, Windows would not boot - pretty normal.  I repaired the installation using the Windows 7 recovery disc.  Now Windows is booting fine.

The only problem is that now the Windows recovery partition is no longer showing up in the Ubuntu boot loader.  I can see it in GParted, and I can see it using the Windows partition tool, and both sides say that the partition is healthy and fine. But it does not show up in the loader.  (Sorry, I am not sure if this happened after I repartitioned, or after I repaired the install - I was going one step at a time at that point.)  I haven't needed it yet, but I'd rather have it and not need it than need it and not have it.

I have Googled everything I can think to Google but can't seem to find anything to even try.  

I would appreciate any suggestions and I am happy to do screenshots, copy and paste outputs, et cetera.  Just let me know what would be helpful to see.

Thanks in advance!

- wmw

---

### Post by MAFoElffen on 2013-03-15
See the boot info script link in my sig line? Could you go to it and please post the results here?

---

### Post by Mark Phelps on 2013-03-16
Your Windows Recovery partition would only do a factory restore -- erasing everything you have right now and forcing you to reinstall not only all your apps, settings, and data, but also do LOTS of Windows Updates to catch up.  This is a LOT of work simply to get Windows back.

A better solution is to install Macrium Reflect (they have a free version) in Win7 and use that to make an image backup of your NOW working Win7 system to an external drive.  Also use the option to create and burn a Boot CD.  That way, if you need to restore Windows, you can do that without hours of additional work.  And -- you can erase the Recovery partition and reuse the space.

---

### Post by whitemagicwoman on 2013-03-16
Absolutely, MAFoElffen. Here are the results:
[I]
> Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

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
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   136,642,559   136,435,712   7 NTFS / exFAT / HPFS
/dev/sda3         276,393,984   338,368,511    61,974,528  83 Linux
/dev/sda4         357,318,656 1,197,897,727   840,579,072   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        30FC66A3FC666358                       ntfs       System Reserved
/dev/sda2        60F868D9F868AF4A                       ntfs       
/dev/sda3        8527c73d-99e0-45e2-8e9b-47976f61dc73   ext4       
/dev/sda4        02DA1E534653A058                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /media/02DA1E534653A058  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 8527c73d-99e0-45e2-8e9b-47976f61dc73
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 8527c73d-99e0-45e2-8e9b-47976f61dc73
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.5.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 8527c73d-99e0-45e2-8e9b-47976f61dc73
    linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=8527c73d-99e0-45e2-8e9b-47976f61dc73 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 8527c73d-99e0-45e2-8e9b-47976f61dc73
    echo    'Loading Linux 3.5.0-25-generic ...'
    linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=8527c73d-99e0-45e2-8e9b-47976f61dc73 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-25-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 8527c73d-99e0-45e2-8e9b-47976f61dc73
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=8527c73d-99e0-45e2-8e9b-47976f61dc73 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 8527c73d-99e0-45e2-8e9b-47976f61dc73
    echo    'Loading Linux 3.5.0-23-generic ...'
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=8527c73d-99e0-45e2-8e9b-47976f61dc73 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 8527c73d-99e0-45e2-8e9b-47976f61dc73
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 8527c73d-99e0-45e2-8e9b-47976f61dc73
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 30FC66A3FC666358
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
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=8527c73d-99e0-45e2-8e9b-47976f61dc73 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.5.0-23-generic               1
               =                boot/initrd.img-3.5.0-25-generic               1
               =                boot/vmlinuz-3.5.0-23-generic                  1
               =                boot/vmlinuz-3.5.0-25-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
[/I]

---

### Post by whitemagicwoman on 2013-03-16
Mark, you make a reasonable point.  I do make image backups using Clonezilla, and if I did have a problem I would probably start by booting into Ubuntu and trying to fix it from there... I will think about what you have said.

---

### Post by MAFoElffen on 2013-03-16
+1 with Mark

Otherwise, the idea I have is to edit /etc/grub.d/40_custom to add it back in: 
```
#!/bin/sh
exec tail -n +3 $0
### /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
## (This is the edit start)
menuentry "Windows 7 Recovery (on /dev/sda2)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
chainloader +1
}
## (This is the edit end.)

```
I note 2 things that should be added as experience from this... If you have to move/resize a Windows partition, do it from inside Windows. GParted and Linux utils will physically move anything, but it doesn't always do it in the "Windows" way, so that Windows can keep track to the order and where it moved to... I also had hair pulling experiences with that years ago. I've done the same early on with the MBR. Another problem is it sometimes breaks the Windows file indexes. (Which can be rebuilt). So now on Windows partitions, I do with Windows Tools. They do that "and" are able to keep track of those moves for Windows to see.

Next is, if I am setting up a multi-boot disk, I always leave a 1MB unallocated space at the start of the disk, for the boot loader to load to if needed. If not, then "sometimes" the bootloader encroaches on the first partition's boot sector... When I was starting out, I didn't know this and would have to fix the Win MBR. After leaving that space now, I haven't had to do that since. Now with GPT, It also needs it's own additional space, at the start and again at the end of the disk.

You could also setup a partition just large enough to copy the win ISO to... and boot the ISO file from Grub

Question- No swap space?

---

### Post by whitemagicwoman on 2013-03-22
MAFoElffen, thanks for the edit suggestion.  It was a clever idea!  I made the change, then rebooted - sadly, the partition still doesn't show up.

At this point, I am thinking I will do one of the following:

1) Restore my backup from before the partitions were changed, re-do the partition from the Windows side
2) Just not worry about it as suggested by Mark.

Your other comments on my partitions are totally on target.  All my dirty laundry airing on the line!  Ah well.  :)  

Thanks very much to both of you for your time and suggestions.

---

