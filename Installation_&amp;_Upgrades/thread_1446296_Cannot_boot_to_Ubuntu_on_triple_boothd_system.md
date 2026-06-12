---
title: "Cannot boot to Ubuntu on triple boot/hd system"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by cappaj1 on 2010-04-03
I have three internal hard drives, one ea. with Win7, Vista and Ubuntu Ultimate 2.4

The drive with Ubunta the last one I installed on. It previously had an older version of Ubuntu Ultimate on it and I formatted the drive and installed the latest 2.4 version over it.

Prior to doing that, I used Supergrub to install a boot menu that would allow me to choose Ubuntu, or then Win7 or Vista.  

After the update to 2.4 version, I lost grub menu and only get Windows boot menu to choose Win7 or Vista. 

I downloaded the latest supergrub and insert that cd and reboot, but it can't locate the grub file and only allows me to exit and then I can get into Ubuntu.

How do I get the grub boot menu back so I can select any of the three operating systems?

Thanks for any help in advance.

---

### Post by oldfred on 2010-04-03
IF you are only getting windows are you booting from the windows drive and not from the Ubuntu drive.

Lets see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by cappaj1 on 2010-04-03
Results.txt below:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=087bea97-1c54-4592-9ade-59c753c02c59)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbce2081

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86c8741f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b1c2173

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xafb10720

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   937,167,839   937,167,777  83 Linux
/dev/sdd2         937,167,840   976,768,064    39,600,225   5 Extended
/dev/sdd5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        D27431CF7431B6D7                       ntfs       Iomega HDD                    
/dev/sdb1        7ABAABA6BAAB5D7F                       ntfs       Vista 64                      
/dev/sdc1        8A744E9C744E8AC1                       ntfs       Win 7                         
/dev/sdd1        087bea97-1c54-4592-9ade-59c753c02c59   ext4                                     
/dev/sdd5        87bfb42c-5789-4794-afbb-3dcb048b4c7b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=jim)


=========================== sdd1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd3,1)
search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro single  splash vga=795
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro single  splash vga=795
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro single  splash vga=795
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 7abaaba6baab5d7f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=087bea97-1c54-4592-9ade-59c753c02c59 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=87bfb42c-5789-4794-afbb-3dcb048b4c7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


  16.4GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
   4.3GB: boot/initrd.img-2.6.31-14-generic
   4.4GB: boot/initrd.img-2.6.31-18-generic
   4.4GB: boot/initrd.img-2.6.31-20-generic
    .4GB: boot/vmlinuz-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-18-generic
  13.1GB: boot/vmlinuz-2.6.31-20-generic
   4.4GB: initrd.img
   4.3GB: initrd.img.old
  13.1GB: vmlinuz
    .4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh sdi sdj 
