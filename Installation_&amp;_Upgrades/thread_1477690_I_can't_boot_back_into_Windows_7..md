---
title: "I can't boot back into Windows 7."
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by iTzDyl on 2010-05-09
I'm currently in the Try Ubuntu feature in the installer. This is what I  did.

I wanted to go back to try Ubuntu again. I used to use it and I wanted  to try it again. So I make a partition on my external hard drive to put  Ubuntu in. I tried WUBI but that wouldn't work, so I downloaded it and  burned it to a disc. I boot into the disc and install Ubuntu NOT on the  partition I made. (It wouldn't install there). So it made it's own  partition on my External Hard Drive. It installs, my computer restarts  and the disc comes out. My computer is booting up when a command line  type screen comes up saying GRUB recovery or something along the lines. I  can't do anything or get past it. So I restart my computer with the  Ubuntu disc in, and it brings me back to the install menu like it never  did anything. I looked in the Disc Utility and saw everything is still  in it's place, so nothing happened.  Can somebody please help me? I  really don't want to be stuck in this Try Ubuntu thing. I can give you  all the information I can. Thanks

Dylan

Here is the Boot Info:

```

                Boot Info Script 0.55    dated February 15th, 2010                     

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same  drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdf

sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe  /grldr

sda2:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr  /wubildr

sda3:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /grldr

sdf1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf2:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf3:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf4:  _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdf5:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdf5  starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdf6:  _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sdf7:  _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   537,061,566   537,061,504   7 HPFS/NTFS
/dev/sda2         537,063,424   598,501,375    61,437,952   7 HPFS/NTFS
/dev/sda3         598,501,575   625,137,344    26,635,770   7 HPFS/NTFS


Drive: sdf ___________________  _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   210,676,409   210,676,347   7 HPFS/NTFS
/dev/sdf2         210,676,410   668,176,430   457,500,021   7 HPFS/NTFS
/dev/sdf3         668,178,432   691,383,839    23,205,408   7 HPFS/NTFS
/dev/sdf4         691,384,318   976,771,071   285,386,754   f W95 Ext d  (LBA)
/dev/sdf5         853,893,120   976,771,071   122,877,952   7 HPFS/NTFS
/dev/sdf6         691,384,320   847,183,871   155,799,552  83 Linux
/dev/sdf7         847,185,920   853,886,975     6,701,056  82 Linux swap  / Solaris


blkid -c /dev/null:  ____________________________________________________________

Device           UUID                                   TYPE       LABEL                          

/dev/loop0                                              squashfs                                  
/dev/sda1        70CC4ED4CC4E93EE                       ntfs       Vista                          
/dev/sda2        BABC596DBC592563                       ntfs        Windows 7                     
/dev/sda3        949CA48C9CA46A86                       ntfs        FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdf1        01CA9AE1DFF2C970                       ntfs        Install and Download          
/dev/sdf2        1A143F8E143F6C3F                       ntfs        Uploads                       
/dev/sdf3        002AE2A42AE29646                       ntfs        Whatever                      
/dev/sdf4: PTTYPE="dos" 
/dev/sdf5        D89E931A9E92EFEC                       ntfs        Ubuntu                        
/dev/sdf6        23882620-ca51-4a91-850d-1e28d2e4209f   ext4                                      
/dev/sdf7        707a93ed-a6f2-4153-8585-6c92251792e9   swap                                      
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdf6/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 23882620-ca51-4a91-850d-1e28d2e4209f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 23882620-ca51-4a91-850d-1e28d2e4209f
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set  23882620-ca51-4a91-850d-1e28d2e4209f
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=23882620-ca51-4a91-850d-1e28d2e4209f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set  23882620-ca51-4a91-850d-1e28d2e4209f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=23882620-ca51-4a91-850d-1e28d2e4209f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set  23882620-ca51-4a91-850d-1e28d2e4209f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set  23882620-ca51-4a91-850d-1e28d2e4209f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 70cc4ed4cc4e93ee
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdf6/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdf6 during installation
UUID=23882620-ca51-4a91-850d-1e28d2e4209f /               ext4     errors=remount-ro 0       1
# swap was on /dev/sdf7 during installation
UUID=707a93ed-a6f2-4153-8585-6c92251792e9 none            swap    sw               0       0

=================== sdf6: Location of files loaded by Grub:  ===================


 384.2GB: boot/grub/core.img
 407.9GB: boot/grub/grub.cfg
 384.2GB: boot/initrd.img-2.6.32-21-generic
 384.1GB: boot/vmlinuz-2.6.32-21-generic
 384.2GB: initrd.img
 384.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc  =======================

Unknown BootLoader  on sdf4

00000000  34 4e eb df c8 db 5b 67  72 96 34 f2 aa fd e6 13   |4N....[gr.4.....|
00000010  8f 1e 34 22 12 44 fb 86  08 6c 6b f4 9b 95 f3 19   |..4".D...lk.....|
00000020  db 2e 81 ef 6f 67 a8 83  0d fe e0 cc 0d a7 6b cf   |....og........k.|
00000030  60 f5 49 ae f0 7d ce 36  a2 34 31 c9 eb b1 4e 9e   |`.I..}.6.41...N.|
00000040  22 18 81 a6 57 cb c3 27  91 77 1f df 1e 40 f5 a7   |"...W..'.w...@..|
00000050  0d 69 ae 51 78 49 36 5b  b4 56 94 fb d9 1b d9 00   |.i.QxI6[.V......|
00000060  31 19 f7 57 60 96 25 b1  40 02 9d 1c c8 2c f0 c0   |1..W`.%.@....,..|
00000070  02 6b d5 90 06 ae e2 62  44 79 4c 6e 61 41 07 1d   |.k.....bDyLnaA..|
00000080  88 42 0a ca 79 97 e8 c4  74 91 af 86 e8 e3 13 2b   |.B..y...t......+|
00000090  e4 c0 da 53 9e 34 38 93  3f d5 57 05 39 e3 7e c2   |...S.48.?.W.9.~.|
000000a0  5a ff 33 27 f6 32 56 f1  93 a7 1a 5f 15 58 5f 66   |Z.3'.2V...._.X_f|
000000b0  ae 77 04 47 52 0a da 60  a4 c0 1a f6 51 50 83 04   |.w.GR..`....QP..|
000000c0  b5 10 6c 55 f0 8c 56 01  ab 47 e4 9f 38 ef 61 04   |..lU..V..G..8.a.|
000000d0  41 29 7d a9 87 32 0c 94  93 c2 bf ee 5d 5c 45 a0   |A)}..2......]\E.|
000000e0  b9 27 e2 e2 f1 e8 6a 37  e8 25 8c c5 0f 00 b5 3a   |.'....j7.%.....:|
000000f0  7f f4 b7 3d 2a 4f 4b d0  19 16 1c 31 3b 85 59 a1   |...=*OK....1;.Y.|
00000100  50 eb 06 cb 96 ee cd d8  3f d6 06 80 20 2d a3 3f   |P.......?... -.?|
00000110  c7 f7 4f e0 8c d0 9d 06  8a e8 c3 b0 ec b4 97 da   |..O.............|
00000120  3a 17 86 24 b7 a0 aa 02  02 fd 10 b3 9d ba 70 66   |:..$..........pf|
00000130  05 f6 90 4b d1 04 b4 8b  a5 4b 35 6f d0 9f 2b c7   |...K.....K5o..+.|
00000140  95 db d1 a9 81 67 dd a9  5f a7 1d 6c 94 c6 f4 01   |.....g.._..l....|
00000150  48 41 77 65 28 d7 68 49  34 12 1d 82 4a f8 72 36   |HAwe(.hI4...J.r6|
00000160  35 d1 a2 1f 3c 9f a5 66  74 d3 b1 2b cb 2f ae 12   |5...<..ft..+./..|
00000170  54 b2 4d a9 ed ef b1 93  35 44 1a 08 b8 ca 58 db   |T.M.....5D....X.|
00000180  5c c6 00 1f eb 3c 47 3c  46 66 b5 6d 59 ea 67 aa   |\....<G<Ff.mY.g.|
00000190  8a 5f a7 b3 73 e5 a3 7d  49 3a bf fa 27 c0 b3 88   |._..s..}I:..'...|
000001a0  46 5d 06 d0 09 1d 2b eb  ad 5d 09 b3 19 9b 3b c1   |F]....+..]....;.|
000001b0  19 2e 02 d2 08 b5 46 50  11 9a 1f 01 c4 77 00 fe   |......FP.....w..|
000001c0  ff ff 07 fe ff ff 02 b0  af 09 00 f8 52 07 00 fe   |............R...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 50 49 09 00 00   |...........PI...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa   |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard  drive==============

