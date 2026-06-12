---
title: "Boot/Grub issue with XP after daily security update"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by Rezinunts on 2011-02-27
OK... So I was in XP just fine a few hours ago... Decided to reboot into Ubuntu and check for daily updates... There were some... I applied the updates and then attempted to reboot into XP... Well now it only shows a black/blank screen when I try to boot into XP... I can't see anything wrong in grubs config and I don't think any of the updates had anything to do with grub... Can anyone help?

Is it possible to overwrite the MBR with XP's boot config/process using the Windows install disk and then reinstall grub once I have verified that I can boot into XP using Windows method?

---

### Post by sikander3786 on 2011-02-27
Welcome to the forums :-)

Please boot Ubuntu and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us take a look at your boot setup and diagnose the problem.

While posting, click the # icon in post menu and paste the text in between the generated [code] tags for readability purposes as this will be a long output.

---

### Post by Rezinunts on 2011-02-27
One step ahead of you... Already ran the script and looked it over... Couldn't see anything wrong but maybe someone can catch something I might have missed...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   160,071,659   160,071,597   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    76,908,543    76,906,496  83 Linux
/dev/sdb2          76,910,590    80,291,839     3,381,250   5 Extended
/dev/sdb5          76,910,592    80,291,839     3,381,248  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   398,283,479   398,283,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A058DC2C58DBFECA                       ntfs       Alpha Reborn                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        75cff649-2522-439b-999c-5c3c08f66482   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        451d8248-fb9b-4bb9-a472-14edb91f27dd   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3C1C06AA1C065F70                       ntfs       Tote Box                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        A214E46914E44241                       ntfs       Omega                         
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd1        /media/Omega             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINXP 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINXP="WinXP Pro SP3" /noexecute=optin /fastdetect 
 

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
search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=75cff649-2522-439b-999c-5c3c08f66482 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=75cff649-2522-439b-999c-5c3c08f66482 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=75cff649-2522-439b-999c-5c3c08f66482 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=75cff649-2522-439b-999c-5c3c08f66482 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=75cff649-2522-439b-999c-5c3c08f66482 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=75cff649-2522-439b-999c-5c3c08f66482 ro single 
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
    search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 75cff649-2522-439b-999c-5c3c08f66482
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "WinXP Pro SP3 (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a058dc2c58dbfeca
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
UUID=451d8248-fb9b-4bb9-a472-14edb91f27dd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  32.3GB: boot/grub/core.img
  30.3GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
   1.2GB: boot/initrd.img-2.6.35-24-generic
   1.3GB: boot/initrd.img-2.6.35-25-generic
  32.4GB: boot/vmlinuz-2.6.35-22-generic
  32.3GB: boot/vmlinuz-2.6.35-24-generic
  33.1GB: boot/vmlinuz-2.6.35-25-generic
   1.3GB: initrd.img
   1.2GB: initrd.img.old
  33.1GB: vmlinuz
  32.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  17 14 02 25 00 2b 2e 02  0b 25 3e 1d 04 0b 3e 00  |...%.+...%>...>.|
00000010  09 00 3f ed 3f ed 12 17  39 11 12 17 39 01 11 12  |..?.?...9...9...|
00000020  17 39 2b 2b 2b 2b 2b 2b  31 30 1b 40 83 0a 18 06  |.9++++++10.@....|
00000030  2f 1a 18 15 2f 26 07 29  23 36 07 39 23 4a 02 45  |/.../&.)#6.9#J.E|
00000040  1f 59 02 59 18 54 1f 50  2f 69 02 65 1f 65 2d 63  |.Y.Y.T.P/i.e.e-c|
00000050  2f 79 02 75 1f 84 1f 84  23 84 36 93 36 18 19 14  |/y.u....#.6.6...|
00000060  19 17 29 14 29 17 3b 14  3b 17 06 14 17 17 b4 2b  |..).).;.;......+|
00000070  2e 14 2b 2b 2e 75 2b 8b  2b 8b 2e 03 2b 2e 17 14  |..++.u+.+...+...|
00000080  37 05 00 1d 90 21 01 21  21 25 3e 1d 04 04 04 0b  |7....!.!!%>.....|
00000090  3e 00 09 41 41 45 be 3d  0d 40 40 48 2a 3a 00 3a  |>..AAE.=.@@H*:.:|
000000a0  35 03 31 03 20 2b 2e 17  14 03 20 06 1a 11 1b 31  |5.1. +.... ....1|
000000b0  b8 ff c0 40 09 09 16 37  31 31 4f 28 1b 1a b8 ff  |...@...711O(....|
000000c0  c0 b3 0e 15 37 1a 2f 2b  ed 11 33 2f 2b ed 12 17  |....7./+..3/+...|
000000d0  39 2f 2f 12 17 39 2f ed  33 2f 00 3f fd 32 2f 3f  |9//..9/.3/.?.2/?|
000000e0  ed 33 2f 3f ed 33 2f 5d  11 12 17 39 5d 87 0e 2e  |.3/?.3/]...9]...|
000000f0  2b 0e 7d 10 c4 00 71 31  30 5d 59 05 22 26 27 35  |+.}...q10]Y."&'5|
00000100  33 16 16 17 16 16 33 32  36 37 36 36 35 34 26 27  |3.....32676654&'|
00000110  26 26 27 26 26 35 34 36  33 32 16 17 15 23 26 26  |&&'&&54632...#&&|
00000120  23 22 06 15 14 16 17 16  16 17 16 16 15 14 06 07  |#"..............|
00000130  06 06 07 16 16 15 14 06  23 22 26 27 35 33 16 16  |........#"&'53..|
00000140  33 32 36 35 34 26 27 06  06 01 b6 70 c3 40 0a 18  |32654&'....p.@..|
00000150  41 36 30 73 3e 2d 66 19  23 1f 49 5d 24 74 31 80  |A60s>-f.#.I]$t1.|
00000160  74 e4 bd 5d bc 40 0a 48  b1 5a 5d 80 4c 54 2a 67  |t..].@.H.Z].LT*g|
00000170  39 7c 7d 39 37 17 2c 1c  01 05 b0 85 25 64 28 09  |9|}97.,.....%d(.|
00000180  18 4e 28 5e 58 01 01 15  24 1a 3b 22 d3 13 2e 19  |.N(^X...$.;"....|
00000190  16 22 15 10 17 34 34 43  44 17 09 18 0e 25 9b 6e  |."...44CD....%.n|
000001a0  97 be 2e 23 c9 39 42 4e  4f 46 45 16 0b 15 0e 1f  |...#.9BNOFE.....|
000001b0  90 7c 48 81 2e 13 1c 0c  12 35 22 a2 ac 0c 00 fe  |.|H......5".....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 33 00 00 00  |............3...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by sikander3786 on 2011-02-27
>  => No boot loader is installed in the MBR of /dev/sdb


Grub isn't there at all. Where did it go? Did the update remove some packages? Follow these commands for re-installation of Grub.

```
sudo mount /dev/sdb1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]b[/COLOR]
```

Note, it is just sdb without an integer in the second one.

Reboot your PC and make 'sdb' your first boot device in Bios. Boot Ubuntu and from installed Ubuntu's Terminal, run this command.

```
sudo update-grub
```

---

