---
title: "Minimal bash (grub)"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by Tkdboy on 2011-05-18
hello,
i upgraded the ubuntu to 10.10 and i cant login to ubuntu neither to Win7.

I can only see:
Minimal bash-like line editing is supported.
grub>

Any ideas?

i have ubuntu and win7.

Thanks

---

### Post by lmarmisa on 2011-05-18
Please, boot your system into a Ubuntu Live CD/USB, open Firefox and visit the page

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then run the Boot Info Script according to instructions.

Finally, post the results here.

---

### Post by Tkdboy on 2011-05-18
thanks man.
I ll try it and i ll post the results...

---

### Post by Tkdboy on 2011-05-19
Here are the results:

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........F.:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 17640 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   315,643,903   312,569,856   7 NTFS / exFAT / HPFS
/dev/sda3         315,643,904   522,741,759   207,097,856   7 NTFS / exFAT / HPFS
/dev/sda4         522,755,100   625,137,344   102,382,245   5 Extended
/dev/sda5         522,755,163   620,864,054    98,108,892  83 Linux
/dev/sda6         620,864,118   625,137,344     4,273,227  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       71352458-3c4a-4648-a71b-f6a35a808784   ext2       casper-rw
/dev/sda1        B4C0BDF1C0BDBA46                       ntfs       WinRE
/dev/sda2        5C76F92176F8FC98                       ntfs       
/dev/sda3        BEF0E1DEF0E19CC1                       ntfs       Data
/dev/sda5        8ff8e748-581c-4626-8d9c-8d8c450812dc   ext4       
/dev/sda6        4ed45762-436a-45f3-ad96-fc8105e6a2df   swap       
/dev/sdb1        7464-7AE7                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, with Linux 2.6.38-9-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    linux    /boot/vmlinuz-2.6.38-9-generic-pae root=UUID=8ff8e748-581c-4626-8d9c-8d8c450812dc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-9-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    echo    'Loading Linux 2.6.38-9-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-9-generic-pae root=UUID=8ff8e748-581c-4626-8d9c-8d8c450812dc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-9-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=8ff8e748-581c-4626-8d9c-8d8c450812dc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    echo    'Loading Linux 2.6.38-9-generic ...'
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=8ff8e748-581c-4626-8d9c-8d8c450812dc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    linux    /boot/vmlinuz-2.6.35-29-generic root=UUID=8ff8e748-581c-4626-8d9c-8d8c450812dc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    echo    'Loading Linux 2.6.35-29-generic ...'
    linux    /boot/vmlinuz-2.6.35-29-generic root=UUID=8ff8e748-581c-4626-8d9c-8d8c450812dc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=8ff8e748-581c-4626-8d9c-8d8c450812dc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=8ff8e748-581c-4626-8d9c-8d8c450812dc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
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
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 8ff8e748-581c-4626-8d9c-8d8c450812dc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 5C76F92176F8FC98
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8ff8e748-581c-4626-8d9c-8d8c450812dc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4ed45762-436a-45f3-ad96-fc8105e6a2df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 249.401193142 = 267.792492032  boot/grub/core.img                             1
 251.983109951 = 270.564804096  boot/grub/grub.cfg                             1
 255.198773861 = 274.017596928  boot/initrd.img-2.6.32-32-generic              2
 250.652577877 = 269.136156160  boot/initrd.img-2.6.35-29-generic              2
 250.667623043 = 269.152310784  boot/initrd.img-2.6.38-9-generic               2
 257.649892330 = 276.649465344  boot/initrd.img-2.6.38-9-generic-pae           2
 253.847211361 = 272.566367744  boot/vmlinuz-2.6.32-32-generic                 1
 254.737615108 = 273.522431488  boot/vmlinuz-2.6.35-29-generic                 1
 256.507672787 = 275.423016448  boot/vmlinuz-2.6.38-9-generic                  1
 256.570298672 = 275.490260480  boot/vmlinuz-2.6.38-9-generic-pae              1
 257.649892330 = 276.649465344  initrd.img                                     2
 250.667623043 = 269.152310784  initrd.img.old                                 2
 256.570298672 = 275.490260480  vmlinuz                                        1
 256.507672787 = 275.423016448  vmlinuz.old                                    1

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

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```
What should I do now??

---

### Post by lmarmisa on 2011-05-19
Try to reinstall GRUB. I recommend to follow this method based on the command chroot:

[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

Please, boot into a Ubuntu Live CD/USB with the same version of Ubuntu which you have installed, open a terminal and type these commands:

```

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
update-grub
grub-install /dev/sda
grub-install --recheck /dev/sda
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt
sudo reboot

```

Abort the procedure if you get some error.

---

### Post by Tkdboy on 2011-05-19
you are GENIUS man, problem solved.

Thanks a lot!!!

---

### Post by lmarmisa on 2011-05-19
Great!!!. Congratulations!!!. But I am not a genius. ):P

Please, mark the thread as SOLVED.

---

### Post by Tkdboy on 2011-05-19
hahaha!!

DONE!!!!

---

### Post by mhgsys on 2011-05-19
see sig

edit; you found how to mark it as solved right before my post.

srry for taking up space

---

