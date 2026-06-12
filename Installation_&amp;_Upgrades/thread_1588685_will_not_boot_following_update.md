---
title: "will not boot following update"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by Vyodacoda on 2010-10-05
My Dell Inspiron 6000 laptop is failing to boot following an update to 10.4
I let the update complete and a restart was requested, which I did.
Getting through the laptops bios it then gets to the part where grub should take over and show me a menu or if set to 0 seconds boot straight into Linux ( I cannot remember if I set it to 0 seconds or not )
What I actually get is the following
GNU GRUB version 1.98-1ubuntu7
Minimal BASH-like editing is supported. etc.

There is no dual boot on this machine as Ubuntu 10.4 occupies the whole drive
I can leave the machine like this for a while if it is of any use for helping with diagnosis of the problem
It does boot on a Live CD ( Memory Stick Version )
Many thanks

---

### Post by ronparent on 2010-10-05
You could try a grub reinstall per: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by Vyodacoda on 2010-10-05
Hi ronparent, Many thanks for your reply
Sadly I still cannot get it to boot so it maybe something more sinister
I went though the fixes as prescribed but I am still getting the same screen
I can reinstall it but it does make me worry if such a thing happens again

---

### Post by Rubi1200 on 2010-10-05
If you hold down Shift as the computer boots it will bring up the GRUB menu.

If you boot into the previous kernel version (the one before the update) do you still have a problem?

Post the results of the boot-script linked at the bottom of my post as well (from the LiveCD).

Thanks.

---

