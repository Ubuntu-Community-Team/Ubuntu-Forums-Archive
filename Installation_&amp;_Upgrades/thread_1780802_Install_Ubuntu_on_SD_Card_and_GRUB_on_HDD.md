---
title: "Install Ubuntu on SD Card and GRUB on HDD"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by juliusnkemdiche on 2011-06-12
Hello,

*before I begin I would like to say I have tried to search for a solution to this but I haven't as of yet so I have come to this forum*

I am trying to install Ubuntu onto an SD Card, and then have GRUB installed onto my laptops hard drive. This would allow me to boot into GRUB and have it present me with the option to start Windows 7 or Ubuntu.

I want Ubuntu on my SD Card because I want to leave Windows 7 on my internal hard drive intact and not sharing hard drive space (which is now becoming limited.

My laptop is not able to boot from SD Cards, but it can with USBs. That's why I am wondering if this is the next best solution by having GRUB boot and then load drivers or modules (or whatever) that will allow my SD Card to show up.

I have attempted to do this by installing Ubuntu onto the SD Card, then boot information onto my hard drive. But when I got to restart my machine, the grub rescue> prompt comes up saying it cant do anything.

I was reading that modifying initramfs-tools/modules would help but I am not having much luck with that.

Please help, thanks!

---

### Post by sanderd17 on 2011-06-12
> **juliusnkemdiche said:**
> Hello,

*before I begin I would like to say I have tried to search for a solution to this but I haven't as of yet so I have come to this forum*

I am trying to install Ubuntu onto an SD Card, and then have GRUB installed onto my laptops hard drive. This would allow me to boot into GRUB and have it present me with the option to start Windows 7 or Ubuntu.

I want Ubuntu on my SD Card because I want to leave Windows 7 on my internal hard drive intact and not sharing hard drive space (which is now becoming limited.

My laptop is not able to boot from SD Cards, but it can with USBs. That's why I am wondering if this is the next best solution by having GRUB boot and then load drivers or modules (or whatever) that will allow my SD Card to show up.

I have attempted to do this by installing Ubuntu onto the SD Card, then boot information onto my hard drive. But when I got to restart my machine, the grub rescue> prompt comes up saying it cant do anything.

I was reading that modifying initramfs-tools/modules would help but I am not having much luck with that.

Please help, thanks!

GRUB needs configuration files that are stored on a UNIX like file system (so you need to have at least a part of Linux on your HDD before GRUB can be on your HDD), without those configuration files, you will be dropped to the GRUB rescue shell and you won't be able to boot anything else.

Why don't you simply install it to your HDD?

---

### Post by juliusnkemdiche on 2011-06-12
Hi, thanks for your response. 

I don't want to shrink my Windows 7 volume basically (although I'm guessing I will have to a little bit for the GRUB install) and I would prefer to run Ubuntu on the SD Card.

Can I manually install GRUB on my HDD then?

---

### Post by sanderd17 on 2011-06-12
> **juliusnkemdiche said:**
> Hi, thanks for your response. 

I don't want to shrink my Windows 7 volume basically (although I'm guessing I will have to a little bit for the GRUB install) and I would prefer to run Ubuntu on the SD Card.

Can I manually install GRUB on my HDD then?

The config files are in /boot/grub on the Ubuntu installation. GRUB certainly needs those files.

But apart from that, I don't know if GRUB is able to load drivers for (in this case) an SD card. Normally all drivers are loaded when the kernel loads, after GRUB. I don't know, so it could be possible to get around that.

PS, run the boot info script to find out how your current config is: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
and see the wiki for configuration questions: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by juliusnkemdiche on 2011-06-12
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 15650 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   625,139,711   624,932,864   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2054 MB, 2054385664 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4012472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     4,012,471     4,012,409   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4075 MB, 4075290624 bytes
126 heads, 62 sectors/track, 1018 cylinders, total 7959552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048     4,884,479     4,882,432  83 Linux
/dev/sdc2           4,884,480     7,958,527     3,074,048  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C09C96649C9654AE                       ntfs       System Reserved
/dev/sda2        E0CC98D1CC98A2F8                       ntfs       
/dev/sdb1        160E-414A                              vfat       PENDRIVE
/dev/sdc1        52cb6640-aa61-41b6-b641-bfc92f2b93a4   ext4       
/dev/sdc2        b706e994-5baa-4c83-83d2-305257b006fa   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/52cb6640-aa61-41b6-b641-bfc92f2b93a4 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc2        /media/b706e994-5baa-4c83-83d2-305257b006fa ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root 52cb6640-aa61-41b6-b641-bfc92f2b93a4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root 52cb6640-aa61-41b6-b641-bfc92f2b93a4
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 52cb6640-aa61-41b6-b641-bfc92f2b93a4
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=52cb6640-aa61-41b6-b641-bfc92f2b93a4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 52cb6640-aa61-41b6-b641-bfc92f2b93a4
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=52cb6640-aa61-41b6-b641-bfc92f2b93a4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 52cb6640-aa61-41b6-b641-bfc92f2b93a4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 52cb6640-aa61-41b6-b641-bfc92f2b93a4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C09C96649C9654AE
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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=52cb6640-aa61-41b6-b641-bfc92f2b93a4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdd2 during installation
UUID=b706e994-5baa-4c83-83d2-305257b006fa /home           ext4    defaults        0       2
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.907543182 = 2.048208896    boot/grub/core.img                             1
   0.303966522 = 0.326381568    boot/grub/grub.cfg                             1
   2.297702789 = 2.467139584    boot/initrd.img-2.6.38-8-generic               2
   2.049385071 = 2.200510464    boot/vmlinuz-2.6.38-8-generic                  1
   2.297702789 = 2.467139584    initrd.img                                     2
   2.049385071 = 2.200510464    vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

