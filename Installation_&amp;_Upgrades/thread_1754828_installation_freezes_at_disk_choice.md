---
title: "installation freezes at disk choice"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by yugi on 2011-05-10
hi everybody, i have just downloaded 11.04 kubuntu 64-bit and burned it on a dvd, then i started to installation but when it comes to disk layout choice it freezes in 5 seconds.
any suggestions?

---

### Post by Rubi1200 on 2011-05-10
Hi and welcome to the forums :-)

From the live desktop, open a terminal and post the output of this command in a new post here please:

```
sudo parted -l
```
(Lowercase L not 1)

Thanks.

---

### Post by yugi on 2011-05-10
Model: ATA ST9500420AS (scsi)
Disk /dev/sda: 500GB
Sektör boyutu (mant&#305;ksal/fiziksel): 512B/512B
Disk bölümü Tablosu: msdos

Numara  Ba&#351;lang&#305;ç  Son     Boyut   Tür       Dosya sistemi  Bayraklar
 1      1049kB     12,6GB  12,6GB  primary   ntfs           diag
 2      12,6GB     12,7GB  105MB   primary   ntfs           önyükleme
 3      12,7GB     120GB   107GB   primary   ntfs
 4      120GB      500GB   380GB   extended                 lba
 6      120GB      173GB   52,4GB  logical   ext4
 5      173GB      500GB   328GB   logical   ntfs

on no6 ext4 another linux installed and i want to remove it and install kubuntu at there

---

### Post by Rubi1200 on 2011-05-10
When you start the installer are you choosing the option to use manual partitioning (called Something Else now I believe)?

Is this when it freezes or does it freeze when it says it is scanning the disks?

Are you sure the image is good?

You can check the integrity to make sure:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by yugi on 2011-05-10
i am sure about the image. and yes i choose manual selection then it freezes.

---

### Post by Rubi1200 on 2011-05-10
Did you burn at the lowest possible speed? And why a DVD and not a CD?

It may not have something to do with it, but it is also worthwhile eliminating this as a possible problem. The recommended burn speed is 2-4x for best results.

I don't see anything wrong with your partition setup that would cause the problem you are describing.

---

### Post by yugi on 2011-05-10
i have done everything you said but the problem is still unsolved

---

### Post by Quackers on 2011-05-10
Maybe the boot script output may shed some light on this?
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by yugi on 2011-05-10
sorry but the command gives `No such file or directory` error
and did you noticed im trying to install kubuntu

---

### Post by Quackers on 2011-05-10
Is the script on your desktop? If it isn't you can drag and drop it there, then the command should run.
Kubuntu doesn't matter.

---

### Post by yugi on 2011-05-10
i copy pasted it but it didnt worked

---

### Post by Quackers on 2011-05-10
Ok where is the downloaded script please? In Downloads?

---

### Post by yugi on 2011-05-10
sorry, now its worked
```

[ Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,598,527    24,596,480  27 Hidden HPFS/NTFS
/dev/sda2    *     24,598,528    24,803,327       204,800   7 HPFS/NTFS
/dev/sda3          24,803,328   234,518,527   209,715,200   7 HPFS/NTFS
/dev/sda4         234,520,574   976,771,071   742,250,498   f W95 Ext d (LBA)
/dev/sda5         336,922,624   976,771,071   639,848,448   7 HPFS/NTFS
/dev/sda6         234,520,576   336,920,575   102,400,000  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E2FCC9E1FCC9B059                       ntfs       Recovery                      
/dev/sda2        DAC68B40C68B1BBF                       ntfs       System Reserved               
/dev/sda3        66E48DFBE48DCE2D                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        A8009EF9009ECE26                       ntfs       Yerel Disk                    
/dev/sda6        6fd0fa59-820a-4ce5-aa39-8239e5b75139   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="7"
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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 6fd0fa59-820a-4ce5-aa39-8239e5b75139
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 6fd0fa59-820a-4ce5-aa39-8239e5b75139
set locale_dir=($root)/boot/grub/locale
set lang=tr_TR
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 6fd0fa59-820a-4ce5-aa39-8239e5b75139
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
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
menuentry 'Ubuntu, Linux 2.6.38-8-generic ile' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 6fd0fa59-820a-4ce5-aa39-8239e5b75139
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6fd0fa59-820a-4ce5-aa39-8239e5b75139 ro vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, Linux 2.6.38-8-generic ile (kurtarma kipi)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 6fd0fa59-820a-4ce5-aa39-8239e5b75139
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6fd0fa59-820a-4ce5-aa39-8239e5b75139 ro single vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, Linux 2.6.35-28-generic ile' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 6fd0fa59-820a-4ce5-aa39-8239e5b75139
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=6fd0fa59-820a-4ce5-aa39-8239e5b75139 ro vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, Linux 2.6.35-28-generic ile (kurtarma kipi)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 6fd0fa59-820a-4ce5-aa39-8239e5b75139
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=6fd0fa59-820a-4ce5-aa39-8239e5b75139 ro single vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 6fd0fa59-820a-4ce5-aa39-8239e5b75139
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 6fd0fa59-820a-4ce5-aa39-8239e5b75139
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root E2FCC9E1FCC9B059
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root DAC68B40C68B1BBF
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=6fd0fa59-820a-4ce5-aa39-8239e5b75139 /               ext4    errors=remount-ro 0       1

=================== sda6: Location of files loaded by Grub: ===================


 161.0GB: boot/grub/core.img
 122.5GB: boot/grub/grub.cfg
 124.4GB: boot/initrd.img-2.6.35-28-generic
 121.6GB: boot/initrd.img-2.6.38-8-generic
 161.2GB: boot/vmlinuz-2.6.35-28-generic
 127.0GB: boot/vmlinuz-2.6.38-8-generic
 121.6GB: initrd.img
 124.4GB: initrd.img.old
 127.0GB: vmlinuz
 161.2GB: vmlinuz.old

```

---

### Post by Quackers on 2011-05-10
Thanks for the script output. 
Sadly, I've looked through it and I see absolutely nothing wrong with it.
I believe that you have checked the md5sum of the iso, so the only thing I can suggest is that you boot from the cd and at the first purple screen press any key. Choose your language then on the next screen select the "check for errors" option.

---

### Post by yugi on 2011-05-10
ok thanks for everything you did

---

### Post by Quackers on 2011-05-10
If you haven't checked the disc it's worth doing.
Wait and see if anybody comes up with a better idea :-)
Sorry I can't be more helpful Good luck!

---

### Post by labatts on 2011-05-11
For the record, I believe that I am having the same problem.  The only difference is that it freezes just prior to the partition selection screen.  This happens regardless of whether I boot the live cd first, or try to install directly.

I have already checked the md5sum, and that is okay.  I have already used two different downloads with two different cds.  No effects, of course.

Any help is appreciated.

---