```

---

### Post by theozzlives on 2010-04-03
Ubuntu 2.4 Ultimate??? No such thing. reply with a correct version and we may be able  to help. GRUB2, GRUB Legacy we don't know....

---

### Post by cappaj1 on 2010-04-03
> **theozzlives said:**
> Ubuntu 2.4 Ultimate??? No such thing. reply with a correct version and we may be able  to help. GRUB2, GRUB Legacy we don't know....

I downloaded a file called ultimate-edition-2.4-x64-gamers.iso

My desktop after installation says Ultimate Edition 2.4.

I think it's a package that includes Release Ubuntu 9.10 (karmic)
GNOME 2.28.1
Kernel 2.6.31-20-generic

---

### Post by oldfred on 2010-04-04
Your grub in sda looks to the Ubuntu install in sdd. Are you booting from sda? It looks like it should work.

I have found grub2 often goes off and installs to sda when you are booting from another drive. Standard install has an advanced buttion after selecting the partitions that lets you choose which drive to install grub to.

I always like to have operating systems on separate drives if you have more than one drive, which you do. But also have that system's boot loader in that drive so each drive can be booted if necessary via BIOS. Grub2 is good at finding other systems so I make it the boot drive in BIOS ( mine is sdc).

I would restall grub2 to sdd and eventually just for insurance install the windows boot loaders to each of their drives.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by cappaj1 on 2010-04-04
I'm booting from sdb (Vista drive) where I get the windows boot menu to choose Win7 or Vista.  

When I set the bios to boot from sdc (Win7 disk) or sdd (Ubuntu disk) I just get a flashing prompt, no boot menu at all.

---

### Post by oldfred on 2010-04-04
Try booting  sda. The syslinuxs must not be set to boot anything so they do not do any good.

---

### Post by cappaj1 on 2010-04-04
> **oldfred said:**
> Try booting  sda. The syslinuxs must not be set to boot anything so they do not do any good.

I can't select sda in the bios. I only have b,c,d and an external esata drive there.
Isn't there a utility that I can boot to that will place the grub on the correct drive?

---

### Post by oldfred on 2010-04-04
This how to has instructions for all the grub and windows versions of boot loaders:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by cappaj1 on 2010-04-04
> **oldfred said:**
> This how to has instructions for all the grub and windows versions of boot loaders:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


I followed the top section of instructions exactly, substituting my drive with linux, sdd1, and nothing. My PC still boots the same - just get Win7 and Vista options with the windows boot loader.

---

### Post by oldfred on 2010-04-04
If you are only getting windows you are booting from sdb or sdc not sdd if grub installed correctly in sdd.

---

### Post by cappaj1 on 2010-04-04
> **oldfred said:**
> If you are only getting windows you are booting from sdb or sdc not sdd if grub installed correctly in sdd.

I'm not sure what I'm doing wrong. When I set the bios to boot from the linux drive it hangs so maybe there's a problem with the grub. Maybe it's not installed correctly.

---

### Post by oldfred on 2010-04-04
IF you rerun the boot_script, it may tell us if it installed and looks ok or not.

---

### Post by cappaj1 on 2010-04-05
> **oldfred said:**
> IF you rerun the boot_script, it may tell us if it installed and looks ok or not.

Here's my grub.cfg file on the linux drive:

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd3,1)
search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro single  splash vga=795
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro single  splash vga=795
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro single  splash vga=795
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 7abaaba6baab5d7f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by oldfred on 2010-04-05
You posted grub.config not a new run of results.txt.

If you use f12 or whatever key at BIOS start says to choose boot device and select the 500GB drive what happens?? You have 3 1000GB drives so it can get confusing on which drive is sda, sdb, etc as BIOS does not label them the same.

---

### Post by cappaj1 on 2010-04-05
I have Win7 and Vista64 both on their own 1TB drives and Linux on a 500GB drive. I also have an external eSata 1TB drive connected to the system.

I'll try again the bios boot to 500GB drive and let you know what happens, shortly.

---

### Post by oldfred on 2010-04-05
I recently saw another post where the esata drive changed the drive order. That user worked with the esata drive on but not with it off as it inserted itself as sda and changed the drive order. Is the esata physically plugged into sata port1 ahead of the others?

---

### Post by cappaj1 on 2010-04-05
> **oldfred said:**
> I recently saw another post where the esata drive changed the drive order. That user worked with the esata drive on but not with it off as it inserted itself as sda and changed the drive order. Is the esata physically plugged into sata port1 ahead of the others?

Nope, the esata drive is external and connected to the esata external port on my pc. I had triple boot working with the system as is before I wiped the 500GB drive and installed newer 2.5 version of Ultimate on it, then lost the three boot option, now just win7/vista.

---

### Post by oldfred on 2010-04-05
But I do not know how esata's are connected internally. Is it plugged into the standard SATA ports on your motherboard or just into the motherboard and not changeable. Can it be changed in BIOS or with some software setting so it is not always sda?

The order of my drives sda, sdb etc is defined by the order plugged into the SATA ports.

---

### Post by cappaj1 on 2010-04-05
> **oldfred said:**
> But I do not know how esata's are connected internally. Is it plugged into the standard SATA ports on your motherboard or just into the motherboard and not changeable. Can it be changed in BIOS or with some software setting so it is not always sda?

The order of my drives sda, sdb etc is defined by the order plugged into the SATA ports.

The external esata is connected to the esata port on the back of my computer which is one of the Asus P6T motherboard's external ports.  I'll try booting to the 500TB drive next.

---

### Post by cappaj1 on 2010-04-05
Okay, when I boot from the linux 500GB drive, I get:

GRUB Loading
error: File not found
grub rescue>_

The flashing prompt doesn't respond to any commands - drive letters, exit, etc..

I inserted a supergrub cd and hit enter and it doesn't recognize anything, just goes back to 
grub rescue>_

I'm thinking the fact it says GRUB loading means it's definitely the linux drive but maybe there's a missing or bad file?

---

### Post by oldfred on 2010-04-05
I am asking about how the external port is internally connected. 

Did you have the esata drive plugged in when you installed (it looks like you did as the install says it is sdd) and then when you booted as the drive order has to be the same.

---

### Post by cappaj1 on 2010-04-05
> **oldfred said:**
> I am asking about how the external port is internally connected. 

Did you have the esata drive plugged in when you installed (it looks like you did as the install says it is sdd) and then when you booted as the drive order has to be the same.

The external drive is connected directly to the back of the motherboard where the ports are for usb, video, audio, etc. out the back of the case.

Yes I had the esata external drive connected when I installed. From looking at the Results.txt you asked for, the external sata drive is sda1, the vista is sdb1, the win7 is sdc1, and ubuntu is sdd1. 

I believe the windows boot file is on the vista drive as that was the first operating system I installed right after building the pc, so it's on sdb1.

These are not labeled the same in the bios. There are to SATA drives listed at 1TB, that are Vista and Win7, and they are Primary(Vista).

Is there anyway to have the grub on this drive, sdb1, where Vista is? That way I wouldn't have to change the bios boot order.

---

### Post by oldfred on 2010-04-05
If you scroll down to the bottom of this page it will show the SATA ports on a motherboard. Does you eSATA internal connection from the computer case to the motherboard plug into one of these, next to your other drives?
[http://www.hardwarezone.com/articles/view.php?cid=19&id=2745&pg=13](http://www.hardwarezone.com/articles/view.php?cid=19&id=2745&pg=13)

You can install grub to the MBR any of your drives but as long as you are plugging in and unplugging the eSATA and it forces its way to be sda the drive order will change and you will have problems. I do not know if there is another solution.

reinstall from working system - first find Ununtu drive, but you can use sda, sdb, sdc etc:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

Or this will reconfigure grub2 and save the location for re-installs:
sudo dpkg-reconfigure grub-pc

---

### Post by cappaj1 on 2010-04-05
> **oldfred said:**
> If you scroll down to the bottom of this page it will show the SATA ports on a motherboard. Does you eSATA internal connection from the computer case to the motherboard plug into one of these, next to your other drives?
[http://www.hardwarezone.com/articles/view.php?cid=19&id=2745&pg=13](http://www.hardwarezone.com/articles/view.php?cid=19&id=2745&pg=13)

You can install grub to the MBR any of your drives but as long as you are plugging in and unplugging the eSATA and it forces its way to be sda the drive order will change and you will have problems. I do not know if there is another solution.

reinstall from working system - first find Ununtu drive, but you can use sda, sdb, sdc etc:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

Or this will reconfigure grub2 and save the location for re-installs:
sudo dpkg-reconfigure grub-pc

No, my esata external drive doesn't connect to a port on the motherboard surface where the other internal drives are connected. There's an esata drive on the back of the board where the external ports are for the case. It's the bottom red one shown here:
[http://www.asus.com/product.aspx?P_ID=QtpKQuERkuYw6trc&templete=2](http://www.asus.com/product.aspx?P_ID=QtpKQuERkuYw6trc&templete=2)

I'm never unplugging the esata external drive. It's always been connected permanently to the pc. I had Ubuntu Ultimate on the same drive it's on now, an older version, and it was connected then and the grub menu worked fine. Since I've installed 2.4 after formatting this drive and starting fresh,I lost it.

I'll try what you suggested and try to install the grub to the vista drive and report back.

---

### Post by cappaj1 on 2010-04-05
Okay, I went into terminal and to install the grub on my vista drive where the windows boot loader, sdb1, I typed:

sudo fdisk -l
sudo grub-install /dev/sdb1

I got a message displaying it was successful, so I closed terminal, rebooted, and still only get the windows boot loader for Vista/Win7.

Wasn't sure if I was supposed to type into terminal at the end
sudo update-grub if I didn't get errors, which I didn't.

---

### Post by oldfred on 2010-04-05
anytime you make changes you want to run 
sudo update-grub

If you are still just getting windows It must not have installed to the drive you use to boot.

---

### Post by cappaj1 on 2010-04-05
> **oldfred said:**
> anytime you make changes you want to run 
sudo update-grub

If you are still just getting windows It must not have installed to the drive you use to boot.

I repeated this time with sudo update-grub, which looked like it completed normally.

Now though, when I boot, I only get GET GRUB_ and can't get to Windows OR Ubuntu.

The only thing I can do is start to a supergrub cd-rom and choose Start Linux and it get's me to Linux but I can't get to windows. Please help! I can't get my Windows 7 which is my main operating sytem back!!

Is there any way to undo what I just did and get my windows boot manager back?

---

### Post by cappaj1 on 2010-04-05
Whew! 

I followed the instructions at [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
under the section titled: [SIZE=5][COLOR=red]How to restore the Windows Vista or 7  bootloader
[/COLOR][/SIZE]n 
and was able to, using my Vista DVD install disk to repair my windows boot and now am back to choosing Win7 or Vista. Still have to boot to the supergrub cd to get to Linux though.
[SIZE=5][COLOR=red]
[/COLOR][/SIZE]

---

### Post by oldfred on 2010-04-05
With 4 drives I do not understand why you cannot install grub to another MBR and still have windows boot on the other MBR and choose in BIOS and have it work. I have 3 drives and generally have 3 different boot loaders and while usually using just grub to choose what to boot can choose to directly boot any drive with f12 or change boot order in BIOS and boot with a different boot loader.

Run your boot_info script again to see what is installed where now that you have moved things around.

---

### Post by leeper69 on 2010-04-06
I am running Ubuntu 9.10 and have 2 Ubuntu,2 Mepis and one Debian operating systems booting from Ubuntu 9.10 install but I chose to use the older grub not grub2. You might just try reinstalling Ubuntu and using the old grub.

---

### Post by cappaj1 on 2010-04-06
> **oldfred said:**
> With 4 drives I do not understand why you cannot install grub to another MBR and still have windows boot on the other MBR and choose in BIOS and have it work. I have 3 drives and generally have 3 different boot loaders and while usually using just grub to choose what to boot can choose to directly boot any drive with f12 or change boot order in BIOS and boot with a different boot loader.

Run your boot_info script again to see what is installed where now that you have moved things around.

```
            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=087bea97-1c54-4592-9ade-59c753c02c59)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /media/sdd1/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 307071 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdd and 
                       looks on partition #1 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbce2081

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86c8741f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b1c2173

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xafb10720

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   937,167,839   937,167,777  83 Linux
/dev/sdd2         937,167,840   976,768,064    39,600,225   5 Extended
/dev/sdd5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        D27431CF7431B6D7                       ntfs       Iomega HDD                    
/dev/sdb1        7ABAABA6BAAB5D7F                       ntfs       Vista 64                      
/dev/sdc1        8A744E9C744E8AC1                       ntfs       Win 7                         
/dev/sdd1        087bea97-1c54-4592-9ade-59c753c02c59   ext4                                     
/dev/sdd5        87bfb42c-5789-4794-afbb-3dcb048b4c7b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=jim)


