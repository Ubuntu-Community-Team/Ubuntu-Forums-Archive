---
title: "booting problem after installing Windows"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by tombaugh on 2011-01-15
Hi all,

After installing Windows 7 on one of my drives, I managed to get the grub menu back by doing this from the live CD:

```
sudo mount /dev/sdd1 /mnt 
sudo grub-install --root-directory=/mnt/ /dev/sdd
```with sdd being my primary Ubuntu drive. At this point the menu doesn't show the Windows 7 system yet.

When selecting my good old Ubuntu 10.10 system in the menu, I'm getting a command line interface, and a few error messages like this:

```
sd 3:0:0:0: timing out command, waited 7s
sd 3:0:0:0: timing out command, waited 7s
```I can then log in and do startx, but something is wrong: gparted doesn't find any devices, and update-grub doesn't find any entries (appears to hang). 

Next step: I tried rebooting several times, and just once the problem described above did not occur. I was then able to do update-grub which resulted in a menu which does show the Windows 7 system (my XP system is not shown any longer though), but after restarting and trying to boot Ubuntu I again get the command line interface, the error messages, and the problem with the devices not being found.

Any help is very much appreciated!
Thanks

---

### Post by presence1960 on 2011-01-15
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by tombaugh on 2011-01-16
Here it is...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   240,091,424   240,091,362   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   957,114,367   957,112,320  83 Linux
/dev/sdc2         957,116,414   976,773,119    19,656,706   5 Extended
/dev/sdc5         957,116,416   976,773,119    19,656,704  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   947,591,167   947,589,120  83 Linux
/dev/sdd2         947,593,214   976,771,071    29,177,858   5 Extended
/dev/sdd5         947,593,216   976,771,071    29,177,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2C88FC3188FBF764                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0533C02F1D377638                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        a670ef1d-2641-47e6-8123-e7407ae3dd3a   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        2b05656c-e2f2-4730-b65a-360c9eb511f7   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        fe2e5b7a-f82f-4974-b695-310d2fe78c48   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        38970f88-ee22-440b-9a87-826b2207c7c0   swap                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2c88fc3188fbf764
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=2b05656c-e2f2-4730-b65a-360c9eb511f7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  58.1GB: boot/grub/core.img
  58.6GB: boot/grub/grub.cfg
  58.7GB: boot/initrd.img-2.6.32-22-generic-pae
  58.9GB: boot/initrd.img-2.6.32-23-generic-pae
  59.1GB: boot/initrd.img-2.6.32-24-generic-pae
  60.1GB: boot/initrd.img-2.6.32-25-generic-pae
  11.3GB: boot/initrd.img-2.6.32-26-generic-pae
  59.2GB: boot/initrd.img-2.6.32-27-generic-pae
  58.2GB: boot/vmlinuz-2.6.32-22-generic-pae
  58.9GB: boot/vmlinuz-2.6.32-23-generic-pae
  58.9GB: boot/vmlinuz-2.6.32-24-generic-pae
  59.1GB: boot/vmlinuz-2.6.32-25-generic-pae
  59.5GB: boot/vmlinuz-2.6.32-26-generic-pae
  59.0GB: boot/vmlinuz-2.6.32-27-generic-pae
  59.2GB: initrd.img
  11.3GB: initrd.img.old
  59.0GB: vmlinuz
  59.5GB: vmlinuz.old

=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
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
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2c88fc3188fbf764
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-22-generic-pae
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

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=38970f88-ee22-440b-9a87-826b2207c7c0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


 146.1GB: boot/grub/core.img
 202.1GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.35-22-generic
 191.2GB: boot/initrd.img-2.6.35-23-generic
    .4GB: boot/initrd.img-2.6.35-24-generic
 146.3GB: boot/vmlinuz-2.6.35-22-generic
 146.5GB: boot/vmlinuz-2.6.35-23-generic
 148.2GB: boot/vmlinuz-2.6.35-24-generic
    .4GB: initrd.img
 191.2GB: initrd.img.old
 148.2GB: vmlinuz
 146.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  00 00 00 00 f0 5e 35 00  ef 09 38 00 00 7b 35 00  |.....^5...8..{5.|
00000010  00 00 00 00 00 00 00 00  e0 63 35 00 e0 79 35 00  |.........c5..y5.|
00000020  a0 74 35 00 00 00 00 00  00 00 00 00 a0 63 35 00  |.t5..........c5.|
00000030  00 0a 38 00 50 6e 35 00  00 00 00 00 00 00 00 00  |..8.Pn5.........|
00000040  00 5f 35 00 e0 6c 35 00  10 5f 35 00 00 00 00 00  |._5..l5.._5.....|
00000050  00 00 00 00 20 5f 35 00  00 00 00 00 00 00 00 00  |.... _5.........|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000080  0a 0a 38 00 a0 70 35 00  19 0a 38 00 80 6a 35 00  |..8..p5...8..j5.|
00000090  29 0a 38 00 90 72 35 00  29 0a 38 00 60 86 35 00  |).8..r5.).8.`.5.|
000000a0  38 0a 38 00 10 88 35 00  46 28 38 00 0c 00 00 00  |8.8...5.F(8.....|
000000b0  14 00 00 00 0c 00 00 00  03 00 00 00 52 28 38 00  |............R(8.|
000000c0  1b 00 00 00 23 00 00 00  1b 00 00 00 03 00 00 00  |....#...........|
000000d0  6d 28 38 00 1c 00 00 00  24 00 00 00 1c 00 00 00  |m(8.....$.......|
000000e0  03 00 00 00 36 2c 38 00  03 00 00 00 01 00 00 00  |....6,8.........|
000000f0  20 40 36 00 00 00 00 00  b0 56 36 00 e1 56 38 00  | @6......V6..V8.|
00000100  02 00 00 00 00 00 00 00  70 40 36 00 00 00 00 00  |........p@6.....|
00000110  b0 56 36 00 43 2c 38 00  05 00 00 00 01 00 00 00  |.V6.C,8.........|
00000120  20 40 36 00 00 00 00 00  70 56 36 00 fd 56 38 00  | @6.....pV6..V8.|
00000130  04 00 00 00 00 00 00 00  70 40 36 00 00 00 00 00  |........p@6.....|
00000140  70 56 36 00 54 2c 38 00  07 00 00 00 01 00 00 00  |pV6.T,8.........|
00000150  c0 40 36 00 00 00 00 00  40 42 36 00 53 30 38 00  |.@6.....@B6.S08.|
00000160  06 00 00 00 00 00 00 00  30 4a 36 00 80 41 36 00  |........0J6..A6.|
00000170  f0 56 36 00 60 2c 38 00  08 00 00 00 00 00 00 00  |.V6.`,8.........|
00000180  80 51 36 00 00 00 00 00  30 55 36 00 68 2c 38 00  |.Q6.....0U6.h,8.|
00000190  01 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  30 55 36 00 73 2c 38 00  00 00 00 00 00 00 00 00  |0U6.s,8.........|
000001b0  00 00 00 00 00 00 00 00  30 55 36 00 bb 47 00 fe  |........0U6..G..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 2b 01 00 00  |............+...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd2

