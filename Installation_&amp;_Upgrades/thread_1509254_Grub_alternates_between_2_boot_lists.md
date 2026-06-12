---
title: "Grub alternates between 2 boot lists"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by shy_guest on 2010-06-14
My system had a dual boot with Karmic & Windows. On Saturday I installed Lucid. 

Now Grub sometimes shows a list with Lucid, Windows & Karmic. More often it shows the old bootlist with Karmic & Windows, so I cannot boot Lucid. I have been unable to detect any logic as to when it shows one list rather than the other. 

The machine is a Sony E series preinstalled with Windows 7. 

I was (& still often am !!!) using Karmic 64 bit. 

The Lucid I installed was 32 bit.

---

### Post by dino99 on 2010-06-14
if grub1 (grub-legacy) was installed previously, you need to remove it completly and the menu.lst too (conflict when building grub2 menu), only grub-pc & grub-common need to be installed.

sudo grub-mkconfig
sudo update-grub

---

### Post by shy_guest on 2010-06-14
I was under the impression that Karmic used Grub 2. Was I mistaken ?

---

### Post by wilee-nilee on 2010-06-14
Post the script in my sig with code tags, this will tell us exactly whats going on.

---

### Post by shy_guest on 2010-06-14
Do not understand about code tags. Could you please explain about which bits I have to tag.   

Here is the beginning of the contents of RESULTS.txt

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x67a88877

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    19,204,095    19,202,048  27 Hidden HPFS/NTFS
/dev/sda2    *     19,204,096    19,408,895       204,800   7 HPFS/NTFS
/dev/sda3          19,408,896   134,287,334   114,878,439   7 HPFS/NTFS
/dev/sda4         134,287,396   976,773,119   842,485,724   5 Extended
/dev/sda5         134,287,398   159,670,034    25,382,637  82 Linux swap / Solaris
/dev/sda6         159,670,098   859,573,889   699,903,792  83 Linux
/dev/sda7         859,573,953   888,876,449    29,302,497  83 Linux
/dev/sda8         888,877,056   973,080,575    84,203,520  83 Linux
/dev/sda9         973,082,624   976,773,119     3,690,496  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9ABC6BBFBC6B9493                       ntfs       Recovery                      
/dev/sda2        729E6CAE9E6C6D13                       ntfs       System Reserved               
/dev/sda3        68C26E2FC26E01A4                       ntfs                                     
/dev/sda5        bdd9b976-4332-496a-abd9-924c01364263   swap                                     
/dev/sda6        306d1034-b400-4e4d-b6cd-73290ddd79cc   ext4                                     
/dev/sda7        2fb03b05-c109-4604-b3e9-4dc121c8d6ba   ext4                                     
/dev/sda8        c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5   ext4                                     
/dev/sda9        20e35f86-b5eb-4c5d-b1c6-405a9ab10c72   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 9abc6bbfbc6b9493
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 729e6cae9e6c6d13
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by shy_guest on 2010-06-14
& here is the rest :


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=306d1034-b400-4e4d-b6cd-73290ddd79cc /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=bdd9b976-4332-496a-abd9-924c01364263 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=75ab919d-7ef7-4bc3-9849-da547cc4d51d none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 443.5GB: boot/grub/core.img
 442.8GB: boot/grub/grub.cfg
 440.9GB: boot/initrd.img-2.6.31-14-generic
 443.7GB: boot/initrd.img-2.6.31-20-generic
 444.0GB: boot/initrd.img-2.6.31-21-generic
 444.0GB: boot/initrd.img-2.6.31-22-generic
 442.0GB: boot/vmlinuz-2.6.31-14-generic
 443.1GB: boot/vmlinuz-2.6.31-20-generic
 443.8GB: boot/vmlinuz-2.6.31-21-generic
 443.9GB: boot/vmlinuz-2.6.31-22-generic
 444.0GB: initrd.img
 444.0GB: initrd.img.old
 443.9GB: vmlinuz
 443.8GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set default="0"
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9abc6bbfbc6b9493
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 729e6cae9e6c6d13
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro single
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2fb03b05-c109-4604-b3e9-4dc121c8d6ba
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=2fb03b05-c109-4604-b3e9-4dc121c8d6ba ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=c81cfa02-ce5c-49d7-b96c-4d50b2ffd8f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=20e35f86-b5eb-4c5d-b1c6-405a9ab10c72 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 485.3GB: boot/grub/core.img
 463.9GB: boot/grub/grub.cfg
 483.4GB: boot/initrd.img-2.6.32-21-generic
 483.6GB: boot/initrd.img-2.6.32-22-generic
 483.1GB: boot/vmlinuz-2.6.32-21-generic
 483.1GB: boot/vmlinuz-2.6.32-22-generic
 483.6GB: initrd.img
 483.4GB: initrd.img.old
 483.1GB: vmlinuz
 483.1GB: vmlinuz.old

---

### Post by darkod on 2010-06-14
It comes down to what bootloader you want to use, grub2 from Karmic or Lucid? It seems you are now using Karmic grub2 and after installing Lucid you haven't updated it.

Just boot Karmic and run:

sudo update-grub

If you want to switch to using Lucif grub2 on the MBR, boot into Lucid once it's in the boot menu, and do:

sudo grub-install /dev/sda

---

