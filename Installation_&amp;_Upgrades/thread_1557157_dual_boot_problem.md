---
title: "dual boot problem"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by ummz on 2010-08-20
Hi,

I'm new to ubuntu. I tried install Ubuntu on a Dell workstation which already has a windows 7 installed. All the installation works fine, and after finishing, it reboots, the menu of selecting ubuntu or windows appeared. I can boot into windows with no problem, but selecting the ubuntu just gave me black screen few seconds later.

One possible cause (I think, after reading some of the previous posts in this forum) is that when I use the CD to install Ubuntu, I asked ubuntu to resize my partitions instead of installing it on a new one, and when booting in windows, the system did ask for checking the consistency of disk.

Is there any way to fix it? I would prefer something without going through the installation process again. but if this is the only way, could I get detailed instructions on what to do to avoid this problem? thanks a lot!

---

### Post by Rubi1200 on 2010-08-20
> **ummz said:**
> Hi,

I'm new to ubuntu. I tried install Ubuntu on a Dell workstation which already has a windows 7 installed. All the installation works fine, and after finishing, it reboots, the menu of selecting ubuntu or windows appeared. I can boot into windows with no problem, but selecting the ubuntu just gave me black screen few seconds later.

One possible cause (I think, after reading some of the previous posts in this forum) is that when I use the CD to install Ubuntu, I asked ubuntu to resize my partitions instead of installing it on a new one, and when booting in windows, the system did ask for checking the consistency of disk.

Is there any way to fix it? I would prefer something without going through the installation process again. but if this is the only way, could I get detailed instructions on what to do to avoid this problem? thanks a lot!
Well, there are a few things here that need to be addressed:

1. what graphics card do you have installed?

2. can you boot the LiveCD? If yes, then click on the link at the bottom of my post and follow the instructions there; post the results back here.

