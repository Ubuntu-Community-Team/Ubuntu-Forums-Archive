---
title: "can't boot windows 7 after ungrading to ubuntu 10.4"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by Korose_Demo on 2010-05-30
I dual boot with windows 7. And I only use Ubuntu for school work and not 2 regularly.

I ungraded my ubuntu on Friday. and when I tried to boot into windows 7 I get a white dash/cursor flashing @ the top left of the screen and windows7 never gets to boot.

Please what do i do to fix this as I do not want to loose important files on both OS.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 275359 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 275359 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 275359 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   957,104,504   957,104,442  83 Linux
/dev/sdb2         957,104,505   976,768,064    19,663,560   5 Extended
/dev/sdb5         957,104,568   976,768,064    19,663,497  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        64741E91741E65D8                       ntfs       System Reserved               
/dev/sda2        D0C82062C82048D4                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        d7d5e98a-e098-4063-8bcb-8ddbc4124d6f   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        09c456d1-f88b-4dd2-9fa7-beaaa846732a   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/D0C82062C82048D4_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/System Reserved_  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="10"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=d7d5e98a-e098-4063-8bcb-8ddbc4124d6f ro  splash vga=799  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=d7d5e98a-e098-4063-8bcb-8ddbc4124d6f ro single  splash vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=d7d5e98a-e098-4063-8bcb-8ddbc4124d6f ro  splash vga=799  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    echo    'Loading Linux 2.6.31-20-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=d7d5e98a-e098-4063-8bcb-8ddbc4124d6f ro single  splash vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=d7d5e98a-e098-4063-8bcb-8ddbc4124d6f ro  splash vga=799  quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    echo    'Loading Linux 2.6.31-19-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=d7d5e98a-e098-4063-8bcb-8ddbc4124d6f ro single  splash vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=d7d5e98a-e098-4063-8bcb-8ddbc4124d6f ro  splash vga=799  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    echo    'Loading Linux 2.6.31-17-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=d7d5e98a-e098-4063-8bcb-8ddbc4124d6f ro single  splash vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d7d5e98a-e098-4063-8bcb-8ddbc4124d6f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 64741e91741e65d8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=d7d5e98a-e098-4063-8bcb-8ddbc4124d6f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=09c456d1-f88b-4dd2-9fa7-beaaa846732a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .6GB: boot/grub/grub.cfg
   5.1GB: boot/initrd.img-2.6.31-17-generic-pae
   5.6GB: boot/initrd.img-2.6.31-19-generic-pae
   2.9GB: boot/initrd.img-2.6.31-20-generic-pae
   2.9GB: boot/initrd.img-2.6.32-22-generic-pae
    .6GB: boot/vmlinuz-2.6.31-17-generic-pae
   5.5GB: boot/vmlinuz-2.6.31-19-generic-pae
   4.3GB: boot/vmlinuz-2.6.31-20-generic-pae
   7.2GB: boot/vmlinuz-2.6.32-22-generic-pae
   2.9GB: initrd.img
   2.9GB: initrd.img.old
   7.2GB: vmlinuz
   4.3GB: vmlinuz.old

```Thanks for your time and much anticipated response

---

### Post by darkod on 2010-05-30
During the upgrade you also installed grub2 to your win7 boot partition. Perform this fix on /dev/sda1:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to fix partition #1 on disk /dev/sda. It should work fine after that.

---

### Post by Korose_Demo on 2010-06-01
Thanks It worked. I am writing this message from windows 7.

---

