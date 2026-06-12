---
title: "no partition table for installing 10.10"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by chidat on 2010-12-21
Hi there! My apologies if this question has already been posed and answered out there..

I had an Asus T91MT netbook with Windows 7 and Ubuntu 10.10, but due to the annoying ExpressGate boot menu (after selecting win7 from the grub menu) that I could not get rid of, I decided to delete the 100MB partition (that I was pretty sure was the ExpressGate), reinstall windows over the same partition it used to be in, and hope that everything would be fine, and I would not have to reinstall Ubuntu, since I did not touch any other partition. Well, Windows works fine, and I don't get the ExpressGate boot menu anymore, but now there's no grub menu to boot into Ubuntu! I figured I might have to reinstall it, which is not too much of a problem, but when manually trying to select the partition to install it on, there seems to be no partition table at all. GParted shows only an unallocated 29.82Gib space (which is the whole HD) with a warning saying "Can't have a partition outside the disk!", which I have no idea what that means. If I attempt to create a new partition table from within the installer, it warns me that all current partitions will be removed, and that all data will be erased.
Btw, here's the output of ```
sudo fdisk -lu

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00094808

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848    41021184    20407168+   7  HPFS/NTFS
/dev/sda2        41021440    58963967     8971264   83  Linux
/dev/sda3        58964031    62541044     1788507    f  W95 Ext'd (LBA)
/dev/sda5        58966016    59858927      446456   82  Linux swap / Solaris
/dev/sda6        59867136    62531567     1332216   82  Linux swap / Solaris

Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7897087     3948512+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 38)

```Is there a way that I can install Ubuntu without wiping out everything else? Thank you very much!

---

### Post by sikander3786 on 2010-12-21
While booted from an Ubuntu Live CD, go to Applications > Accessories > Terminal and post the output of this command.

```
sudo fdisk -lu
```

And a screenshot of Gparted would also be helpful.

---

### Post by chidat on 2010-12-21
Thank you for your quick response!

I added the output of sudo fdisk -lu above, and here I attached a screenshot of GParted. Thanks![IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by sikander3786 on 2010-12-21
The problem seems to lie here.

> Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total [COLOR="Red"]62533296[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00094808

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848    41021184    20407168+   7  HPFS/NTFS
/dev/sda2        41021440    58963967     8971264   83  Linux
/dev/sda3        58964031    [COLOR="Red"]62541044[/COLOR]     1788507    f  W95 Ext'd (LBA)
/dev/sda5        58966016    59858927      446456   82  Linux swap / Solaris
/dev/sda6        59867136    62531567     1332216   82  Linux swap / Solaris


And the solution here.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by psusi on 2010-12-21
Post the output of sudo parted print

Nevermind.. good catch there, I didn't see that.

---

### Post by chidat on 2010-12-21
Hi, thanks for the the solution! It worked very nicely, and now GParted recognizes the partitions (see attached screenshot).

However, I am still unable to boot into Ubuntu 10.10 when starting up my computer; there is no grub menu. I am not sure what all of the partitions are for, so I am not even sure that Ubuntu is accessible.. when I look at what the installer says, it shows me one partition for Ubuntu 10.10 and one for Ubuntu (see other attached screenshots).. I'm guessing that the Ubuntu 10.10 is the one that I had left installed? I know that if I try installing Ubuntu now, I'll probably get into a very unpleasant situation, for this looks very familiar, and I did this not too long ago and was stuck with only Ubuntu..

Thanks again for your time!

---

### Post by sikander3786 on 2010-12-21
While booted from the Live CD, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us about your boot and any problems with it.

---

### Post by chidat on 2010-12-21
here is the output of bootinfoscript:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

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

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *        206,848    41,021,184    40,814,337   7 HPFS/NTFS
/dev/sda2          41,021,440    58,963,967    17,942,528  83 Linux
/dev/sda3          58,964,031    62,533,295     3,569,265   f W95 Ext d (LBA)
/dev/sda5          58,966,016    59,858,927       892,912  82 Linux swap / Solaris
/dev/sda6          59,867,136    62,531,567     2,664,432  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,897,087     7,897,025   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FEE421DFE4219B43                       ntfs                                     
/dev/sda2        dadee321-41d1-4af4-8d2b-e23b038cf70a   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        c3265fb7-e4f4-4620-a0ca-95ee95843515   swap                                     
/dev/sda6        2881512f-155f-45ce-ae2a-c802873acac6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6CC8-3211                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set dadee321-41d1-4af4-8d2b-e23b038cf70a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set dadee321-41d1-4af4-8d2b-e23b038cf70a
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set dadee321-41d1-4af4-8d2b-e23b038cf70a
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=dadee321-41d1-4af4-8d2b-e23b038cf70a ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set dadee321-41d1-4af4-8d2b-e23b038cf70a
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=dadee321-41d1-4af4-8d2b-e23b038cf70a ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set dadee321-41d1-4af4-8d2b-e23b038cf70a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dadee321-41d1-4af4-8d2b-e23b038cf70a ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set dadee321-41d1-4af4-8d2b-e23b038cf70a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dadee321-41d1-4af4-8d2b-e23b038cf70a ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set dadee321-41d1-4af4-8d2b-e23b038cf70a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set dadee321-41d1-4af4-8d2b-e23b038cf70a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a6a667a0a6676fab
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=dadee321-41d1-4af4-8d2b-e23b038cf70a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c3265fb7-e4f4-4620-a0ca-95ee95843515 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  25.8GB: boot/grub/core.img
  23.4GB: boot/grub/grub.cfg
  22.3GB: boot/initrd.img-2.6.35-22-generic
  22.4GB: boot/initrd.img-2.6.35-23-generic
  25.9GB: boot/vmlinuz-2.6.35-22-generic
  25.9GB: boot/vmlinuz-2.6.35-23-generic
  22.4GB: initrd.img
  22.3GB: initrd.img.old
  25.9GB: vmlinuz
  25.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 e0 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 7f 78 00 10 1e 00 00  00 00 00 00 02 00 00 00  |..x.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 11 32 c8 6c 4e  4f 20 4e 41 4d 45 20 20  |..).2.lNO NAME  |
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
00000100  7d 00 66 b8 e0 e7 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

### Post by psusi on 2010-12-21
Windows trashed grub, so you need to reinstall it.  Google for reinstall grub; there are plenty of guides.

---

### Post by sikander3786 on 2010-12-21
Make sure the disc you are booted from currently is not an older Ubuntu than 9.10. You need Maverick/Lucid or Karmic and then from Terminal,

```
sudo mount /dev/sda2 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sd[COLOR="Red"]a[/COLOR]
```

Note, for the second one it is just sda without an integer.

Reboot and hopefully, it should boot Ubuntu now. If it didn't list Windows, from installed Ubuntu's Terminal,

```
sudo update-grub
```

Good Luck!

---

### Post by chidat on 2010-12-21
Everything works perfectly now! Thank you very much! I don't know how you did it, but that was awesome! You saved me a lot of time and effort!

Thanks again!

---

