---
title: "Trouble Installing Ubuntu 10.10 Dual Boot"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by ftresident on 2011-03-25
Hi Everyone, 

I have a fairly old Dell Dimension 8400 with two disks. 
I have Windows XP on the first disk (750GB) and have a second unused 200GB disk that I installed Ubuntu 10.10 onto. 

Here are the problems I had:

1) After the install, the computer would only boot into Linux.  I had no options at all at boot up for which OS to boot into. 

2) I verified that my 750GB WinXP disk was still intact (/dev/sda).  I tried created a file for WinXP in /etc/grub.d taken from the 40_custom file.  I added a menuentry section to it and ran grub-update.  grub-update complained about an error ddf1 invalid # of disks in RAID partition.  

3) Ubuntu didn't seem to know about my Linksys AE1000 wireless adapter.  And since I has no Wireless on the computer, I couldn't download drivers. 

4) I rebooted the computer after trying to update grub and now my PC boots into Windows again. 

Can anyone guess where I went wrong here?  I expected to install Ubuntu and then have grub2 give me a choice of WinXP or Linux.  Why did it intitally boot only into Linux, and why did it strangely revert back to WinXP later on? 

I'd like to try this again.  Can anybody please advise me on how to get this right the first time? 

Thanks!

---

### Post by Quackers on 2011-03-25
If grub2 was installed as normal to the mbr of the drive you would expect Ubuntu to boot up directly. This is because grub2 has over-written the Windows part of the mbr. To get grub2 to recognise (and boot) the Windows installation you just need to open a terminal and run ```
sudo update-grub
``` 
The Windows loader should then appear in grub.cfg which will allow Windows to boot from the grub menu.

There is normally no need for a custom entry.

---

### Post by ftresident on 2011-03-25
> **Quackers said:**
> If grub2 was installed as normal to the mbr of the drive you would expect Ubuntu to boot up directly. This is because grub2 has over-written the Windows part of the mbr. To get grub2 to recognise (and boot) the Windows installation you just need to open a terminal and run ```
sudo update-grub
```The Windows loader should then appear in grub.cfg which will allow Windows to boot from the grub menu.

There is normally no need for a custom entry.

So I'm not sure what went wrong.  I'd think grub2 installed to the mbr on disk2 since I installed linux there.  Also, if it has overwritten the mbr on the Windows disk, I would not be able to boot into Windows now, right?  I didn't run fixmbr or fixboot so the original mbr must have been preserved.

I really have no idea what happened, except that I installed Ubuntu, it installed cleanly, I was then able to ONLY boot into Linux, and then after trying to run grub-update, I am now only able to boot into Windows.

---

### Post by Quackers on 2011-03-25
If you left the grub install settings as default, it was probably installed to sda, the first hard drive. Windows should now boot through the grub menu, even though Ubuntu is on sdb drive and Windows is on sda.

---

### Post by ftresident on 2011-03-25
> **Quackers said:**
> If you left the grub install settings as default, it was probably installed to sda, the first hard drive. Windows should now boot through the grub menu, even though Ubuntu is on sdb drive and Windows is on sda.

I don't see any menu.  It just boots right into Windows like it did before I installed linux. 

How can I verify whether grub2 installed into sda or sdb (from Windows, since I can no longer boot linux).

---

### Post by Quackers on 2011-03-25
Now I'm lost :-)
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ftresident on 2011-03-27
Thanks.  Here you go.


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of 
    /dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba and 
    looks on the same drive in partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,465,127,999 1,465,127,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   374,792,191   374,790,144  83 Linux
/dev/sdb2         374,794,238   390,721,535    15,927,298   5 Extended
/dev/sdb5         374,794,240   390,721,535    15,927,296  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     7,897,087     7,897,025   b W95 FAT32


Drive: ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba ___________________ _____________________________________________________

Disk /dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba: 749.6 GB, 749606010880 bytes
255 heads, 63 sectors/track, 91134 cylinders, total 1464074240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba1   *             63 1,465,127,999 1,465,127,937   7 HPFS/NTFS

/dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba1 ends after the last sector of /dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba: PTTYPE="dos" 
/dev/sda1        1A7C8E2B7C8E01AD                       ntfs                                     
/dev/sda         Dell                                  ddf_raid_member                               
/dev/sdb1        69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        34c4f3cd-c3a1-4881-9e14-9c57962705c1   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        EE71-6520                              vfat       NEW VOLUME                    
/dev/sdc: PTTYPE="dos" 
error: /dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba1: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/NEW VOLUME        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set 69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c
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

### BEGIN /etc/grub.d/06_windowsxp ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows XP Home (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0060ff4060ff3acc
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/06_windowsxp ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=34c4f3cd-c3a1-4881-9e14-9c57962705c1 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 133.2GB: boot/grub/core.img
  73.1GB: boot/grub/grub.cfg
  73.3GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
  73.3GB: initrd.img
    .3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  69 76 9c 25 81 65 f5 88  4b 2e ce 16 f5 48 94 a4  |iv.%.e..K....H..|
00000010  41 0c 74 02 e9 2f 46 6f  54 bb 30 3f 2a 88 cb 72  |A.t../FoT.0?*..r|
00000020  87 3d 03 a0 39 fd ae 01  26 ad 83 ef c0 9a 15 a2  |.=..9...&.......|
00000030  6b 62 1d df 7d 53 24 fc  73 ca 83 c1 00 08 33 3c  |kb..}S$.s.....3<|
00000040  9b 38 24 af 0d 81 1c cb  12 c3 80 89 76 41 dc 28  |.8$.........vA.(|
00000050  11 00 01 11 00 31 ed 44  a2 fa c1 22 1c 12 24 64  |.....1.D..."..$d|
00000060  97 3c f7 dc 08 e1 71 fc  2c 4b e0 c2 7c 3d 41 d7  |.<....q.,K..|=A.|
00000070  40 89 58 a3 2a 21 27 6d  f9 f7 57 6e f6 9c 05 c3  |@.X.*!'m..Wn....|
00000080  ad de de de c3 b5 6b 00  0c 43 b8 58 62 10 0c 24  |......k..C.Xb..$|
00000090  17 b0 a0 a7 90 45 47 00  23 4e e8 e6 6a 31 38 00  |.....EG.#N..j18.|
000000a0  00 1e 5c 04 99 0e 58 23  27 a6 b0 9f 84 c6 1a 76  |..\...X#'......v|
000000b0  f7 3f 83 81 0c 08 d1 3d  64 f7 32 8e b7 e7 16 0c  |.?.....=d.2.....|
000000c0  6d a3 49 4c 41 24 da 85  e2 b4 c9 06 28 26 2c 93  |m.ILA$......(&,.|
000000d0  63 26 e7 7a 30 e5 90 cd  c8 33 13 f4 43 99 44 c6  |c&.z0....3..C.D.|
000000e0  2c 29 ed a3 60 81 71 b7  ad 28 54 c6 d6 01 5f 3f  |,)..`.q..(T..._?|
000000f0  53 a2 f2 2f c6 da 8b d4  c7 cc dc 08 74 26 00 e6  |S../........t&..|
00000100  1d 31 79 2b 1d b4 6c dc  b0 50 54 5c 31 74 9f e6  |.1y+..l..PT\1t..|
00000110  ce bf 03 e0 89 41 06 61  8c d6 8d 53 ba 56 19 18  |.....A.a...S.V..|
00000120  b8 c2 a5 21 93 ec 7a 61  84 fc 9b 71 19 2f 3d b9  |...!..za...q./=.|
00000130  f2 a9 0e f9 62 e7 5b fd  0e a4 5d b3 af 1b 1c 37  |....b.[...]....7|
00000140  3d 01 b8 b6 50 25 8e c5  ec 76 13 b3 dc 1d 9a 26  |=...P%...v.....&|
00000150  ae 1c c2 03 90 01 c8 ed  b0 e8 e8 0e c7 47 40 76  |.............G@v|
00000160  24 3f 53 18 16 10 16 b5  3d 98 67 9e 13 d1 80 48  |$?S.....=.g....H|
00000170  1c f4 85 28 30 0f 04 07  a6 c1 14 fc 1e 31 d2 2c  |...(0........1.,|
00000180  ab 28 00 49 13 4e 08 49  ce 09 c7 8a 47 42 50 91  |.(.I.N.I....GBP.|
00000190  41 06 a8 fa 3a 92 e9 20  3f 2e 75 ea 08 01 cd 10  |A...:.. ?.u.....|
000001a0  82 71 41 4a 83 16 42 1d  25 a8 c1 68 89 60 5b 24  |.qAJ..B.%..h.`[$|
000001b0  70 2e 22 2b 1e 31 eb 24  1d 30 db 36 76 54 00 fe  |p."+.1.$.0.6vT..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 f3 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba1



=============================== StdErr Messages: ===============================

ERROR: ddf1: wrong # of devices in RAID set "ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba" [1/2] on /dev/sda
ERROR: ddf1: wrong # of devices in RAID set "ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba" [1/2] on /dev/sda
ERROR: creating degraded mirror mapping for "ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba"
ERROR: dos: partition address past end of RAID device
ERROR: ddf1: wrong # of devices in RAID set "ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba" [1/2] on /dev/sda
ERROR: ddf1: wrong # of devices in RAID set "ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba" [1/2] on /dev/sda
hexdump: /dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba1: No such file or directory
hexdump: /dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba1: No such file or directory
ERROR: ddf1: wrong # of devices in RAID set "ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba" [1/2] on /dev/sda
ERROR: dos: partition address past end of RAID device

```

---

### Post by Hedgehog1 on 2011-03-27
> **ftresident said:**
> Thanks.  Here you go.

ftresident,

The trick is that while the grub scripts are stored in /dev/sdb1, the MBR of /dev/sda is the one that needs to have the grub boot loader installed on it.  ***The commands below are correct for your PC based on your script results - you can cut and paste them.***

Please boot off your LiveCD/LiveUSB, select 'TRY'

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**b1** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

***The Hedge***

:KS

p.s. this should give you the 'dual boot' menu and let you select Ubuntu or Windows.

---

### Post by ftresident on 2011-03-27
Hedgehog1, 

Thanks.  I tried these two commands.  It said Installation Successful when I was done but the computer still always boot into Windows without giving me a choice.

---

### Post by Quackers on 2011-03-27
WHich drives are part of a raid array?
Also which drive is set first to boot in your bios?

---

### Post by ftresident on 2011-03-27
> **Quackers said:**
> WHich drives are part of a raid array?
Also which drive is set first to boot in your bios?

I don't have a RAID array.  I have two disks that are not RAIDed.
BIOS first boots off USB or CD, then my SATA drives.  It doesn't let me pick which SATA drive to boot from.

---

### Post by Quackers on 2011-03-27
> **ftresident said:**
> I don't have a RAID array.  I have two disks that are not RAIDed.
BIOS first boots off USB or CD, then my SATA drives.  It doesn't let me pick which SATA drive to boot from.

I see, so which drive is set to boot in the bios? You have a 750GB drive and a 200GB drive.
Drive sda is showing a mounting problem for sda1, which, I presume, is because it has raid metadata on it. Was the 750GB drive used in another machine, which had a raid array?
See the bit in red from your boot script output below
```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba: PTTYPE="dos" 
/dev/sda1        1A7C8E2B7C8E01AD                       ntfs                                     
/dev/sda         Dell                                  [COLOR="Red"]ddf_raid_member[/COLOR]                               
/dev/sdb1        69bf89ca-e27d-47cb-b9f3-e00c5deaaf1c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        34c4f3cd-c3a1-4881-9e14-9c57962705c1   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        EE71-6520                              vfat       NEW VOLUME                    
/dev/sdc: PTTYPE="dos" 
[COLOR="Red"]error: /dev/mapper/ddf1_44656c6c202020201000006010281f0c3789c1f9ee665eba1: No such file or directory[/COLOR]
```

---

### Post by ftresident on 2011-03-27
> **Quackers said:**
> I see, so which drive is set to boot in the bios? You have a 750GB drive and a 200GB drive.


The 750GB drive.

> **Quackers said:**
> 
Drive sda is showing a mounting problem for sda1, which, I presume, is because it has raid metadata on it. Was the 750GB drive used in another machine, which had a raid array?


Yes, it was in another computer.
The disk was pulled from a PowerEdge server, and wiped clean with a hardware wiper.  
I would have thought that the wiping process would have erased the RAID configuration.

How can I get rid of the RAID metadata on the disk?   
And why didn't Windows complain about this?

---

### Post by Quackers on 2011-03-27
Ok, that makes sense. The raid metadata remains until it is specifically removed, unfortunately.
Am I correct in thinking that nothing boots now?

---

### Post by ftresident on 2011-03-27
> **Quackers said:**
> Ok, that makes sense. The raid metadata remains until it is specifically removed, unfortunately.
Am I correct in thinking that nothing boots now?

No, I can boot into Windows with no problem, just as it did before I installed Ubuntu onto the second disk.

---

### Post by Quackers on 2011-03-27
Ah, ok, thanks.
We can try to remove the raid metadata using the Ubuntu live cd/usb. I'm not 100% sure it will work from the live desktop, but it's definitely worth trying.
Please boot from the Ubuntu live cd/usb and select "try ubuntu".
When the desktop loads open up a terminal and copy/paste the command below
```
sudo dmraid -rE /dev/sda
``` and press enter.
If no errors are reported, reboot, taking out the cd/usb and then see if the grub menu appears.

---

### Post by ftresident on 2011-03-27
It didn't work.

It asked me if I was sure I want to erase all raid metadata.
I said "y" and it returned "ERROR:" before each of the next 3 lines.

---

### Post by Quackers on 2011-03-27
Oh dear! What were the next 3 lines please?

---

### Post by ftresident on 2011-03-27
```

ubuntu@ubuntu:~$ sudo dmraid -rE /dev/sda
Do you really want to erase "ddf1" ondisk metadata on /dev/sda ? [y/n] :y
ERROR: ddf1: seeking device "/dev/sda" to 384080063234048
ERROR: writing metadata to /dev/sda, offset 750156373504 sectors, size 0 bytes returned 0
ERROR: erasing ondisk metadata on /dev/sda
ubuntu@ubuntu:~$ 

```

It seems to have no effect.  It still boots right into Windows.

---

### Post by Quackers on 2011-03-27
Hmm, I'm a bit stuck here.
I would advise re-installing grub, but if it's going to install itself to a drive with raid metadata, it's just going to have the same problems, I suspect.
I will ask another member to take a look, but I don't know if he's online at the moment.

---

### Post by ronparent on 2011-03-27
Let's not get tangled up in what windows xp see and what Ubuntu sees. XP requires a driver to see a raid array. No driver = no array. The same with ubuntu except that is the dmraid program. I usually prefer to erase the meta data before uninstalling dmraid for just the reason of what is occurring here. A long time after a drive is no longer used as raid and you forget the meta data is there a new install pops it back at you. But that is not the issue here.

For some reason the sda mbr is pointing to sda1 for the grub. The grub is actually installed on sdb1. The suggested grub 2 reinstall should do it, except it should be **--root-directory=/mnt/** not** /mnt**! I don't know why it would ber booting directly into window unless sdc were first in boot order? It is unlikely that your bios does't allow you to shuffle your boot order. So I would check that first. It is probably best to leave the MBR that boots windows alone so you can always boot windows if everything else gets mucked up.

I would suggest trying the grub reinstall first. We can worry about the meta data next if it is still bothering something. The install itself shouldn't have dmraid installed, so it may not be material. Keep posting, Quackers can probaly untangle any raining problems once you are up and running.

---

### Post by ftresident on 2011-03-28
> **ronparent said:**
> 
For some reason the sda mbr is pointing to sda1 for the grub. The grub is actually installed on sdb1. The suggested grub 2 reinstall should do it, except it should be **--root-directory=/mnt/** not** /mnt**! I don't know why it would ber booting directly into window unless sdc were first in boot order? It is unlikely that your bios does't allow you to shuffle your boot order. So I would check that first. It is probably best to leave the MBR that boots windows alone so you can always boot windows if everything else gets mucked up.

I would suggest trying the grub reinstall first. We can worry about the meta data next if it is still bothering something. The install itself shouldn't have dmraid installed, so it may not be material. Keep posting, Quackers can probaly untangle any raining problems once you are up and running.

So just to get this straight, I should do the following:

```

sudo mount /dev/sdb1 /mnt

```

```

sudo grub-install --root-directory=/mnt/ /dev/sda

```

Right? 

As for BIOS, it lets me pick from various devices, including SATA Drive and IDE drive.  Since I have two SATA drives, it doesn't let me pick WHICH SATA drive to boot from.  
At least, I don't think so.    

I'd think setting the boot device in BIOS would be the easiest option, since each disk would be totally independent and would not need to know anything about the other one.

It doesn't see to be an option though.

---

### Post by ronparent on 2011-03-28
Yes those two commands should get the Ubuntu up and running and find any other installed OS's on the system.

It is not conceivable that you cannot shuffle the boot order in your bios. Have a closer look at it - it would give you better options.

---

### Post by drmathprog on 2011-04-01
I seem to have the same dual boot problem.  Can someone kindly diagnose my results.txt and suggest a solution?

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   490,223,474   490,223,412   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63       144,584       144,522  de Dell Utility
/dev/sdc2             144,585   245,651,462   245,506,878   7 HPFS/NTFS
/dev/sdc3         245,653,502   488,396,799   242,743,298   5 Extended
/dev/sdc5         245,653,504   478,445,567   232,792,064  83 Linux
/dev/sdc6         478,447,616   488,396,799     9,949,184  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63       353,429       353,367  de Dell Utility
/dev/sdd2    *        353,430   522,947,879   522,594,450   7 HPFS/NTFS
/dev/sdd3         522,947,880 1,250,258,624   727,310,745   5 Extended
/dev/sdd5         522,947,943 1,250,258,624   727,310,682   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        12CC960FCC95ED6B                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C0D8362BD8361FD8                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        07D4-030A                              vfat       DellUtility                   
/dev/sdc2        5E5CD1015CD0D53D                       ntfs       Data Disc (E:)                
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        82b58ff7-e74f-4d30-8054-c0a4aa4b56a1   ext4                                     
/dev/sdc6        b1a0400a-4b06-4bda-b05a-4530df1d469c   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        07D4-030A                              vfat       DellUtility                   
/dev/sdd2        1EA8699BA8697267                       ntfs       Windows                       
/dev/sdd3: PTTYPE="dos" 
/dev/sdd5        1EB287D01693A333                       ntfs       Program Files                 
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/New Volume_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /media/Data Disc         (E:)       fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd5        /media/Program Files     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/82b58ff7-e74f-4d30-8054-c0a4aa4b56a1 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd2        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 82b58ff7-e74f-4d30-8054-c0a4aa4b56a1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 82b58ff7-e74f-4d30-8054-c0a4aa4b56a1
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
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 82b58ff7-e74f-4d30-8054-c0a4aa4b56a1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=82b58ff7-e74f-4d30-8054-c0a4aa4b56a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 82b58ff7-e74f-4d30-8054-c0a4aa4b56a1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=82b58ff7-e74f-4d30-8054-c0a4aa4b56a1 ro single 
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
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 82b58ff7-e74f-4d30-8054-c0a4aa4b56a1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 82b58ff7-e74f-4d30-8054-c0a4aa4b56a1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdd2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set 1ea8699ba8697267
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

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=82b58ff7-e74f-4d30-8054-c0a4aa4b56a1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=b1a0400a-4b06-4bda-b05a-4530df1d469c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 138.8GB: boot/grub/core.img
 216.1GB: boot/grub/grub.cfg
 126.6GB: boot/initrd.img-2.6.35-22-generic
 126.1GB: boot/vmlinuz-2.6.35-22-generic
 126.6GB: initrd.img
 126.1GB: vmlinuz

================================ sdd2/boot.ini: ================================

[boot loader] 
timeout=2 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc3

00000000  72 1d 42 21 a6 67 5a 4c  e5 52 be d3 b5 00 57 51  |r.B!.gZL.R....WQ|
00000010  7e 65 91 a5 70 0b 92 b3  3e 0a 6a 9c 2b 29 b4 95  |~e..p...>.j.+)..|
00000020  b4 a8 0e 1f 6c ef 1b f0  fe ac f4 e6 a5 43 80 39  |....l........C.9|
00000030  8c 65 c1 89 35 e7 7e 28  d7 19 23 49 93 34 88 05  |.e..5.~(..#I.4..|
00000040  d1 24 96 f0 ee 07 91 9f  1d 16 8a 66 67 8a 4b f0  |.$.........fg.K.|
00000050  9a 94 8f 88 c5 b7 96 ad  5e fc d9 83 3b f8 b7 ca  |........^...;...|
00000060  83 ab 5c d2 7e e9 26 4f  a2 99 12 b6 f3 37 0b f1  |..\.~.&O.....7..|
00000070  de 3b fe f8 d7 ff ff ff  fc 66 95 ff 6a c6 d8 91  |.;.......f..j...|
00000080  56 85 20 08 d8 4d d2 c4  1b 19 be 3b 37 c2 f7 f9  |V. ..M.....;7...|
00000090  87 54 6f 4e a3 66 9f 97  95 31 b3 52 6c f8 85 ea  |.ToN.f...1.Rl...|
000000a0  e1 41 a5 10 71 dd 1f d7  d4 00 00 ce 32 9a bf ad  |.A..q.......2...|
000000b0  d9 f8 0c 53 1a 78 13 55  50 2f a6 cc db a8 f3 b7  |...S.x.UP/......|
000000c0  11 97 43 72 09 96 4c a0  50 23 20 2d 02 98 96 4a  |..Cr..L.P# -...J|
000000d0  75 05 c1 b0 20 41 1d 48  ac 0e 26 21 e9 69 73 47  |u... A.H..&!.isG|
000000e0  ca e3 4c 4b be 94 28 95  0d 15 b4 3a d2 71 01 d6  |..LK..(....:.q..|
000000f0  6e d1 32 71 1f 25 dc 52  df 10 b9 b4 b6 9e f2 d1  |n.2q.%.R........|
00000100  39 bb 7f 8e a6 be d9 65  e7 6f b7 f7 d6 7d fb 99  |9......e.o...}..|
00000110  7f ef 8b 45 07 31 87 61  87 e9 59 28 d9 34 7b e5  |...E.1.a..Y(.4{.|
00000120  10 59 c5 d2 11 cc ab a7  4b 2b 70 ff 8b cc 3b e4  |.Y......K+p...;.|
00000130  2e f5 0c 37 e4 d3 10 9f  62 0b bc 9a a4 25 8b 45  |...7....b....%.E|
00000140  75 81 8f c5 c8 88 4d 85  75 c5 52 35 58 4c 03 4f  |u.....M.u.R5XL.O|
00000150  b6 02 f7 b9 4e a3 1b a7  63 74 f2 e8 75 fe 94 36  |....N...ct..u..6|
00000160  90 12 79 23 92 ab 37 aa  dc bf 98 fb 83 49 40 06  |..y#..7......I@.|
00000170  0f 07 42 d2 f0 02 2a 22  51 98 59 5a d9 9a 36 14  |..B...*"Q.YZ..6.|
00000180  1e b4 4f e4 25 a9 a1 24  19 28 c8 29 0c 57 ad b5  |..O.%..$.(.).W..|
00000190  c7 a0 eb bb 02 9a 5a 08  03 b4 a7 8a 96 cc 6f b9  |......Z.......o.|
000001a0  67 96 53 63 89 ef 89 1d  58 d4 7b fa 9e 26 86 cd  |g.Sc....X.{..&..|
000001b0  fd 41 56 f4 1c 58 4a e8  86 d1 03 90 d8 af 00 fe  |.AV..XJ.........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 e0 0d 00 fe  |........... ....|
000001d0  ff ff 05 fe ff ff 02 20  e0 0d 00 d8 97 00 00 00  |....... ........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by oldfred on 2011-04-02
@drmathprog Welcome to the forums.

If the solutions posted have not worked please start a new thread. I do not see anything obvious in boot script, others may. What works and what does not. Your boot.ini in sdd2 thinks it is drive 0 or sda, but the drivemap command in grub's menu is supposed to make windows think it is in sda & ok. Did you move drives around? Are they all SATA?

---

### Post by drmathprog on 2011-04-02
Sorry, my problems seems like the original poster.  I have an old Dell.  It has 4 ATA drives.  Win XP is installed on Drive 1, which is a partitioned drive.

I installed Ubuntu 10.1 on drive 3.  Drives 0 and 1 are Win data drives.

The machine boots directly into windows with no display of grub offering a choice of dual boot.

I can boot into Ubuntu using the live CD and try it, so I was able to download and run the Boot Script Info.  I was hoping my issue was simply that grub was mis-installed.

---

### Post by Quackers on 2011-04-02
> **drmathprog said:**
> Sorry, my problems seems like the original poster.  I have an old Dell.  It has 4 ATA drives.  Win XP is installed on Drive 1, which is a partitioned drive.

I installed Ubuntu 10.1 on drive 3.  Drives 0 and 1 are Win data drives.

The machine boots directly into windows with no display of grub offering a choice of dual boot.

I can boot into Ubuntu using the live CD and try it, so I was able to download and run the Boot Script Info.  I was hoping my issue was simply that grub was mis-installed.

It appears that grub is installed to /dev/sda, whereas your Ubuntu system is on /dev/sdc
I would boot from the live cd and run these commands in the terminal
```
sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
```
Then on reboot, enter your bios and set sdc as the first boot device (after cd drive).
Ubuntu should now boot directly. If it does, open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run, to see if the Windows Loader is picked up. If it is, reboot and you should see a grub menu giving you the choice of which OS to boot.

---

### Post by drmathprog on 2011-04-02
I can't change the disc boot order; it's C: or nothing.

It seems I can place a USB device prior to the discs, however.

Perhaps I should install Ubuntu on a thumb drive and dual boot from that?

---

### Post by Quackers on 2011-04-02
C: ?  C: isn't a disc! You have 4 hard drives and can't specify which one boots?

---

### Post by drmathprog on 2011-04-02
I have three bios menus that seem to affect booting:
1)  Drive Configuration
2)  Hard Disc Drive Sequence
3)  Boot Sequence

Within each menu, I have:

1)  Drive Configuration  ("This enable or disables each of the following")
     a)  Diskette Drive A
     b)  Primary Master Drive
     c)  Primary Slave Drive
     d)  Secondary Master Drive
     e)  Secondary Slave Drive
     f)   IDE Drive UDMA
2)  Hard Disk Drive Sequence ("Determines the order in which hard drives will be configured in the system.  The first hard drive in the system will be the bootable C: drive")
     a)  System BIOS Boot Devices
     b)  USB Device
3)  Boot Sequence ("Determines the order in which devices will be used")
     a)  IDE CD-ROM device
     b)  Hard-Disk Drive C:
     c)  Diskette Drive
     d)  Integrated NIC

---

### Post by oldfred on 2011-04-02
C: then is just windows speak for first windows 'drive'. If you have multiple windows on different physical drives then which ever you boot is C: and the others are D: etc. 
It should let you boot other drives. But with Ubuntu it will not be C: but sda, sdb, sdc etc.

Windows also moves boot files from a second install to the first install unless you force it not to. Grub will only boot your first install of windows as the other installs do not have boot files. 

Is this system old enough to have the 137GB BIOS boot limit? Older systems will not boot from partitions beyond 137GB. They will read data from above the limit.

---

### Post by drmathprog on 2011-04-02
I think it's about a 2004 or 2005 model.  The Windows drive is 640G, so I assume it's not limited in that way.

---