=========================== sdd1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd3,1)
search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro single  splash vga=795
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro single  splash vga=795
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 087bea97-1c54-4592-9ade-59c753c02c59
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=087bea97-1c54-4592-9ade-59c753c02c59 ro single  splash vga=795
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 7abaaba6baab5d7f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=087bea97-1c54-4592-9ade-59c753c02c59 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=87bfb42c-5789-4794-afbb-3dcb048b4c7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   4.6GB: boot/grub/grub.cfg
   4.3GB: boot/initrd.img-2.6.31-14-generic
   4.4GB: boot/initrd.img-2.6.31-18-generic
   4.4GB: boot/initrd.img-2.6.31-20-generic
    .4GB: boot/vmlinuz-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-18-generic
  13.1GB: boot/vmlinuz-2.6.31-20-generic
   4.4GB: initrd.img
   4.3GB: initrd.img.old
  13.1GB: vmlinuz
    .4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh sdi sdj 

```

Do not understand what sda1: is??  It says it's type is Windows XP, but I don't have XP. 

sdb1 is Vista, so that's one 1TB drive and it's in Bios as SATA: PM-SAMSUNG HD 

sdc1 is Win7, so that's second 1TB drive and it's in Bios as SATA: SS-SAMSUNG HD
 
sdd1 is Ubuntu, 500MG drive in Bios (I BELIEVE??) as SATA: 4M-ST3500418A 

sdd2 and sdd5 are extended partion and swap file on Ubuntu drive I believe.

external eSATA drive doesn't look like it's listed but it has nothing but files on it anyway.

---

### Post by oldfred on 2010-04-06
Is not the sda the esata. It just says it is XP formated as it starts at sector 63 which XP & linux does where Vista and 7 start at 2048.

I just noticed you do not have any boot flag on sdd. Linux does not need one, windows does. Some BIOS require a boot flag so I would add one to see if that makes any difference. 

It looks like booting from sda or sdd should boot Ubuntu. But sdd says 
Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /media/sdd1/boot/grub.

normally it should not have the extra mount path /media/add1.

This is my entry:
Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

---

### Post by cappaj1 on 2010-04-06
> **oldfred said:**
> Is not the sda the esata. It just says it is XP formated as it starts at sector 63 which XP & linux does where Vista and 7 start at 2048.

I just noticed you do not have any boot flag on sdd. Linux does not need one, windows does. Some BIOS require a boot flag so I would add one to see if that makes any difference. 

It looks like booting from sda or sdd should boot Ubuntu. But sdd says 
Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /media/sdd1/boot/grub.

normally it should not have the extra mount path /media/add1.

This is my entry:
Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

You're right, sda is the esata external. It's shown as 1000.2GB and that's the only thing it could be cause it's the only other 1TB drive I have besides Vista and Win7 drives. 

Anyway, I'm not following you as to what to try next, sorry.

---

### Post by oldfred on 2010-04-06
Use gparted to add a boot flag to sdd1, right click on partition and eidt flags. Linux does not need it but some BIOS want one. 

Your sdd MBR does not look correct and you may need to reinstall grub. Does you grub in sda allow you to boot?

---

### Post by cappaj1 on 2010-04-06
> **oldfred said:**
> Use gparted to add a boot flag to sdd1, right click on partition and eidt flags. Linux does not need it but some BIOS want one. 

Your sdd MBR does not look correct and you may need to reinstall grub. Does you grub in sda allow you to boot?

Sorry, don't know what gparted is or how to use it. Could you guide me through it? If it's a download, a link?

I don't have a grub in sda. That's my external drive anyway. I would LIKE to reinstall grub, how do I do that? I have a couple different supergrub disks I created and can't figure out how to reinstall grub.

---

### Post by oldfred on 2010-04-06
The boot info script shows sda with grub installed in the MBR as the beginning of the script.

Gparted is the partitioning program. It is one just about every liveCD or separate download of a liveCD , in Ubuntu under system, administration, gparted. It is not normally in your install as it only can be used on unmounted partitions, but if you have multiple drives you can download from synaptic to edit unmounted drives/partitions. It is also the screen you see when installing that shows partitions.

I suggest reinstalling grub to sdd. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by cappaj1 on 2010-04-06
I used gparted to add a boot flag to sdd1, with a right click on partition and Manage flags.
Set bios to boot from linux drive. results in a
GET GRUB
and flashing curser.  Doesn't respond to any key strokes or inserting grub disk.
Set back to boot from Vista drive and back to just windows boot menu.

---

### Post by oldfred on 2010-04-06
Have you tried booting from sda and did you reinstall grub to sdd as that was the one that did not look correct.

---

### Post by cappaj1 on 2010-04-08
I'm going to put this on hold until I get someone from a linux users group locally to give me a hand. Thanks for all your help though; appreciated.

---

