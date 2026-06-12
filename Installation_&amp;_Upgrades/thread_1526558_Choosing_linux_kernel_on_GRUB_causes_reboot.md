---
title: "Choosing linux kernel on GRUB causes reboot"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by Zens on 2010-07-08
Hi all,

I recently decided to venture into the world of Linux/GNU by installing Ubuntu.

Before installing, I had a 190gb partition for windows 7 and 45gb of unallocated space. Through Wubi, I used the advanced partition editor to make a 6gb swap partition and a 22gb root partition for Ubuntu. All went well, but when I rebooted, I was unable to choose linux.

I installed Ubuntu by using Unetbootin to put the Ubuntu ISO on my USB drive. After installing, I disconnected the USB drive, and I was unable to choose the linux kernel option on the GRUB menu. When I do, my system just restarts and presents me with the GRUB menu again. However, windows 7 boots up perfectly.

I'm assuming that GRUB is somehow trying to boot the linux kernel from the USB. How do I change it to boot from the installation I made on my harddrive?

Thank you :p

---

### Post by dabl on 2010-07-08
Here is a good guide for all things Grub 2:  [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by oldfred on 2010-07-08
to see if something is missing:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Zens on 2010-07-08
I skimmed over the GRUB guide, but I'm unsure as to how to edit the GRUB files since it's my first time using the konsole. I tried using the 'e' option on the GRUB menu, but I didn't know what to edit.

After rebooting a few times, choosing the Ubuntu option yielded a blinking cursor. I waited for a few minutes but nothing happened. Now, selecting the Ubuntu option causes the restart loop again.

I was able to boot up Ubuntu through my USB drive and run the script.

Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   396,224,511   396,222,464   7 HPFS/NTFS
/dev/sda2         396,226,558   451,287,039    55,060,482   5 Extended
/dev/sda5         396,226,560   439,568,383    43,341,824  83 Linux
/dev/sda6         439,570,432   451,287,039    11,716,608  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D0465FF3465FD8B4                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        aec27060-70dc-4fe5-a630-5736b5221dc2   ext4                                     
/dev/sda6        6255de07-b956-48d2-8ffb-0be23095a641   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         0AD7-E685                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set aec27060-70dc-4fe5-a630-5736b5221dc2
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set aec27060-70dc-4fe5-a630-5736b5221dc2
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set aec27060-70dc-4fe5-a630-5736b5221dc2
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=aec27060-70dc-4fe5-a630-5736b5221dc2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set aec27060-70dc-4fe5-a630-5736b5221dc2
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=aec27060-70dc-4fe5-a630-5736b5221dc2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set aec27060-70dc-4fe5-a630-5736b5221dc2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set aec27060-70dc-4fe5-a630-5736b5221dc2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d0465ff3465fd8b4
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=aec27060-70dc-4fe5-a630-5736b5221dc2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6255de07-b956-48d2-8ffb-0be23095a641 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 209.9GB: boot/grub/core.img
 222.4GB: boot/grub/grub.cfg
 209.8GB: boot/initrd.img-2.6.32-21-generic
 203.0GB: boot/vmlinuz-2.6.32-21-generic
 209.8GB: initrd.img
 203.0GB: vmlinuz
```

Thank you!

---

### Post by oldfred on 2010-07-08
I do not see anything in your script that looks out of place. Perhaps someone else will.

We have seen some strange issues like floppy configured in BIOS, but no floppy so system goes awry. My boot was slow if I had two USB keys installed at boot. One user left a CD in the tray and the system tried running chkdsk for an hour, then he did boot. I am surprised he waited that long.

You could try editing out the entire search line. Sometimes that makes a difference.

---

### Post by Zens on 2010-07-09
Hmm, that's weird. My BIOS has no enabled floppy settings, and I've removed all media devices besides my HDD and disc drive.

I don't know how I got the blinking cursor for once, but it's back to rebooting after choosing the first linux option. The same thing occurs if I choose the recovery mode option.

How would I go about editing the search line?

---

### Post by oldfred on 2010-07-09
At the grub menu press e and scroll down to the search line and delete it. control x then lets you boot. You should see brief instructions on the menu and edit menu.

If it is booting I would try reinstalling grub after you have booted just to make sure it is ok.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by Zens on 2010-07-09
Hi,

I tried removing the search line and rebooting afterward, but I got the same error.

Could it possibly have been a corrupt install?

Can I delete the root and swap partitions and retry the installation, or would that interfere with the GRUB files and not allow me to boot into windows 7?

---

### Post by oldfred on 2010-07-09
The grub in the MBR depends on the Ubuntu partition for the rest of its boot. If you immediately reinstall you should be fine as it will reinstall grub to the MBR. If not you will have to reinstall a windows boot loader.

You will have to use manual install so you can choose the existing partitions or else it will create a second install. Just choose  your curretn / ()root) as root and what format ext3 or ext4, it finds swap on its own normally.

---

### Post by Zens on 2010-07-21
Just wanted to update this post for anyone that has or may encounter this error in the future:

The problem was a corrupt install from my USB. My USB seemed to be faulty, so I made a live CD and installed Ubuntu from there. I used the same partitions after formatting, and everything works now.

Thank you for the help! :)

---

### Post by oldfred on 2010-07-21
Glad you got it working. 

Sometimes reinstall is the quickest fix and if new or recent you have nothing to lose. But as you use system then good backups are important.

---

