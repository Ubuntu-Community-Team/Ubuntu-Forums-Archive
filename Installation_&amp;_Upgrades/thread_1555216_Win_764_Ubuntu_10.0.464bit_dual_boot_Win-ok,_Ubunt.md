---
title: "Win 7/64 Ubuntu 10.0.4/64bit dual boot Win-ok, Ubuntu-fail"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by gleydon on 2010-08-17
Dell Prec T5500 (Xeon E5504) with two 1T drives, 24G ram, NVidia Quadro NVS420


Windows 7 Pro 64 bit was installed first and works fine

SATA 0 is Win 7 Pro 64 bit , 1 NTFS partition
SATA 1 is partioned as follows
  8G swap
  200G EXT4 mounted as /
  800G NTFS 

I booted from Ubuntu cd, ran install chose manual partition scheme and set up SATA 1 as above.

Grub2 boots into Windows 7 with no problems and I can see/use NTFS partition on SATA1

When I try to boot into default Ubuntu the screen goes black and then loses video signal and nothing happens, doesn't sound like the disk is doing anything.

Grub for the linux boot is as follows
recordfail
insmode ext2
set root='(hd1,2)'
search --no-floppy --fs-UUID --set a05...yadayada....b7a
linux  /boot/vmlinuz-2.6.32-21-generic root=UUID=a05....yadayada...b7a ro quiet splash
initrd /boot/initrd.img -2.6.32-21-generic

If I boot into Live CD I can mount EXT4 on SATA 1 partition and everything looks fine, e.g the files /boot/vmlinuz-2.6.32.21-generic and initrd.img-2.26.32-21-generic are both there and the UUID of that drive is the same as referenced in GRUB2.

Any ideas appreciated

---

### Post by uRock on 2010-08-17
Have you run ```
sudo update-grub
``` from the terminal within the LiveCD?

---

### Post by presence1960 on 2010-08-17
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by gleydon on 2010-08-18
Thanks uRock and presence1960
     I downloaded the bootinfo script, ran it from livecd terminal and Results.txt is included below I think I see the issue in Results.txt it's looking for /boot/grub on the wrong disk but not sure how to fix that.
I DID NOT run sudo update-grub first. Will this fix the issue?


```
       
         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325 1,070,843,834 1,070,763,510   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    16,386,299    16,386,237  82 Linux swap / Solaris
/dev/sdb2          16,386,300   425,979,539   409,593,240  83 Linux
/dev/sdb3         425,979,540 1,953,520,064 1,527,540,525   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        1A3A4AC73A4A9F9D                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6d14018d-b899-4d19-acb3-14f50f22ec87   swap       swap                          
/dev/sdb2        a05a90c4-7c84-47aa-aabd-9d9bb2663b7a   ext4                                     
/dev/sdb3        6C64A66F3021A981                       ntfs       data                          
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set a05a90c4-7c84-47aa-aabd-9d9bb2663b7a
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set a05a90c4-7c84-47aa-aabd-9d9bb2663b7a
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
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a05a90c4-7c84-47aa-aabd-9d9bb2663b7a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a05a90c4-7c84-47aa-aabd-9d9bb2663b7a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a05a90c4-7c84-47aa-aabd-9d9bb2663b7a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a05a90c4-7c84-47aa-aabd-9d9bb2663b7a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a05a90c4-7c84-47aa-aabd-9d9bb2663b7a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a05a90c4-7c84-47aa-aabd-9d9bb2663b7a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1a3a4ac73a4a9f9d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=a05a90c4-7c84-47aa-aabd-9d9bb2663b7a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=6d14018d-b899-4d19-acb3-14f50f22ec87 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 214.7GB: boot/grub/core.img
  87.9GB: boot/grub/grub.cfg
 214.7GB: boot/initrd.img-2.6.32-21-generic
 214.6GB: boot/vmlinuz-2.6.32-21-generic
 214.7GB: initrd.img
 214.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 

```

---

### Post by presence1960 on 2010-08-18
There are two ways to fix this. Boot the Ubuntu live cd (10.04) and boot to the desktop. Open a terminal and run ```
sudo mount /dev/sdb2 /mnt
```This will mount your 10.04 / partition

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot without the cd and boot to ubuntu. Open a terminal and run ```
sudo update-grub
```

