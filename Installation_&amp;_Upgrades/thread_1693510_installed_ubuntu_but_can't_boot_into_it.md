---
title: "installed ubuntu but can't boot into it"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by bowentwo on 2011-02-22
i got ubuntu installed everything went well but when it said to reboot i clicked to reboot.. then the cdrw drive ejected the cd and i got it and closed the tray and hit enter... rebooted right into wiindows 7 64bit.
 
System
 
2 1TB HD's 1 each for windows and ubuntu and a 250gb drive for backup. i don't know where i went wrong but any help to get booted or to be able to choose between the two on boot would be great sorry if this is a noob question.. but i a total noob lol.

---

### Post by sikander3786 on 2011-02-23
Did you enter the Bios and try to boot both your HDDs one-by-one? Or there must be a quick boot short-cut key printed on the Bios logo screen, mostly F10?

If that doesn't help, please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us dig deep into your boot setup and diagnose/solve the problem.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by bowentwo on 2011-02-23
Ok I hope i don't get kicked for how big this is but here is the results from the script

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks at sector 92557376 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,250,258,624 1,250,258,562   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdd2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1               2,048   195,311,615   195,309,568  83 Linux
/dev/sde2         195,313,662 1,953,523,711 1,758,210,050   5 Extended
/dev/sde5         195,313,664 1,074,216,959   878,903,296  83 Linux
/dev/sde6       1,074,219,008 1,089,841,151    15,622,144  82 Linux swap / Solaris
/dev/sde7       1,089,843,200 1,953,523,711   863,680,512  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        5660-709F                              vfat       My Book                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        36CC4D7BCC4D3681                       ntfs       System Reserved               
/dev/sdd2        241C615D1C612ACE                       ntfs       BigPapa                       
/dev/sdd: PTTYPE="dos" 
/dev/sde1        5cce175b-aa39-4058-a86b-13db40e65103   ext4                                     
/dev/sde2: PTTYPE="dos" 
/dev/sde5        294c22d1-97b7-4e53-a6ea-c25333e486d8   ext4                                     
/dev/sde6        053ec7c5-77ea-45e3-b21e-8ecba6103660   swap                                     
/dev/sde7        ab3a62fe-a361-4b72-a410-dbdc082e27c8   ext4                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sda: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sde7        /media/ab3a62fe-a361-4b72-a410-dbdc082e27c8 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sde1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos7)'
search --no-floppy --fs-uuid --set ab3a62fe-a361-4b72-a410-dbdc082e27c8
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 5cce175b-aa39-4058-a86b-13db40e65103
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
    search --no-floppy --fs-uuid --set 5cce175b-aa39-4058-a86b-13db40e65103
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5cce175b-aa39-4058-a86b-13db40e65103 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 5cce175b-aa39-4058-a86b-13db40e65103
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5cce175b-aa39-4058-a86b-13db40e65103 ro single 
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
    search --no-floppy --fs-uuid --set 5cce175b-aa39-4058-a86b-13db40e65103
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 5cce175b-aa39-4058-a86b-13db40e65103
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 36cc4d7bcc4d3681
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

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdd1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdd5 during installation
UUID=294c22d1-97b7-4e53-a6ea-c25333e486d8 /home           ext4    defaults        0       2
# /usr was on /dev/sdd7 during installation
UUID=ab3a62fe-a361-4b72-a410-dbdc082e27c8 /usr            ext4    defaults        0       2
# swap was on /dev/sdd6 during installation
UUID=053ec7c5-77ea-45e3-b21e-8ecba6103660 none            swap    sw              0       0

=================== sde1: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
  52.2GB: boot/initrd.img-2.6.35-22-generic
  47.3GB: boot/vmlinuz-2.6.35-22-generic
  52.2GB: initrd.img
  47.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde2

00000000  a4 81 00 00 00 00 00 00  fe 06 5e 4d fe 06 5e 4d  |..........^M..^M|
00000010  fd 06 5e 4d fe 06 5e 4d  00 00 00 00 00 00 00 00  |..^M..^M........|
00000020  00 00 08 00 01 00 00 00  0a f3 00 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 26 13 3a 7c  00 00 00 00 00 00 00 00  |....&.:|........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 0c 70 6e 30  10 48 30 73 0c 70 6e 30  |.....pn0.H0s.pn0|
00000090  fd 06 5e 4d 10 48 30 73  00 00 00 00 00 00 00 00  |..^M.H0s........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  a4 81 00 00 9e 04 00 00  f8 06 5e 4d f8 06 5e 4d  |..........^M..^M|
00000110  f8 06 5e 4d 00 00 00 00  00 00 01 00 08 00 00 00  |..^M............|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  01 00 00 00 01 c4 80 03  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 c2 12 3a 7c  00 00 00 00 00 00 00 00  |......:|........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 1c b2 f0 d4  0c fe 2b d0 fc 95 a2 c6  |..........+.....|
00000190  f8 06 5e 4d fc 95 a2 c6  00 00 00 00 00 00 00 00  |..^M............|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 63 34 00 fe  |............c4..|
000001d0  ff ff 05 fe ff ff 75 05  63 34 8d 62 ee 00 00 00  |......u.c4.b....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sda

---

### Post by sikander3786 on 2011-02-23
Yes the result is quite long but if you could post in ```
 tags, it wouldn't have taken much of space here.

Anyhow, Grub is installed to the MBR of sdc but isn't correctly pointed to the location of core.img. It is recommended to have Grub installed to the MBR of the same HDD to which Ubuntu is installed but we'll not touch the Windows MBR there.

Make sure you didn't switch HDD cables after posting the Results.txt and before doing the following commands.

Boot an Ubuntu Live CD, go to Applications > Accessories > Terminal:

[code]sudo mount /dev/sde1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]c[/COLOR]
```

Note it is just sdc without integer in the second command.

If you decide to install Grub to the same drive to which Ubuntu is actually installed, follow the first command above and skip the second one. Instead follow this one.

```
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]e[/COLOR]
```

Reboot and make sure your sdc (or sde, if you installed Grub to sde) drive is selected as the first boot device in Bios menu. Hopefully it would boot Ubuntu successfully this time.

If it didn't detect Windows, go to Applications > Accessories > Terminal of Ubuntu booted from your HDD and,

```
sudo update-grub
```

Good Luck!

---

