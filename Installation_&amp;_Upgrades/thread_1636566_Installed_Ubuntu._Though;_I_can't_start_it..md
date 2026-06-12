---
title: "Installed Ubuntu. Though; I can't start it."
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Nocturnal.kaldorei on 2010-12-03
Hello there!

I just installed the 10.10 version of Ubuntu and while doing so I also deleted the whole partition on the harddrive.

While I where installing the OS. I got this message:

[IMG]http://s1046.photobucket.com/albums/b465/Dennis_Quick/?action=view&current=DSC00232.jpg[/IMG]Sorry. An error occurred and it was not possible
to install the bootloader at the specified location.
(Here I get to choose either if I want to choose a different place to put the bootloader on. Or if I want to continue without a bootloader or if I would want to cancel the installation.)

I am currently writing from the live CD.
[B]
And If I try to boot without the CD. The computer tells me that there is no bootable device.[/B]

I have tried to reinstall Grub. 
I have also tried to reinstall the whole Ubuntu 10.10. I have also tried to install Ubuntu 10.04. Both with the original CD.

I have searched through the whole internet for solutions and none have worked. And from what I have seen. I am not the only one with this problem.

Thanks.
[IMG]http://s1046.photobucket.com/albums/b465/Dennis_Quick/?action=view&current=DSC00232.jpg[/IMG]
[IMG]http://s1046.photobucket.com/albums/b465/Dennis_Quick/?action=view&current=DSC00232.jpg[/IMG]

---

### Post by Quackers on 2010-12-03
From in the live cd environment and after making sure you have an internet connection please go to the site below and download the boot script to the DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Nocturnal.kaldorei on 2010-12-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

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
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 137     3,842,047     3,841,911   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b6ecd4b9-c70e-4ffc-ae5c-09eacb010efd   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c6b5d8ae-c5bd-4e27-a97b-acadd035b38e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4488-52F3                              vfat       PHONE CARD                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sdb1        /media/PHONE CARD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda1        /media/b6ecd4b9-c70e-4ffc-ae5c-09eacb010efd ext4       (rw,nosuid,nodev,uhelper=udisks)


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
UUID=b6ecd4b9-c70e-4ffc-ae5c-09eacb010efd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c6b5d8ae-c5bd-4e27-a97b-acadd035b38e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  71.0GB: boot/grub/core.img
    .5GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
    .3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f4 89 d0 8b 75 f8 8b 7d  fc 89 ec 5d c3 8d 76 00  |....u..}...]..v.|
