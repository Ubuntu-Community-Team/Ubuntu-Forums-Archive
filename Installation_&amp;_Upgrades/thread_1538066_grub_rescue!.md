---
title: "grub rescue!"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by laimigrante on 2010-07-24
i was trying to install ubuntu in a usb, just to learn, because im a new user, i was trying before to install pclinuxos and ubuntu together and cant do it, didnt work, so in my other laptop with windows 7 i try to install ubuntu in a usb and trying to keep updated and when i learn how to install ubuntu and pclinuxos together i will have the usb uddated, but now im having problems with windows do not open windows if im not using the usb, i need to resolve this, the worst part it that kinda work both togegher that will be great is that is in my hard disk not in a usb.
maybe the problem is easy to solve but i dont have any idea.

---

### Post by kansasnoob on 2010-07-24
What happens is that currently (behavior to change soon) when installing to a USB drive or any non-first hard drive grub is still installed to /dev/sda. Meierfra wrote a bit about that:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

If that's a bit too technical for you then please post the output of the Boot Info Script as described below and I'll type some personalized commands for you:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by laimigrante on 2010-07-24
i try to do as both links u gave me, the first one try to write as said in the page but when i restart the computer the same problem, then go to the other link an give Authentication failure, everytime i write su when i type the password, and also try to dowload the link in the page and also didnt work.
:( still lost here.

---

### Post by kansasnoob on 2010-07-24
Maybe these instructions for the Boot Info Script will be easier to follow:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Note that by default Firefox in Karmic and Lucid downloads things to "~/Downloads", you can see by going to Edit > Preferences > General in Firefox (I always set mine to ask me).

---

### Post by laimigrante on 2010-07-24
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    29,362,175    29,360,128  27 Hidden HPFS/NTFS
/dev/sda2    *     29,362,176   625,141,759   595,779,584   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4066 MB, 4066377728 bytes
126 heads, 62 sectors/track, 1016 cylinders, total 7942144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,936,991     7,936,930  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D01A099C1A0980A8                       ntfs       PQSERVICE                     
/dev/sda2        7C444289444245DC                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6ad86166-3726-4886-bb4c-90cf9f3c0a5f   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 6ad86166-3726-4886-bb4c-90cf9f3c0a5f
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
search --no-floppy --fs-uuid --set 6ad86166-3726-4886-bb4c-90cf9f3c0a5f
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6ad86166-3726-4886-bb4c-90cf9f3c0a5f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6ad86166-3726-4886-bb4c-90cf9f3c0a5f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6ad86166-3726-4886-bb4c-90cf9f3c0a5f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6ad86166-3726-4886-bb4c-90cf9f3c0a5f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6ad86166-3726-4886-bb4c-90cf9f3c0a5f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6ad86166-3726-4886-bb4c-90cf9f3c0a5f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d01a099c1a0980a8
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7c444289444245dc
    chainloader +1
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
/dev/sdc1       /               ext4    errors=remount-ro 0       1

=================== sdb1: Location of files loaded by Grub: ===================


    .8GB: boot/grub/core.img
   2.6GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.32-21-generic
   1.7GB: boot/vmlinuz-2.6.32-21-generic
    .8GB: initrd.img
   1.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by kansasnoob on 2010-07-25
It looks you're part way there already but just to be certain boot into the Ubuntu on the external drive and copy-n-paste the following commands:

```
sudo grub-install /dev/sdb
```

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Then you should be able to boot Windows with the external drive unplugged, and both Ubuntu or Windows with the external plugged in.

---

### Post by laimigrante on 2010-07-25
thank u so much, now windows is working normally without the usb.
thanks!

did u know some easy way how to install pclinuxos and ubuntu together? is because i try but i can access the first one after the other is install, and pclinuxox updates are too many, so i dont want me to take me forever doing all over again.
thanks again.

---

### Post by leclerc65 on 2010-07-25
pclinuxos on the PC and Ubuntu on the USB ?

When installing Ubuntu click on _Advanced_ then put the Grub on the USB.

---

### Post by kansasnoob on 2010-07-25
> **laimigrante said:**
> thank u so much, now windows is working normally without the usb.
thanks!

did u know some easy way how to install pclinuxos and ubuntu together? is because i try but i can access the first one after the other is install, and pclinuxox updates are too many, so i dont want me to take me forever doing all over again.
thanks again.

I'm not familiar with the PCLinuxOS installer so I'm not sure what it's options are regarding the installation of grub.

Where are you planning on installing it? A separate external?

I doubt it would fit on that small 4GB drive along side Ubuntu.

One thing I'd particularly warn you of: always use only Windows own tools for changing partition sizes in Win7 or Vista! Shrinking Vista or Win7 partitions using Gparted can cause very bad problems.

---

### Post by laimigrante on 2010-07-25
not is not in the usb or the laptop with windows, i have another that i erase windows and want to use just to learn linux, so i want to have in the same hard disk ubuntu and pclinuxos, is a laptop too, but in the last updated i run in pclinuxos something happend that i cant thether with my phone, so i want to have another distro just in case and to learn, and the only gnome i like is ubuntu and pclinuxos gnome, but i dont want distros from the same family. and also is so easy for me using my phone with ubuntu and works greats.

---

