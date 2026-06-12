---
title: "Grub Restore Prompt"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by brainard52 on 2011-04-28
Here's the story: I noticed that I didn't have a swap partition. I had 3 partitions at the time. two 15 gig partitions; holding winXP and Ubuntu. the 3rd partition was the rest of the space. I was using it as a file storage partition so that I could easily reinstall either of the OS's without having to back up my files. I deleted the 3rd partition, and formatted a bit into a swap partition. then I tried to format the rest into my file storage. i couldn't so i rebooted. I got the grub restore prompt. I immediately googled it, and got the below page.

[http://ubuntuforums.org/showthread.php?t=1326788](http://ubuntuforums.org/showthread.php?t=1326788)

I followed the steps and got:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    31,464,719    31,464,657   7 HPFS/NTFS
/dev/sda2          31,464,781   625,141,759   593,676,979   f W95 Ext d (LBA)
/dev/sda5         593,688,576   625,141,759    31,453,184  83 Linux
/dev/sda6          31,471,398    45,142,649    13,671,252  82 Linux swap / Solaris
/dev/sda7          31,464,783    31,471,396         6,614  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4041 MB, 4041211392 bytes
4 heads, 32 sectors/track, 61663 cylinders, total 7892991 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             32     7,892,990     7,892,959   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B6704499704461EB                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c34d8ef4-9c20-443f-9fe1-5592f1f5d71f   ext4                                     
/dev/sda7        f79331ef-520d-4a84-99d0-248ee15f26e5   swap       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdf1        6413-0209                              vfat       LANDON                        
/dev/sdf: PTTYPE="dos" 
/dev/sdg         0A97-F778                              vfat       Landon                        
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/LANDON            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdg         /media/Landon            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/B6704499704461EB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/c34d8ef4-9c20-443f-9fe1-5592f1f5d71f ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
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
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=c34d8ef4-9c20-443f-9fe1-5592f1f5d71f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=c34d8ef4-9c20-443f-9fe1-5592f1f5d71f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=c34d8ef4-9c20-443f-9fe1-5592f1f5d71f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=c34d8ef4-9c20-443f-9fe1-5592f1f5d71f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=c34d8ef4-9c20-443f-9fe1-5592f1f5d71f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=c34d8ef4-9c20-443f-9fe1-5592f1f5d71f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c34d8ef4-9c20-443f-9fe1-5592f1f5d71f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c34d8ef4-9c20-443f-9fe1-5592f1f5d71f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set c34d8ef4-9c20-443f-9fe1-5592f1f5d71f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b6704499704461eb
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=c34d8ef4-9c20-443f-9fe1-5592f1f5d71f /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 317.0GB: boot/grub/core.img
 318.0GB: boot/grub/grub.cfg
 305.1GB: boot/initrd.img-2.6.32-21-generic
 305.9GB: boot/initrd.img-2.6.32-29-generic
 308.3GB: boot/initrd.img-2.6.32-30-generic
 318.9GB: boot/initrd.img-2.6.32-31-generic
 317.5GB: boot/vmlinuz-2.6.32-21-generic
 305.7GB: boot/vmlinuz-2.6.32-29-generic
 308.3GB: boot/vmlinuz-2.6.32-30-generic
 318.7GB: boot/vmlinuz-2.6.32-31-generic
 318.9GB: initrd.img
 308.3GB: initrd.img.old
 318.7GB: vmlinuz
 308.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff ff ff ff ff ff ff ff  cf 93 2c 7b 57 7d 83 88  |..........,{W}..|
00000010  ff ff ff ff ff ff ff ff  91 ac e7 59 2b ea 62 7a  |...........Y+.bz|
00000020  ff ff ff ff ff ff ff ff  ab 72 87 51 fc 7d 55 55  |.........r.Q.}UU|
00000030  ff ff ff ff ff ff ff ff  b2 ac 87 51 a5 25 25 b5  |...........Q.%%.|
00000040  ff ff ff ff ff ff ff ff  71 a4 ef 93 57 ce d2 e7  |........q...W...|
00000050  ff ff ff ff ff ff ff ff  71 a4 ce 93 5a 87 e2 5b  |........q...Z..[|
00000060  ff ff ff ff ff ff ff ff  0f 9c 85 41 7a 60 c0 c0  |...........Az`..|
00000070  ff ff ff ff ff ff ff ff  28 62 e4 38 d5 25 02 a8  |........(b.8.%..|
00000080  ff ff ff ff ff ff ff ff  ef 93 08 5a 55 f9 01 09  |...........ZU...|
00000090  ff ff ff ff ff ff ff ff  30 a4 28 52 55 55 57 78  |........0.(RUUWx|
000000a0  ff ff ff ff ff ff ff ff  69 5a e7 49 0b 3d f5 d5  |........iZ.I.=..|
000000b0  ff ff ff ff ff ff ff ff  69 5a 45 39 58 e0 88 5a  |........iZE9X..Z|
000000c0  ff ff ff ff ff ff ff ff  69 5a 45 39 55 55 58 62  |........iZE9UUXb|
000000d0  ff ff ff ff ff ff ff ff  45 39 41 18 70 a0 00 00  |........E9A.p...|
000000e0  ff ff ff ff ff ff ff ff  28 52 24 31 01 35 57 f5  |........(R$1.5W.|
000000f0  ff ff ff ff ff ff ff ff  69 5a 24 31 08 00 8b 75  |........iZ$1...u|
00000100  ff ff ff ff ff ff ff ff  07 4a 25 39 00 28 15 95  |.........J%9.(..|
00000110  ff ff ff ff ff ff ff ff  e7 49 e3 28 60 80 00 80  |.........I.(`...|
00000120  ff ff ff ff ff ff ff ff  85 41 c3 28 d5 d5 d6 70  |.........A.(...p|
00000130  ff ff ff ff ff ff ff ff  0b 7b e3 28 25 b5 d5 55  |.........{.(%..U|
00000140  ff ff ff ff ff ff ff ff  cd 93 a6 49 02 aa aa a9  |...........I....|
00000150  ff ff ff ff ff ff ff ff  0e a4 4b 8b fa 57 e3 03  |..........K..W..|
00000160  ff ff ff ff ff ff ff ff  ed a3 2a 8b 7f d5 bf 00  |..........*.....|
00000170  ff ff ff ff ff ff ff ff  cc 9b e9 82 7f 7f ee a8  |................|
00000180  ff ff ff ff ff ff ff ff  8b 93 a8 7a d7 ff aa 00  |...........z....|
00000190  ff ff ff ff ff ff ff ff  ac 9b e9 82 e7 57 2a 0a  |.............W*.|
000001a0  ff ff ff ff ff ff ff ff  ed 9b e9 82 ff 55 aa 00  |.............U..|
000001b0  ff ff ff ff ff ff ff ff  cc 9b 0a 83 ff f5 00 fe  |................|
000001c0  ff ff 83 fe ff ff b3 da  82 21 00 f0 df 01 00 fe  |.........!......|
000001d0  ff ff 05 fe ff ff d8 19  00 00 55 9b d0 00 00 00  |..........U.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

Anyway, I would like some instruction on how to get my computer up and running again please :)

---

### Post by Hedgehog1 on 2011-04-28
I believe your system is acting up because you managed to create 2 swap partitons rather than a data and swap partiton - and one of those partitons is 'not right'. You also have a boot loader installation error.

```
sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
**[COLOR="red"]mount: unknown filesystem type ''[/COLOR]**

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
```


```
/dev/sda6          31,471,398    45,142,649    13,671,252  82 **[COLOR="red"]Linux swap / Solaris[/COLOR]**
/dev/sda7          31,464,783    31,471,396         6,614  82 Linux swap / Solaris
```


```
/dev/sda5        c34d8ef4-9c20-443f-9fe1-5592f1f5d71f   ext4                                     
[COLOR="Red"]**/dev/sda6 has no UUID**[/COLOR]
/dev/sda7        f79331ef-520d-4a84-99d0-248ee15f26e5   swap       New Volume 
```

So, using gparted from the LiveCD/LiveUSB, please removed and then re-add the /dev/sda6 partition, making it 'ntfs' or 'fat32' so you can share data, and format it.

Additionally, you have installed your boot loader on /dev/sda2 rather than on /dev/sda.

Again from the LiveCD/LiveUSB, do this:


```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

These two changes should have you booting again.

***The Hedge***

:KS

---

### Post by brainard52 on 2011-04-28
thanks. i'll let you know how it turns out :)

---

### Post by brainard52 on 2011-04-28
I LOVE YOU (eh, my way of saying thankyouthankyouthankyouIamForeverInDebtToYou!)! thank you :)

---

### Post by Hedgehog1 on 2011-04-28
> **brainard52 said:**
> I LOVE YOU (eh, my way of saying thankyouthankyouthankyouIamForeverInDebtToYou!)! thank you :)

I will assume that worked.  <in my best Mr Burn's voice> **'Excellent!'**


***The 'Helpful' Hedge***

:KS

p.s. Please mark the thread as solved using the thread tool in the upper right hand corner of the page.

---

### Post by brainard52 on 2011-04-30
yes it did. and My compy can handle quite a bit more now because of the swap xD

---

