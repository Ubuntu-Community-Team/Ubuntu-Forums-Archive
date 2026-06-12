---
title: "Boot from Flash Drive 10.10 Grub Rescue"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by halcyonz on 2010-10-24
Hey all,
First time poster and recent Ubuntu adopter. I recently installed 10.10 on my main HD alongside a separate windows (xp) partition (it worked perfectly). Then I decided to get fancy and installed 10.10 to a flash drive directly from a live cd. I attempted to boot from the flash drive, and got a black screen with a blinking underscore for about 10 minutes, then I forcefully rebooted. Now, whenever I attempt to boot at all from my main HD I get "error: no such device and a ton of misc numbers. And the flash drive will not allow me to boot from it. Currently, I'm working within the Live CD. 

Any help would be greatly appreciated, I have a few projects I need to complete with Dreamweaver inside XP, so recovering it completely would be nice. :)

Thanks!

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    17,848,214    17,848,152   c W95 FAT32 (LBA)
/dev/sda2    *     17,848,215   456,385,442   438,537,228   7 HPFS/NTFS
/dev/sda3         456,386,558   488,396,799    32,010,242   5 Extended
/dev/sda5         456,386,560   486,961,151    30,574,592   7 HPFS/NTFS
/dev/sda6         486,963,200   488,396,799     1,433,600  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 8000 MB, 8000110592 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               2,048    14,852,095    14,850,048  83 Linux
/dev/sdf2          14,854,142    15,624,191       770,050   5 Extended
/dev/sdf5          14,854,144    15,624,191       770,048  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        43AC-4BD7                              vfat       HP_RECOVERY                   
/dev/sda2        C8AC62D7AC62C014                       ntfs       HP_PAVILION                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        06BD74FF0F793D37                       ntfs                                     
/dev/sda6        eab9ee7b-0236-40f2-9e74-38b72295e663   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46   ext4                                     
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        d6742556-afd1-4871-8809-2818fbed0928   swap                                     
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
/dev/sdf1        /media/7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdf1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46 ro single 
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 7c7bab34-4cf3-4cd1-b1ab-0b24004c9f46
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 43ac-4bd7
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set c8ac62d7ac62c014
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f9807416-8cd1-4ff6-9521-e7c148db3e21
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f9807416-8cd1-4ff6-9521-e7c148db3e21 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f9807416-8cd1-4ff6-9521-e7c148db3e21
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f9807416-8cd1-4ff6-9521-e7c148db3e21 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sdf1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=d6742556-afd1-4871-8809-2818fbed0928 none            swap    sw              0       0

=================== sdf1: Location of files loaded by Grub: ===================


   4.7GB: boot/grub/core.img
   4.7GB: boot/grub/grub.cfg
   3.6GB: boot/initrd.img-2.6.35-22-generic
   4.7GB: boot/vmlinuz-2.6.35-22-generic
   3.6GB: initrd.img
   4.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader  on sda3