00000010  31 d2 89 d9 89 f8 e8 05  26 ed ff 89 c2 eb d0 ba  |1.......&.......|
00000020  f4 ff ff ff eb d8 8d 76  00 8d bc 27 00 00 00 00  |.......v...'....|
00000030  55 89 e5 57 56 89 c6 53  8d 80 10 01 00 00 83 ec  |U..WV..S........|
00000040  24 89 45 dc e8 27 fa 12  00 8b 8e f0 00 00 00 8d  |$.E..'..........|
00000050  55 f0 89 f0 ff 51 08 85  c0 0f 85 4e 02 00 00 8b  |U....Q.....N....|
00000060  9e d0 00 00 00 85 db 0f  8e d2 00 00 00 8d 8e f4  |................|
00000070  00 00 00 31 ff 89 4d e4  c7 45 d8 00 00 00 00 90  |...1..M..E......|
00000080  8b 9e f0 00 00 00 8d 4d  e8 89 fa 89 f0 ff 53 14  |.......M......S.|
00000090  8b 9e f0 00 00 00 8d 4d  ec 89 fa 89 f0 ff 53 18  |.......M......S.|
000000a0  8b 45 e8 83 f8 01 74 68  0f 83 da 00 00 00 8b 96  |.E....th........|
000000b0  f4 00 00 00 8d 5a b4 8b  43 4c 0f 18 00 90 39 55  |.....Z..CL....9U|
000000c0  e4 74 6d 89 75 e0 8b 75  e4 eb 19 90 8d 74 26 00  |.tm.u..u.....t&.|
000000d0  8d 58 b4 89 c2 8b 43 4c  0f 18 00 90 39 d6 0f 84  |.X....CL....9...|
000000e0  64 01 00 00 39 7b 20 75  e7 8b 55 f0 3b 55 ec 8b  |d...9{ u..U.;U..|
000000f0  43 1c 0f 8c f8 00 00 00  8b 88 d0 00 00 00 ba 01  |C...............|
00000100  00 00 00 ff 51 08 8b 43  4c eb c5 90 8d 74 26 00  |....Q..CL....t&.|
00000110  8b 55 f0 8b 4d ec 39 ca  7d 09 80 be e8 00 00 00  |.U..M.9.}.......|
00000120  00 74 0d 89 f0 89 3c 24  e8 83 f2 ff ff 8d 76 00  |.t....<$......v.|
00000130  83 c7 01 39 be d0 00 00  00 0f 8f 41 ff ff ff 8b  |...9.......A....|
00000140  8e ec 00 00 00 85 c9 0f  85 2b 01 00 00 8b 45 f0  |.........+....E.|
00000150  89 86 e4 00 00 00 80 be  e8 00 00 00 00 0f 85 2d  |...............-|
00000160  01 00 00 8b 96 e0 00 00  00 85 d2 0f 85 ef 00 00  |................|
00000170  00 8b 45 dc e8 b7 f6 12  00 83 c4 24 5b 5e 5f 5d  |..E........$[^_]|
00000180  c3 8d b4 26 00 00 00 00  83 f8 02 74 7b 83 f8 03  |...&.......t{...|
00000190  75 9e 8b 45 f0 3b 45 ec  7c 96 8b 86 f0 00 00 00  |u..E.;E.|.......|
000001a0  8b 58 20 85 db 74 0e b9  03 00 00 00 89 fa 89 f0  |.X ..t..........|
000001b0  ff d3 89 45 d8 8b 4d d8  85 c9 0f 85 70 ff 00 fe  |...E..M.....p...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 40 01 00  |.<.MSWIN4.1..@..|
00000010  02 00 02 00 00 f8 1b 01  20 00 40 00 89 00 00 00  |........ .@.....|
00000020  60 9f 3a 00 00 00 29 f3  52 88 44 20 20 20 20 20  |`.:...).R.D     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |      FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
```

Here you go!

Thank you for the fast reply!

---

### Post by Quackers on 2010-12-03
It seems that for some reason you have no /boot/grub/grub.cfg in your sda1 
I don't know why that may be. I would suggest that you purge and re-install grub.

Please copy/paste the following lines into your terminal and press enter after each line.

```
sudo mkdir /mnt/temp
sudo mount /dev/sda1 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```

Then go to the following guide and scroll down to the "Why chroot?" section (in RED) and follow the guide from item no 2

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

When you get the option about where to install grub, choose sda (NOT sda1) by highlighting it and then pressing the space bar to put an asterisk in its box then tab to ok and press enter.

---

### Post by Nocturnal.kaldorei on 2010-12-03
When typing the following:
```
sudo mount /dev/sda1 /mnt/temp
```

I get the following error: 
```
mount: mount point /mnt/temp does not exist
```

Thank you!

---

### Post by Quackers on 2010-12-03
Sorry! Try this line first
```
sudo mkdir /mnt/temp
```

---

### Post by Nocturnal.kaldorei on 2010-12-03
I did everything you wrote and everything from the 2nd item on the link. It all purged and installed just fine without any problems or errors. 
Though: When I where done and restarted my computer I still had the same problem and it says that I have no bootable device..

Thank you.

---

### Post by Quackers on 2010-12-03
Ok, there is one last thing.
Your boot script output shows that you have no partition marked as bootable. This is not a problem for Ubuntu, however, it can be a problem for some computer BIOSes.
Please boot from the Live cd again and select "try ubuntu".
When the desktop loads go to System > Admin > Gparted. When Gparted opens it will take a few seconds to scan your hard drive for partitions. When it finishes the window will show all your partitions. Right-click on sda1 and choose Manage Flags and in the small window that opens check the box for "Boot". Apply changes, if necessary (via the green tick in the toolbar).
Then reboot and see if things are different.

---

### Post by Nocturnal.kaldorei on 2010-12-03
After I did what you wrote, I restarted the computer and instead of saying that there is no bootable device found, it instead makes my screen pitch black after booting a while.

---

### Post by Quackers on 2010-12-03
Aha! it could be trying to boot but have a graphics problem - hopefully!
When you try to boot from the hard drive hold down the shift key until the grub menu appears. When it appears and your Ubuntu installation is highlighted (it should be by default) press the "e" key and then press the down arrow and right arrow until you get to the line which ends with "quiet splash", then delete the quiet splash and type in nomodeset and press ctrl+x to reboot.
Hopefully it will boot and get to the desktop. You will then get the chance to install hardware drivers for your video card, if any are available.

---

### Post by Nocturnal.kaldorei on 2010-12-03
> **Quackers said:**
> Aha! it could be trying to boot but have a graphics problem - hopefully!
When you try to boot from the hard drive hold down the shift key until the grub menu appears. When it appears and your Ubuntu installation is highlighted (it should be by default) press the "e" key and then press the down arrow and right arrow until you get to the line which ends with "quiet splash", then delete the quiet splash and type in nomodeset and press ctrl+x to reboot.
Hopefully it will boot and get to the desktop. You will then get the chance to install hardware drivers for your video card, if any are available.

Works perfectly now!

Thank you so much! <3

---

### Post by Quackers on 2010-12-03
Aha! :-) I like happy endings :-)
Please mark the thread as solved using the Thread Tools near the top of the page. Thanks.
Don't forget to install video drivers if any are available, otherwise you will need to edit a file to run nomodeset at every boot - maybe.

---

