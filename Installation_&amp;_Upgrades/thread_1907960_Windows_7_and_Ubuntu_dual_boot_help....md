---
title: "Windows 7 and Ubuntu dual boot help..."
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by Anoobus on 2012-01-12
I have gotten Ubuntu to work but in the boot screen when I try to boot windows it just takes me back to the boot screen. Any ideas?

---

### Post by BC59 on 2012-01-12
Looks like you have problem with the Windows boot manager.

Try to repair it with Boot-Repair
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
If you have a Vista/Win7 repair CD, then boot from it and run Startup Repair. Don't be discouraged if it doesn't work at first maybe you need to do it several times to completely repair the booting process.

---

### Post by darkod on 2012-01-12
Did you use any programs like EasyBCD to add entry for ubuntu into the windows bootloader?

If you did, you created a loop.

---

### Post by Anoobus on 2012-01-12
I've been using the windows 7 boot disk for startup repair but it hasn't come up with any errors. Is this normal?

---

### Post by darkod on 2012-01-12
Follow the link in my signature and run the boot info script. Post the results as explained there. They will show more details.

---

### Post by Anoobus on 2012-01-12
Heres what it says... 



 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 874622094 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    19,431,423    19,429,376  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     19,431,424    19,636,223       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          19,636,224   874,371,071   854,734,848   7 NTFS / exFAT / HPFS
/dev/sda4         874,373,118   976,771,071   102,397,954   5 Extended
/dev/sda5         874,373,120   874,874,879       501,760  83 Linux
/dev/sda6         874,876,928   878,780,415     3,903,488  82 Linux swap / Solaris
/dev/sda7         878,782,464   898,312,191    19,529,728  83 Linux
/dev/sda8         898,314,240   976,771,071    78,456,832  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F09ADE3B9ADDFDD2                       ntfs       Recovery
/dev/sda2        18B80C83B80C619C                       ntfs       System Reserved
/dev/sda3        BA440DEA440DA9E9                       ntfs       
/dev/sda5        09da10a9-b95f-424f-b465-e56084bc5db0   ext2       
/dev/sda6        e3279351-d8cc-4354-8645-5d58fbfad744   swap       
/dev/sda7        75d5bf76-73e1-42f4-b34e-028cebccca9e   ext4       
/dev/sda8        b40cdde7-cf84-45c2-bd2d-6cb98f6eb238   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /boot                    ext2       (rw)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda8        /home                    ext4       (rw,commit=0)


============================= sda5/grub/grub.cfg: ==============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 75d5bf76-73e1-42f4-b34e-028cebccca9e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux    /vmlinuz-3.0.0-14-generic-pae root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-14-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    echo    'Loading Linux 3.0.0-14-generic-pae ...'
    linux    /vmlinuz-3.0.0-14-generic-pae root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-14-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux    /vmlinuz-3.0.0-14-generic root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /vmlinuz-3.0.0-14-generic root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux    /vmlinuz-3.0.0-12-generic root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root F09ADE3B9ADDFDD2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 18B80C83B80C619C
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

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  2
               =                grub/grub.cfg                                  1
               =                initrd.img-3.0.0-12-generic                   80
               =                initrd.img-3.0.0-14-generic                   59
               =                initrd.img-3.0.0-14-generic-pae               59
               =                vmlinuz-3.0.0-12-generic                      21
               =                vmlinuz-3.0.0-14-generic                      21
               =                vmlinuz-3.0.0-14-generic-pae                  22

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 75d5bf76-73e1-42f4-b34e-028cebccca9e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux    /vmlinuz-3.0.0-14-generic-pae root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-14-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    echo    'Loading Linux 3.0.0-14-generic-pae ...'
    linux    /vmlinuz-3.0.0-14-generic-pae root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-14-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux    /vmlinuz-3.0.0-14-generic root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /vmlinuz-3.0.0-14-generic root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux    /vmlinuz-3.0.0-12-generic root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 09da10a9-b95f-424f-b465-e56084bc5db0
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root F09ADE3B9ADDFDD2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 18B80C83B80C619C
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=75d5bf76-73e1-42f4-b34e-028cebccca9e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=09da10a9-b95f-424f-b465-e56084bc5db0 /boot           ext2    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=b40cdde7-cf84-45c2-bd2d-6cb98f6eb238 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e3279351-d8cc-4354-8645-5d58fbfad744 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             2
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic              80
               =                boot/initrd.img-3.0.0-14-generic              59
               =                boot/initrd.img-3.0.0-14-generic-pae          59
               =                boot/vmlinuz-3.0.0-12-generic                 21
               =                boot/vmlinuz-3.0.0-14-generic                 21
               =                boot/vmlinuz-3.0.0-14-generic-pae             22
               =                initrd.img                                    59
               =                initrd.img.old                                80
               =                vmlinuz                                       21
               =                vmlinuz.old                                   21

=============================== StdErr Messages: ===============================

unlzma: Decoder error
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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by darkod on 2012-01-12
```

sda2: __________________________________________________  ________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 874622094 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
```You installed grub2 to the PBR of /dev/sda2. It should be on the MBR.
/dev/sda2 is where you win7 boot files are and it needs to have a windows bootsector.

Remove grub2 from the PBR of /dev/sda2 using these instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Then install grub2 to the MBR of the disk. It seems /dev/sda5 is a /boot partition. Did you install ubuntu with separate /boot partition or not?

Boot with ubuntu cd in live mode and to install grub2 to the MBR do:
(with separate /boot)
```
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --boot-partition=/mnt/boot /dev/sda
```(without separate /boot)
```
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```In the latest ubuntu it seems there were small changes if you have separate /boot, that's why in the first option the parameter is --boot-directory and in the second option it's --root-directory. I think it should work like this. If not, maybe it should be --root-directory too in the first option. But it all depends if you have separate /boot anyway. You only need to run one group of commands, depending on that.

---

### Post by Anoobus on 2012-01-12
Thanks that fixed it!

---

