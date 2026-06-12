---
title: "Dual Boot Failure After Installation"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Cason on 2010-06-29
Okay, I must preface all of this by saying I'm an extreme noob when it comes to Linux. I've been searching these forums for a couple of hours to try to find a solution to my problem, but can't. Here's the issue:
 
I looked into Ubuntu at the behest of a friend, was intrigued by it, and decided to try it out. I downloaded 10.04 netbook remix, and made a bootable USB thumb drive with it. I liked the test run with the USB, so decided to install it on my netbook. I chose the option in the installer for having a dual boot, told it to create a 40 GB partition for Ubuntu, then let the installer do it's thing. It finished, and I rebooted.
 
Now, everytime I reboot my computer I'm let to the boot selection screen (which I've come to understand is called Grub). I have two issues when I try to boot, one major, and one minor.
 
Major Issue: When I select to boot Windows XP, it immediatley goes to the black windows XP splash screen with the loading bar at the bottom, but within a few seconds the blue screen of death appears, but only for a split second (not long enough to read the error), then the computer restarts and I'm back to Grub. This happens regardless of whether I use Safe Mode or a Normal Startup. I really need to be able to boot to XP; what can I do?
 
Minor issue: When I select to boot Ubuntu, I'm immediately taken to an all black screen with a flashing white underscore cursor ( _ ); looks almost exactly like a console, and it lets me type. If I let the computer be, nothing happens. If I type a bunch of random characters untill it won't let me type anymore, Ubuntu boots momentarily. It's REALLY wierd, and I don't understand it. How can I get it to just boot?
 
I've come to understand that you guys like for people with these kinds of problems to post their Boot Info Script, so mine is below. I'm really stuck here, and help would be very much appreciated!
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
    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM
sda3: _________________________________________________________________________
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
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63   195,360,464   195,360,402   7 HPFS/NTFS
/dev/sda2         296,849,070   312,576,704    15,727,635  1c Hidden W95 FAT32 (LBA)
/dev/sda3         195,360,766   296,847,359   101,486,594   5 Extended
/dev/sda5         195,360,768   292,605,951    97,245,184  83 Linux
/dev/sda6         292,608,000   296,847,359     4,239,360  82 Linux swap / Solaris
 
blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda1        A22403E62403BC73                       ntfs       TI102717P0A                   
/dev/sda2        A429-150F                              vfat       HDDRECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        d2139a9e-b3ee-4684-a7ee-d654bbfcccd7   ext4                                     
/dev/sda6        f409dc79-2aca-4c8c-aa13-9196cfa0c03a   swap                                     
/dev/sda: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/TI102717P0A       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
 
================================ sda1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
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
search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
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
search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
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
 search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 ro   quiet splash
 initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
 echo 'Loading Linux 2.6.32-21-generic ...'
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set d2139a9e-b3ee-4684-a7ee-d654bbfcccd7
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
 insmod ntfs
 set root='(hd0,1)'
 search --no-floppy --fs-uuid --set a22403e62403bc73
 drivemap -s (hd0) ${root}
 chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
 insmod fat
 set root='(hd0,2)'
 search --no-floppy --fs-uuid --set a429-150f
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f409dc79-2aca-4c8c-aa13-9196cfa0c03a none            swap    sw              0       0
=================== sda5: Location of files loaded by Grub: ===================
 
 134.6GB: boot/grub/core.img
 117.3GB: boot/grub/grub.cfg
 134.7GB: boot/initrd.img-2.6.32-21-generic
 134.6GB: boot/vmlinuz-2.6.32-21-generic
 134.7GB: initrd.img
 134.6GB: vmlinuz

```

---

### Post by dabl on 2010-06-29
I can't say that I know for certain what the problem is/are, but I see a couple things in your boot info that may be relevant.

First, the "black screen with blinky white cursor" is a classic video display problem, regarding "framebuffers" and/or power-management features of the GPU.  Possibly pressing Alt-F1 will switch you to a tty console and normal command line login prompt.  In a console window you can run ```
lspci -vv
``` to see the exact make and model of your video chip/card, and then a search on this forum will lead you to whatever kernel boot option is needed to get through the boot screens to the GUI login.  Just use the model of your card and "kernel boot option" to search.

On the Windows issues:

1. The boot flag is set on the hard drive's first partition, which is a NTFS formatted partition -- is that where Win XP is actually installed?  This would be /dev/sda1 to Linux, and (hd0,1) to Grub.

2. If that's the case, what is the deal with the "hidden W95 FAT32 .." partition on /dev/sda2?"  Grub thinks there is a Win 2000 OS there, which is probably not true.

So, you will need to open the file /etc/grub.d/30_os-prober with your text editor in root mode ( i.e. "gkesu gedit /etc/grub.d/30_os-prober") and put a "#" mark in front of each line of the menu for "Windows 2000", so it looks like this when you save it:

```
#menuentry "Windows NT/2000/XP (on /dev/sda2)" {
 #insmod fat
 #set root='(hd0,2)'
 #search --no-floppy --fs-uuid --set a429-150f
 #drivemap -s (hd0) ${root}
 #chainloader +1
