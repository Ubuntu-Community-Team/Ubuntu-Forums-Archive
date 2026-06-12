---
title: "help reinstalling ubuntu 9.10"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by valued customer on 2010-03-11
ok so i deleted the ubuntu partition and managed to get windows xp to boot again, reinstalled ubuntu but when it tries to boot i get an error.

grub loading
error no such partition
grub rescue

any ideas how to get this up and running again?

---

### Post by jjcv on 2010-03-11
This problems comes up every few days.   I suggest you do a but of a search on "grub rescue" or "installing grub".

It may be that you will need to reinstall grub on your MBR.

---

### Post by presence1960 on 2010-03-11
> **valued customer said:**
> ok so i deleted the ubuntu partition and managed to get windows xp to boot again, reinstalled ubuntu but when it tries to boot i get an error.

grub loading
error no such partition
grub rescue

any ideas how to get this up and running again?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by valued customer on 2010-03-11
```
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x782c782c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   291,531,554   291,531,492   7 HPFS/NTFS
/dev/sda2         291,531,555   312,576,704    21,045,150   5 Extended
/dev/sda5         291,531,618   311,580,674    20,049,057  83 Linux
/dev/sda6         311,580,738   312,576,704       995,967  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        F834B16134B12412                       ntfs                                     
/dev/sda5        57583b68-8155-44e0-937a-779339848282   ext4                                     
/dev/sda6        5e401826-b70c-4f5e-b980-c65408a311a6   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 57583b68-8155-44e0-937a-779339848282
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 57583b68-8155-44e0-937a-779339848282
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=57583b68-8155-44e0-937a-779339848282 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 57583b68-8155-44e0-937a-779339848282
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=57583b68-8155-44e0-937a-779339848282 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f834b16134b12412
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=57583b68-8155-44e0-937a-779339848282 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5e401826-b70c-4f5e-b980-c65408a311a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 151.9GB: boot/grub/core.img
 151.9GB: boot/grub/grub.cfg
 150.1GB: boot/initrd.img-2.6.31-14-generic
 151.6GB: boot/vmlinuz-2.6.31-14-generic
 150.1GB: initrd.img
 151.6GB: vmlinuz

```

---

### Post by presence1960 on 2010-03-11
As soon as you told me the errors I looked here: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

But reading this and comparing the contents of your grub.cfg file I don't think this is the problem. I think it may be a case of your BIOS having a limit on how far into your hard disk the BIOS can read. usually it is 137 GB unless your BIOS is really older. newer BIOS do not have this problem. If this is indeed the case you need to put the files needed to boot within the 137 GB limit by installing ubuntu or creating a separate /boot partition within that limit. Note where your files needed to boot are located:

```
=================== sda5: Location of files loaded by Grub: ===================


 [COLOR="Red"]151.9GB[/COLOR]: boot/grub/core.img
 [COLOR="Red"]151.9GB[/COLOR]: boot/grub/grub.cfg
 [COLOR="Red"]150.1GB[/COLOR]: boot/initrd.img-2.6.31-14-generic
 [COLOR="Red"]151.6GB[/COLOR]: boot/vmlinuz-2.6.31-14-generic
 [COLOR="Red"]150.1GB[/COLOR]: initrd.img
 [COLOR="Red"]151.6GB[/COLOR]: vmlinuz

```
They are outside of 137 GB. You can check the documentation to your BIOS or contact the vendor. If you have a newer BIOS then this is not the problem.

---

