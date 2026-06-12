---
title: "Can't get windows back, grub issues"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by t man x on 2011-01-11
Hello all, first off I'd just like to say that I'm a complete newb when it comes to ubuntu and I'm liking what I see so far, except I've hid a major hurdle.

I installed ubuntu for the first time, but then I used to get two boot options, "ubuntu" or "windows". So I loaded up windows and after googling a few things, managed to set ubuntu as the default option by going to system settings in windows and changing the boot options.

I am totally regretting this now, but I set the time limit to zero (ie load ubuntu without prompt) and now I can't get windows back? I have installed startup manager but the windows option on there "windows loader" does not work and does not bring it back (the screen stays blank until I have to restart).

Please help?

---

### Post by Quackers on 2011-01-11
Welcome to UF :-)
Is this a wubi installation?

---

### Post by t man x on 2011-01-11
Thanks for the welcome, Quacks

Whats a wubi? 

I'm reading another thread where someone else is also having a similar problem (windows 7 not showing up on boot)

---

### Post by Quackers on 2011-01-11
In all honesty reading about other similar problems can be misleading. Similar symptoms can have very different causes.
How did you install Ubuntu? Was it from within Windows or by booting from a live cd/usb?

---

### Post by t man x on 2011-01-11
Well first I downloaded desktop 10.04 from the install version, and I set windows as default (which for me the "windows loader option does work") so all I ended getting was a blank screen on start up. Then I got a cd and installed netbook, and thats what I'm using now

---

### Post by Quackers on 2011-01-11
Try holding down the shift key whilst booting. This should bring up the grub menu.

---

### Post by t man x on 2011-01-11
I can see the grub menu, but when I click "windows loader" it doesnt do anything

before (originally) I used to get 2 options, 1 windows, and 2 ubuntu. If I selected windows it would load, and if I selected ubuntu it would give me the options thats its giving me now (with the ubuntu recovry and windows loader etc) it skips the first part entirely

and thats the bit which I'm trying to get back

---

### Post by Quackers on 2011-01-11
Ok, please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by t man x on 2011-01-11
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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
    Boot files/dirs:   /Boot/BCD /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2             145,408    40,249,343    40,103,936   7 HPFS/NTFS
/dev/sda3    *     40,249,344   901,159,544   860,910,201   7 HPFS/NTFS
/dev/sda4         901,160,958   976,771,071    75,610,114   5 Extended
/dev/sda5         901,160,960   973,576,191    72,415,232  83 Linux
/dev/sda6         973,578,240   976,771,071     3,192,832  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       42cb883d-13f0-4df9-a428-75010d946bf6   ext4                                     
/dev/sda1        07DA-0109                              vfat       DellUtility                   
/dev/sda2        E03EAD513EAD2190                       ntfs       RECOVERY                      
/dev/sda3        7810B0B610B07CA6                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b8e3f9ae-39a1-4ac2-bbce-f329a269760c   ext4                                     
/dev/sda6        154d2687-3513-49e5-8493-e462cd5b239d   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 7810b0b610b07ca6
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 7810b0b610b07ca6
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-27-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7810b0b610b07ca6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7810b0b610b07ca6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7810b0b610b07ca6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7810b0b610b07ca6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e03ead513ead2190
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


  10.9GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.32-24-generic
    .2GB: boot/initrd.img-2.6.32-27-generic
  11.0GB: boot/vmlinuz-2.6.32-24-generic
  11.0GB: boot/vmlinuz-2.6.32-27-generic
    .2GB: initrd.img
    .6GB: initrd.img.old
  11.0GB: vmlinuz
  11.0GB: vmlinuz.old

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
search --no-floppy --fs-uuid --set b8e3f9ae-39a1-4ac2-bbce-f329a269760c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b8e3f9ae-39a1-4ac2-bbce-f329a269760c
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8e3f9ae-39a1-4ac2-bbce-f329a269760c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b8e3f9ae-39a1-4ac2-bbce-f329a269760c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8e3f9ae-39a1-4ac2-bbce-f329a269760c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b8e3f9ae-39a1-4ac2-bbce-f329a269760c ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8e3f9ae-39a1-4ac2-bbce-f329a269760c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8e3f9ae-39a1-4ac2-bbce-f329a269760c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set e03ead513ead2190
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
UUID=b8e3f9ae-39a1-4ac2-bbce-f329a269760c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=154d2687-3513-49e5-8493-e462cd5b239d none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 470.3GB: boot/grub/core.img
 474.5GB: boot/grub/grub.cfg
 474.5GB: boot/initrd.img-2.6.35-22-generic
 461.7GB: boot/vmlinuz-2.6.35-22-generic
 474.5GB: initrd.img
 461.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

I really appreciate this quacks, I know you're a brit like me (read it on the other thread) and I know you must be feeling sleepy like meeeeeeeeeeee, aargh

I'm going to download the windows repair disks tomorrow and give it a try that way :S

---

### Post by t man x on 2011-01-11
One thing I just noticed right now, I can see all my Windows 7 files, thats good, not lost anything :)

---

### Post by Quackers on 2011-01-11
You might need one! You appear to have a wubi installation and a dual boot installation, I think!
If you want to repair the one which you installed inside Windows look here for answers
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I'm not 100% sure, but if you want to repair your actual dual boot installation I think you may need to delete the wubi installation first.
Maybe another user more familiar with wubi could advise you better in that respect.

Sleep well :-)

---

### Post by bcbc on 2011-01-12
The only way to fix this I know of (without being able to boot Windows obviously) is to boot a windows 7 repair CD or DVD to a repair prompt, and manually change the timeout.
[http://technet.microsoft.com/en-us/library/cc721886(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc721886(WS.10).aspx)
> How to change boot manager time-out
To change the length of time the computer waits until the default operating system is selected, type the following:

bcdedit /timeout TimeOut

 
Option	 Explanation
TimeOut
Specifies the time to wait, in seconds, before the boot manager selects a default entry.
For example, the following command sets the boot manager TimeOut to 15 seconds:

bcdedit /timeout 15

---

### Post by t man x on 2011-01-12
Thanks for the replies guys, just to let you know I got it working!

The bcdedit thing didn't work for me, I used bootrec.exe /fixmgr which I saw on another thread and it worked :) Though it did get rid of the two ubuntu installations I had on the hard drive.

I think this happens with windows 7 as I've read about it quite a bit on other threads. Glad to have windows working again.

---

### Post by Quackers on 2011-01-12
If you get bored sometime you can try re-installing grub and see if your Ubuntu installation re-appears :-) I think it might.

---

### Post by bcbc on 2011-01-12
+1 on reinstalling grub

And the wubi is there too, just need to add an entry to bcd again.

Hint - if you reinstall grub's bootloader, you can also boot the Wubi install (without going through Windows boot manager). Just add a custom entry or hit 'c' to command prompt and enter:
```
insmod ntfs
set root=(hd0,3)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda3 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

Not really sure why you want both - but if you're using it you can keep using it that way - or just extract your data off it.

PS: thanks for the feedback on fixing the problem. I'll remember that as it crops up every so often.

---

