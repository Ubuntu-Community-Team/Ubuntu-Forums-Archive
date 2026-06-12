---
title: "Triple boot: OS X, Ubuntu &amp; Windows 7 = Trouble"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by lifelike27 on 2011-04-25
Hey,

So I'm following this tutorial for going about the triple booting all three operating systems: [http://bigfloppydonkeydisk.blogspot.com/2010/07/triple-boot-windows-7-mac-os-x-snow.html](http://bigfloppydonkeydisk.blogspot.com/2010/07/triple-boot-windows-7-mac-os-x-snow.html)

I'm able to successfully install Mac OS X followed by Windows 7. At this point, when restarting, Windows 7 ignores the OS X operating system (as mentioned in the article), and boots up Windows. 

Then, after installing Ubuntu and doing the first restart required, I get an error saying:
```
Intel UNDI, PXE-2.1 (build 083)
Copyright (C) 1997-2000 Intel Corporation

This Product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776 and US6,327,625

Realtek PCIe GBE Family Controller Series v2.29 (06/30/09)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.

Operating System not found.
```

From what I understand, it has something to do with the MBR file system. Mac OS X, requires a GUID partitions system, so OS X is installed first for that reason with partitions made for the other operating system during the OS X installation.

I should also mention my computer specs, which are found here:
[http://dl.dropbox.com/u/8515110/hardinfo_report.html](http://dl.dropbox.com/u/8515110/hardinfo_report.html)

Thanks in advance!

---

### Post by Hedgehog1 on 2011-04-25
What are you, Nuts! :D

Not really - just kidding!  Or best chance of helping you starts with getting disk info from you.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by lifelike27 on 2011-04-25
Thanks! I haven't partitioned the hard drive the way I'm supposed to be though. I had to go back to using MBR because I needed Windows 7 and Ubuntu working more importantly. 

I'm getting OS X because I might be getting a job in an Apple store so I need to something about the ridiculous thing first! Never bothered to learn more about it in detail before.

---

### Post by Hedgehog1 on 2011-04-25
A job at the Apple store sounds rather fun - Hope you get it!

One thought is to go to a DIFFERENT apple store and play with the hardware there. ** Wear a false mustache or something.**


***The 'Undercover' Hedge***

:KS

---

### Post by lifelike27 on 2011-04-25
Haha, brilliant idea.  I'm done I can stick ubuntu logo stickers where those Apple logos are! That'll be my trademark sign!

---

### Post by lifelike27 on 2011-04-25
> **Hedgehog1 said:**
> What are you, Nuts! :D

Not really - just kidding!  Or best chance of helping you starts with getting disk info from you.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

Here's the results from running the boot info script:

Web link as well: [http://dl.dropbox.com/u/8515110/RESULTS.txt](http://dl.dropbox.com/u/8515110/RESULTS.txt)


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   197,396,734   197,396,672   7 HPFS/NTFS
/dev/sda2         197,398,528   379,232,255   181,833,728  83 Linux
/dev/sda3         394,793,469   976,773,167   581,979,699   7 HPFS/NTFS
/dev/sda4         379,232,256   394,792,959    15,560,704  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BC427FAB427F68D2                       ntfs       OS                            
/dev/sda2        aa8f4543-9ca0-4741-98c2-a72fc546caf0   ext4                                     
/dev/sda3        C4F29556F2954D94                       ntfs       store                         
/dev/sda4        422c0513-a0fa-4d3b-ba0b-8c3ca4e022ba   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sda2        /media/aa8f4543-9ca0-4741-98c2-a72fc546caf0 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root aa8f4543-9ca0-4741-98c2-a72fc546caf0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root aa8f4543-9ca0-4741-98c2-a72fc546caf0
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root aa8f4543-9ca0-4741-98c2-a72fc546caf0
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=aa8f4543-9ca0-4741-98c2-a72fc546caf0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root aa8f4543-9ca0-4741-98c2-a72fc546caf0
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=aa8f4543-9ca0-4741-98c2-a72fc546caf0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root aa8f4543-9ca0-4741-98c2-a72fc546caf0
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=aa8f4543-9ca0-4741-98c2-a72fc546caf0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root aa8f4543-9ca0-4741-98c2-a72fc546caf0
    echo    'Loading Linux 2.6.38-7-generic ...'
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=aa8f4543-9ca0-4741-98c2-a72fc546caf0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-7-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root aa8f4543-9ca0-4741-98c2-a72fc546caf0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root aa8f4543-9ca0-4741-98c2-a72fc546caf0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BC427FAB427F68D2
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
# Commented out by Dropbox
# UUID=aa8f4543-9ca0-4741-98c2-a72fc546caf0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=422c0513-a0fa-4d3b-ba0b-8c3ca4e022ba none            swap    sw              0       0
UUID=aa8f4543-9ca0-4741-98c2-a72fc546caf0 / ext4 errors=remount-ro,user_xattr 0 1
/dev/sda3       /media/store        ntfs    rw,user,auto,fmask=0177,dmask=0077,uid=1000   0       0

=================== sda2: Location of files loaded by Grub: ===================


 105.5GB: boot/grub/core.img
 105.5GB: boot/grub/grub.cfg
 148.5GB: boot/initrd.img-2.6.38-7-generic
 119.8GB: boot/initrd.img-2.6.38-8-generic
 101.3GB: boot/vmlinuz-2.6.38-7-generic
 109.5GB: boot/vmlinuz-2.6.38-8-generic
 119.8GB: initrd.img
 148.5GB: initrd.img.old
 109.5GB: vmlinuz
 101.3GB: vmlinuz.old
```

---

### Post by Hedgehog1 on 2011-04-25
This boot script is an MBR disk with Windows and Ubuntu.

I don't see an install attempt of OSX on it - is this the 'after you cleaned it up' version?

***The Hedge***

:KS

---

### Post by lifelike27 on 2011-04-25
> **lifelike27 said:**
> Thanks! I haven't partitioned the hard drive the way I'm supposed to be though. I had to go back to using MBR because I needed Windows 7 and Ubuntu working more importantly. 


Yup. :)

---

### Post by lifelike27 on 2011-04-26
Bump?

---

### Post by lifelike27 on 2011-05-03
Can anyone help me with that error I get after I install Ubuntu? I don't want to have only OS X and Windows if can't enjoy Ubuntu. I live off it! :D

---