sdb sdc sdd sde 
```This is what I get from F Disk
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33431   268530752    7  HPFS/NTFS
/dev/sda2           33431       37255    30718976    7  HPFS/NTFS
/dev/sda3           37256       38913    13317885    7  HPFS/NTFS

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00076272

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       13114   105338173+   7  HPFS/NTFS
/dev/sdf2           13115       41593   228750010+   7  HPFS/NTFS
/dev/sdf3           41593       43037    11602704    7  HPFS/NTFS
/dev/sdf4           43037       60802   142693377    f  W95 Ext'd (LBA)
/dev/sdf5           53153       60802    61438976    7  HPFS/NTFS
/dev/sdf6           43037       52735    77899776   83  Linux
/dev/sdf7           52735       53153     3350528   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by iTzDyl on 2010-05-09
I'm going to bed now. I will be here in the morning. Thanks,

Dylan

---

### Post by Zireth ZH on 2010-05-09
Hey pal ... welcome back to ubuntu... I hope this link helps you.. 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by iTzDyl on 2010-05-09
I tried reinstalling GRUB, still not working. I'm downloading the Windows 7 recovery disc at the moment. Hope this works :)

---

### Post by darkod on 2010-05-09
You have quite a decent mess, hold on, don't try too many things at the same time.

You see in the top of the results file it says grub2 installed on /dev/sda and looking in partition 6 for grub files. But in the fdisk results the disk with 7 partitions is /dev/sdf, not /dev/sda.

Also, on /dev/sda1 and /dev/sda2 you have some remains from wubi and grub (grldr) which shouldn't be there. I guess this is blocking the windows load files starting correctly.

Get rid of any wubi install you might have, check in Add/Remove programs. Deinstall it.

Make a plan which disk you want to boot from (I guess the internal one), and set HDD as boot options before USB-HDD in BIOS.

Otherwise it doesn't look too bad. And another thing, when you created the partition for ubuntu did you do it from windows? In that case it would be NTFS and of course linux doesn't install on ntfs. No need to create partitions in advance, even of linux type. Just leave the space as unallocated, not belonging to any partition, and then during the install process either use one of the guided methods or the manual partitioning.

---

### Post by nikefalcon on 2010-05-09
> **darkod said:**
> 
Get rid of any wubi install you might have, check in Add/Remove programs. Deinstall it.



How will he be able to do that??(he can't boot into windows, right??)

---

### Post by iTzDyl on 2010-05-09
I'm typing this from Windows 7 right now. I reinstalled the Windows 7 bootloader through my recovery disc. Everything seems fine and I have a partition with 80gb on it (thats on my external HDD). I think that was the one I made during the installation. I forgot Ubuntu couldn't install on NTFS. 

So I should install Ubuntu on the 80gb of space on my extrenal hard drive? It is not formated to NTFS, it just empty space. I probably can install it onto my internal hard drive, but there is hardly any space left on it.

---

### Post by darkod on 2010-05-09
> **iTzDyl said:**
> I'm typing this from Windows 7 right now. I reinstalled the Windows 7 bootloader through my recovery disc. Everything seems fine and I have a partition with 80gb on it (thats on my external HDD). I think that was the one I made during the installation. I forgot Ubuntu couldn't install on NTFS. 

So I should install Ubuntu on the 80gb of space on my extrenal hard drive? It is not formated to NTFS, it just empty space. I probably can install it onto my internal hard drive, but there is hardly any space left on it.

Right now it's up to you. The ubuntu on /dev/sdf6 should still be there, you just have to install grub back. Also, if you plan to boot your PC with the ext hdd disconnected, you actually need to install grub2 on the ext hdd, not the int. Grub files will be on /dev/sdf6 and it won't boot without the ext if you put grub on the internal.

So, you can keep using the ubuntu on /dev/sdf6 or delete /dev/sdf6 and /dev/sdf7, maybe even /dev/sdf5 if that was the one you created for ubuntu, and install ubuntu on all that unallocated space after deleting them. In that case you should also delete /dev/sdf4 which is the extanded partition container for 5, 6 and 7. Ubuntu installer will create new extended partition in that space.

And make sure the bootloader goes to /dev/sdf (the ext hdd) as stated above. You can check that in the last screen of the installer clicking on the Advanced button.

If you want to keep using the current install just let us know and I can give you the commands to reinstall grub2 to /dev/sdf, no need to reinstall anything else.

---

### Post by iTzDyl on 2010-05-09
> **darkod said:**
> Right now it's up to you. The ubuntu on /dev/sdf6 should still be there, you just have to install grub back. Also, if you plan to boot your PC with the ext hdd disconnected, you actually need to install grub2 on the ext hdd, not the int. Grub files will be on /dev/sdf6 and it won't boot without the ext if you put grub on the internal.

So, you can keep using the ubuntu on /dev/sdf6 or delete /dev/sdf6 and /dev/sdf7, maybe even /dev/sdf5 if that was the one you created for ubuntu, and install ubuntu on all that unallocated space after deleting them. In that case you should also delete /dev/sdf4 which is the extanded partition container for 5, 6 and 7. Ubuntu installer will create new extended partition in that space.

And make sure the bootloader goes to /dev/sdf (the ext hdd) as stated above. You can check that in the last screen of the installer clicking on the Advanced button.

If you want to keep using the current install just let us know and I can give you the commands to reinstall grub2 to /dev/sdf, no need to reinstall anything else.

Your post blew my mind lol. Anyway, this is what I would like to have...

Currently, I have windows 7 ands Vista on my internal hard drive. So I have one partition for Vista, one for Win 7 and another as a recover. On my External, I have 4 partitions. One for games / software, one for movies / music, one for whatever and one that I was going to install Ubuntu to. I also have one that is not formatted to NTFS. I would like to install Ubuntu to the partition that is /dev/sdf6. I would like it so when I boot, it comes up with either the Windows boot loader or GRUB (I don't really care), and it asks me to boot into Win 7, vista or Ubuntu. Is it possible to install it to /dev/sdf6 on my external hard drive and have it ask to boot into Win 7 / Vista? Thanks for all the help so far.

---

### Post by iTzDyl on 2010-05-09
Oh, and in my Add or Remove Programs menu, I see something installed as Ubuntu. This might be from when I tried to install Ubuntu from Wubi. Should I uninstall that or leave it? It says it was installed on 5/3/10.

---

### Post by darkod on 2010-05-09
> **iTzDyl said:**
> Your post blew my mind lol. Anyway, this is what I would like to have...

Currently, I have windows 7 ands Vista on my internal hard drive. So I have one partition for Vista, one for Win 7 and another as a recover. On my External, I have 4 partitions. One for games / software, one for movies / music, one for whatever and one that I was going to install Ubuntu to. I also have one that is not formatted to NTFS. I would like to install Ubuntu to the partition that is /dev/sdf6. I would like it so when I boot, it comes up with either the Windows boot loader or GRUB (I don't really care), and it asks me to boot into Win 7, vista or Ubuntu. Is it possible to install it to /dev/sdf6 on my external hard drive and have it ask to boot into Win 7 / Vista? Thanks for all the help so far.


/dev/sdf1   *           [COLOR=Red]1       13114[/COLOR]   105338173+   7  HPFS/NTFS
/dev/sdf2 [COLOR=Red]          13115       41593[/COLOR]   228750010+   7  HPFS/NTFS
/dev/sdf3           [COLOR=Red]41593       43037[/COLOR]    11602704    7  HPFS/NTFS
/dev/sdf4           [COLOR=Red]43037       60802[/COLOR]   142693377    f  W95 Ext'd (LBA)
/dev/sdf5           53153       60802    61438976    7  HPFS/NTFS
/dev/sdf6           43037       52735    77899776   83  Linux
/dev/sdf7           52735       53153     3350528   82  Linux swap / Solaris

The ext 500GB hdd has 60802 cylinders. As far as I can see, it's all used for partitions (whether with data or empty it doesn't matter).

/dev/sdf5, /dev/sdf6 and /dev/sdf7 are logical partitions inside /dev/sdf4.

If you want to boot without the ext hdd sometimes, grub2 must be on the ext hdd.

So, you would have:
Boot without the ext hdd, the windows bootloader from /dev/sda kicks in giving you options for 7 and Vista.
Boot with the ext hdd plugged, selecting at boot the USB-HDD as boot device (either in BIOS or in a boot menu by pressing F12 or similar, depending on the computer), then Grub2 from /dev/sdf would kick in, giving you options for ubuntu and windows, if you select windows there will be second menu to select 7 or Vista. This is a limitation of Microsoft which combines boot files if you have 2 or more version of windows installed.

In some cases there are exceptions but in most default cases your 7 and Vista files are already combined together and grub can't boot them directly without the second menu as a middle step.

Options:

1. Keep the current ubuntu from /dev/sdf6 and swap partition /dev/sdf7, use the approx 66GB ntfs /dev/sdf5 partition for anything you want.

For this option you just need to reinstall grub2 to /dev/sdf. Boot with the 10.04 cd in Try Ubuntu option, open terminal and do:

sudo fdisk (check that the ext hdd is really /dev/sdf)
sudo mount /dev/sdf6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdf

That will install grub2 on /dev/sdf with the root partition being /dev/sdf6. Restart, boot into ubuntu and do:
sudo update-grub

to recreate the grub menu.

2. If you want to use the whole space currently taken by /dev/sdf5-7 for ubuntu, boot the live desktop, open Gparted and delete in this order: /dev/sdf5, /dev/sdf6, /dev/sdf7 and /devsdf4. Before deleting /dev/sdf7 you will have to right-click it and select Swapoff, that will remove the keys lock symbol from it.
Click on the big green button in Gparted to execute the changes.
After that boot the ubuntu installer and select to install on /dev/sdf using the Use Largest Available Free space option, it will use the whole unallocated space created by deleting the partitions.
In the last screen of the installer click on Advanced and make sure the bootloder (grub2) gets installed on /dev/sdf.

---

### Post by darkod on 2010-05-09
> **iTzDyl said:**
> Oh, and in my Add or Remove Programs menu, I see something installed as Ubuntu. This might be from when I tried to install Ubuntu from Wubi. Should I uninstall that or leave it? It says it was installed on 5/3/10.

Yes, that is wubi. I would try removing it although now it might complain about not finding some files to remove because the windows boot restore possibly overwrote some wubi boot files.

---

### Post by iTzDyl on 2010-05-10
Okay, I did what you said in option one. The terminal said there was no errors. When I restarted, I was given the choice to either boot into Win 7, Vista or Ubuntu. When I hit Ubuntu, it gave me an error that it couldn't be booted, so I went back and booted into Win 7 with no problem. Any ideas? Should I try option 2?

---

### Post by darkod on 2010-05-10
Post another results file from the live mode. Lets see how it looks now. I'm starting to think it changed device name, or your device.map is not correct.

---

### Post by iTzDyl on 2010-05-10
New Boot Info:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdf and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /grldr

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdf5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdf6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   537,061,566   537,061,504   7 HPFS/NTFS
/dev/sda2         537,063,424   598,501,375    61,437,952   7 HPFS/NTFS
/dev/sda3         598,501,575   625,137,344    26,635,770   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   210,676,409   210,676,347   7 HPFS/NTFS
/dev/sdf2         210,676,410   668,176,430   457,500,021   7 HPFS/NTFS
/dev/sdf3         668,178,432   691,383,839    23,205,408   7 HPFS/NTFS
/dev/sdf4         691,384,318   976,771,071   285,386,754   f W95 Ext d (LBA)
/dev/sdf5         853,893,120   976,771,071   122,877,952   7 HPFS/NTFS
/dev/sdf6         691,384,320   847,183,871   155,799,552  83 Linux
/dev/sdf7         847,185,920   853,886,975     6,701,056  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        70CC4ED4CC4E93EE                       ntfs       Vista                         
/dev/sda2        BABC596DBC592563                       ntfs       Windows 7                     
/dev/sda3        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdf1        01CA9AE1DFF2C970                       ntfs       Install and Download          
/dev/sdf2        1A143F8E143F6C3F                       ntfs       Uploads                       
/dev/sdf3        002AE2A42AE29646                       ntfs       Whatever                      
/dev/sdf4: PTTYPE="dos" 
/dev/sdf5        D89E931A9E92EFEC                       ntfs       Ubuntu                        
/dev/sdf6        23882620-ca51-4a91-850d-1e28d2e4209f   ext4                                     
/dev/sdf7        707a93ed-a6f2-4153-8585-6c92251792e9   swap                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdf6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 23882620-ca51-4a91-850d-1e28d2e4209f
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 23882620-ca51-4a91-850d-1e28d2e4209f
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
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 23882620-ca51-4a91-850d-1e28d2e4209f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=23882620-ca51-4a91-850d-1e28d2e4209f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 23882620-ca51-4a91-850d-1e28d2e4209f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=23882620-ca51-4a91-850d-1e28d2e4209f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 23882620-ca51-4a91-850d-1e28d2e4209f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 23882620-ca51-4a91-850d-1e28d2e4209f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 70cc4ed4cc4e93ee
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdf6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdf6 during installation
UUID=23882620-ca51-4a91-850d-1e28d2e4209f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf7 during installation
UUID=707a93ed-a6f2-4153-8585-6c92251792e9 none            swap    sw              0       0

=================== sdf6: Location of files loaded by Grub: ===================


 384.2GB: boot/grub/core.img
 407.9GB: boot/grub/grub.cfg
 384.2GB: boot/initrd.img-2.6.32-21-generic
 384.1GB: boot/vmlinuz-2.6.32-21-generic
 384.2GB: initrd.img
 384.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdf4

00000000  34 4e eb df c8 db 5b 67  72 96 34 f2 aa fd e6 13  |4N....[gr.4.....|
00000010  8f 1e 34 22 12 44 fb 86  08 6c 6b f4 9b 95 f3 19  |..4".D...lk.....|
00000020  db 2e 81 ef 6f 67 a8 83  0d fe e0 cc 0d a7 6b cf  |....og........k.|
00000030  60 f5 49 ae f0 7d ce 36  a2 34 31 c9 eb b1 4e 9e  |`.I..}.6.41...N.|
00000040  22 18 81 a6 57 cb c3 27  91 77 1f df 1e 40 f5 a7  |"...W..'.w...@..|
00000050  0d 69 ae 51 78 49 36 5b  b4 56 94 fb d9 1b d9 00  |.i.QxI6[.V......|
00000060  31 19 f7 57 60 96 25 b1  40 02 9d 1c c8 2c f0 c0  |1..W`.%.@....,..|
00000070  02 6b d5 90 06 ae e2 62  44 79 4c 6e 61 41 07 1d  |.k.....bDyLnaA..|
00000080  88 42 0a ca 79 97 e8 c4  74 91 af 86 e8 e3 13 2b  |.B..y...t......+|
00000090  e4 c0 da 53 9e 34 38 93  3f d5 57 05 39 e3 7e c2  |...S.48.?.W.9.~.|
000000a0  5a ff 33 27 f6 32 56 f1  93 a7 1a 5f 15 58 5f 66  |Z.3'.2V...._.X_f|
000000b0  ae 77 04 47 52 0a da 60  a4 c0 1a f6 51 50 83 04  |.w.GR..`....QP..|
000000c0  b5 10 6c 55 f0 8c 56 01  ab 47 e4 9f 38 ef 61 04  |..lU..V..G..8.a.|
000000d0  41 29 7d a9 87 32 0c 94  93 c2 bf ee 5d 5c 45 a0  |A)}..2......]\E.|
000000e0  b9 27 e2 e2 f1 e8 6a 37  e8 25 8c c5 0f 00 b5 3a  |.'....j7.%.....:|
000000f0  7f f4 b7 3d 2a 4f 4b d0  19 16 1c 31 3b 85 59 a1  |...=*OK....1;.Y.|
00000100  50 eb 06 cb 96 ee cd d8  3f d6 06 80 20 2d a3 3f  |P.......?... -.?|
00000110  c7 f7 4f e0 8c d0 9d 06  8a e8 c3 b0 ec b4 97 da  |..O.............|
00000120  3a 17 86 24 b7 a0 aa 02  02 fd 10 b3 9d ba 70 66  |:..$..........pf|
00000130  05 f6 90 4b d1 04 b4 8b  a5 4b 35 6f d0 9f 2b c7  |...K.....K5o..+.|
00000140  95 db d1 a9 81 67 dd a9  5f a7 1d 6c 94 c6 f4 01  |.....g.._..l....|
00000150  48 41 77 65 28 d7 68 49  34 12 1d 82 4a f8 72 36  |HAwe(.hI4...J.r6|
00000160  35 d1 a2 1f 3c 9f a5 66  74 d3 b1 2b cb 2f ae 12  |5...<..ft..+./..|
00000170  54 b2 4d a9 ed ef b1 93  35 44 1a 08 b8 ca 58 db  |T.M.....5D....X.|
00000180  5c c6 00 1f eb 3c 47 3c  46 66 b5 6d 59 ea 67 aa  |\....<G<Ff.mY.g.|
00000190  8a 5f a7 b3 73 e5 a3 7d  49 3a bf fa 27 c0 b3 88  |._..s..}I:..'...|
000001a0  46 5d 06 d0 09 1d 2b eb  ad 5d 09 b3 19 9b 3b c1  |F]....+..]....;.|
000001b0  19 2e 02 d2 08 b5 46 50  11 9a 1f 01 c4 77 00 fe  |......FP.....w..|
000001c0  ff ff 07 fe ff ff 02 b0  af 09 00 f8 52 07 00 fe  |............R...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 50 49 09 00 00  |...........PI...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by darkod on 2010-05-10
I can't see anything specifically wrong right now. Sorry. I'll see if some idea comes up.

