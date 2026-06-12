---
title: "GRUB RESCUE&gt; After installation of 9.10 next to Windows"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by dannyfel on 2010-02-10
Dear Ubuntu Gurus...

Yesterday I installed Ubuntu 9.10 from the Live CD, and chose for the option to install side by side with Windows XP, on the same hard drive. For this, naturally the installation had to resize partitions and make new ones. After the installation completed, I rebooted the computer and received the following:

GRUB loading
 Error: no such partition
 Grub rescue >

HELP!!!

---

### Post by l3git.h4cker on 2010-02-10
Heh, I had this same issue.
After a lot of research, I concluded that GRUB had 'broke' the file-system of my partition.
In other words, I corrupted all of my data.

Were you installing a ext4 or ext3 file-system? - if it was ext4, that would explain the corruption.

Sorry to say, but you might have to reformat everything on your hard drive.

---

### Post by dannyfel on 2010-02-10
If it corrupted something it would be the partition tables, not the whole drive. I guess I can still save the data using photorec or testdisk on another computer... but before doing that I would like to fix the problem if it's possible.
Btw, it was the default settings, so I think it installed it in ext3...

---

### Post by kansasnoob on 2010-02-10
> **l3git.h4cker said:**
> Heh, I had this same issue.
After a lot of research, I concluded that GRUB had 'broke' the file-system of my partition.
In other words, I corrupted all of my data.

Were you installing a ext4 or ext3 file-system? - if it was ext4, that would explain the corruption.

Sorry to say, but you might have to reformat everything on your hard drive.

That's an incredible stretch! This:

> I concluded that GRUB had 'broke' the file-system of my partition.

Is virtually impossible!

---

### Post by kansasnoob on 2010-02-10
> **dannyfel said:**
> Dear Ubuntu Gurus...

Yesterday I installed Ubuntu 9.10 from the Live CD, and chose for the option to install side by side with Windows XP, on the same hard drive. For this, naturally the installation had to resize partitions and make new ones. After the installation completed, I rebooted the computer and received the following:

GRUB loading
 Error: no such partition
 Grub rescue >

HELP!!!

Please boot the Live CD and post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That will give us a much better look at your installation.

---

### Post by Sef on 2010-02-10
Also from the Live CD:

Applications > Accessories > Terminal

then copy and paste this code:

```
sudo fdisk -l
```

Copy and paste the results back here.

---

### Post by Objekt on 2010-02-10
> **dannyfel said:**
> Dear Ubuntu Gurus...

Yesterday I installed Ubuntu 9.10 from the Live CD, and chose for the option to install side by side with Windows XP, on the same hard drive. For this, naturally the installation had to resize partitions and make new ones. After the installation completed, I rebooted the computer and received the following:

GRUB loading
 Error: no such partition
 Grub rescue >

HELP!!!

Don't panic!  It is likely that the disk's master boot record (MBR) or GRUB2 config files are the only things messed up.  Your Windows XP install is probably still safe and sound on its NTFS partition.  Getting your system to boot will be a matter of pointing GRUB2 to the right partitions.

There is a command, "update-grub," which in theory could fix your problems.  The problem with this approach is that you have to first boot to at least a command-line interface before you can run the command.  Which is what you can't do, since your system won't boot.

Is it possible to use the "update-grub" command to fix a 9.10 install from within a Live CD session?  Anyone know?

---

### Post by dannyfel on 2010-02-10
Okay, so I started the computer with Ubuntu Live CD. 
First of all, no disk appeared to be corrupted. I could access all the Windows drives. They were all mounted automatically except sda2 and sda6.
 
I ran fdisk and the boot info summary script:
 