00000000  69 a7 71 2a 1a 0a b4 64  f0 1c 34 66 a1 60 30 1d  |i.q*...d..4f.`0.|
00000010  60 70 5e 5d b0 45 62 f4  6a 38 28 0c 10 d5 6a 7f  |`p^].Eb.j8(...j.|
00000020  36 df b1 4e e3 3e cf 79  ce e5 cd b9 b2 fb 62 3f  |6..N.>.y......b?|
00000030  55 86 27 d6 22 b0 68 ff  46 26 47 6c 8f b0 79 e8  |U.'.".h.F&Gl..y.|
00000040  00 c2 2d 01 21 3b 5f 73  07 1e e0 e7 37 fb ee 0c  |..-.!;_s....7...|
00000050  69 3a aa d5 2b 05 79 87  b0 94 f3 52 cc 45 8a 31  |i:..+.y....R.E.1|
00000060  0d ed 04 cc aa 87 3d 5d  7e a0 0c 84 cb ed e5 41  |......=]~......A|
00000070  48 1b 54 18 79 aa 87 bf  06 2c 4e 56 59 d6 58 ed  |H.T.y....,NVY.X.|
00000080  e7 70 45 ca 48 2a 22 ad  ac f2 b6 55 07 cd 30 a6  |.pE.H*"....U..0.|
00000090  5f 67 bc 8a e0 6e 69 c3  51 28 7b 47 85 ed 25 f7  |_g...ni.Q({G..%.|
000000a0  7a d5 9d 25 ca 8e 0c c9  cb 08 e0 d5 38 96 cd 2c  |z..%........8..,|
000000b0  80 88 aa a2 f7 b5 72 9d  d4 6f 24 4b 12 b5 2b 2c  |......r..o$K..+,|
000000c0  7f df 1c 73 73 ff ea 2d  2c ab 2c 4a 14 9e 3a 2f  |...ss..-,.,J..:/|
000000d0  04 46 13 aa dc b7 2f 44  0e 20 8d ca 5b 84 8a 35  |.F..../D. ..[..5|
000000e0  78 48 f7 cb 97 b6 af c9  a2 89 ba 32 58 07 ae 78  |xH.........2X..x|
000000f0  65 fb 47 b6 71 62 41 c6  ab e1 2a e0 28 4c 0c 98  |e.G.qbA...*.(L..|
00000100  42 68 bd 50 06 09 25 8c  e4 1b ff 07 69 58 4c 9e  |Bh.P..%.....iXL.|
00000110  7f d9 4d 56 1b fe 5e 0d  06 1f 4a a8 18 14 63 dc  |..MV..^...J...c.|
00000120  06 10 1b cf 67 2b 43 cb  f0 0c 55 f0 36 a1 1e 95  |....g+C...U.6...|
00000130  f6 9c 1d 2f cc 4e 5b bd  18 b6 a5 12 c4 aa 57 14  |.../.N[.......W.|
00000140  8a 30 a5 8e 78 63 63 4a  01 80 70 58 fe 4d 71 26  |.0..xccJ..pX.Mq&|
00000150  f6 45 d0 94 da 32 ef 4f  71 fe 46 fd 26 63 75 0a  |.E...2.Oq.F.&cu.|
00000160  27 8c c7 c0 1f 9f b3 b0  bd 9e 92 d8 b1 b4 28 cf  |'.............(.|
00000170  28 25 25 11 d3 08 e3 f4  cd 34 da c5 41 ea a6 f6  |(%%......4..A...|
00000180  35 c4 2b f1 11 e5 db 83  ab bc 40 82 b2 1f 2e 81  |5.+.......@.....|
00000190  03 61 32 4c ba 20 d5 a9  2c 1e 42 fe c3 4b 08 00  |.a2L. ..,.B..K..|
000001a0  9a df 2e 4f 7b a0 61 72  55 c5 c2 a4 f7 76 f8 6c  |...O{.arU....v.l|
000001b0  d5 9c 0e 08 4a 0e 81 93  02 1a bf c6 e8 f2 00 fe  |....J...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 38 bd 01 00 00  |...........8....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by presence1960 on 2011-01-16
Everything looks OK to me. Do you have the sdd disk set as first to boot in the hard disk boot order in BIOS?

As far as your XP entry goes that is not coming back. When you installed win7 you did not change the boot flag to the partition onto which you were installing win7 so Windows did what it is programmed to do: which is combine the bootloaders. See here:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   [COLOR="Blue"]/boot.ini[/COLOR] [COLOR="Red"]/bootmgr /Boot/BCD [/COLOR][COLOR="Blue"]/ntldr /NTDETECT.COM[/COLOR]
```

The blue above is XP's boot files, the red above are part of windows 7's boot files. What will happen from GRUB when you choose windows you will then get the windows boot menu with a choice of either 7 or XP. This is because you did not change the boot flag when you installed the second version of windows.

I bowl in my league today, I won't be around till this afternoon. Post back and I will follow up.

---

### Post by tombaugh on 2011-01-16
Yes sdd is the disk to boot first. I'm indeed getting a second menu when choosing Windows 7, but when I then select "Earlier Version of Windows" the pc just reboots. But Windows is not really a concern right now, I would first like to get my Ubuntu system to work properly.

This is what I'm getting when selecting Ubuntu 10.10 (there probably is better way to make screenshots):

[IMG]http://i51.tinypic.com/3g9yw.jpg[/IMG]

If I then wait long enough it goes to the graphical login screen (or I can login and startx). Additional problems after logging in:

- I cannot mount any other drives, gparted doesn't find any devices
- I am asked for a password to unlock the login keyring, this didn't happen before
- after a minute or so the screen goes black and I'm taken to the login screen again

Thanks!

---

### Post by tombaugh on 2011-01-16
Here's an update:

- I found out that everything works fine when I disconnect the Windows 7 drive.
- I managed to boot Windows XP by doing fixmbr from the installation CD.
- When I do connect the Windows 7 drive and try to boot Ubuntu 10.04: I briefly get a CLI and see the "failed command" message but then it continues and everything appears to work as expected. With the drive disconnected I'm not getting the CLI and I'm taken straight to the desktop.
- When I do connect the Windows 7 drive and try to boot Ubuntu 10.10: I  get a CLI and experience all the problems described earlier, I can get to my desktop but other devices are not detected (for example, boot info script hangs when run on this system).

I ran the boot info script again:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   240,091,424   240,091,362   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   957,114,367   957,112,320  83 Linux
/dev/sdc2         957,116,414   976,773,119    19,656,706   5 Extended
/dev/sdc5         957,116,416   976,773,119    19,656,704  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   947,591,167   947,589,120  83 Linux
/dev/sdd2         947,593,214   976,771,071    29,177,858   5 Extended
/dev/sdd5         947,593,216   976,771,071    29,177,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2C88FC3188FBF764                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0533C02F1D377638                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        a670ef1d-2641-47e6-8123-e7407ae3dd3a   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        2b05656c-e2f2-4730-b65a-360c9eb511f7   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        fe2e5b7a-f82f-4974-b695-310d2fe78c48   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        38970f88-ee22-440b-9a87-826b2207c7c0   swap                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/0533C02F1D377638  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/fe2e5b7a-f82f-4974-b695-310d2fe78c48 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2c88fc3188fbf764
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=2b05656c-e2f2-4730-b65a-360c9eb511f7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  58.1GB: boot/grub/core.img
  58.4GB: boot/grub/grub.cfg
  58.7GB: boot/initrd.img-2.6.32-22-generic-pae
  58.9GB: boot/initrd.img-2.6.32-23-generic-pae
  59.1GB: boot/initrd.img-2.6.32-24-generic-pae
  60.1GB: boot/initrd.img-2.6.32-25-generic-pae
  11.3GB: boot/initrd.img-2.6.32-26-generic-pae
  59.2GB: boot/initrd.img-2.6.32-27-generic-pae
  58.2GB: boot/vmlinuz-2.6.32-22-generic-pae
  58.9GB: boot/vmlinuz-2.6.32-23-generic-pae
  58.9GB: boot/vmlinuz-2.6.32-24-generic-pae
  59.1GB: boot/vmlinuz-2.6.32-25-generic-pae
  59.5GB: boot/vmlinuz-2.6.32-26-generic-pae
  59.0GB: boot/vmlinuz-2.6.32-27-generic-pae
  59.2GB: initrd.img
  11.3GB: initrd.img.old
  59.0GB: vmlinuz
  59.5GB: vmlinuz.old

=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
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
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2c88fc3188fbf764
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-22-generic-pae
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

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=38970f88-ee22-440b-9a87-826b2207c7c0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


 146.1GB: boot/grub/core.img
 202.2GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.35-22-generic
 191.2GB: boot/initrd.img-2.6.35-23-generic
    .4GB: boot/initrd.img-2.6.35-24-generic
 146.3GB: boot/vmlinuz-2.6.35-22-generic
 146.5GB: boot/vmlinuz-2.6.35-23-generic
 148.2GB: boot/vmlinuz-2.6.35-24-generic
    .4GB: initrd.img
 191.2GB: initrd.img.old
 148.2GB: vmlinuz
 146.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  00 00 00 00 f0 5e 35 00  ef 09 38 00 00 7b 35 00  |.....^5...8..{5.|
00000010  00 00 00 00 00 00 00 00  e0 63 35 00 e0 79 35 00  |.........c5..y5.|
00000020  a0 74 35 00 00 00 00 00  00 00 00 00 a0 63 35 00  |.t5..........c5.|
00000030  00 0a 38 00 50 6e 35 00  00 00 00 00 00 00 00 00  |..8.Pn5.........|
00000040  00 5f 35 00 e0 6c 35 00  10 5f 35 00 00 00 00 00  |._5..l5.._5.....|
00000050  00 00 00 00 20 5f 35 00  00 00 00 00 00 00 00 00  |.... _5.........|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000080  0a 0a 38 00 a0 70 35 00  19 0a 38 00 80 6a 35 00  |..8..p5...8..j5.|
00000090  29 0a 38 00 90 72 35 00  29 0a 38 00 60 86 35 00  |).8..r5.).8.`.5.|
000000a0  38 0a 38 00 10 88 35 00  46 28 38 00 0c 00 00 00  |8.8...5.F(8.....|
000000b0  14 00 00 00 0c 00 00 00  03 00 00 00 52 28 38 00  |............R(8.|
000000c0  1b 00 00 00 23 00 00 00  1b 00 00 00 03 00 00 00  |....#...........|
000000d0  6d 28 38 00 1c 00 00 00  24 00 00 00 1c 00 00 00  |m(8.....$.......|
000000e0  03 00 00 00 36 2c 38 00  03 00 00 00 01 00 00 00  |....6,8.........|
000000f0  20 40 36 00 00 00 00 00  b0 56 36 00 e1 56 38 00  | @6......V6..V8.|
00000100  02 00 00 00 00 00 00 00  70 40 36 00 00 00 00 00  |........p@6.....|
00000110  b0 56 36 00 43 2c 38 00  05 00 00 00 01 00 00 00  |.V6.C,8.........|
00000120  20 40 36 00 00 00 00 00  70 56 36 00 fd 56 38 00  | @6.....pV6..V8.|
00000130  04 00 00 00 00 00 00 00  70 40 36 00 00 00 00 00  |........p@6.....|
00000140  70 56 36 00 54 2c 38 00  07 00 00 00 01 00 00 00  |pV6.T,8.........|
00000150  c0 40 36 00 00 00 00 00  40 42 36 00 53 30 38 00  |.@6.....@B6.S08.|
00000160  06 00 00 00 00 00 00 00  30 4a 36 00 80 41 36 00  |........0J6..A6.|
00000170  f0 56 36 00 60 2c 38 00  08 00 00 00 00 00 00 00  |.V6.`,8.........|
00000180  80 51 36 00 00 00 00 00  30 55 36 00 68 2c 38 00  |.Q6.....0U6.h,8.|
00000190  01 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  30 55 36 00 73 2c 38 00  00 00 00 00 00 00 00 00  |0U6.s,8.........|
000001b0  00 00 00 00 00 00 00 00  30 55 36 00 bb 47 00 fe  |........0U6..G..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 2b 01 00 00  |............+...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd2

00000000  69 a7 71 2a 1a 0a b4 64  f0 1c 34 66 a1 60 30 1d  |i.q*...d..4f.`0.|
00000010  60 70 5e 5d b0 45 62 f4  6a 38 28 0c 10 d5 6a 7f  |`p^].Eb.j8(...j.|
00000020  36 df b1 4e e3 3e cf 79  ce e5 cd b9 b2 fb 62 3f  |6..N.>.y......b?|
00000030  55 86 27 d6 22 b0 68 ff  46 26 47 6c 8f b0 79 e8  |U.'.".h.F&Gl..y.|
00000040  00 c2 2d 01 21 3b 5f 73  07 1e e0 e7 37 fb ee 0c  |..-.!;_s....7...|
00000050  69 3a aa d5 2b 05 79 87  b0 94 f3 52 cc 45 8a 31  |i:..+.y....R.E.1|
00000060  0d ed 04 cc aa 87 3d 5d  7e a0 0c 84 cb ed e5 41  |......=]~......A|
00000070  48 1b 54 18 79 aa 87 bf  06 2c 4e 56 59 d6 58 ed  |H.T.y....,NVY.X.|
00000080  e7 70 45 ca 48 2a 22 ad  ac f2 b6 55 07 cd 30 a6  |.pE.H*"....U..0.|
00000090  5f 67 bc 8a e0 6e 69 c3  51 28 7b 47 85 ed 25 f7  |_g...ni.Q({G..%.|
000000a0  7a d5 9d 25 ca 8e 0c c9  cb 08 e0 d5 38 96 cd 2c  |z..%........8..,|
000000b0  80 88 aa a2 f7 b5 72 9d  d4 6f 24 4b 12 b5 2b 2c  |......r..o$K..+,|
000000c0  7f df 1c 73 73 ff ea 2d  2c ab 2c 4a 14 9e 3a 2f  |...ss..-,.,J..:/|
000000d0  04 46 13 aa dc b7 2f 44  0e 20 8d ca 5b 84 8a 35  |.F..../D. ..[..5|
000000e0  78 48 f7 cb 97 b6 af c9  a2 89 ba 32 58 07 ae 78  |xH.........2X..x|
000000f0  65 fb 47 b6 71 62 41 c6  ab e1 2a e0 28 4c 0c 98  |e.G.qbA...*.(L..|
00000100  42 68 bd 50 06 09 25 8c  e4 1b ff 07 69 58 4c 9e  |Bh.P..%.....iXL.|
00000110  7f d9 4d 56 1b fe 5e 0d  06 1f 4a a8 18 14 63 dc  |..MV..^...J...c.|
00000120  06 10 1b cf 67 2b 43 cb  f0 0c 55 f0 36 a1 1e 95  |....g+C...U.6...|
00000130  f6 9c 1d 2f cc 4e 5b bd  18 b6 a5 12 c4 aa 57 14  |.../.N[.......W.|
00000140  8a 30 a5 8e 78 63 63 4a  01 80 70 58 fe 4d 71 26  |.0..xccJ..pX.Mq&|
00000150  f6 45 d0 94 da 32 ef 4f  71 fe 46 fd 26 63 75 0a  |.E...2.Oq.F.&cu.|
00000160  27 8c c7 c0 1f 9f b3 b0  bd 9e 92 d8 b1 b4 28 cf  |'.............(.|
00000170  28 25 25 11 d3 08 e3 f4  cd 34 da c5 41 ea a6 f6  |(%%......4..A...|
00000180  35 c4 2b f1 11 e5 db 83  ab bc 40 82 b2 1f 2e 81  |5.+.......@.....|
00000190  03 61 32 4c ba 20 d5 a9  2c 1e 42 fe c3 4b 08 00  |.a2L. ..,.B..K..|
000001a0  9a df 2e 4f 7b a0 61 72  55 c5 c2 a4 f7 76 f8 6c  |...O{.arU....v.l|
000001b0  d5 9c 0e 08 4a 0e 81 93  02 1a bf c6 e8 f2 00 fe  |....J...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 38 bd 01 00 00  |...........8....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by tombaugh on 2011-01-17
Another update. I reinstalled Windows XP and Windows 7 with the other drives disconnected, but my Ubuntu 10.10 still won't boot properly nor detect any other drives when the Windows 7 drive is connected.

Concerning the problematic Ubuntu 10.10 drive, is this normal (msdos1)?

```
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
```

Script run on the Ubuntu 10.04 system, there are a lot of references to msdos in the sdc part (non functional 10.10) but not in the sdb part (functional 10.04):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   957,114,367   957,112,320  83 Linux
/dev/sdb2         957,116,414   976,773,119    19,656,706   5 Extended
/dev/sdb5         957,116,416   976,773,119    19,656,704  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   947,591,167   947,589,120  83 Linux
/dev/sdc2         947,593,214   976,771,071    29,177,858   5 Extended
/dev/sdc5         947,593,216   976,771,071    29,177,856  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   240,091,424   240,091,362   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0533C02F1D377638                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a670ef1d-2641-47e6-8123-e7407ae3dd3a   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2b05656c-e2f2-4730-b65a-360c9eb511f7   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        fe2e5b7a-f82f-4974-b695-310d2fe78c48   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        38970f88-ee22-440b-9a87-826b2207c7c0   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        2C88FC3188FBF764                       ntfs                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2c88fc3188fbf764
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 0533c02f1d377638
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdd1)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=2b05656c-e2f2-4730-b65a-360c9eb511f7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  58.1GB: boot/grub/core.img
  58.4GB: boot/grub/grub.cfg
  58.7GB: boot/initrd.img-2.6.32-22-generic-pae
  58.9GB: boot/initrd.img-2.6.32-23-generic-pae
  59.1GB: boot/initrd.img-2.6.32-24-generic-pae
  60.1GB: boot/initrd.img-2.6.32-25-generic-pae
  11.3GB: boot/initrd.img-2.6.32-26-generic-pae
  59.2GB: boot/initrd.img-2.6.32-27-generic-pae
  58.2GB: boot/vmlinuz-2.6.32-22-generic-pae
  58.9GB: boot/vmlinuz-2.6.32-23-generic-pae
  58.9GB: boot/vmlinuz-2.6.32-24-generic-pae
  59.1GB: boot/vmlinuz-2.6.32-25-generic-pae
  59.5GB: boot/vmlinuz-2.6.32-26-generic-pae
  59.0GB: boot/vmlinuz-2.6.32-27-generic-pae
  59.2GB: initrd.img
  11.3GB: initrd.img.old
  59.0GB: vmlinuz
  59.5GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2c88fc3188fbf764
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic-pae (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-22-generic-pae
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=38970f88-ee22-440b-9a87-826b2207c7c0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 146.1GB: boot/grub/core.img
 202.2GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.35-22-generic
 191.2GB: boot/initrd.img-2.6.35-23-generic
    .4GB: boot/initrd.img-2.6.35-24-generic
 146.3GB: boot/vmlinuz-2.6.35-22-generic
 146.5GB: boot/vmlinuz-2.6.35-23-generic
 148.2GB: boot/vmlinuz-2.6.35-24-generic
    .4GB: initrd.img
 191.2GB: initrd.img.old
 148.2GB: vmlinuz
 146.5GB: vmlinuz.old

================================ sdd1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  00 00 00 00 f0 5e 35 00  ef 09 38 00 00 7b 35 00  |.....^5...8..{5.|
00000010  00 00 00 00 00 00 00 00  e0 63 35 00 e0 79 35 00  |.........c5..y5.|
00000020  a0 74 35 00 00 00 00 00  00 00 00 00 a0 63 35 00  |.t5..........c5.|
00000030  00 0a 38 00 50 6e 35 00  00 00 00 00 00 00 00 00  |..8.Pn5.........|
00000040  00 5f 35 00 e0 6c 35 00  10 5f 35 00 00 00 00 00  |._5..l5.._5.....|
00000050  00 00 00 00 20 5f 35 00  00 00 00 00 00 00 00 00  |.... _5.........|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000080  0a 0a 38 00 a0 70 35 00  19 0a 38 00 80 6a 35 00  |..8..p5...8..j5.|
00000090  29 0a 38 00 90 72 35 00  29 0a 38 00 60 86 35 00  |).8..r5.).8.`.5.|
000000a0  38 0a 38 00 10 88 35 00  46 28 38 00 0c 00 00 00  |8.8...5.F(8.....|
000000b0  14 00 00 00 0c 00 00 00  03 00 00 00 52 28 38 00  |............R(8.|
000000c0  1b 00 00 00 23 00 00 00  1b 00 00 00 03 00 00 00  |....#...........|
000000d0  6d 28 38 00 1c 00 00 00  24 00 00 00 1c 00 00 00  |m(8.....$.......|
000000e0  03 00 00 00 36 2c 38 00  03 00 00 00 01 00 00 00  |....6,8.........|
000000f0  20 40 36 00 00 00 00 00  b0 56 36 00 e1 56 38 00  | @6......V6..V8.|
00000100  02 00 00 00 00 00 00 00  70 40 36 00 00 00 00 00  |........p@6.....|
00000110  b0 56 36 00 43 2c 38 00  05 00 00 00 01 00 00 00  |.V6.C,8.........|
00000120  20 40 36 00 00 00 00 00  70 56 36 00 fd 56 38 00  | @6.....pV6..V8.|
00000130  04 00 00 00 00 00 00 00  70 40 36 00 00 00 00 00  |........p@6.....|
00000140  70 56 36 00 54 2c 38 00  07 00 00 00 01 00 00 00  |pV6.T,8.........|
00000150  c0 40 36 00 00 00 00 00  40 42 36 00 53 30 38 00  |.@6.....@B6.S08.|
00000160  06 00 00 00 00 00 00 00  30 4a 36 00 80 41 36 00  |........0J6..A6.|
00000170  f0 56 36 00 60 2c 38 00  08 00 00 00 00 00 00 00  |.V6.`,8.........|
00000180  80 51 36 00 00 00 00 00  30 55 36 00 68 2c 38 00  |.Q6.....0U6.h,8.|
00000190  01 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  30 55 36 00 73 2c 38 00  00 00 00 00 00 00 00 00  |0U6.s,8.........|
000001b0  00 00 00 00 00 00 00 00  30 55 36 00 bb 47 00 fe  |........0U6..G..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 2b 01 00 00  |............+...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  69 a7 71 2a 1a 0a b4 64  f0 1c 34 66 a1 60 30 1d  |i.q*...d..4f.`0.|
00000010  60 70 5e 5d b0 45 62 f4  6a 38 28 0c 10 d5 6a 7f  |`p^].Eb.j8(...j.|
00000020  36 df b1 4e e3 3e cf 79  ce e5 cd b9 b2 fb 62 3f  |6..N.>.y......b?|
00000030  55 86 27 d6 22 b0 68 ff  46 26 47 6c 8f b0 79 e8  |U.'.".h.F&Gl..y.|
00000040  00 c2 2d 01 21 3b 5f 73  07 1e e0 e7 37 fb ee 0c  |..-.!;_s....7...|
00000050  69 3a aa d5 2b 05 79 87  b0 94 f3 52 cc 45 8a 31  |i:..+.y....R.E.1|
00000060  0d ed 04 cc aa 87 3d 5d  7e a0 0c 84 cb ed e5 41  |......=]~......A|
00000070  48 1b 54 18 79 aa 87 bf  06 2c 4e 56 59 d6 58 ed  |H.T.y....,NVY.X.|
00000080  e7 70 45 ca 48 2a 22 ad  ac f2 b6 55 07 cd 30 a6  |.pE.H*"....U..0.|
00000090  5f 67 bc 8a e0 6e 69 c3  51 28 7b 47 85 ed 25 f7  |_g...ni.Q({G..%.|
000000a0  7a d5 9d 25 ca 8e 0c c9  cb 08 e0 d5 38 96 cd 2c  |z..%........8..,|
000000b0  80 88 aa a2 f7 b5 72 9d  d4 6f 24 4b 12 b5 2b 2c  |......r..o$K..+,|
000000c0  7f df 1c 73 73 ff ea 2d  2c ab 2c 4a 14 9e 3a 2f  |...ss..-,.,J..:/|
000000d0  04 46 13 aa dc b7 2f 44  0e 20 8d ca 5b 84 8a 35  |.F..../D. ..[..5|
000000e0  78 48 f7 cb 97 b6 af c9  a2 89 ba 32 58 07 ae 78  |xH.........2X..x|
000000f0  65 fb 47 b6 71 62 41 c6  ab e1 2a e0 28 4c 0c 98  |e.G.qbA...*.(L..|
00000100  42 68 bd 50 06 09 25 8c  e4 1b ff 07 69 58 4c 9e  |Bh.P..%.....iXL.|
00000110  7f d9 4d 56 1b fe 5e 0d  06 1f 4a a8 18 14 63 dc  |..MV..^...J...c.|
00000120  06 10 1b cf 67 2b 43 cb  f0 0c 55 f0 36 a1 1e 95  |....g+C...U.6...|
00000130  f6 9c 1d 2f cc 4e 5b bd  18 b6 a5 12 c4 aa 57 14  |.../.N[.......W.|
00000140  8a 30 a5 8e 78 63 63 4a  01 80 70 58 fe 4d 71 26  |.0..xccJ..pX.Mq&|
00000150  f6 45 d0 94 da 32 ef 4f  71 fe 46 fd 26 63 75 0a  |.E...2.Oq.F.&cu.|
00000160  27 8c c7 c0 1f 9f b3 b0  bd 9e 92 d8 b1 b4 28 cf  |'.............(.|
00000170  28 25 25 11 d3 08 e3 f4  cd 34 da c5 41 ea a6 f6  |(%%......4..A...|
00000180  35 c4 2b f1 11 e5 db 83  ab bc 40 82 b2 1f 2e 81  |5.+.......@.....|
00000190  03 61 32 4c ba 20 d5 a9  2c 1e 42 fe c3 4b 08 00  |.a2L. ..,.B..K..|
000001a0  9a df 2e 4f 7b a0 61 72  55 c5 c2 a4 f7 76 f8 6c  |...O{.arU....v.l|
000001b0  d5 9c 0e 08 4a 0e 81 93  02 1a bf c6 e8 f2 00 fe  |....J...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 38 bd 01 00 00  |...........8....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by tombaugh on 2011-01-17
I decided to ditch the Windows 7 drive, but I really need XP. Right now I can boot both Ubuntu systems, but when I select XP I just get a blinking cursor. Maybe I should start a new topic for that?

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 285477584 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   240,091,424   240,091,362   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   957,114,367   957,112,320  83 Linux
/dev/sdb2         957,116,414   976,773,119    19,656,706   5 Extended
/dev/sdb5         957,116,416   976,773,119    19,656,704  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   947,591,167   947,589,120  83 Linux
/dev/sdc2         947,593,214   976,771,071    29,177,858   5 Extended
/dev/sdc5         947,593,216   976,771,071    29,177,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2C88FC3188FBF764                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a670ef1d-2641-47e6-8123-e7407ae3dd3a   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2b05656c-e2f2-4730-b65a-360c9eb511f7   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        fe2e5b7a-f82f-4974-b695-310d2fe78c48   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        38970f88-ee22-440b-9a87-826b2207c7c0   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER 

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
set default="4"
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
search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
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

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2c88fc3188fbf764
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=2b05656c-e2f2-4730-b65a-360c9eb511f7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  58.1GB: boot/grub/core.img
  58.5GB: boot/grub/grub.cfg
  58.7GB: boot/initrd.img-2.6.32-22-generic-pae
  58.9GB: boot/initrd.img-2.6.32-23-generic-pae
  59.1GB: boot/initrd.img-2.6.32-24-generic-pae
  60.1GB: boot/initrd.img-2.6.32-25-generic-pae
  11.3GB: boot/initrd.img-2.6.32-26-generic-pae
  59.2GB: boot/initrd.img-2.6.32-27-generic-pae
  58.2GB: boot/vmlinuz-2.6.32-22-generic-pae
  58.9GB: boot/vmlinuz-2.6.32-23-generic-pae
  58.9GB: boot/vmlinuz-2.6.32-24-generic-pae
  59.1GB: boot/vmlinuz-2.6.32-25-generic-pae
  59.5GB: boot/vmlinuz-2.6.32-26-generic-pae
  59.0GB: boot/vmlinuz-2.6.32-27-generic-pae
  59.2GB: initrd.img
  11.3GB: initrd.img.old
  59.0GB: vmlinuz
  59.5GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
set locale_dir=($root)/boot/grub/locale
set lang=en
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

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-24-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set fe2e5b7a-f82f-4974-b695-310d2fe78c48
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a670ef1d-2641-47e6-8123-e7407ae3dd3a
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=a670ef1d-2641-47e6-8123-e7407ae3dd3a ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2c88fc3188fbf764
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=fe2e5b7a-f82f-4974-b695-310d2fe78c48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=38970f88-ee22-440b-9a87-826b2207c7c0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 146.1GB: boot/grub/core.img
 214.5GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.35-22-generic
 191.2GB: boot/initrd.img-2.6.35-23-generic
    .4GB: boot/initrd.img-2.6.35-24-generic
 146.3GB: boot/vmlinuz-2.6.35-22-generic
 146.5GB: boot/vmlinuz-2.6.35-23-generic
 148.2GB: boot/vmlinuz-2.6.35-24-generic
    .4GB: initrd.img
 191.2GB: initrd.img.old
 148.2GB: vmlinuz
 146.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  00 00 00 00 f0 5e 35 00  ef 09 38 00 00 7b 35 00  |.....^5...8..{5.|
00000010  00 00 00 00 00 00 00 00  e0 63 35 00 e0 79 35 00  |.........c5..y5.|
00000020  a0 74 35 00 00 00 00 00  00 00 00 00 a0 63 35 00  |.t5..........c5.|
00000030  00 0a 38 00 50 6e 35 00  00 00 00 00 00 00 00 00  |..8.Pn5.........|
00000040  00 5f 35 00 e0 6c 35 00  10 5f 35 00 00 00 00 00  |._5..l5.._5.....|
00000050  00 00 00 00 20 5f 35 00  00 00 00 00 00 00 00 00  |.... _5.........|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000080  0a 0a 38 00 a0 70 35 00  19 0a 38 00 80 6a 35 00  |..8..p5...8..j5.|
00000090  29 0a 38 00 90 72 35 00  29 0a 38 00 60 86 35 00  |).8..r5.).8.`.5.|
000000a0  38 0a 38 00 10 88 35 00  46 28 38 00 0c 00 00 00  |8.8...5.F(8.....|
000000b0  14 00 00 00 0c 00 00 00  03 00 00 00 52 28 38 00  |............R(8.|
000000c0  1b 00 00 00 23 00 00 00  1b 00 00 00 03 00 00 00  |....#...........|
000000d0  6d 28 38 00 1c 00 00 00  24 00 00 00 1c 00 00 00  |m(8.....$.......|
000000e0  03 00 00 00 36 2c 38 00  03 00 00 00 01 00 00 00  |....6,8.........|
000000f0  20 40 36 00 00 00 00 00  b0 56 36 00 e1 56 38 00  | @6......V6..V8.|
00000100  02 00 00 00 00 00 00 00  70 40 36 00 00 00 00 00  |........p@6.....|
00000110  b0 56 36 00 43 2c 38 00  05 00 00 00 01 00 00 00  |.V6.C,8.........|
00000120  20 40 36 00 00 00 00 00  70 56 36 00 fd 56 38 00  | @6.....pV6..V8.|
00000130  04 00 00 00 00 00 00 00  70 40 36 00 00 00 00 00  |........p@6.....|
00000140  70 56 36 00 54 2c 38 00  07 00 00 00 01 00 00 00  |pV6.T,8.........|
00000150  c0 40 36 00 00 00 00 00  40 42 36 00 53 30 38 00  |.@6.....@B6.S08.|
00000160  06 00 00 00 00 00 00 00  30 4a 36 00 80 41 36 00  |........0J6..A6.|
00000170  f0 56 36 00 60 2c 38 00  08 00 00 00 00 00 00 00  |.V6.`,8.........|
00000180  80 51 36 00 00 00 00 00  30 55 36 00 68 2c 38 00  |.Q6.....0U6.h,8.|
00000190  01 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  30 55 36 00 73 2c 38 00  00 00 00 00 00 00 00 00  |0U6.s,8.........|
000001b0  00 00 00 00 00 00 00 00  30 55 36 00 bb 47 00 fe  |........0U6..G..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 2b 01 00 00  |............+...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  69 a7 71 2a 1a 0a b4 64  f0 1c 34 66 a1 60 30 1d  |i.q*...d..4f.`0.|
00000010  60 70 5e 5d b0 45 62 f4  6a 38 28 0c 10 d5 6a 7f  |`p^].Eb.j8(...j.|
00000020  36 df b1 4e e3 3e cf 79  ce e5 cd b9 b2 fb 62 3f  |6..N.>.y......b?|
00000030  55 86 27 d6 22 b0 68 ff  46 26 47 6c 8f b0 79 e8  |U.'.".h.F&Gl..y.|
00000040  00 c2 2d 01 21 3b 5f 73  07 1e e0 e7 37 fb ee 0c  |..-.!;_s....7...|
00000050  69 3a aa d5 2b 05 79 87  b0 94 f3 52 cc 45 8a 31  |i:..+.y....R.E.1|
00000060  0d ed 04 cc aa 87 3d 5d  7e a0 0c 84 cb ed e5 41  |......=]~......A|
00000070  48 1b 54 18 79 aa 87 bf  06 2c 4e 56 59 d6 58 ed  |H.T.y....,NVY.X.|
00000080  e7 70 45 ca 48 2a 22 ad  ac f2 b6 55 07 cd 30 a6  |.pE.H*"....U..0.|
00000090  5f 67 bc 8a e0 6e 69 c3  51 28 7b 47 85 ed 25 f7  |_g...ni.Q({G..%.|
000000a0  7a d5 9d 25 ca 8e 0c c9  cb 08 e0 d5 38 96 cd 2c  |z..%........8..,|
000000b0  80 88 aa a2 f7 b5 72 9d  d4 6f 24 4b 12 b5 2b 2c  |......r..o$K..+,|
000000c0  7f df 1c 73 73 ff ea 2d  2c ab 2c 4a 14 9e 3a 2f  |...ss..-,.,J..:/|
000000d0  04 46 13 aa dc b7 2f 44  0e 20 8d ca 5b 84 8a 35  |.F..../D. ..[..5|
000000e0  78 48 f7 cb 97 b6 af c9  a2 89 ba 32 58 07 ae 78  |xH.........2X..x|
000000f0  65 fb 47 b6 71 62 41 c6  ab e1 2a e0 28 4c 0c 98  |e.G.qbA...*.(L..|
00000100  42 68 bd 50 06 09 25 8c  e4 1b ff 07 69 58 4c 9e  |Bh.P..%.....iXL.|
00000110  7f d9 4d 56 1b fe 5e 0d  06 1f 4a a8 18 14 63 dc  |..MV..^...J...c.|
00000120  06 10 1b cf 67 2b 43 cb  f0 0c 55 f0 36 a1 1e 95  |....g+C...U.6...|
00000130  f6 9c 1d 2f cc 4e 5b bd  18 b6 a5 12 c4 aa 57 14  |.../.N[.......W.|
00000140  8a 30 a5 8e 78 63 63 4a  01 80 70 58 fe 4d 71 26  |.0..xccJ..pX.Mq&|
00000150  f6 45 d0 94 da 32 ef 4f  71 fe 46 fd 26 63 75 0a  |.E...2.Oq.F.&cu.|
00000160  27 8c c7 c0 1f 9f b3 b0  bd 9e 92 d8 b1 b4 28 cf  |'.............(.|
00000170  28 25 25 11 d3 08 e3 f4  cd 34 da c5 41 ea a6 f6  |(%%......4..A...|
00000180  35 c4 2b f1 11 e5 db 83  ab bc 40 82 b2 1f 2e 81  |5.+.......@.....|
00000190  03 61 32 4c ba 20 d5 a9  2c 1e 42 fe c3 4b 08 00  |.a2L. ..,.B..K..|
000001a0  9a df 2e 4f 7b a0 61 72  55 c5 c2 a4 f7 76 f8 6c  |...O{.arU....v.l|
000001b0  d5 9c 0e 08 4a 0e 81 93  02 1a bf c6 e8 f2 00 fe  |....J...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 38 bd 01 00 00  |...........8....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

