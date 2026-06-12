---
title: "Trouble Triple Booting Windows 7 32/64 Bits and Ubuntu 10.04"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by y2kardell on 2010-07-13
Hello
I am having an issue trying to triple boot Win 7 32Bit.....64Bit and Ubuntu 64Bit. I have my 2 Win 7's installed already and am able to boot into either one fine but when I install Ubunut 64Bit when it reboots and gives me the Grub loader, if I want to select one of the Win 7 OS's at the Win 7 Bootloader screen, it just gives a black screen and puts me back at the Grub screen each time. Is there something I am missing or is this a bug of some sort...............any info will be very helpful as this is driving me crazy as I have installed over and over only to come across the same problem.
 
Thanks,

---

### Post by Mark Phelps on 2010-07-13
Can you boot into ANY of the OS's? Or, is just booting into Win7 failing?

If the latter is the case, how did you make room on your drive for Ubuntu? Did you allow the Ubuntu installer to shrink one of your Win7 partitions?

If that is what you did, you will have to boot from a Win7 Repair CD and repair the boot loader of the Win7 version that is not booting.

This will wipe out GRUB, but it will get Win7 booting again.

---

### Post by y2kardell on 2010-07-13
No I split the drive into 3 partitions and installed Ubuntu on 1 that was recognized as free space. Ubuntu runs fine its just when I go to the Windows Bootloader, and try to select that it just goes through a loop and ends up right back at the Grub installer. So as of right now I no longer have access to any version of Windows 7, 32Bit or 64 after installing Ubuntu 10.04.

---

### Post by oldfred on 2010-07-13
Post the results.txt so we can see where everything is installed:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by y2kardell on 2010-07-13
> **oldfred said:**
> Post the results.txt so we can see where everything is installed:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.


                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 458135232 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 329589542. But according to the info from 
                       fdisk, sda5 starts at sector 653186898.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   323,596,287   323,389,440   7 HPFS/NTFS
/dev/sda3         323,598,334   976,773,167   653,174,834   f W95 Ext d (LBA)
/dev/sda5         653,186,898   976,773,167   323,586,270   7 HPFS/NTFS
/dev/sda6         323,598,336   653,185,023   329,586,688  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        1C18F81918F7EF9E                       ntfs       System Reserved               
/dev/sda2        A40CFADC0CFAA906                       ntfs       Windows 7 Nvidia 64 Bit       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9228622028620397                       ntfs       Windows 7 Neo Edition 32 Bit  
/dev/sda6        033caaad-2f10-4241-b2af-a7d3b00eaa2f   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 033caaad-2f10-4241-b2af-a7d3b00eaa2f
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 033caaad-2f10-4241-b2af-a7d3b00eaa2f
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
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 033caaad-2f10-4241-b2af-a7d3b00eaa2f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=033caaad-2f10-4241-b2af-a7d3b00eaa2f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 033caaad-2f10-4241-b2af-a7d3b00eaa2f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=033caaad-2f10-4241-b2af-a7d3b00eaa2f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 033caaad-2f10-4241-b2af-a7d3b00eaa2f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=033caaad-2f10-4241-b2af-a7d3b00eaa2f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 033caaad-2f10-4241-b2af-a7d3b00eaa2f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=033caaad-2f10-4241-b2af-a7d3b00eaa2f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 033caaad-2f10-4241-b2af-a7d3b00eaa2f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 033caaad-2f10-4241-b2af-a7d3b00eaa2f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1c18f81918f7ef9e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 234.5GB: boot/grub/core.img
 245.3GB: boot/grub/grub.cfg
 234.6GB: boot/initrd.img-2.6.32-21-generic
 234.6GB: boot/initrd.img-2.6.32-22-generic
 234.5GB: boot/vmlinuz-2.6.32-21-generic
 234.5GB: boot/vmlinuz-2.6.32-22-generic
 234.6GB: initrd.img
 234.6GB: initrd.img.old
 234.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by oldfred on 2010-07-13
You installed grub2 to the windows boot partitions:

sda1: _____________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot secto[/COLOR]r of sda1 and 
                       looks at sector 458135232 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Your windows in sda5 is in a logical partition and will only be bootable thru the copy of windows in sda1 or another primary partition.

---

### Post by oldfred on 2010-07-13
When/If you get windows working then you will need to reinstall grub to drive sda (not partition sda1 or sda2).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD install on sda6 and want grub2 in drive sda's MBR:
Find linux partition, change sda6 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