### Post by Vyodacoda on 2010-10-05
Hi Rubi1200
Many thanks for that
This machine is obviously telling me something cos Holding down shift through the boot process still does not get me anywhere. 
I obviously cannot boot to the previous kernel as I have no menu
The content of results.txt follows
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   305,096,703   305,094,656  83 Linux
/dev/sda2         305,098,750   312,580,095     7,481,346   5 Extended
/dev/sda5         305,098,752   312,580,095     7,481,344  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2055 MB, 2055019520 bytes
64 heads, 62 sectors/track, 1011 cylinders, total 4013710 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     4,011,647     4,011,586   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       f09b600f-2584-43a0-908e-323d88b77354   ext3                                     
/dev/sda1        c8cd0dee-ea91-4238-bb54-847545986959   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cf7cdd03-69e0-4ddb-b94d-596af80c24d5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3EA0-B507                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=c8cd0dee-ea91-4238-bb54-847545986959 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=c8cd0dee-ea91-4238-bb54-847545986959 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c8cd0dee-ea91-4238-bb54-847545986959 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c8cd0dee-ea91-4238-bb54-847545986959 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c8cd0dee-ea91-4238-bb54-847545986959 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c8cd0dee-ea91-4238-bb54-847545986959 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c8cd0dee-ea91-4238-bb54-847545986959
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=c8cd0dee-ea91-4238-bb54-847545986959 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cf7cdd03-69e0-4ddb-b94d-596af80c24d5 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/core.img
 137.7GB: boot/grub/grub.cfg
  47.4GB: boot/initrd.img-2.6.32-21-generic
  47.4GB: boot/initrd.img-2.6.32-24-generic
  47.5GB: boot/initrd.img-2.6.32-25-generic
  47.3GB: boot/vmlinuz-2.6.32-21-generic
  47.4GB: boot/vmlinuz-2.6.32-24-generic
  47.5GB: boot/vmlinuz-2.6.32-25-generic
  47.5GB: initrd.img
  47.4GB: initrd.img.old
  47.5GB: vmlinuz
  47.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  84 18 c6 84 18 ce 84 18  c6 84 18 ce 84 21 c6 7b  |.............!.{|
00000010  18 ce 84 21 c6 84 21 ce  84 21 ce 84 18 ce 84 21  |...!..!..!.....!|
00000020  ce 84 18 ce 84 21 c6 84  18 c6 84 18 c6 84 18 c6  |.....!..........|
00000030  84 21 c6 84 18 ce 8c 29  c6 84 21 ce 8c 29 c6 84  |.!.....)..!..)..|
00000040  29 ce 84 29 c6 84 21 ce  84 21 ce 84 21 ce 84 21  |)..)..!..!..!..!|
00000050  ce 84 21 ce 84 29 ce 84  21 ce 8c 29 ce 84 21 ce  |..!..)..!..)..!.|
00000060  8c 29 ce 84 29 ce 84 29  ce 84 21 ce 8c 29 ce 84  |.)..)..)..!..)..|
00000070  21 ce 8c 29 c6 84 21 ce  8c 29 ce 84 29 ce 84 31  |!..)..!..)..)..1|
00000080  ce 84 29 ce 84 31 ce 84  29 ce 84 29 ce 84 29 d6  |..)..1..)..)..).|
00000090  8c 31 ce 84 29 ce 84 29  ce 84 29 ce 8c 31 ce 84  |.1..)..)..)..1..|
000000a0  29 ce 8c 29 ce 84 21 ce  8c 29 c6 84 21 ce 8c 21  |)..)..!..)..!..!|
000000b0  c6 84 21 ce 8c 29 ce 84  21 ce 8c 29 ce 84 29 d6  |..!..)..!..)..).|
000000c0  8c 31 ce 8c 29 ce 84 29  ce 84 29 ce 8c 29 ce 84  |.1..)..)..)..)..|
000000d0  29 ce 8c 29 ce 84 29 ce  8c 31 c6 84 31 c6 8c 31  |)..)..)..1..1..1|
000000e0  c6 84 31 ce 8c 39 ce 8c  31 ce 8c 39 c6 84 31 c6  |..1..9..1..9..1.|
000000f0  8c 39 c6 84 31 ce 8c 31  c6 84 31 ce 8c 39 ce 84  |.9..1..1..1..9..|
00000100  31 ce 8c 31 c6 84 31 ce  8c 31 c6 84 31 ce 84 31  |1..1..1..1..1..1|
00000110  c6 84 31 ce 8c 39 ce 84  31 ce 8c 31 ce 84 29 ce  |..1..9..1..1..).|
00000120  8c 29 ce 84 29 ce 8c 29  ce 84 29 ce 8c 29 ce 84  |.)..)..)..)..)..|
00000130  29 ce 8c 31 c6 84 29 c6  8c 31 c6 84 29 c6 84 31  |)..1..)..1..)..1|
00000140  c6 7b 29 ce 84 31 ce 84  29 ce 8c 31 c6 84 29 ce  |.{)..1..)..1..).|
00000150  8c 29 ce 84 29 ce 84 29  c6 84 29 ce 84 31 c6 84  |.)..)..)..)..1..|
00000160  29 ce 8c 29 c6 84 29 ce  8c 31 ce 84 31 ce 84 31  |)..)..)..1..1..1|
00000170  c6 7b 29 c6 8c 39 c6 94  4a d6 ad 63 de bd 7b e7  |.{)..9..J..c..{.|
00000180  ce 94 e7 ce 9c ef de ad  ef de ad f7 e7 b5 f7 e7  |................|
00000190  b5 ff f7 c6 f7 ef c6 ff  ff ce ff ff d6 ff ff e7  |................|
000001a0  ff ff ef ff ff f7 ff ff  f7 ff ff ff ff ff ff ff  |................|
000001b0  ff ff ff ff ff ff ff ff  ff ff f7 ff ff f7 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 28 72 00 00 00  |...........(r...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Rubi1200 on 2010-10-05
Is sdb an external drive? Have you tried disconnecting it and then booting (changing the boot order in BIOS if needs be)?

The results look normal; in other words, there doesn't appear to be anything obviously wrong.

---

### Post by Vyodacoda on 2010-10-05
Hi Rubi1200
Many thanks for your quick reply again
I assume that sdb is the memory stick that I am booting on for the Live CD
The hard drive is the first in the boot list and I change it for the memory stick by pressing F12 at boot
I have tried to boot both with the memory stick and without to the same effect
This machine has always been slightly gaga on booting
Many thanks again

---

### Post by drs305 on 2010-10-05
In cases where the boot info script results look normal, I usually recommend purging and reinstalling G2 via the LiveCD and chroot. Reinstalling may not recover a failing system if files are missing. 

There is very little risk if your power supply and Internet are stable. Here's the link:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD ]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by Vyodacoda on 2010-10-05
Hi drs305
Many thanks for this. I will give it a try!

---

### Post by Vyodacoda on 2010-10-06
Hi again drs305
Tried this early this morning and got a first time runner ( worked like a charm )
Many thanks for the very clear instructions
I think I will make a copy of the document in all my document folders ( just in case )
Many thanks again

---

