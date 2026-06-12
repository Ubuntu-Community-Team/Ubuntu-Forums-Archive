---
title: "Installed GRUB, Win7 won't boot..."
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by Vepar on 2011-09-09
So i had to format my whole computer, and i had Win7 only before that, got a new computer so it had only Win7.

Now i want to dual boot with Ubuntu like i used to, but can't seem to get it right all of a sudden...

I installed Win7 first, then Ubuntu 11.04.
Now, when Ubuntu finished installing, in grub i could see Win7 bootloader /dev/sda1 but when i try to boot into it, the screen goes black, then returns to grub... I could only boot into Ubuntu. I tried to repair Win7 bootloader using Win7 DVD, but it didn't work. It kept telling me that it couldn't find any problems. I thought that's because the bootloader is still there if the Windows finds no problems with it.

Now i reinstalled Win7 (no big deal, had nothing on it), reformatted all the partitions like i want and i want to install Ubuntu 11.04 again, but i don't want to mess up anything again.

Also, when i got to the choice in the Ubuntu installation, where i want to put grub, i choose to put it on dev/sda1 where windows bootloader was. Was that stupid? :D Did this cause windows not to boot?

Where should i put GRUB so i can use it as my default bootloader?
Or rather, what option should i choose in the installation for grub?

Please, any help would be appretiated. :confused:

Summary:
- Win7 bootloader is on /dev/sda1
- I chose to put grub on /dev/sda1 too
- I'm using Ubuntu 11.04
- I have 1 HDD, 3 Primary partitions, 1 Extended (primary    partitions: 1 - boot, 2 - win7 installation (C: ), 3 - Ubuntu root, extended: 1st - D: disk, 2nd - E: disk, 4th - swap, 5th - /home)

If you need any more info on my system and configuration please ask, i don't know what you might need.

---

### Post by Quackers on 2011-09-09
Putting grub in sda1 is the cause of your problems. Grub does not normally go into a partition. It goes in the mbr of the disc - ie /dev/sda, for instance.

---

### Post by Rubi1200 on 2011-09-09
I recommend you post the results of the boot info script so we can get a better overview of what is where on your system.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by Vepar on 2011-09-09
> **Quackers said:**
> Putting grub in sda1 is the cause of your problems. Grub does not normally go into a partition. It goes in the mbr of the disc - ie /dev/sda, for instance.

So thats what caused it... So i just choose dev/sda option in install and its going to work? 

Also, this is the result text from the script Rubi1200 gave me.
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

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

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 7746 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   209,922,047   209,715,200   7 NTFS / exFAT / HPFS
/dev/sda3         209,922,048   224,602,111    14,680,064  83 Linux
/dev/sda4         224,604,158 1,953,523,711 1,728,919,554   5 Extended
/dev/sda5         224,604,160 1,063,464,959   838,860,800   7 NTFS / exFAT / HPFS
/dev/sda6       1,063,467,008 1,902,327,807   838,860,800   7 NTFS / exFAT / HPFS
/dev/sda7       1,902,329,856 1,910,327,295     7,997,440  82 Linux swap / Solaris
/dev/sda8       1,910,329,344 1,953,523,711    43,194,368  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1014 MB, 1014497280 bytes
250 heads, 32 sectors/track, 247 cylinders, total 1981440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     1,981,439     1,981,408   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        424EEA2F4EEA1C03                       ntfs       System Reserved
/dev/sda2        8A6EF1E56EF1CA49                       ntfs       
/dev/sda3        573adc08-6860-452b-88e6-8c1d269f1a2d   ext4       
/dev/sda5        6A18211C1820E8B1                       ntfs       Disk Dva
/dev/sda6        EE8018DE8018AF59                       ntfs       Disk Tri
/dev/sda7        0f2db119-7d66-46df-bff5-2d1b59503cea   swap       
/dev/sda8        98f144b6-4841-41f8-b51b-38c047b64a18   ext4       
/dev/sdb1        0815-0A5D                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 573adc08-6860-452b-88e6-8c1d269f1a2d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 573adc08-6860-452b-88e6-8c1d269f1a2d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 573adc08-6860-452b-88e6-8c1d269f1a2d
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=573adc08-6860-452b-88e6-8c1d269f1a2d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 573adc08-6860-452b-88e6-8c1d269f1a2d
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=573adc08-6860-452b-88e6-8c1d269f1a2d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 573adc08-6860-452b-88e6-8c1d269f1a2d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=573adc08-6860-452b-88e6-8c1d269f1a2d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 573adc08-6860-452b-88e6-8c1d269f1a2d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=573adc08-6860-452b-88e6-8c1d269f1a2d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 573adc08-6860-452b-88e6-8c1d269f1a2d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 573adc08-6860-452b-88e6-8c1d269f1a2d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root EAEA7796EA775DAF
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=573adc08-6860-452b-88e6-8c1d269f1a2d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=98f144b6-4841-41f8-b51b-38c047b64a18 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=0f2db119-7d66-46df-bff5-2d1b59503cea none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 104.613849640 = 112.328265728  boot/grub/core.img                             1
 100.300941467 = 107.697315840  boot/grub/grub.cfg                             1
 103.911132812 = 111.573729280  boot/initrd.img-2.6.38-11-generic              2
 102.903320312 = 110.491598848  boot/initrd.img-2.6.38-8-generic               2
 102.970039368 = 110.563237888  boot/vmlinuz-2.6.38-11-generic                 1
 105.003238678 = 112.746369024  boot/vmlinuz-2.6.38-8-generic                  1
 103.911132812 = 111.573729280  initrd.img                                     2
 102.903320312 = 110.491598848  initrd.img.old                                 2
 102.970039368 = 110.563237888  vmlinuz                                        1
 105.003238678 = 112.746369024  vmlinuz.old                                    1

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

=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

Well ill go write it on the MBR now and see what happens... :)

---

### Post by Mark Phelps on 2011-09-09
Do yourself a favor and use the Win7 Backup feature to create a burn a Win7 Repair CD.  This way, if you have boot problems again, you can use this CD to repair them -- without having to reinstall Win7 again.

---

### Post by Vepar on 2011-09-09
> **Mark Phelps said:**
> Do yourself a favor and use the Win7 Backup feature to create a burn a Win7 Repair CD.  This way, if you have boot problems again, you can use this CD to repair them -- without having to reinstall Win7 again.

Well this time it was a clean install of Win7, so no harm done, but i'll do that, so in the future i won't mess up badly... :)

Anyway, Ubuntu is installed and GRUB is on the MBR now, so everything works fine, i can boot into both systems.

Thanks everyone for your help!


EDIT: Also, how do i mark the thread as [solved]?

---

### Post by Rubi1200 on 2011-09-10
Glad you got things worked out,

You mark a thread Solved by going to the Thread Tools near the top of the page and choosing the relevant option.

Enjoy :-)

---