Or the method I personally prefer is to put GRUB on the MBR of the disk that has ubuntu (sdb). Boot your machine with the 10.04 live cd and go into BIOS. Set the sdb hard disk as first to boot in the hard disk boot order. Save changes to CMOS & continue booting the live cd. Boot to the desktop and open a terminal and run ```
sudo mount /dev/sdb2 /mnt
```

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot without the live cd and boot into ubuntu. Open a terminal and run ```
sudo dpkg-reconfigure grub-pc
``` When you get to the last window use the spacebar to deselect sda and then use the spacebar to select sdb. This will insure all grub updates go to the MBR of sdb.

---

### Post by gleydon on 2010-08-19
Thanks so much for taking the time with this. So far no luck.

I tried option 1:

boot to Ubuntu 10.4 liveCD

sudo -s
mount /dev/sdb2 /mnt
(ls /mnt to confirm it's my ubuntu partition)

grub-install --root-directory=/mnt/  /dev/sda

This resulted in a Grub configuration identical to the one that Ubuntu created when I installed the OS and likewise fails to boot Ubuntu on sdb2 though does boot Win7 just fine.

When it tries to boot there is disk activity for a couple of seconds, then screen goes black (still showing signal) and finally screen goes into no signal mode, no disk activity. 



I tried option 2
Change Boot order so system boots from SATA1 (sdb) first, then SATA0 (sda)
(confirmed this by unplugging SATA0 and booting, got the No boot device message)

boot to Ubuntu 10.4 liveCD
sudo -s
mount /dev/sdb2 /mnt

(ls /mnt to confirm it's my ubuntu partition)

grub-install --root-directory=/mnt/ /dev/sdb

Try rebooting, get Grub menu (hit e to look at it, same exact config as previous) fails to boot ubuntu, and boots win7 just fine.  Double check it's using sdb Grub by disconnecting SATA0 and looking at Grub config via e, identical to all previous configs.


I'm going to try reinstalling ubuntu directly onto sdb2 with sda disconnected from the system entirely and will report results.

thanks again for taking the time

---

### Post by gleydon on 2010-08-19
Ok....so it looks like it's a problem with Ubuntu 10.0.4 and Dell T5500 and/or the nVidia Quadro NVS420. 

Found lots of problems with people trying to get ubuntu onto various incarnations of the Prec T3500 AND T5500.

To simplify things I tried an absolutely default install, reformat, let ubuntu pick partitions etc on just a single drive (sda) and the system failed to boot in exactly the same way. (i.e. disk activity for a few seconds then black screen, then no video signal.

adding nomodereset to linux line in grub got the system to boot. From there I assume I can get updated drivers (or live with the limited resolution until a fix).

So all the things that looked like Grub problems are most likely video problems. Odd that the liveCD boots up just fine with no video issues.

---

### Post by gleydon on 2010-08-19
It was a video driver issue nomodeset fixed everything

Gritty details:

Removed SATA0 (Win 7 system with Grub bootloader)
Connected SATA1 drive to SATA0
Boot from Unbunu 10.0.4 LTS cd
Do stock install letting it format my drive, took all defaults on installation
System fails to boot, black screen, some disk activity, then no video signal, then no disk activity.

Reboot holding down shift to get in to grub 
edit linux line, add nomodeset to end of linux /vmlinuz.... ro quiet splash nomodeset

System boots to login screen, lots of flickering/blinking
Login and run System/Administration/hardware drivers
system puts up dialog for installing nVidia accelerated drivers I took the recommended version

Reboot and all is well.

Shutdown
connect Win7 drive with grub as SATA0
connect Ubuntu drive at SATA1
reboot

invalid (or not found) UUID
grub recovery> 

Grub fails as expected due to different UUID for SATA1 
Boot to live CD
from terminal
```

sudo -s

mount /dev/sdb1 /mnt

grub-install --root-directory=/mnt/ /dev/sda

Reboot into Ubuntu

from terminal
sudo update-grub


```all is fine

Can now boot into Win7 or Ubuntu

not sure about nomodeset but based on perusing the web it seems it doesn't hurt to have it so I put it in as default. Seems to be less flickering on login screen

```

sudo -s
nano /etc/defaults/grub

change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

change
GRUB_CMDLINE_LINUX=""
to
GRUB_CMDLINE_LINUX="nomodeset"

grub-update

```thanks for the tips and help

---

