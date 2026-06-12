---
title: "Ubuntu Installation Problems on hdd partition"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by Mimaste7 on 2011-02-19
**[SIZE=2]Hello, This is my first time installing Ubuntu10.10 on my desktop and every time I try to install, I get a screen with a bunch of pixelated garbage.  I have tried to boot without installing and I have also tried checking the apci = off option for installation.   I am currently running Windows 7 Ultimate x86 and I am trying to install Ubuntu to a partition on my HDD. Any help would be greatly appreciated.  My hardware specs are as follows:[/SIZE]**

**[SIZE=2] _HDD_: 320GB 7200 RPM 8MB Cache SATA 3.0Gb/s[/SIZE]**

**[SIZE=2]_RAM_: Mushkin Enhanced Silverline 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Desktop Memory Model 996768[/SIZE]**

**[SIZE=2]_CPU_: Intel Core 2 Quad Q8400 Yorkfield 2.66GHz 4MB L2 Cache LGA 775 95W Quad-Core Processor BX80580Q8400[/SIZE]**

**[SIZE=2]_POWER SUPPLY_: FSP Group FSP300-60GHS-R 300W Micro ATX 80 PLUS Certified Power Supply[/SIZE]**

**[SIZE=2]_GRAPHICS_: EVGA 512-P3-1242-LR GeForce GT 240 Superclocked 512MB 128-bit GDDR5 PCI Express 2.0 x16 HDCP Ready  Video Card[/SIZE]**

**[SIZE=2]_MOTHER BOARD_: ASRock G43Twins-FullHD LGA 775 Intel G43 Micro ATX Intel Motherboard[/SIZE]**

[SIZE=2]
[/SIZE]

---

### Post by Quackers on 2011-02-19
Welcome to UF.
When booting from the Ubuntu live cd/usb, at the first purple screen (the one with the little man at the bottom) press any key. Choose language then on the next screen select the option to check the cd for errors.
If that reports no errors, from the same screen press F6 and some options should appear, bottom right. Try the "nomodeset" option and see if the live desktop comes up (after a while).

---

### Post by Mimaste7 on 2011-02-20
Okay I was able to successfully boot Ubuntu from my CD but I tried installing it alongside Windows 7 (in a 15GB partition) and now I am not able to get to Windows.  When I bot my computer, it tries to boot my Ubuntu installation (without giving me the option to boot Windows) and then proceeds to go to the pixelated garbage I mentioned earlier.  I'm still able to boot the Live CD but I am not able to get to either operating system (although sometimes it gives me the option at startup to go into Ubuntu recovery mode).  Is there any way that I get to Ubuntu successfully and have the option of accessing my Windows 7 portion of my harddrive?

---

### Post by Mimaste7 on 2011-02-22
> **Mimaste7 said:**
> Okay I was able to successfully boot Ubuntu from my CD but I tried installing it alongside Windows 7 (in a 15GB partition) and now I am not able to get to Windows.  When I bot my computer, it tries to boot my Ubuntu installation (without giving me the option to boot Windows) and then proceeds to go to the pixelated garbage I mentioned earlier.  I'm still able to boot the Live CD but I am not able to get to either operating system (although sometimes it gives me the option at startup to go into Ubuntu recovery mode).  Is there any way that I get to Ubuntu successfully and have the option of accessing my Windows 7 portion of my harddrive?

asdf

---

### Post by Quackers on 2011-02-22
If you used the nomodeset option to boot the live cd, you will need to use that option to boot the installed version (or at least the first time you try).
While booting from the hard drive, hold down the shift key. This should bring up the grub menu. The top item should be your Ubuntu installation and it should be highlighted. If that is the case press the "e" key. On the new screen, using the arrow keys, navigate to the end of the line which says "quiet slpash" then delete those words and type in nomodeset, then press ctrl+X to boot.
If the desktop loads go to Applications menu > Accessories > terminal and open it. In the terminal copy/paste this```
sudo update-grub
``` and hit enter.
Then watch as grub.cfg is run. It should pick up a Windows Loader (maybe 2 of them). If it does you will get the grub menu by default on future startups, where you will be able to choose which OS to boot.

Whilst you are doing the above, you may get an item in the top panel which says something about installing graphics drivers. Allow the installation and then reboot. 
If nothing about graphics drivers appears, go to System > Admin > Additional Drivers and choose the recommended driver (if there are more than one) and install it. Then reboot. Hopefully this time you won't need the nomodeset option.

---

### Post by Mimaste7 on 2011-02-22
Yes! Now I can get onto Ubuntu at least...However, I believe I may have accidentally erased the Windows portion of my hard drive.  At this point, unless there is some way that you know of that I could recover Windows 7, I think I may just try putting Windows 7 on a separate hard drive.  If you know of any way that I could recover Windows 7, that would make my day, but you have helped a great deal so far.  Thank you for all your help.  :)

---

### Post by Quackers on 2011-02-22
Sadly, if you chose the "install alongside" option in the 10.10 installer, it may be the case that the installation of Ubuntu over-wrote the Windows partition. It is a fault with the installer that has been fairly well publicised recently.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mimaste7 on 2011-02-23
Here it is.  For the record, I found an old hard drive from a G3 PowerMac and I used Darik's Boot & Nuke to remove all the data from the hard drive (indicated below as sdb1).  In Ubuntu, I formatted the hard drive as ntfs using GParted.  Then, I attempted to install Windows 7 Ultimate on that hard drive (sdb1) and when given the option to choose which hard drive I wanted to install Windows on, received a message saying that the installer could not find any partition on the hard drive I had selected.   I am thinking it may be safer to just install Windows 7 on this new hard drive, but I'm running into these problems.  Nevertheless, here is my readout:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   600,565,759   600,563,712  83 Linux
/dev/sda2         600,567,806   625,141,759    24,573,954   5 Extended
/dev/sda5         600,567,808   625,141,759    24,573,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   160,831,487   160,829,440   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c08e0d58-9a4b-4a23-9846-8f0c6b7cb070   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a1770745-9568-44f6-8195-05ae6e9009b7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E224B61524B5ED23                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c08e0d58-9a4b-4a23-9846-8f0c6b7cb070
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c08e0d58-9a4b-4a23-9846-8f0c6b7cb070
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c08e0d58-9a4b-4a23-9846-8f0c6b7cb070
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=c08e0d58-9a4b-4a23-9846-8f0c6b7cb070 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c08e0d58-9a4b-4a23-9846-8f0c6b7cb070
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=c08e0d58-9a4b-4a23-9846-8f0c6b7cb070 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c08e0d58-9a4b-4a23-9846-8f0c6b7cb070
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c08e0d58-9a4b-4a23-9846-8f0c6b7cb070
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/core.img
  60.2GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-25-generic-pae
  47.3GB: boot/vmlinuz-2.6.35-25-generic-pae
    .9GB: initrd.img
  47.3GB: vmlinuz


```

---

