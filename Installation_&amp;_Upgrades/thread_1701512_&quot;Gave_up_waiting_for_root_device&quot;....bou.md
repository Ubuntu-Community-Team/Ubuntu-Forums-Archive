---
title: "&quot;Gave up waiting for root device&quot;....bout to go insane..."
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by AceXMachine on 2011-03-06
Ok,
 
Been working on this since 9pm last night, ent to bed at 5:30am, back up at 8am, it is now 3pm the next day and I cannot get past the %^$%& boot message.
 
To be fair, I am new to Ubuntu and it has been years (about 10) since I did anything with Linux so I am understandably a bit rusty and alot has changed. That being said, I am trying to sideload (no separate partition) Ubuntu Netbook 10.10 on a HP Mini 311 1037NR so I can "get back in the game". This was supposed to be simple but now that I am seeing double and can't stop my eyes from watering from staring at these screens so long, time to ask for help. I used the wubi installer and the ubuntu i386 netbook iso, downloaded to a folder on Windows 7, then ran the installer, set it for Ubuntu Netbook, 20-25GB, then "install". Installation goes without a hitch apparently and after reboot, I get the Windows 7/Ubuntu boot prompt. Every time I select Unbootu, it get a flashing prompt for a few seconds then:
```
 "Gave up waiting for root device...blah blah blah... ALERT! /dev/sdb2 does not exist".
``` 
Now I know this has to be something stupid like sdb2 being my RECOVERY D: drive or USB device, but for the life of me I cannot figure out how to confirm this, and then, I'm assuming, mount/chroot to the correct one. Output of "ls /dev" lists sda, sda1, sda2, sda3, disk, sdb, and sdb1...there is no sdb2 as the error states. I need to be able to correct this without having to boot to USB/CD. I have tried uninstalling/reinstalling and attempted to boot into ubuntu recovery, no dice. 
 
Any assistance would be appreciated
 
Thx

---

### Post by AceXMachine on 2011-03-06
Small update here.  Managed to create a USB stick which allows me to boot into Ubuntu....but WIFI doesn't work...Broadcom won't install and I don't have an ethernet connection to download updates to fix it.  So I can't use the BootInfoScript I know someone is gonna ask me for.  Still working on that now...man I'm tired...

---

### Post by wyliecoyoteuk on 2011-03-06
sdb2 does not exist, but sdb1 does.
sda is the first hard disk, sdb the second and so on...
This would seem to indicate more than one hard disk.
Do you have a USB drive or a card reader attached?
This might be part of the problem, as they might be screwing up the drive numbering.

---

### Post by wyliecoyoteuk on 2011-03-06
Unfortunately, the easiest way to get wifi working is to use an ethernet connection. You probably need to install some firmware for the broadcom card.
This [link ]("http://superuser.com/questions/229602/how-to-install-wireless-drivers-without-internet-access")might help

---

### Post by AceXMachine on 2011-03-06
Ok, Got WIFI working, don't ask me how lol.  Typing this from USB/Ubuntu now.  Yes, this netbook has a biultin SD card reader (miniSD at that....who uses miniSD? lol).  So, can someone tell me how to correct the root device?  BootInfoScript below...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1977 MB, 1977614336 bytes
62 heads, 61 sectors/track, 1021 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          8,199     3,862,527     3,854,329   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sdb2             409,600   289,939,455   289,529,856   7 HPFS/NTFS
/dev/sdb3         289,939,456   312,578,047    22,638,592   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1015 MB, 1015808000 bytes
5 heads, 4 sectors/track, 99200 cylinders, total 1984000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 249     1,983,999     1,983,751   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       a7337590-c074-634a-9e71-ee5957c51437   ext2       casper-rw                     
/dev/loop2       9421749c-9e8a-4e97-88e0-cebc3f26c154   ext4                                     
/dev/sda1        12F8-54ED                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BAC4473AC446F861                       ntfs       SYSTEM                        
/dev/sdb2        966C5AF96C5AD399                       ntfs                                     
/dev/sdb3        84A0B64AA0B6428A                       ntfs       RECOVERY                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        34B2-D99D                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/casper-rw         ext2       (rw,nosuid,nodev,uhelper=udisks)


======================== sdb2/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 966c5af96c5ad399
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 966c5af96c5ad399
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set bac4473ac446f861
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 966c5af96c5ad399
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 84a0b64aa0b6428a
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

============================= sdb2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb2/Wubi: Location of files loaded by Grub: =================


   6.5GB: boot/grub/grub.cfg
   2.3GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
   2.3GB: initrd.img
    .3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 10 52 11  |.X.SYSLINUX...R.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 07 20 00 00  |........?.... ..|