3. did you try running a chkdsk from within Windows? I suggest you do so.
[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

Good luck!

---

### Post by ummz on 2010-08-23
Hi, I runed the ckdsk but booting the ubuntu still gives me black screens. the result of the scripts are:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,278,015   488,275,968   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,171,406,020 1,171,403,973   7 HPFS/NTFS
/dev/sdb2       1,171,406,846 1,953,523,711   782,116,866   5 Extended
/dev/sdb5       1,171,406,848 1,921,783,807   750,376,960  83 Linux
/dev/sdb6       1,921,785,856 1,953,523,711    31,737,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        98AC62B3AC628C16                       ntfs       System                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9AD215BBD2159D17                       ntfs       New Volume                    
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        167b79b6-93f7-4029-9c07-291957fea1f7   ext4                                     
/dev/sdb6        fad31a8c-dba5-4ba9-9057-daea692c6968   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 167b79b6-93f7-4029-9c07-291957fea1f7
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 167b79b6-93f7-4029-9c07-291957fea1f7
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 167b79b6-93f7-4029-9c07-291957fea1f7
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=167b79b6-93f7-4029-9c07-291957fea1f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 167b79b6-93f7-4029-9c07-291957fea1f7
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=167b79b6-93f7-4029-9c07-291957fea1f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 167b79b6-93f7-4029-9c07-291957fea1f7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 167b79b6-93f7-4029-9c07-291957fea1f7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 98ac62b3ac628c16
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=167b79b6-93f7-4029-9c07-291957fea1f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=fad31a8c-dba5-4ba9-9057-daea692c6968 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 924.1GB: boot/grub/core.img
 849.1GB: boot/grub/grub.cfg
 924.1GB: boot/initrd.img-2.6.32-24-generic
 924.1GB: boot/vmlinuz-2.6.32-24-generic
 924.1GB: initrd.img
 924.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  20 20 20 20 20 20 20 20  20 31 0d 0a 20 20 20 33  |         1..   3|
00000010  31 37 20 20 20 20 20 20  20 20 20 20 20 31 20 20  |17           1  |
00000020  20 20 20 20 20 20 20 20  20 31 20 20 20 20 20 20  |         1      |
00000030  20 20 20 20 20 31 20 20  20 20 20 20 20 31 2e 30  |     1       1.0|
00000040  30 30 20 20 20 20 20 20  20 30 2e 30 30 30 20 20  |00       0.000  |
00000050  20 20 20 20 20 20 20 20  20 31 0d 0a 20 20 20 33  |         1..   3|
00000060  31 38 20 20 20 20 20 20  20 20 20 20 20 31 20 20  |18           1  |
00000070  20 20 20 20 20 20 20 20  20 31 20 20 20 20 20 20  |         1      |
00000080  20 20 20 20 20 31 20 20  20 20 20 20 20 31 2e 30  |     1       1.0|
00000090  30 30 20 20 20 20 20 20  20 30 2e 30 30 30 20 20  |00       0.000  |
000000a0  20 20 20 20 20 20 20 20  20 31 0d 0a 20 20 20 33  |         1..   3|
000000b0  31 39 20 20 20 20 20 20  20 20 20 20 20 31 20 20  |19           1  |
000000c0  20 20 20 20 20 20 20 20  20 31 20 20 20 20 20 20  |         1      |
000000d0  20 20 20 20 20 31 20 20  20 20 20 20 20 31 2e 30  |     1       1.0|
000000e0  30 30 20 20 20 20 20 20  20 30 2e 30 30 30 20 20  |00       0.000  |
000000f0  20 20 20 20 20 20 20 20  20 31 0d 0a 20 20 20 33  |         1..   3|
00000100  32 30 20 20 20 20 20 20  20 20 20 20 20 31 20 20  |20           1  |
00000110  20 20 20 20 20 20 20 20  20 31 20 20 20 20 20 20  |         1      |
00000120  20 20 20 20 20 31 20 20  20 20 20 20 20 31 2e 30  |     1       1.0|
00000130  30 30 20 20 20 20 20 20  20 30 2e 30 30 30 20 20  |00       0.000  |
00000140  20 20 20 20 20 20 20 20  20 31 0d 0a 20 20 20 33  |         1..   3|
00000150  32 31 20 20 20 20 20 20  20 20 20 20 20 31 20 20  |21           1  |
00000160  20 20 20 20 20 20 20 20  20 31 20 20 20 20 20 20  |         1      |
00000170  20 20 20 20 20 31 20 20  20 20 20 20 20 31 2e 30  |     1       1.0|
00000180  30 30 20 20 20 20 20 20  20 30 2e 30 30 30 20 20  |00       0.000  |
00000190  20 20 20 20 20 20 20 20  20 31 0d 0a 20 20 20 33  |         1..   3|
000001a0  32 32 20 20 20 20 20 20  20 20 20 20 20 31 20 20  |22           1  |
000001b0  20 20 20 20 20 20 20 20  20 31 20 20 20 20 00 fe  |         1    ..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d8 b9 2c 00 fe  |.............,..|
000001d0  ff ff 05 fe ff ff 02 d8  b9 2c 00 50 e4 01 00 00  |.........,.P....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by oldfred on 2010-08-23
I see you have wubi and a full install but otherwise results.txt look ok.

As Rubi1200 asked what video card? I have nvidia and both install and first boot turned off monitor.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO on USB, or in USB's syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa

---

### Post by kansasnoob on 2010-08-23
It appears that you can run the the Live CD, if so please post the output of:

```
lspci | grep VGA
```

That will tell us exactly what GPU you have. This certainly sounds more like a graphics problem than a grub problem.

---

### Post by Rubi1200 on 2010-08-23
Agree with oldfred, I just have a general question:

> => Windows is installed in the MBR of /dev/sdb

Doesn't GRUB2 need to be installed in the MBR of sdb?

Or is this indicating that it is looking at the regular install on sdb?

> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
     partition #5 for /boot/grub.

---

### Post by ummz on 2010-08-23
yes, I checked, my video card is nvidia. so I followed the steps as oldfred posted: change the "quiet splash" to the word nomodeset, then I can boot into ubuntu and download the drive.

Wooohoooo!!! it works!!! thanks, Rubi1200, kansasnoob and oldfred! thank you guys so much!

---

### Post by oldfred on 2010-08-23
Glad you got it working.

Grub likes to default to sda. The boot script or grub2 often mis-identify which drive it looks at (It does that on my computer also). So even though the script says same drive it may be another.

I prefer to have an operating system on each drive and that system's boot loader on the same drive. Then if you ever have one drive fail you can still boot the other. But it is not essential, there are always liveCDs or USB boots as backups, if you have them. You can reinstall grub to sdb and set BIOS to boot sdb and install a windows boot loader to sda, if you want.

I have 3 drives with 3 versions of Ubuntu & XP. Each drive can boot a separate system. Then I have several liveCDs and recently set up two USB's. One boots all my repair ISOs and another is a full install of Ubuntu. I just want to have many ways to boot my system - just in case. (May be a little overkill:)).

---