[SIZE=4]#sudo fdisk -l[/SIZE]

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x293e293d
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       38913   292085797+   f  W95 Ext'd (LBA)
/dev/sda5            2551       20397   143355996    7  HPFS/NTFS
/dev/sda6           20398       30032    77393106    7  HPFS/NTFS
/dev/sda7           30033       38727    69842556   83  Linux
/dev/sda8           38728       38913     1494013+  82  Linux swap / Solaris
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4a7d62e
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    c  W95 FAT32 (LBA)
Disk /dev/sdc: 16.4 GB, 16416315904 bytes
255 heads, 63 sectors/track, 1995 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ef631df
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1995    16024806    b  W95 FAT32

 
 
[SIZE=4]Boot Info Summary: [/SIZE]
============================= ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS
sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   
sda6: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   
sda7: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda8: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdc: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc has 
                       1939136 sectors.. But according to the info from the 
                       partition table , it has 32063116 sectors.
    Mounting failed:
mount: /dev/sdc already mounted or FD/sdc busy
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x293e293d
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   625,137,344   584,171,595   f W95 Ext d (LBA)
/dev/sda5          40,965,813   327,677,804   286,711,992   7 HPFS/NTFS
/dev/sda6         327,677,868   482,464,079   154,786,212   7 HPFS/NTFS
/dev/sda7         482,464,143   622,149,254   139,685,112  83 Linux
/dev/sda8         622,149,318   625,137,344     2,988,027  82 Linux swap / Solaris

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4a7d62e
Partition  Boot         Start           End          Size  Id System
/dev/sdb1    *             63   156,296,384   156,296,322   c W95 FAT32 (LBA)

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        BCF44C74F44C32C6                       ntfs                                     
/dev/sda5        F05034055033D158                       ntfs                                     
/dev/sda6        8C1011A310119574                       ntfs                                     
/dev/sda7        8c76f1d0-82c2-4dc9-8642-0fccc5090456   ext4                                     
/dev/sda8        f1f07fcb-8617-46d2-83ab-3c484fd2e629   swap                                     
/dev/sdb1        0461-0462                              vfat       NIV2003                       
/dev/sdc1        0DAE-8F71                              vfat                                     
/dev/sdc         49ED-21FF                              vfat                                     
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/NIV2003           vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/BCF44C74F44C32C6  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/F05034055033D158  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6        /media/DISK1             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/0DAE-8F71         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

================================ sda1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== sda7/boot/grub/grub.cfg: ===========================
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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 8c76f1d0-82c2-4dc9-8642-0fccc5090456
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
 set root=(hd0,7)
 search --no-floppy --fs-uuid --set 8c76f1d0-82c2-4dc9-8642-0fccc5090456
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=8c76f1d0-82c2-4dc9-8642-0fccc5090456 ro   quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 insmod ext2
 set root=(hd0,7)
 search --no-floppy --fs-uuid --set 8c76f1d0-82c2-4dc9-8642-0fccc5090456
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=8c76f1d0-82c2-4dc9-8642-0fccc5090456 ro single 
 initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
 insmod ntfs
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set bcf44c74f44c32c6
 drivemap -s (hd0) ${root}
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sda7/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=8c76f1d0-82c2-4dc9-8642-0fccc5090456 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=f1f07fcb-8617-46d2-83ab-3c484fd2e629 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=================== sda7: Location of files loaded by Grub: ===================

 247.0GB: boot/grub/core.img
 247.0GB: boot/grub/grub.cfg
 247.0GB: boot/initrd.img-2.6.31-14-generic
 247.0GB: boot/vmlinuz-2.6.31-14-generic
 247.0GB: initrd.img
 247.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sdb1
00000000  eb 58 90 50 41 52 41 47  4f 4e 23 00 02 20 20 00  |.X.PARAGON#..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  82 e4 50 09 fc 94 00 00  00 00 00 00 02 00 00 00  |..P.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 62 04 61 04 4e  49 56 32 30 30 33 20 20  |..)b.a.NIV2003  |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  0d 0a 50 57 2f 44 42 20  62 79 20 4b 49 52 20 56  |..PW/DB by KIR V|
000001d0  2e 20 28 43 29 20 50 61  72 61 67 6f 6e 20 31 39  |. (C) Paragon 19|
000001e0  39 37 2d 31 39 39 39 00  00 00 00 00 00 00 00 00  |97-1999.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by dannyfel on 2010-02-10
btw, I didn't run update-grub.

