---
title: "Can't boot into any OS"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by tjl30 on 2010-09-16
The Error Message
==================
"BOOTMGR is missing Press Ctrl+Alt+Del to restart"

The Setup
==================
My computer has 3 HD's the first drive dual booted windows7/ubuntu10.4
The other HD's are NTFS slave drives will all my data on them.

After a lot of reading the fix I found was to use my windows7 repair disk, but I don't have a repair disk. I also cant torrent at my school so I cant install a repair disk via a torrent file.

What I Did
==================
I reinstalled ubuntu 9.10 wiping clean my first HD (sda). I restarted my computer and still got this error.

Please Help!

---

### Post by pricetech on 2010-09-16
Yes, the error message is windows telling you it can't find boot code.

If you're still getting the message after installing Ubuntu, then it didn't install.

First things first:  Boot to the live CD and back up your data before you lose it.

Then try again, being very careful to read and understand all the screens during the install.

---

### Post by Rubi1200 on 2010-09-16
As pricetech already said, backup things now.

Additionally, I suggest you use the LiveCD to boot the computer and in live mode post the results of the bootscript linked to at the bottom of my post.

The results will give us a better overview of your setup and make offering solutions easier.

Thanks.

---

### Post by tjl30 on 2010-09-16
Unfortunately I lost a lot of stuff already when I accidentally wiped out my Ubuntu install. With that being said I have two drives for music and docs that didn't get wiped.

Anyways I ran that script, please see attachment for the results.

Thanks for the Help

---

### Post by Rubi1200 on 2010-09-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048   468,520,959   468,518,912  83 Linux
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb2         264,192 1,953,523,711 1,953,259,520 Linux or Data

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,465,145,343 1,465,143,296   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3b54c2f8-24ac-49dc-9d62-e6317f1d043e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        87fe97e0-aca8-4c39-a69b-92d15aa32e84   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2        744C481B4C47D690                       ntfs       Backup                        
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        2A5A30FF5A30C8F9                       ntfs       Backup                        
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
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
search --no-floppy --fs-uuid --set 3b54c2f8-24ac-49dc-9d62-e6317f1d043e
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
search --no-floppy --fs-uuid --set 3b54c2f8-24ac-49dc-9d62-e6317f1d043e
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3b54c2f8-24ac-49dc-9d62-e6317f1d043e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=3b54c2f8-24ac-49dc-9d62-e6317f1d043e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3b54c2f8-24ac-49dc-9d62-e6317f1d043e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=3b54c2f8-24ac-49dc-9d62-e6317f1d043e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3b54c2f8-24ac-49dc-9d62-e6317f1d043e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3b54c2f8-24ac-49dc-9d62-e6317f1d043e
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
UUID=3b54c2f8-24ac-49dc-9d62-e6317f1d043e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=87fe97e0-aca8-4c39-a69b-92d15aa32e84 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
 165.7GB: boot/grub/grub.cfg
  25.9GB: boot/initrd.img-2.6.32-21-generic
  25.9GB: boot/vmlinuz-2.6.32-21-generic
  25.9GB: initrd.img
  25.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c6 db 7f 1b 6d fc 6d b7  f1 b6 df c6 db 7f 1b 6d  |....m.m........m|