00000000  d4 e3 d9 ad 31 b7 aa 92  6d 03 33 ab cd 6e 4b cc  |....1...m.3..nK.|
00000010  b6 2f 31 05 23 f0 d8 3f  b1 22 5b 5b 62 15 6f 91  |./1.#..?."[[b.o.|
00000020  45 ee f2 76 de 77 ab f3  96 55 cf 8b c1 95 2b 55  |E..v.w...U....+U|
00000030  f1 ee 0f 12 d0 f5 b8 58  c5 db d2 b9 2d 2c a4 9b  |.......X....-,..|
00000040  17 ca 6c e0 88 20 84 2f  cc 8d b1 e0 56 b5 66 15  |..l.. ./....V.f.|
00000050  23 d5 f8 b2 dd ab af 0d  d9 7a b3 c6 a0 74 03 95  |#........z...t..|
00000060  97 37 e2 fc bb e9 ab dd  f2 d5 86 67 2a 9e c5 ee  |.7.........g*...|
00000070  fb 79 62 09 7b 1d 68 6c  4a 3b 05 14 cf 5d f7 96  |.yb.{.hlJ;...]..|
00000080  b2 cb 24 5a 58 8e 4a 83  88 49 5c 3a 1f 81 c6 7f  |..$ZX.J..I\:....|
00000090  f9 9e f5 ef 56 ec e2 04  66 e5 40 e1 30 30 28 12  |....V...f.@.00(.|
000000a0  f8 19 b0 85 9a cc ca 9d  36 e2 41 db 10 18 de 42  |........6.A....B|
000000b0  a6 64 0e 19 ce 6c bc 46  7c 14 63 e0 60 84 01 d8  |.d...l.F|.c.`...|
000000c0  a3 fa 99 4e d9 db 6d 5a  51 47 81 9b 8f 81 98 03  |...N..mZQG......|
000000d0  ed fe 46 b1 bb db 2e 45  16 da 81 6b 02 90 86 0f  |..F....E...k....|
000000e0  01 03 78 3c 04 0e 63 d6  37 c2 58 1d b7 d9 96 6f  |..x<..c.7.X....o|
000000f0  95 5b 67 db a8 e5 d9 d2  ac 83 1a f2 05 c1 00 74  |.[g............t|
00000100  3c 92 26 2e 69 ae 07 19  3a 53 db 16 19 70 ea 18  |<.&.i...:S...p..|
00000110  9b 13 37 e4 9e 99 39 23  50 9b 0a 77 ed 3c 01 df  |..7...9#P..w.<..|
00000120  d2 fb 98 70 10 04 b0 0f  54 a8 94 18 4a f0 20 cb  |...p....T...J. .|
00000130  c8 a9 ee 70 51 8a 6a a5  43 ef 2a 9c 70 90 07 cb  |...pQ.j.C.*.p...|
00000140  fe c4 77 bd 24 6d ee 72  1f ef 97 7b ed f9 cf 4f  |..w.$m.r...{...O|
00000150  07 80 81 0c 18 7e 0f 01  01 e8 07 03 5d 53 ef 6d  |.....~......]S.m|
00000160  24 07 80 83 94 1e 03 fc  90 78 08 1f ff d1 2c 7d  |$........x....,}|
00000170  e9 6a ab b0 f5 75 57 ed  87 83 60 ad 05 02 46 d5  |.j...uW...`...F.|
00000180  04 24 cd 6a db 99 ca 6e  70 e2 49 65 dc 51 de 55  |.$.j...np.Ie.Q.U|
00000190  f8 53 0d 04 e2 d4 e9 14  4b 73 0a a5 ed 90 80 e2  |.S......Ks......|
000001a0  bc b6 d9 c4 50 ff 86 c3  c8 28 c1 81 0c 0e 83 26  |....P....(.....&|
000001b0  06 fd 48 25 cb a2 57 ff  dc db 10 55 e4 18 00 fe  |..H%..W....U....|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 88 d2 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 6a 8c  d2 01 98 e3 15 00 00 00  |......j.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

Open to any and all suggestions!

---

### Post by oldfred on 2010-10-24
You were bit by the grub likes to install to sda "feature". Since you have wubi you have to have windows booting from sda and you needed to install grub2 to sdf (or whatever drive the USB flash drive is).

It is no different from an external drive and this is a fix for external drives.

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

You need to reinstall a windows boot loader the above link use lilo which works well. Or you can use a windows repair CD and run fixboot or BootRec.exe /fixmbr depending on version of windows.

I also installed Ubuntu to a flash drive using a flash drive and the drive numbers changed and the search function seemed to not find UUID possiblely due to gap in drive letters. If you have issues booting flash post back.

Some settings for flash:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler
[https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes)

---

### Post by halcyonz on 2010-10-24
Actually, I originally tried Wubi and then decided shortly after to install and partioned the HD to do so. However, I never uninstalled Wubi because I have been doing most of my work on the companies computer and haven't needed my windows partition at home, so hadn't touched it since I installed Ubuntu. Then, the other day I decide to install 10.10 to a flash drive for the hell of it, and now I cannot boot from the HD. 

So long story short, Wubi is there although I use the Ubuntu install instead. Probably should have cleared that up first, my apologies! Willing to try your advice, oldfred ,if it still applies! (does it?:confused:)

---

### Post by cejack on 2010-10-24
Easy BCD can give you a ton of boot options.  

Check it out.  Must run from Windows to my knowledge though.  

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

You may find that a Windows Vista or Windows 7 disk "Startup Repair" will generally sniff your Windows installation and create a usable Windows boot menu.  But it will typically hose your Grub.  (Moral of the story - when you get more advanced with Ubuntu install from the CD or a bootable USB stick and use the manual partition install options.  I prefer the CD.  Don't use Wubi automated install.)    

You will likely lose your Grub boot menu if you use any of the Windows Startup Repair / multi-boot configurations.  Windows does not typically envision anybody wanting to use Linux on the same system.  They only envision you wanting to install other Windows versions.  Never tried LILO yet.  Haven't had to.  May be a solution - don't know.  

If you can add a second hard drive, this is often the most elegant solution.  1. Install Windows to the hard drive set as boot drive in BIOS.  2.  After Windows install is done - change bios to set boot drive to newly installed internal second hard disk you installed and install Ubuntu flavor of your choice.  Grub will generally sense both OS's on each drive.  3.  If you have any problems in the future, the elegant part of this setup is that you can take second drive off line or switch the boot drive back to Windows drive and you will be back to Windows only system until you figure out your Grub / Ubuntu problem.  No need to know all this stuff about fancy terminal commands and what not if you set up like this...

---

### Post by halcyonz on 2010-10-24
Deleted: No longer relevant.

---

### Post by halcyonz on 2010-10-25
> **oldfred said:**
> You were bit by the grub likes to install to sda "feature". Since you have wubi you have to have windows booting from sda and you needed to install grub2 to sdf (or whatever drive the USB flash drive is).

It is no different from an external drive and this is a fix for external drives.

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

You need to reinstall a windows boot loader the above link use lilo which works well. Or you can use a windows repair CD and run fixboot or BootRec.exe /fixmbr depending on version of windows.

I also installed Ubuntu to a flash drive using a flash drive and the drive numbers changed and the search function seemed to not find UUID possiblely due to gap in drive letters. If you have issues booting flash post back.

Some settings for flash:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler
[https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes)
So I managed to fix the windows MBR with Lilo as per instructions oldfred, and even reinstalled grub to sda. However on boot I am taken to a Grub screen with "minimal bash scripting allowed" (its not a grub_rescue such as before), and still cannot boot into my original Ubuntu 10.10 partition. So i repaired the windows MBR again with lilo, and am now working inside XP. I uninstalled my previous wubi install and now just need to be able to boot into my original 10.10 distribution. Any idea's?

Edit: 
I tried the sourceforge link for installing grub to an external drive and wasn't able to using the commands. It just asked "Installing more than 1 device?" and then displayed the list of help commands. Cejack, I tried easy BCD now that I am able to work within windows again, and it was unable to locate my BCD (lol). It also seems to be more oriented towards dealing with Vista compatibility issues. 

Should I give this a try for the flash drive? I have a feeling it would work if I changed the ubuntu iso filename to 10.10, but I would rather get my Ubuntu partition booting again...
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

---

### Post by oldfred on 2010-10-25
This normally works. 

Install MBR from LiveCD, Ubuntu install on sdf1 and want grub2 in drive sdf's MBR:
Find linux partition, change sdf1 if not correct, and/or even sdf if different drive wanted:
#To confirm it still is sdf1
sudo fdisk -l
sudo mount /dev/sdf1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdf
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdf

Be sure to install to drive sdf not partition sdf1, only the mount uses the partition sdf1.

---

### Post by halcyonz on 2010-10-25
> **oldfred said:**
> This normally works. 

Install MBR from LiveCD, Ubuntu install on sdf1 and want grub2 in drive sdf's MBR:
Find linux partition, change sdf1 if not correct, and/or even sdf if different drive wanted:
#To confirm it still is sdf1
sudo fdisk -l
sudo mount /dev/sdf1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdf
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdf

Be sure to install to drive sdf not partition sdf1, only the mount uses the partition sdf1.
```

**ubuntu@ubuntu:~$ sudo fdisk -l**

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1111     8924076    c  W95 FAT32 (LBA)
/dev/sda2   *        1112       28409   219268614    7  HPFS/NTFS
/dev/sda3           28409       30402    16005121    5  Extended
/dev/sda5           28409       30312    15287296    7  HPFS/NTFS
/dev/sda6           30313       30402      716800   82  Linux swap / Solaris

Disk /dev/sdf: 8000 MB, 8000110592 bytes
247 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a7da7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         970     7425024   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(924, 127, 35) logical=(969, 206, 58)
Partition 1 does not end on cylinder boundary.
/dev/sdf2             970        1021      385025    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(924, 160, 3) logical=(969, 239, 59)
Partition 2 has different physical/logical endings:
     phys=(972, 143, 3) logical=(1020, 63, 6)
Partition 2 does not end on cylinder boundary.
/dev/sdf5             970        1021      385024   82  Linux swap / Solaris
[B]ubuntu@ubuntu:~$ sudo mount /dev/sdf1/mnt
mount: can't find /dev/sdf1/mnt in /etc/fstab or /etc/mtab[/B]


```

And thats as far as I got. I am also not able to mount the nix partition through the gui or gparted, and the partition does not even show in the gui filemanager unless gparted is open. So now i'm thoroughly confused.

---

### Post by oldfred on 2010-10-25
You are missing a space.

sudo mount /dev/sdf[COLOR=Red]1/[/COLOR]mnt

sudo mount /dev/sdf1 /mnt

It is often better to copy & paste commands.

Not sure if any of the messages are vital or not.

---

### Post by halcyonz on 2010-10-26
Cleared my ubuntu partition, just going to do a fresh reinstall of the ubuntu in sda3, then clear my flash drive and try that again. When in doubt, figure out how to do it right and start over. :) Thanks for the help everyone, especially you oldfred!

---