00000020  f9 cf 3a 00 57 07 00 00  00 00 00 00 02 00 00 00  |..:.W...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ed 54 f8 12 4e  4f 20 4e 41 4d 45 20 20  |..).T..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 70 f6 15 00  66 ba 00 00 00 00 bb 00  |}.f.p...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by bcbc on 2011-03-06
Select Ubuntu, hit 'e' on first entry, change root=/dev/sdb2 to root=/dev/sda2
Then CTRL+x to boot.

When booted, drop to a terminal (CTRL+ALT+t) and run "sudo update-grub".

The bios should dictate the drive order, so not sure if it will switch it around later. But that's how to change it if that happens.

---

### Post by AceXMachine on 2011-03-06
OK, this is rediculously hard and disheartening.  I was able to get this WIFI working using the LiveUSB, but now that I can successfully boot into ubuntu (thanks alot to those that got me there!), I cannot get the WIFI working.  I CANNOT get ethernet here.  Everything must be done manually by transferring from my desktop rubbing Win7 via USB.  So where the hell can I get the ^&%^&$ "headers/tools/build-essential", how in Gods name are you supposed to install them, and for the love of God why is there no clear intructions on how to do this.  I found "build-essential_11.3ubuntu1_i386.dep, but it won't install stating "Dependency is not satisfiable: libc6-dev|libc-dev".  Every step I make forces me to make another and now I dunno where the f*ck I am.  How in God's name can it be this hard to get a WIFI driver installed?  I may be spoiled on Windows, but Jesus Christ...

---

### Post by AceXMachine on 2011-03-06
Ok, almost 24 hours and I finally have a working install of ubuntu. According to my research, I just happen to fall in that itty bitty crack between "ubuntu expects you to be connected to the internet" and "broadcom sucks ****". 
Since I didn't have ethernet, had to go the hard way. I'm gonna post what I did, just incase anyone else runs into this particular scenario. I'm not sure if this is ALL you would need to do to get this done since I did so much, but I don't think anything I did prior would affect this.

 
First, you will need the CD/ISO of ubuntu (I was using the 10.10 maverick/netbook i386 CD/ISO). Copy the following files to a folder on your computer
 
 

```
 
/pool/main/b/build-essential/build-essential_11.5_i386.deb (build/version numbers may change)
/pool/main/d/dpkg/dpkg-dev_1.15.8.4ubuntu3_all.deb
/pool/main/e/eglibc/libc6-dev_2.12.1-0ubuntu6_i386.deb
/pool/main/e/eglibc/libc-dev-bin_2.12.1-0ubuntu6_i386.deb
/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb
/pool/main/g/gcc-4.4/gcc-4.4_4.4.4-14ubuntu5_i386.deb
/pool/main/g/gcc-defaults/gcc_4.4.4-1ubuntu2_i386.deb
/pool/main/l/linux/linux-libc-dev_2.6.35-1022.33.deb
/pool/main/m/manpages/manpages-dev_3.24-1ubuntu1_all.deb
/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb
 

and then finally
 

/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb

 
note that this is in "/pool/restricted/" and not "/pool/main/" like the others...

```
 
Now, I installed all of these one at a time using Ubuntu Software Center, mostly to give me a break from the command line.  Of course it was only after that that I found out you can install multiple packages with a single command from the directory all the files are in.
 
```
 
 sudo dpkg -i *.deb

```
 
I don't know if you need to have the dpkg-dev_1.15.8.4ubuntu3_all.deb installed first to be able to do that, but even so, its helpful.
Reboot and you should be up and running on WIFI.

---

### Post by wyliecoyoteuk on 2011-03-07
Well done!
And be reassured it isn't always this hard.:D

---

### Post by msamon1 on 2011-03-10
okay, so I have the exact same problem........ with one exception.  mine says something along the lines of Alert! ( a bunch of numbers) can not be found.............. I have looked at a million different other threads and can't find an answer......... 

Here is my Boot Info Summary.  I have been trying for 3 days now so any help will be great.


                ```

```Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 25542928 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             38     7,839,719     7,839,682   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   300,292,095   300,290,048  83 Linux
/dev/sdb2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sdb5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0025-7162                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        21575745-6f3d-45ec-b95e-1d5e8c34f37d   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        5c51c11a-9066-4eed-9180-6d740ea25240   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 21575745-6f3d-45ec-b95e-1d5e8c34f37d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 21575745-6f3d-45ec-b95e-1d5e8c34f37d
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 21575745-6f3d-45ec-b95e-1d5e8c34f37d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=21575745-6f3d-45ec-b95e-1d5e8c34f37d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 21575745-6f3d-45ec-b95e-1d5e8c34f37d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=21575745-6f3d-45ec-b95e-1d5e8c34f37d ro single 
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
    search --no-floppy --fs-uuid --set 21575745-6f3d-45ec-b95e-1d5e8c34f37d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 21575745-6f3d-45ec-b95e-1d5e8c34f37d
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
# / was on /dev/sdb1 during installation
UUID=21575745-6f3d-45ec-b95e-1d5e8c34f37d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5c51c11a-9066-4eed-9180-6d740ea25240 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
  25.9GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
    .2GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
    .2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 20 00  |.X.SYSLINUX..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 26 00 00 00  |........?...&...|