00000010  fc 6d b7 f1 b6 df c6 db  7f 1b 6d fc 6d b7 f1 b6  |.m........m.m...|
00000020  df c6 db 7f 1b 6d fb 00  30 31 77 62 80 01 00 00  |.....m..01wb....|
00000030  ff fb 94 64 0b 0e f4 0c  4b d1 9b 2c 4a f2 2e e1  |...d....K..,J...|
00000040  28 b1 31 82 14 0f 69 1f  48 6c bd 0b c0 c1 07 a2  |(.1...i.Hl......|
00000050  c0 f7 8c 98 36 3f 00 d2  72 f3 92 b0 2a 49 3b 2b  |....6?..r...*I;+|
00000060  87 20 87 c0 53 55 25 53  86 0e cc 04 98 5c 25 1c  |. ..SU%S.....\%.|
00000070  9c 1f 88 c1 68 80 d6 19  19 38 3f 3a 47 80 e1 00  |....h....8?:G...|
00000080  8d 51 e4 27 56 6d 13 5b  2a 71 ea 29 31 81 62 e4  |.Q.'Vm.[*q.)1.b.|
00000090  a9 22 3c d4 16 59 2a 67  2e 4a bf 5b 9e c9 28 54  |."<..Y*g.J.[..(T|
000000a0  17 96 6d 3a af df 96 fd  f3 cb 85 d5 6e c3 27 9b  |..m:........n.'.|
000000b0  eb ff fe dc 6a d3 dd dc  f7 05 77 5e 23 89 6b 20  |....j.....w^#.k |
000000c0  08 cd 92 a8 29 c9 4b a0  28 fc f0 18 1a 01 1f 06  |....).K.(.......|
000000d0  0c 01 5e 0c 4f b8 a4 5c  26 48 42 61 ce 03 3e 71  |..^.O..\&HBa..>q|
000000e0  c8 a7 ab f2 5b f4 23 ff  ff b2 ed 3f ff fd 41 5a  |....[.#....?..AZ|
000000f0  1d 06 12 0c 58 d0 e0 39  36 70 e7 86 a4 dc 99 db  |....X..96p......|
00000100  6c f7 0d f9 96 d4 45 4a  62 34 65 4a 8d 4a c0 de  |l.....EJb4eJ.J..|
00000110  f9 95 5c d6 da a0 59 8c  c1 02 f1 5c 98 57 df ae  |..\...Y....\.W..|
00000120  1c 1b 98 e1 44 6d 64 66  86 fd 3c 22 89 c4 63 18  |....Dmdf..<"..c.|
00000130  97 38 68 b8 ba 30 72 79  42 c6 45 28 2f 41 3d 40  |.8h..0ryB.E(/A=@|
00000140  c3 8b 68 73 3b e8 68 f1  92 f6 39 6c e5 65 b9 ae  |..hs;.h...9l.e..|
00000150  6a 65 fd 4a 17 38 97 a4  56 8a ed a7 a5 83 7b 9b  |je.J.8..V.....{.|
00000160  79 2e e4 cd c2 e5 0b a1  0a 5b e8 27 f8 af a5 60  |y........[.'...`|
00000170  c8 44 ca b2 f1 e5 e0 44  7d 41 29 16 47 56 28 ca  |.D.....D}A).GV(.|
00000180  34 a2 44 0e 2d cc 28 a2  6e 7b 0b 37 70 b3 59 c9  |4.D.-.(.n{.7p.Y.|
00000190  37 73 bf fa bf ff ff ff  6f d6 00 00 14 a2 4e 5c  |7s......o.....N\|
000001a0  d0 37 12 fc 80 00 86 a4  49 c0 45 db 9e 15 2b 94  |.7......I.E...+.|
000001b0  30 30 64 63 52 1f 00 00  00 00 01 b6 51 60 00 fe  |00dcR.......Q`..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 2f 01 00 00  |...........@/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```I see you have GPT in sdb; I know this can sometimes cause complications. Please wait for one of the more experienced forum members to come along and advise you.

Thanks.

---

### Post by srs5694 on 2010-09-16
The user "oldfred" has posted solutions to mixed-partition-table issues and GRUB in the past; for instance, see his first post in [this thread.](http://ubuntuforums.org/showthread.php?t=1545165) I can't promise this will solve your problem, though; from the error message, it sounds like GRUB isn't installed or isn't loading.

How is your BIOS configured to boot? It's possible that the BIOS is trying to boot from /dev/sdb or /dev/sdc, but GRUB is installed on /dev/sda. Most modern computers enable easy switching between boot devices at boot time, typically by pressing F10, F12, or some other key at a critical point in the boot process. Try that and see if you can get the system to boot by selecting another hard disk. If this works, you can go into your BIOS setup utility and change the default boot device.

You might also want to try [Super GRUB Disk,](http://www.supergrubdisk.org) which can often boot a system even when GRUB on the hard disk is damaged. If you can get Linux booted, that will enable you to re-install GRUB to the hard disk.

---

