---
title: "Installed new linux OS and it messed up my GRUB!"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by lifelike27 on 2011-01-18
I got this linux operating system to try out called Crunchbang, Installation went fine, but when I was done, it reinstalled my custom boot manager (Burg) with GRUB and now it doesn't detect my Windows or Ubuntu partition, only Crunchbang and I can't install the wireless driver on it because I only have my universities wireless to count on. =(

Can anyone help me figure out how to get this fixed, because I'm completely clueless with this. Help is much appreciated!

---

### Post by lifelike27 on 2011-01-18
Forgot to add this just in case:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4600c452

   Device Boot      Start        End      Blocks          Id     System
/dev/sda1               1           5            40131          de    Dell Utility
/dev/sda2           50319       55944    45182976+   5     Extended
/dev/sda3            2300        8906      53057536   83     Linux
/dev/sda4            8906        50319    332651520    7    HPFS/NTFS
/dev/sda5   *       50319       53464    25261056   83     Linux
/dev/sda6           53464       55944    19920896   82     Linux swap / Solaris

Partition table entries are not in disk order


The linux swap partition is the one for Crunchbang, the new OS I tried installing.

---

### Post by lifelike27 on 2011-01-18
I found the original grub.cfg file also if that's any help. I'm using my PC from my Ubuntu live CD.

---

### Post by presence1960 on 2011-01-18
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by lifelike27 on 2011-01-18
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2         808,366,079   898,732,031    90,365,953   5 Extended
/dev/sda5    *    808,366,080   858,888,191    50,522,112  83 Linux
/dev/sda6         858,890,240   898,732,031    39,841,792  82 Linux swap / Solaris
/dev/sda3          36,945,920   143,060,991   106,115,072  83 Linux
/dev/sda4         143,060,992   808,364,031   665,303,040   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2: PTTYPE="dos" 
/dev/sda3        fc68504f-916d-40e3-8d93-0225a71a6a20   ext4                                     
/dev/sda4        D8EECC50EECC2898                       ntfs       OS                            
/dev/sda6        5f6f469f-7fea-4d9f-8502-8a84b56d5ea5   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sda5: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sda3        /media/fc68504f-916d-40e3-8d93-0225a71a6a20 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fc68504f-916d-40e3-8d93-0225a71a6a20 ro   quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fc68504f-916d-40e3-8d93-0225a71a6a20 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fc68504f-916d-40e3-8d93-0225a71a6a20 ro   quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fc68504f-916d-40e3-8d93-0225a71a6a20 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fc68504f-916d-40e3-8d93-0225a71a6a20 ro   quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fc68504f-916d-40e3-8d93-0225a71a6a20 ro single 
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set fc68504f-916d-40e3-8d93-0225a71a6a20
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set d8eecc50eecc2898
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=fc68504f-916d-40e3-8d93-0225a71a6a20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=49768d01-cab8-4f21-842f-3d1ce9157510 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  18.9GB: boot/grub/core.img
  19.0GB: boot/grub/grub.cfg
  26.6GB: boot/initrd.img-2.6.35-22-generic
  31.1GB: boot/initrd.img-2.6.35-23-generic
  21.1GB: boot/initrd.img-2.6.35-24-generic
  18.9GB: boot/vmlinuz-2.6.35-22-generic
  30.6GB: boot/vmlinuz-2.6.35-23-generic
  23.0GB: boot/vmlinuz-2.6.35-24-generic
  21.1GB: initrd.img
  31.1GB: initrd.img.old
  23.0GB: vmlinuz
  30.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory

---

### Post by garvinrick4 on 2011-01-18
In a LIve CD:
```
sudo mount /dev/sda3 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```.
Go into Hard Drive and:
```
sudo update-grub
```#Do not know if os-prober in grub2 will find crunch-bang at all. I guess we know why the name Huh.

---

### Post by lifelike27 on 2011-01-19
Brilliant! I got everything back, it fixed my annoying plymouth error where it showed the kubuntu splash screen AND I got crunchbang in grub!

It's the first time I've got help fast enough for me to solve a problem like this!

Thanks once again, really appreciate it! =D

---

### Post by garvinrick4 on 2011-01-19
#Good glad we could help, in upper right corner of post mark as solved please.
#When you have a long post as your RESULTS file you can highlight the whole
text after pasted and hit the little # in the upper right corner of message box
and will put in nice box to read from. It is called code tags, enjoy your ubuntu.

---

