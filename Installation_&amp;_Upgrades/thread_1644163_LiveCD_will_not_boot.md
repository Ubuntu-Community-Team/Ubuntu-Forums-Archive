---
title: "LiveCD will not boot"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by WickedShadow on 2010-12-12
When i pop in the live cd to boot from it gets stuck on the loading screen the one that looks like this:
[CENTER]Ubuntu
. . . . .[/CENTER]

The dots move until like 2 mins in and then they get stuck and nothing happens i let it sit for like 30 mins.

The reason im using the cd is i already have installed ubuntu but then i installed windows xp on another partition and so im trying to get the grub back using the livecd.

Please help.
-Thanks

---

### Post by Quackers on 2010-12-12
At the purple Ubuntu screen press any key and a new screen will appear. On the new screen press the4 F6 key and some boot options will appear on the right. As your problem is probably graphics card related you could try the nomodeset option if you have a nvidia graphics card or a i915 option if you have Intel integrated graphics.

---

### Post by WickedShadow on 2010-12-12
I do that then it goes to the for terminal type loadup then is says
"Kernel panic - not syncing: Attempting to kill Init!"
then spits out a bunch of code and stops.

---

### Post by Quackers on 2010-12-12
First, have you checked the downloaded .iso file has been correctly downloaded?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok boot from the live cd again and tap the F6 key during boot. You should get a screen which offers you the chance to check the cd for errors. Try that.

---

### Post by WickedShadow on 2010-12-13
So i checked everything turns out i have a bad disk made a new one works fine now the whole reason i needed one was to get grub back after i installed windows xp after ubuntu and ive done everything its just when i get to the actual installing i get this
> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/b2f78c97-a7c1-42cf-ae39-5bc86f0bd553/ /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.


I was using this guide:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Quackers on 2010-12-13
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by WickedShadow on 2010-12-13
Here you go:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   155,539,455   155,537,408  83 Linux
/dev/sda2    *    155,539,456   307,093,503   151,554,048   7 HPFS/NTFS
/dev/sda3         307,095,550   320,172,031    13,076,482   5 Extended
/dev/sda5         307,095,552   320,172,031    13,076,480  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdb2         204,796,620   488,392,064   283,595,445   f W95 Ext d (LBA)
/dev/sdb5         204,796,683   488,392,064   283,595,382   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b2f78c97-a7c1-42cf-ae39-5bc86f0bd553   ext4                                     
/dev/sda2        D2B4248EB42476DF                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        a7e93351-fa99-4dac-bb18-192a2e7ae381   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5860147E60146552                       ntfs       Games                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        01CB992F40CC13E0                       ntfs       Windows                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/b2f78c97-a7c1-42cf-ae39-5bc86f0bd553 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set b2f78c97-a7c1-42cf-ae39-5bc86f0bd553
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b2f78c97-a7c1-42cf-ae39-5bc86f0bd553
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b2f78c97-a7c1-42cf-ae39-5bc86f0bd553
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b2f78c97-a7c1-42cf-ae39-5bc86f0bd553 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b2f78c97-a7c1-42cf-ae39-5bc86f0bd553
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b2f78c97-a7c1-42cf-ae39-5bc86f0bd553 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b2f78c97-a7c1-42cf-ae39-5bc86f0bd553
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b2f78c97-a7c1-42cf-ae39-5bc86f0bd553 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b2f78c97-a7c1-42cf-ae39-5bc86f0bd553
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b2f78c97-a7c1-42cf-ae39-5bc86f0bd553 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b2f78c97-a7c1-42cf-ae39-5bc86f0bd553
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b2f78c97-a7c1-42cf-ae39-5bc86f0bd553
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5860147e60146552
    drivemap -s (hd0) ${root}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b2f78c97-a7c1-42cf-ae39-5bc86f0bd553 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a7e93351-fa99-4dac-bb18-192a2e7ae381 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  28.0GB: boot/grub/core.img
  15.4GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic
   2.0GB: boot/initrd.img-2.6.35-23-generic
   7.2GB: boot/vmlinuz-2.6.35-22-generic
   7.2GB: boot/vmlinuz-2.6.35-23-generic
   2.0GB: initrd.img
   1.0GB: initrd.img.old
   7.2GB: vmlinuz
   7.2GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```

---

### Post by msandoy on 2010-12-13
There is probably a problem with ACPI, when booting from the CD, after choosing language and keymap, press F6, and switch off ACPI. This has helped me many times. Can't explain why, it usually just works.

Answered too quickly, didn't read the whole thread.

---

### Post by Quackers on 2010-12-13
From the live cd desktop open a terminal and copy/paste these commands in one at a time pressing enter after each one.
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If it reports "no errors"
then reboot and after Ubuntu loads open a terminal again and run
```
sudo update-grub
```
and watch the terminal screen as grub.cfg is configured to see if both XP installations are found.

---

### Post by WickedShadow on 2010-12-13
I tried to do:

```
 sudo update-grub
```

but then it said

```
 /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

so i mounted it in the places menu and it still didnt work.

---

### Post by Quackers on 2010-12-13
As stated in my last post ```
sudo update-grub
```

is to be run after you have rebooted into the Ubuntu installation - not whilst booted from the live cd.

---

### Post by WickedShadow on 2010-12-13
Thanks all is well (said i from my ubuntu 10.10 operating system!)

-Thanks

---

### Post by Quackers on 2010-12-13
Excellent :-)
You're welcome.
Please mark the thread as solved using the Thread Tools near the top of the page. Thanks.

---

