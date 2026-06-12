---
title: "Stops at Grub, might be EasyBCD, might not"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by B-Navigator on 2010-11-26
Ok, here's the situation.  I had a few system problems, and decided installing Linux might offer a good tool for fixing them up, plus I've been meaning to kick the tires on the latest version.  Anyways, after a bit of futzing with disks, windows and linux install disks and the bios, the problems seem to have fixed themselves, and I've got a partition with Linux on my boot drive.
Now, as soon as I successfully booted to the grub menu I booted into windows and used EasyBCD to set up the dual boot as per [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu).  Then I tried booting into Ubuntu (Version 10.10), and after one or two screens flashed by too fast for me to really make them out, it halted on a black screen with white text.  At the top was the line:
Grub4dos q.4.55 2010=07=25, mem 636k/3326m/4864m end:34c6cb
There was a boxed paragraph explaining minimal "Bash like" editing was supported, then below was
Grub>

And of course because I modified the boot before booting from the origional loader, I don't actually know if this is a problem with the install or something messed up by EasyBCD.

---

### Post by wilee-nilee on 2010-11-26
Personally; easybcd2 is a last ditch need in my book.

Post the bootscript in my signature. Read the instruction on getting the text file generated. Come back to your thread open a reply window, then click on the # in the reply panel. Magically code tags will appear, paste all of the text from the generated file in between.

---

### Post by B-Navigator on 2010-11-27
Ok, sorry for the delay, but had a few other things that needed doing first.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #4 for (,gpt4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 2 in the file /NST/nst_linux.mbr looks at sector 
                       2831550944 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 2,712,032,724 2,711,825,877   7 HPFS/NTFS
/dev/sda3       2,712,033,278 2,930,276,351   218,243,074   5 Extended
/dev/sda5       2,712,033,280 2,921,318,399   209,285,120  83 Linux
/dev/sda6       2,921,320,448 2,930,276,351     8,955,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        820EC8C20EC8B109                       ntfs       System Reserved               
/dev/sda2        9636CB4136CB20DB                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        90ea2151-656b-44e9-a0b3-ccc7346c8898   ext4                                     
/dev/sda6        a50ac44a-aff2-4f18-b761-f76716d0f714   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C8E65906E658F662                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        50E239EBE239D5C6                       ntfs       Disk Second                   
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        72B0C4BFB0C48B55                       ntfs       Drive3                        
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 90ea2151-656b-44e9-a0b3-ccc7346c8898
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 90ea2151-656b-44e9-a0b3-ccc7346c8898
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 90ea2151-656b-44e9-a0b3-ccc7346c8898
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=90ea2151-656b-44e9-a0b3-ccc7346c8898 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 90ea2151-656b-44e9-a0b3-ccc7346c8898
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=90ea2151-656b-44e9-a0b3-ccc7346c8898 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 90ea2151-656b-44e9-a0b3-ccc7346c8898
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 90ea2151-656b-44e9-a0b3-ccc7346c8898
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 820ec8c20ec8b109
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=90ea2151-656b-44e9-a0b3-ccc7346c8898 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a50ac44a-aff2-4f18-b761-f76716d0f714 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


1444.6GB: boot/grub/core.img
1436.0GB: boot/grub/grub.cfg
1389.4GB: boot/initrd.img-2.6.35-23-generic-pae
1444.5GB: boot/vmlinuz-2.6.35-23-generic-pae
1389.4GB: initrd.img
1444.5GB: vmlinuz
```

---

### Post by Quackers on 2010-11-27
Grub is installed in the mbr of sdd. It needs to be installed to the mbr of sda.
Boot from the Ubuntu Live cd or usb and open up a terminal (Applications > Accessories > Terminal) and copy/paste these commands to the terminal one line at a time.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Then reboot. If the system boots straight to Ubuntu (without seeing a grub menu) open up a terminal and run
```
sudo update-grub
```
and watch as grub.cfg is configured to see if the Windows (loader) is picked up.
If it is you should be able to reboot and from the grub menu choose Windows 7 as a boot option.
If not please come back :-)

---