00000020  c2 9f 77 00 bd 03 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 62 71 25 00 4e  4f 20 4e 41 4d 45 20 20  |..)bq%.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 5a 3d 02 00  66 ba 00 00 00 00 bb 00  |}.f.Z=..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  7b 0a 1b 74 a9 30 59 8e  68 56 b3 ac aa 44 57 56  |{..t.0Y.hV...DWV|
00000010  a3 af 02 cf 32 34 d1 46  47 ff 01 f1 39 6f 8a ea  |....24.FG...9o..|
00000020  8d ec 89 15 3b dd 21 d9  de 9b 67 ba 6a dd 62 42  |....;.!...g.j.bB|
00000030  ff e1 e2 e4 11 1e 74 65  6d 34 5a 5c b5 84 4d e4  |......tem4Z\..M.|
00000040  2c 6f c2 e4 df b8 e0 db  73 d0 9d e9 47 1d 2a 8b  |,o......s...G.*.|
00000050  4d e0 e6 9e 68 4f 23 2d  ef 79 9f 9c df 54 63 73  |M...hO#-.y...Tcs|
00000060  a8 4d b7 b8 38 a2 79 c9  64 2b 44 32 46 78 4d 7d  |.M..8.y.d+D2FxM}|
00000070  e6 19 ea 9c b0 0b e6 77  fd d5 bd 5e 9c 07 a6 f7  |.......w...^....|
00000080  a9 ec 79 d3 e6 c9 fa 7b  9e 5c aa 2a dc 26 49 14  |..y....{.\.*.&I.|
00000090  14 02 de 1d 50 49 34 29  b6 67 af 13 2d f4 e8 75  |....PI4).g..-..u|
000000a0  a5 b1 36 75 4f 0e 7c 16  19 d6 34 c7 64 2f c3 b5  |..6uO.|...4.d/..|
000000b0  d5 c4 54 09 66 8a 06 9d  02 23 5a d1 06 00 d8 13  |..T.f....#Z.....|
000000c0  ef 51 c4 76 ef fa 96 38  fb bd 61 5d 8b 5c 4a 29  |.Q.v...8..a].\J)|
000000d0  78 d4 13 f0 98 d8 ca e8  60 a7 e9 7f ae e3 9b a7  |x.......`.......|
000000e0  2c fb f7 ef 63 31 19 ad  68 f7 07 15 90 7f a4 2f  |,...c1..h....../|
000000f0  68 88 f5 a2 83 6f 9a 2f  0e ff 05 ff 30 53 53 b1  |h....o./....0SS.|
00000100  ca 98 fd 89 ba e5 d3 0f  f2 4d e6 4e c3 ff 3d 0f  |.........M.N..=.|
00000110  e8 c2 00 45 65 37 3f 9f  2f 05 fe c2 db 2c 8b 8c  |...Ee7?./....,..|
00000120  b0 ce 77 21 50 d5 6c 2e  2a 6c 00 61 ba 2b 67 63  |..w!P.l.*l.a.+gc|
00000130  0e 87 b4 45 15 cb fd 0e  68 63 d5 5c 28 67 13 ee  |...E....hc.\(g..|
00000140  4b b5 c5 95 4e 01 80 f8  c6 7e 3b 0b 78 6d 7c 58  |K...N....~;.xm|X|
00000150  f4 9c 23 67 3d 7f 79 b0  bf ff 0b 5e 05 44 62 f3  |..#g=.y....^.Db.|
00000160  e2 66 ee ad 2b 8e 4a af  ce ed 61 8c d6 6a 46 46  |.f..+.J...a..jFF|
00000170  65 f8 9c d9 1a 98 b3 07  7d c1 c8 c3 d8 f7 eb 19  |e.......}.......|
00000180  43 23 60 66 ff fe bd bb  c1 25 50 32 d2 29 ad 70  |C#`f.....%P2.).p|
00000190  10 34 a9 a2 8c e0 5f 9a  54 8b 78 24 aa fc 8a 49  |.4...._.T.x$...I|
000001a0  74 e2 ff 12 c4 53 37 9f  dc 40 27 21 57 17 ff df  |t....S7..@'!W...|
000001b0  70 7d bb 3f c3 00 57 4e  d4 57 79 09 ba 3b 00 fe  |p}.?..WN.Wy..;..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by wyliecoyoteuk on 2011-03-11
Grub is looking for the core-image on sdb,
sda looks like a 4gb USB stick, or it could be a windows recovery partition.

---