```

Then you need to run ```
sudo update-grub
``` to make /boot/grub/grub.cfg pick up the change.  Then restart your system, and maybe it will boot Windows.  No guarantees -- sorry.

---

### Post by Cason on 2010-06-29
Thanks for the reply!
 
I'll look into the video driver issue. I got sorta lost in all the technical terms, but I think I can figure that out...
 
> **dabl said:**
> 
 
On the Windows issues:
 
1. The boot flag is set on the hard drive's first partition, which is a NTFS formatted partition -- is that where Win XP is actually installed? This would be /dev/sda1 to Linux, and (hd0,1) to Grub.
 
2. If that's the case, what is the deal with the "hidden W95 FAT32 .." partition on /dev/sda2?" Grub thinks there is a Win 2000 OS there, which is probably not true.
 
So, you will need to open the file /etc/grub.d/30_os-prober with your text editor in root mode ( i.e. "gkesu gedit /etc/grub.d/30_os-prober") and put a "#" mark in front of each line of the menu for "Windows 2000", so it looks like this when you save it:
 
```
#menuentry "Windows NT/2000/XP (on /dev/sda2)" {
 #insmod fat
 #set root='(hd0,2)'
 #search --no-floppy --fs-uuid --set a429-150f
 #drivemap -s (hd0) ${root}
 #chainloader +1
```
 
Then you need to run ```
sudo update-grub
``` to make /boot/grub/grub.cfg pick up the change. Then restart your system, and maybe it will boot Windows. No guarantees -- sorry.
 
As for this, I'm pretty sure that hidden partition is the "Factory Restore" partition made to be used in conjunction with the Factory Restore CD from within Windows XP. Regardless, I know that XP is installed on the first patition, and that's what I need to be able to boot to.
 
I'm wondering if maybe the installer deleted some key files for XP when it created the new partition for Ubuntu? But I don't know. Any other ideas?

---

### Post by dabl on 2010-06-29
You're probably right about the "factory restore partition" thing.  I'm not sure whether commenting out the false Win 2000 menu entry in /etc/grub.d/30_os-prober will fix it or not, but it's worth a try.

On the video issue, once you know the make and model of the GPU, start here: [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

---

### Post by wilee-nilee on 2010-06-29
So if you resized XP for the Ubuntu install it should have run a chkdsk did this ever happen on the initial reboot into XP. Do you have a XP install disc?, if not here is a link to a legit one, as it will probably need a chkdsk /r/f run.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

As far as the Ubuntu problem, it sounds like a graphic driver problem. If you do a low graphic boot by at the grub choice gui hit e and use the arrow keys to remove the splash reference at the end of the kernel, an put in nomodset the hold down the ctrl key and hit x to boot in.

This is only to get you to the desktop where you will have to find the graphic card/chip driver if it is the problem and install it.

To identify the card in the terminal.
```
lspci | grep VGA
```

---

### Post by Cason on 2010-06-29
:popcorn:

I have solved both problems; thank you for all who helped! For those of you with similar problems, or who just want to know, they were fixed as follows:

The Ubuntu boot issue was not a video card problem, but atually had to do with a setting in the BIOS for my particular unit (Toshiba NB205). The fix for that can be found in this [thread]("http://ubuntuforums.org/showthread.php?t=1476638&highlight=toshiba+NB205+slow+boot").

The issue with Windows booting, however, was more complicated. As suggested, I booted from a Windows XP installer CD and opened the Recovery Application, which lead me to a DOS prompt. After running a CHKDSK (check disk), it told me there were a few bad sectors, but I knew that before I ever had a problem.

After snooping around using the HELP command, i used the BOOTFIX command, then rebooted with my fingers crossed. When I chose WinXP from the Grub selector, it booted without a problem! Windows had to re-recognize most of my hardware, but after I restarted again it was operating perfectly!

Thanks again to those who helped, and good luck to those who have similar issues!

---