---

### Post by oldfred on 2010-05-10
Darko mentioned it - print out your device.map

less /boot/grub/device.map

Something does not seem right as Ubuntu wants hd1
set root='(hd1,6)'

but everything else is sdf????

---

### Post by iTzDyl on 2010-05-11
> **oldfred said:**
> Darko mentioned it - print out your device.map

less /boot/grub/device.map

Something does not seem right as Ubuntu wants hd1
set root='(hd1,6)'

but everything else is sdf????

I don't get what your saying.

Go into the Live CD, go to that directory and open it and Paste what it says here?

---

### Post by oldfred on 2010-05-11
Path may not be right if you are on liveCD.(oops).

Need to see what your system has in its version.
Path may add /media (or more?)  to the mount point of your install.

---

### Post by iTzDyl on 2010-05-14
I guess I'll bump this to see if anybody can give me some help.

oldfred, sorry but I still don't understand what your trying to say :(

---

### Post by darkod on 2010-05-14
Boot with the ubuntu cd in live mode (since you can't boot your ubuntu installation).
Click on Places, you will see your root partition in there, it will probably say something like 80GB filesystem. Click on it to open it.

Once inside, just follow the path, /boot/grub and there should be file device.map. Open it and copy the content here.

I'm not sure if the terminal commands are easier for you, or opening the folders in a GUI. With text commands in terminal I guess the following should work:

sudo mount /dev/sdf6 /mnt
less /mnt/boot/grub/device.map

---

### Post by iTzDyl on 2010-05-14
Hmmm, there is no device.map. Do you think that is the problem?

Tried both the GUI and terminal. There is no file in the GUI terminal says no file found :(

---

### Post by darkod on 2010-05-14
Hmmm... but in that case it wouldn't be able to boot windows neither.

OK, to create it from live mode, execute:

sudo mount /dev/sdf6 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
chroot /mnt grub-mkdevicemap
chroot /mnt update-grub
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc

Lets see if that helps.

---

### Post by iTzDyl on 2010-05-14
When I type: chroot /mnt grub-mkdevicemap

I get: chroot: cannot change root directory to /mnt: Operation not permitted

---

### Post by oldfred on 2010-05-15
When you use the liveCD does the external come up as sdf?

Did you copy the commands and not type them as a typo can cause problems?

---