---

### Post by kansasnoob on 2010-02-10
OK, even though your exact error is:

> GRUB loading
Error: no such partition
Grub rescue >

I suspect it might be this (you're grub2 just doesn't appear to be pointing to a UUID):

> error: no such device: 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
This error is the result of a failure of the GRUB 2 search function. There are various bugs associated with the search function. To boot into your system, highlight the OS you want to boot. Press "e" to edit the menuentry. Delete the entire "search ..." line, then CTRL-x to boot.

Once you have booted into the system, you will modify the /usr/lib/grub/grub-mkconfig_lib file in accordance with this link:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Kudos to Dave for this:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by kansasnoob on 2010-02-10
This also discusses how to use the Grub Rescue:

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

---

### Post by meierfra. on 2010-02-10
Maybe you bios are not able to read your whole hard drive. 
Type 

```
ls
```
at the "grub>rescue" prompt and post the output.

Also check whether your Bios think that your 320GB hard drive  only has size 137GB.

---

### Post by dannyfel on 2010-02-11
Thanks for the hint meierfra.

Although I haven't checked it yet, I have a feeling that the reason GRUB can't find the partition is that it's located past the 137GB limit, as it is a relatively old computer (several years).

Is there a way to reinstall Ubuntu side by side Windows (which boot record is located in the beginning of the disk, in a 20GB partition), while pushing the rest of the Windows partition a bit? That way I can place the /boot in a dedicated partition just after the 20GB of windows so that it will be inside the 137GB limit.

Is this possible to accomplish during the installation of Ubuntu?

---

### Post by meierfra. on 2010-02-11
> Is there a way to reinstall Ubuntu side by side Windows (which boot record is located in the beginning of the disk, in a 20GB partition), while pushing the rest of the Windows partition a bit? That way I can place the /boot in a dedicated partition just after the 20GB of windows so that it will be inside the 137GB limit.

I would use "gparted" on the LiveCD to either shrink your Windows partition by say  200MB from the end, or shrink  /dev/sda5  by 200MB from the start.  Shrinking  /dev/sda5 is a little  safer since you won't be messing with operating system, but will take a lot longer. And as long as you don't move the start point of your Window partition,  you shouldn't really have any problems.  
Then use the 200GB to create a ext4 partition.

Whatever partition you decide to shrink:

Backup any value data.
Defrag and run "chkdsk /f" on that partition before hand.
After resizing and before reinstalling Ubuntu:  boot into Window XP a couple of times.

Then just reinstall using the 200MB partition as a boot partition.

> Although I haven't checked it yet, I have a feeling that the reason GRUB can't find the partition is that it's located past the 137GB limit, as it is a relatively old computer (several years).
Make sure to check before reinstalling. If  your problem isn't caused by the 137GB limit, reinstalling probably  won't do any good.

---

### Post by dannyfel on 2010-02-13
So the reason for the GRUB RESCUE> prompt was indeed because of the old BIOS not recognizing the full size of the 320GB disk. The BIOS sees only up to 137GB. Since the GRUB files and Linux boot image were installed after the original Windows partition, in 247GB of the disk, GRUB could not find the partition or boot from it at all. Hence, "no such partition".
 
> 
=================== sda7: Location of files loaded by Grub: ===================
 
247.0GB: boot/grub/core.img
247.0GB: boot/grub/grub.cfg
247.0GB: boot/initrd.img-2.6.31-14-generic
247.0GB: boot/vmlinuz-2.6.31-14-generic
247.0GB: initrd.img
247.0GB: vmlinuz

 
I will now try to resize the Windows data partition from the beginning, so there will be place for /boot in the beginning of the disk.
 
Thanks meierfra.!

---

