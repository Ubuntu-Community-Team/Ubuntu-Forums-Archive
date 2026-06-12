---
title: "boot partition erased"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by topias.l on 2010-08-10
hi, i have a weird problem. I have a acer aspire one a150 that has ubuntu 10.04 and windows xp installed. A couple months ago, when i was installing ubuntu on it, i managed to get two hard drive partitions with ubuntu on them but no boot partition. When i finally got ubuntu running, i could see three hard drives in the places menu. i knew one was for windows and i supposed the two other ones were the hard drive partitions i had made. Now, today, i decided to get rid of them. i went to the disk manager in the system/administration menu. i emptied two partitions that i thought were the partitions that i wanted to erase and i rebooted the computer. i had a surprise coming. When the computer rebooted it showed the bios screen as usually but then it showed "error: no such partition. grub rescue>" where the os selection menu should have been. I can't boot on to any os now. I guess i erased some boot partition. How can i get my computer running again? I think reinstalling ubuntu would work but could i use windows after that? Any help would be greatly appreciated.

---

### Post by topias.l on 2010-08-11
Please! i really want to know a way i could do this without reinstalling ubuntu. i have a ton of files and apps i would have to reinstall if i did this.:(

---

### Post by dabl on 2010-08-11
How do we know you did not delete 100% of your Ubuntu installation?

You'll to boot a Live CD, mount the partitions that you have, and then look at the contents to see what you have left.

---

### Post by topias.l on 2010-08-11
the partitions i erased were both only about 3 gb. I dont think my ubuntu install would fit in there. i know it was dumb to delete those partitions...

---

### Post by dabl on 2010-08-11
If you actually deleted the partitions, then the partition numbering was changed on the hard drive.  That would screw up /etc/fstab, which was written by the installer when you installed Ubuntu.

If this is the problem, you can boot a Live CD and fix it.  Run

```
fdisk -lu
``` to see the designation of partitions and filesystems.

run ```
sudo blkid
``` to see the UUIDs for each partition.

You'll have to mount the partition where Ubuntu is installed.  Then use gedit to edit /etc/fstab (of the mounted filesystem with Ubuntu on it) and change the partition UUIDs to the correct ones as shown in blkid.

---

### Post by topias.l on 2010-08-11
i typed "fdisk -lu" and nothing happened. then i typed "sudo blkid" and this showed up:

/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="PQSERVICE" UUID="0159-6699" TYPE="vfat"
/dev/sda2: LABEL="ACER" UUID="4A1C5A171C59FDDFF" TYPE="ntfs"
/dev/sda5: UUID="8bc94a0b-13a6-43bc-b438-b8dc6b5f55ae" TYPE="swap"
/dev/sda6: UUID="7dbec17d-3cc4-4f79-ac91-10019d0ecfed" TYPE="swap"
/dev/sda7: UUID="083323a9-015c-49ea-a188-4b0f5d32ed88" TYPE="ext4"
/dev/sda8: UUID="dfd7e9c0-592b-48df-9025-de016f25196c" TYPE="swap"
/dev/sdb1: LABEL="KINGSTON" UUID="7CF7-8C82" TYPE="vfat"

looks like sda3 and sda4 are missing.

---

### Post by wilee-nilee on 2010-08-11
Post the boot script in my signature. Put it in code tags by my description in the signature or just highlight the txt in the response and click on the # (code tags).

---

### Post by topias.l on 2010-08-11
what boot script do you mean?

---

### Post by dabl on 2010-08-11
> **topias.l said:**
> i typed "fdisk -lu" and nothing happened.



Ooops -- make that sudo fdisk -lu

> 

/dev/loop0: TYPE="squashfs"



This is your CD.

> 
/dev/sda1: LABEL="PQSERVICE" UUID="0159-6699" TYPE="vfat"


This is a "repair utility/recovery" partition.

> 

/dev/sda2: LABEL="ACER" UUID="4A1C5A171C59FDDFF" TYPE="ntfs"



This is your Windows partition.

> 
/dev/sda5: UUID="8bc94a0b-13a6-43bc-b438-b8dc6b5f55ae" 
TYPE="swap"



This is your (first) Linux swap partition.  It is the first logical partition in an Extended partition.  Logical partitions begin number with "5".

> 
/dev/sda6: UUID="7dbec17d-3cc4-4f79-ac91-10019d0ecfed" TYPE="swap"



Oooops -- this is a second and unneeded swap partition!

> 
/dev/sda7: UUID="083323a9-015c-49ea-a188-4b0f5d32ed88" TYPE="ext4"



This is your Linux Ubuntu partition.

> 
/dev/sda8: UUID="dfd7e9c0-592b-48df-9025-de016f25196c" TYPE="swap"



Oooops -- swap partition #3 -- also not needed.


> 
/dev/sdb1: LABEL="KINGSTON" UUID="7CF7-8C82" TYPE="vfat"



This is your USB stick.

---

### Post by topias.l on 2010-08-11
this is what i found for the boot script:

#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2    *     10,233,405   165,765,117   155,531,713   7 HPFS/NTFS
/dev/sda3         165,765,118   312,580,095   146,814,978   5 Extended
/dev/sda5         306,720,768   312,580,095     5,859,328  82 Linux swap / Solaris
/dev/sda6         170,651,648   170,995,711       344,064  82 Linux swap / Solaris
/dev/sda7         176,996,352   301,328,383   124,332,032  83 Linux
/dev/sda8         301,330,432   306,712,575     5,382,144  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,935,999     7,927,936   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0159-6699                              vfat       PQSERVICE                     
/dev/sda2        4A1C5A171C59FDFF                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        8bc94a0b-13a6-43bc-b438-b8dc6b5f55ae   swap                                     
/dev/sda6        7dbec17d-3cc4-4f79-ac91-10019d0ecfed   swap                                     
/dev/sda7        083323a9-015c-49ea-a188-4b0f5d32ed88   ext4                                     
/dev/sda8        dfd7e9c0-592b-48df-9025-de016f25196c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7CF7-8C82                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /media/083323a9-015c-49ea-a188-4b0f5d32ed88 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/menu.lst: ===========================

# defoptions=elevator=noop quiet splash

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=083323a9-015c-49ea-a188-4b0f5d32ed88 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=083323a9-015c-49ea-a188-4b0f5d32ed88 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=083323a9-015c-49ea-a188-4b0f5d32ed88 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=083323a9-015c-49ea-a188-4b0f5d32ed88 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=083323a9-015c-49ea-a188-4b0f5d32ed88 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=083323a9-015c-49ea-a188-4b0f5d32ed88 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=083323a9-015c-49ea-a188-4b0f5d32ed88 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=083323a9-015c-49ea-a188-4b0f5d32ed88 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 083323a9-015c-49ea-a188-4b0f5d32ed88
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0159-6699
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4a1c5a171c59fdff
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 10.04 LTS (10.04) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0d55a367-7cf6-46f3-9831-745af5a21e19
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda7
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=083323a9-015c-49ea-a188-4b0f5d32ed88 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=dfd7e9c0-592b-48df-9025-de016f25196c none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 142.3GB: boot/grub/core.img
  95.7GB: boot/grub/grub.cfg
 142.3GB: boot/grub/menu.lst
 142.5GB: boot/initrd.img-2.6.32-21-generic
 143.1GB: boot/initrd.img-2.6.32-22-generic
 143.1GB: boot/initrd.img-2.6.32-23-generic
 143.1GB: boot/initrd.img-2.6.32-24-generic
 142.2GB: boot/vmlinuz-2.6.32-21-generic
 142.6GB: boot/vmlinuz-2.6.32-22-generic
 143.1GB: boot/vmlinuz-2.6.32-23-generic
 143.1GB: boot/vmlinuz-2.6.32-24-generic
 143.1GB: initrd.img
 143.1GB: initrd.img.old
 143.1GB: vmlinuz
 143.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  11 04 00 00 01 04 00 00  10 03 00 00 10 03 00 00  |................|
00000010  01 00 00 00 73 00 00 00  80 00 00 00 83 00 00 00  |....s...........|
00000020  02 00 00 00 47 00 00 00  5c 00 00 00 6c 00 00 00  |....G...\...l...|
00000030  03 00 00 00 1f 00 00 00  34 00 00 00 40 00 00 00  |........4...@...|
00000040  04 00 00 00 0f 00 00 00  15 00 00 00 1a 00 00 00  |................|
00000050  05 00 00 00 09 00 00 00  0d 00 00 00 0e 00 00 00  |................|
00000060  06 00 00 00 07 00 00 00  ee 0c 00 00 08 00 00 00  |................|
00000070  ff 0d 00 00 ff 0d 00 00  ef 0d 00 00 ef 0d 00 00  |................|
00000080  fe 0d 00 00 fe 0d 00 00  df 0d 00 00 df 0d 00 00  |................|
00000090  fd 0d 00 00 fd 0d 00 00  cf 0d 00 00 cf 0d 00 00  |................|
000000a0  0a 00 00 00 0b 00 00 00  fb 0c 00 00 0c 00 00 00  |................|
000000b0  fc 0d 00 00 fc 0d 00 00  de 0d 00 00 de 0d 00 00  |................|
000000c0  ed 0d 00 00 ed 0d 00 00  bf 0d 00 00 bf 0d 00 00  |................|
000000d0  ce 0d 00 00 ce 0d 00 00  ec 0d 00 00 ec 0d 00 00  |................|
000000e0  dd 0c 00 00 af 0c 00 00  fa 0c 00 00 be 0c 00 00  |................|
000000f0  eb 0c 00 00 cd 0c 00 00  dc 0c 00 00 9f 0c 00 00  |................|
00000100  10 00 00 00 11 00 00 00  12 00 00 00 13 00 00 00  |................|
00000110  f9 0c 00 00 ea 0c 00 00  bd 0c 00 00 db 0c 00 00  |................|
00000120  8f 0c 00 00 f8 0c 00 00  cc 0c 00 00 9e 0c 00 00  |................|
00000130  e9 0c 00 00 7f 0c 00 00  f7 0c 00 00 ad 0c 00 00  |................|
00000140  da 0c 00 00 bc 0c 00 00  6f 0c 00 00 14 00 00 00  |........o.......|
00000150  ae 0d 00 00 ae 0d 00 00  0f 0d 00 00 0f 0d 00 00  |................|
00000160  16 00 00 00 17 00 00 00  18 00 00 00 19 00 00 00  |................|
00000170  cb 0b 00 00 cb 0b 00 00  f6 0b 00 00 f6 0b 00 00  |................|
00000180  8e 0c 00 00 e8 0c 00 00  5f 0c 00 00 9d 0c 00 00  |........_.......|
00000190  f5 0b 00 00 f5 0b 00 00  7e 0b 00 00 7e 0b 00 00  |........~...~...|
000001a0  e7 0b 00 00 e7 0b 00 00  ac 0b 00 00 ac 0b 00 00  |................|
000001b0  1b 00 00 00 1c 00 00 00  1d 00 00 00 1e 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 d0  66 08 00 68 59 00 00 fe  |........f..hY...|
000001d0  ff ff 05 fe ff ff 00 6c  4a 00 02 64 05 00 00 00  |.......lJ..d....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by wilee-nilee on 2010-08-11
From the top of the bootscript.
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
**partition #9** for /boot/grub. You have no partition 9 anymore but you do have a Ubuntu install in sda7 so from a live cd run theses two commands, here is a link as well that shows the commands.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
So from a live karmic or later cd.
```
sudo mount /dev/sda7 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

then reboot to Ubuntu and run ```
sudo update-grub
```

You have 2 extra swap partitions you need look at the hard drive from gparted, to install gparted from the terminal.
```
sudo apt-get install gparted
```

From this program you should be doing HD maintenance only, basically, and can only be done on unmounted partitions which entails using the live cd at times.

---

### Post by topias.l on 2010-08-11
this is my result for sudo fdisk -lu:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    10233404     5116671   12  Compaq  diagnostics
/dev/sda2   *    10233405   165765117    77765856+   7  HPFS/NTFS
/dev/sda3       165765118   312580095    73407489    5  Extended
/dev/sda5       306720768   312580095     2929664   82  Linux swap /  Solaris
/dev/sda6       170651648   170995711      172032   82  Linux swap /  Solaris
/dev/sda7       176996352   301328383    62166016   83  Linux
/dev/sda8       301330432   306712575     2691072   82  Linux swap /  Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x867419e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7935999     3963968    b  W95 FAT32
```

---

### Post by topias.l on 2010-08-11
sorry i didn't see your last post

---

### Post by topias.l on 2010-08-11
Thanks! I can boot on to ubuntu now and access all my files. Thanks for everything. 

I have one more question: Are sda6 and sda8 extra? Are they the extra partitions i made back then and was trying to remove?

---

### Post by wilee-nilee on 2010-08-11
> **topias.l said:**
> Thanks! I can boot on to ubuntu now and access all my files. Thanks for everything. 

I have one more question: Are sda6 and sda8 extra? Are they the extra partitions i made back then and was trying to remove?

You only need one swap file, usually equal to your ram size for hibernation.

---

