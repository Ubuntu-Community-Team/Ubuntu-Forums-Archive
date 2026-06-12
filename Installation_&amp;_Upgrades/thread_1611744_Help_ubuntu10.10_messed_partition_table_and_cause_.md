---
title: "Help: ubuntu10.10 messed partition table and cause xp's failure of booting"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by wild_tiger on 2010-11-02
Since the old ubuntu 9.10 of my laptop always prompted me for kernel collapse, I had to install a new version which I select is 10.10. During installing procedure, I chose to put grub2 onto logical partition. The installation was sucessful. Then I reboot the machine and booted xp. But instead of blue sky and white cloud, it presented blue screen. I guessed the reason for this might be a change of main partition table on mbr. So I restored a backup of a previous mbr, and found that xp booted happily.
I compared the two versions of mbr before and after installation of 10.10 carefully, and found that the only difference is extended partition table.
Extended partition table before installation of 10.10:
start sector: 01D4B178, size: 050D905D, both are hexcimal.
Extended partition table after installation of 10.10:
start sector: 01D4B1B5, size: 0527C64B, both are hexcimal too.
It seems that the extended partition are moved forward about 61 sectors and growing bigger. According to winhex in win environment, my hdd has 7189 (decimal) cylinders, namely 115491285(decimal) cylinders. But fdisk in ubuntu environment says that my hdd has more--7296 heads--means 117210240 sectors. Contradict result! Which one is right? I'm confused. 
 
Help!

---

### Post by wild_tiger on 2010-11-02
Is there anyone can help me?

---

### Post by oldfred on 2010-11-03
Post this so we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by wild_tiger on 2010-11-03
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst /boot.ini

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /grub.cfg /boot.ini

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,716,279    30,716,217   7 HPFS/NTFS
/dev/sda2          30,716,341   117,194,174    86,477,834   f W95 Ext d (LBA)
/dev/sda5          30,716,343    71,682,029    40,965,687   b W95 FAT32
/dev/sda6          71,682,093    75,585,824     3,903,732   b W95 FAT32
/dev/sda7          75,585,888   115,443,089    39,857,202  83 Linux
/dev/sda8         115,443,153   117,194,174     1,751,022  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0E48F8E348F8CA8B                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        30E8-098D                              vfat                                     
/dev/sda6        E66D-C5DE                              vfat                                     
/dev/sda7        8918b729-97a1-4dd0-a85f-d6d6b48ef7de   ext4                                     
/dev/sda8        554d3b3e-5a49-4d07-8743-82b2e6cc36b9   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/menu.lst: ================================

title Install Ubuntu 10.10 
root (hd0,0) 
kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.10-desktop-i386.iso 
initrd (hd0,0)/initrd.lz 
 
title Ubuntu, Linux 2.6.35-22-generic 
root (hd0,6) 
kernel /boot/vmlinuz-2.6.35-22-generic root=UUID=8918b729-97a1-4dd0-a85f-d6d6b48ef7de ro   quiet splash 
initrd /boot/initrd.img-2.6.35-22-generic 
title Ubuntu, Linux 2.6.35-22-generic (recovery mode) 
root (hd0,6) 
kernel /boot/vmlinuz-2.6.35-22-generic root=UUID=8918b729-97a1-4dd0-a85f-d6d6b48ef7de ro single 
initrd /boot/initrd.img-2.6.35-22-generic 

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\grldr="GRUB4DOS" 
C:\ubuntu.mbr="ubuntu" 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: initrd.lz
    ??GB: menu.lst
    ??GB: vmlinuz

================================ sda5/menu.lst: ================================

title Install Ubuntu 9.10 
root (hd0,0) 
kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/ubuntu-9.10-desktop-i386.iso 
initrd (hd0,0)/initrd.lz
================================ sda5/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda5: Location of files loaded by Grub: ===================


    ??GB: ??
    ??GB: ??
    myGB: menu.lst

================================ sda6/grub.cfg: ================================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
set locale_dir=($root)/boot/grub/locale
set lang=zh
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8918b729-97a1-4dd0-a85f-d6d6b48ef7de ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8918b729-97a1-4dd0-a85f-d6d6b48ef7de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

================================ sda6/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda6: Location of files loaded by Grub: ===================


    ??GB: grub.cfg

=========================== sda7/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
set locale_dir=($root)/boot/grub/locale
set lang=zh
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8918b729-97a1-4dd0-a85f-d6d6b48ef7de ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8918b729-97a1-4dd0-a85f-d6d6b48ef7de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8918b729-97a1-4dd0-a85f-d6d6b48ef7de
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=8918b729-97a1-4dd0-a85f-d6d6b48ef7de /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=554d3b3e-5a49-4d07-8743-82b2e6cc36b9 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  45.4GB: boot/grub/core.img
  45.4GB: boot/grub/grub.cfg
  51.8GB: boot/initrd.img-2.6.35-22-generic
  45.4GB: boot/vmlinuz-2.6.35-22-generic
  51.8GB: initrd.img
  45.4GB: vmlinuz

---

### Post by oldfred on 2010-11-03
When you installed, did you create partitions in advance, or let installer move things around automatically. Supposedly it will not move existing partitions but has to make space and therefore rewrite partition table. 

I always manually create partitions in advance and make sure systems, boot after partition changes before install.

I do not know the grub4dos way of booting as I use grub or grub2.

---

