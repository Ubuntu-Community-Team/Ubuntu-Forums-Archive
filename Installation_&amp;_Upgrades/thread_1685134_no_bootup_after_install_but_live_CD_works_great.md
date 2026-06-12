---
title: "no bootup after install but live CD works great"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by LineAxe on 2011-02-10
:redface: No Bootup just a Black Screen with a frozen cursor after install, but LIVE CD works in 1024x768 mode?  :redface:

Well, I have a Sony Bravia 32xTV with HDMI input coming out of a ZOTAC  nvidia type of card. The live CD will recognize the HDMI graphics card and Sony TV/monitor and thus works like Ubuntu normally does. But when I go to install to a hard drive and try to boot up I get just a Black Screen with a frozen cursor. I even have another Ubuntu 8.04 version running on the Sony Bravia TV , so no problem with TV end of things. what do I do now, oh great Ubuntu gurus out there in cyberland?  what could I possibly do , what do I read, where do I go , what, where, who, how, when ,which way?  I thank all for any ideas on what to do now !! ):P

---

### Post by sikander3786 on 2011-02-10
Try using the nomodeset parameter.

Press and hold down Shift key from Bios until you see Grub menu. Highlighting the first entry there, press 'e' to edit it. Navigate to words "quiet splash" delete them and type "nomodeset" (without quotes) in their place. Press Ctrl + X to continue boot. Hopefully, you'll see the desktop this time.

Then go to System > Administration > Hardware Drivers and install the proper drivers for your card and the issue might go away for ever.

More info here.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Let us know how that goes, as there can be some other causes to this problem as well.

---

### Post by LineAxe on 2011-02-10
I just tried to hit the shift key to invoke a  Grub menu ,tried left shift and right shift. No grub menu . Just the same black screen with a blinking cursor at top left corner. :confused: 
Thanks for the info , I think I may need it if I can get further than this screen !

---

### Post by P4man on 2011-02-10
You have to press the shift key at the right moment, and you dont have much time. SHould be right after the bios splash and before it actually starts booting.

---

### Post by sikander3786 on 2011-02-11
Press and _hold_ down Shift key from Bios screen.

If you can't still see the Grub menu, please boot an Ubuntu live CD and post the output of bootinfoscript as per instructions here to let us see what is going on in there.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by LineAxe on 2011-02-12
Got another chance to work on the UBUNTU 10.10 computer again :)  Here comes my bootinfoscript information. I hope this helps. I sure see all the folders and everything else is on the drive. Not sure what else to look for ! I wonder how does the live CD figure out what resolution to go to but the installed version can't? why?why?why? Ow! I 
bumped my head ... why? ?    
 
-------------------                 RESULTS.TXT          ----------------
 
               Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
sdb1: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1               2,048 1,905,559,551 1,905,557,504  83 Linux
/dev/sdb2       1,905,561,598 1,953,523,711    47,962,114   5 Extended
/dev/sdb5       1,905,561,600 1,953,523,711    47,962,112  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        724ED5544ED51229                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6b23ce23-9111-4b55-be72-2a92f3320275   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0f38b1ec-5e36-4c1c-9d8f-528b4528f9c5   swap                                     
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== sdb1/boot/grub/grub.cfg: ===========================
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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6b23ce23-9111-4b55-be72-2a92f3320275
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6b23ce23-9111-4b55-be72-2a92f3320275
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
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set 6b23ce23-9111-4b55-be72-2a92f3320275
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6b23ce23-9111-4b55-be72-2a92f3320275 ro   quiet splash
 initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set 6b23ce23-9111-4b55-be72-2a92f3320275
 echo 'Loading Linux 2.6.35-22-generic ...'
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6b23ce23-9111-4b55-be72-2a92f3320275 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set 6b23ce23-9111-4b55-be72-2a92f3320275
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set 6b23ce23-9111-4b55-be72-2a92f3320275
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 724ed5544ed51229
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
=============================== sdb1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=6b23ce23-9111-4b55-be72-2a92f3320275 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0f38b1ec-5e36-4c1c-9d8f-528b4528f9c5 none            swap    sw              0       0
=================== sdb1: Location of files loaded by Grub: ===================

 627.2GB: boot/grub/core.img
 161.2GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.35-22-generic
 627.2GB: boot/vmlinuz-2.6.35-22-generic
    .4GB: initrd.img
 627.2GB: vmlinuz

---

### Post by Quackers on 2011-02-12
The boot script reports that you have 2 hard drives - not mentioned previously.
Grub2 is installed to sda and is looking for its boot files in the first partition of sda. The boot files, though, are in the first partition of sdb, so grub can't find what it needs. How it got like that, I'm not sure, but to try to fix it see below.

From the live cd desktop open up a terminal and copy/paste these commands into it, one line at a time and pressing enter after each line.

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Then reboot. Ubuntu should now boot directly. If it does, open up a terminal and run ```
sudo update-grub
```
then watch as grub.cfg is configured to check that the Windows Loader is picked up. If it is, you can reboot and try to boot Windows from your new Grub menu.

---

### Post by LineAxe on 2011-02-12
Hi , I just tried the two lines...

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

from the live cd in a terminal... and then rebooted and still have only got a blinking cursor. Still hoping to figure out what ubuntu wants me to change...thanks for any help :)

---

### Post by Quackers on 2011-02-12
Is the second hard drive a bootable option in your bios?
If so, please make that drive the first bootable device then re-run those commands EXCEPT change the second command to read /dev/sdb at the end (instead of /dev/sda), then reboot.
Do you have a Windows repair disc (or installation disc)?

In fact, while you are in the live cd desktop you can add a boot flag to sdb. Sometimes a pc's bios requires it to boot.
Please go to System > Admin > gparted
After it has scanned your discs look in the top right, where it says /dev/sda. There is a little down arrow next to it. Click that and select /dev/sdb. When the drive's partitions appear in the main window, right-click on the sdb1 partition and select "Manage Flags" then in the new window check the box marked "boot", then close that window. Then click on the green arrow in the toolbar (if required, not sure). Then quit the program.

---

### Post by LineAxe on 2011-02-12
nice work dudes!!
We got it, it indeed was related to hard drives
I had them setup a bit different and needed to change them in the bios 
when i did that, I got ubuntu up and running.. Heh I have 3 computers setup similar to this. One running fiesty Studio ,one running Hardy Server , and now Meerkat it looks like11 :) I don't remember running into any HD problems on the other two systems though, I musta lucked out and got them right. I guess I did done [COLOR="Red"]something [/COLOR]this time around !  thanks dudes :popcorn:

---

