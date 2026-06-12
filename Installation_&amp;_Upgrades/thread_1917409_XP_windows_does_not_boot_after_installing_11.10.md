---
title: "XP windows does not boot after installing 11.10"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by gaiamuse on 2012-01-30
XP windows does not boot after installing 11.10 Hello,  Below is an issue posted on the Ubuntu Asus forum with 220 views but no responses. Hoping I can get a response in this forum.   Using Asus EEEPC 10001P Netbook  I upgraded from Ubuntu 10.10 remix to 11.04 to 11.10. Windows XP does not boot anymore. I was able to dual boot with 10.10 remix. Ubuntu 11.10 works just fine but when choosing winXP I just get an upper left underscore blinking and windows hangs with a black screen.  I do not have a windows XP restore disk as Asus did not supply with this model. Windows XP is NTFS files system partition: /dev/sda1 (37 Gb), /dev/sda3 possibly restore (47 Mb) and Ubuntu on /dev/sda5 (101 Gb)  Is is possible to restore the MBR of XP without a windows XP restore disk so I can still dual boot?    Addendum: If there is no way whatsoever to recover XP for a dual boot, is there a way to at least recover the allocated storage space that XP was using so I can at least use this as a storage drive for Ubuntu? Right now I cannot access it at all.  thanks for any help.  gaiamuse

---

### Post by surenot on 2012-01-30
I had a similar problem a while back when trying to triple boot my macintosh with Mac OSX, Ubuntu, and Windows XP.  I wouldn't rush into doing this yet, because someone might still be able to help you, but in the worst case scenario you might have to use gparted or disk utility to reformat the Windows XP partition.  Or have you already tried that?

---

### Post by darkod on 2012-01-30
Restoring windows mbr will not make it dual boot, it will make it load windows directly. It's not aware of linux.

The blinking cursor top left might mean grub bootloader installed to the XP partition boot sector (PBR). Follow the link in my signature to run the boot info script and post the results as explained there. It will show more details.

---

### Post by gaiamuse on 2012-02-01
Thanks so much for your replies.

I have not done anything to partitions or deleted windows. 

Below is result.txt file:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda1 has 
                       156280256 sectors, but according to the info from 
                       fdisk, it has 78187734 sectors.
    Mounting failed:   Failed to read last sector (156280256): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
Failed to read last sector (156280256): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   Failed to read last sector (156280256): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
Failed to read last sector (156280256): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    78,187,797    78,187,735   7 NTFS / exFAT / HPFS
/dev/sda2         298,134,270   312,480,314    14,346,045  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)
/dev/sda4          78,188,542   298,133,503   219,944,962   5 Extended
/dev/sda5          78,188,544   291,991,551   213,803,008  83 Linux
/dev/sda6         291,993,600   298,133,503     6,139,904  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        628C8AC18C8A8EEB                       ntfs       
/dev/sda2        CCED-990E                              vfat       PE
/dev/sda5        f4c7bc81-a0a0-4a01-b729-304df000c834   ext4       
/dev/sda6        9ef0dd58-a0c5-42a8-8bf3-2b0ef1b8c10b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root f4c7bc81-a0a0-4a01-b729-304df000c834
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root f4c7bc81-a0a0-4a01-b729-304df000c834
  set locale_dir=($root)/boot/grub/locale
  set lang=en_NZ
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f4c7bc81-a0a0-4a01-b729-304df000c834
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f4c7bc81-a0a0-4a01-b729-304df000c834 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f4c7bc81-a0a0-4a01-b729-304df000c834
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f4c7bc81-a0a0-4a01-b729-304df000c834 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f4c7bc81-a0a0-4a01-b729-304df000c834
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=f4c7bc81-a0a0-4a01-b729-304df000c834 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f4c7bc81-a0a0-4a01-b729-304df000c834
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=f4c7bc81-a0a0-4a01-b729-304df000c834 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f4c7bc81-a0a0-4a01-b729-304df000c834
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f4c7bc81-a0a0-4a01-b729-304df000c834
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 628C8AC18C8A8EEB
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f4c7bc81-a0a0-4a01-b729-304df000c834 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9ef0dd58-a0c5-42a8-8bf3-2b0ef1b8c10b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  42.384140015 = 45.509623808   boot/grub/core.img                             1
  42.127483368 = 45.234040832   boot/grub/grub.cfg                             1
  56.166061401 = 60.307849216   boot/initrd.img-2.6.38-12-generic              2
  39.194328308 = 42.084589568   boot/initrd.img-3.0.0-12-generic               3
  39.533512115 = 42.448785408   boot/vmlinuz-2.6.38-12-generic                 2
  56.100017548 = 60.236935168   boot/vmlinuz-3.0.0-12-generic                  2
  39.194328308 = 42.084589568   initrd.img                                     3
  56.166061401 = 60.307849216   initrd.img.old                                 2
  56.100017548 = 60.236935168   vmlinuz                                        2
  39.533512115 = 42.448785408   vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  55 aa 03 e9 7a 00 93 00  00 00 00 00 00 00 00 00  |U...z...........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  ff ff 00 00 00 9b cf 00  |................|
00000030  ff ff 00 00 00 93 cf 00  ff ff 00 00 00 9a 0f 00  |................|
00000040  ff ff 00 00 00 92 0f 00  27 00 20 00 00 00 00 00  |........'. .....|
00000050  ff ff 00 00 00 00 00 00  10 00 44 65 76 69 63 65  |..........Device|
00000060  56 4d 20 52 6f 6d 20 4c  6f 61 64 65 72 00 00 00  |VM Rom Loader...|
00000070  01 31 31 2f 32 32 2f 32  30 30 37 00 00 00 00 00  |.11/22/2007.....|
00000080  0e 58 2e a3 42 02 68 00  00 1f 68 00 00 07 57 2e  |.X..B.h...h...W.|
00000090  8d 3e 00 06 2e 80 7d 20  03 75 17 9c 60 b8 03 00  |.>....} .u..`...|
000000a0  cd 10 61 9d 2e 8d 3e 8c  03 e8 fd 02 b4 00 50 cd  |..a...>.......P.|
000000b0  16 58 5f b8 03 00 c1 e0  09 89 c3 0e 07 26 66 8b  |.X_..........&f.|
000000c0  47 0c 66 85 c0 74 05 2e  66 a3 56 00 fa 66 31 c0  |G.f..t..f.V..f1.|
000000d0  8c c8 66 c1 e0 04 2e 66  01 06 4a 00 fb 2e 66 a3  |..f....f..J...f.|
000000e0  3a 00 b0 9a 2e a2 3d 00  66 50 e8 25 03 66 58 66  |:.....=.fP.%.fXf|
000000f0  50 66 51 1e c8 0c 00 00  0e 1f 66 31 c0 3e a1 06  |PfQ.......f1.>..|
00000100  00 66 c1 e0 09 66 2d 03  00 00 00 66 50 2e 66 a1  |.f...f-....fP.f.|
00000110  56 00 66 50 66 31 c0 66  31 c9 b9 00 06 8c c8 66  |V.fPf1.f1......f|
00000120  c1 e0 04 66 01 c8 66 50  e8 cb 01 c9 1f 66 59 66  |...f..fP.....fYf|
00000130  58 fa 2e 0f 01 16 48 00  0f 20 c0 0c 01 0f 22 c0  |X.....H.. ....".|
00000140  2e 66 8b 36 56 00 66 67  66 67 8b 06 66 3d eb 3e  |.f.6V.fgfg..f=.>|
00000150  45 54 74 14 0f 20 c0 24  fe 0f 22 c0 57 2e 8d 3e  |ETt.. .$..".W..>|
00000160  5a 03 e8 44 02 5f cd 18  0f 20 c0 24 fe 0f 22 c0  |Z..D._... .$..".|
00000170  06 53 8c cb 8e c3 bb 00  06 e8 e0 00 5b 07 c8 0c  |.S..........[...|
00000180  00 00 66 b8 00 02 00 00  66 50 2e 66 a1 56 00 66  |..f.....fP.f.V.f|
00000190  50 66 31 c0 66 31 c9 b9  00 06 8c c8 66 c1 e0 04  |Pf1.f1......f...|
000001a0  66 01 c8 66 50 e8 4e 01  c9 2e 66 8b 36 56 00 66  |f..fP.N...f.6V.f|
000001b0  89 e0 66 50 16 66 29 db  bb 48 00 66 29 c9 8c c9  |..fP.f)..H.f)...|
000001c0  66 c1 e1 04 66 01 d9 66  51 66 29 c0 66 29 c9 b8  |f...f..fQf).f)..|
000001d0  08 00 66 50 b8 14 02 8c  c9 66 c1 e1 04 66 01 c1  |..fP.....f...f..|
000001e0  66 51 66 29 c0 89 e0 66  29 c9 8c d1 66 c1 e1 04  |fQf)...f)...f...|
000001f0  66 01 c1 fa 2e 0f 01 16  48 00 0f 20 c0 0c 01 0f  |f.......H.. ....|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error




Many thanks 
gaiamuse

---

### Post by darkod on 2012-02-01
/dev/sda3 is EFI partition according to fdisk. Do you use EFI boot or BIOS boot?

---

### Post by gaiamuse on 2012-02-02
Darko,  I am sorry, I do not know how to determine if my netbook uses EFI or BIOS boot. Can you explain how?  many thanks, gaiamuse

---

### Post by gaiamuse on 2012-02-04
Hi Darkod,
After some research and finally getting into my BIOS i do have boot booster enabled which uses the efi partition. So answer is yes, it is booting from efi.

So where to from here?

cheers gaiamuse

---

### Post by darkod on 2012-02-04
I'm not sure, I don't use EFI.
But from what I have seen mentioned, it seems both windows and ubuntu are trying to take the system EFI partition for themselves, deleting the boot files of the OS installed first.
In this case ubuntu would delete the boot files of XP if I understood it right.

Try googling for EFI dual boot and see what you can find, I think this is the problem you need to focus on. Sorry but I don't use EFI and know almost nothing about it.

---

### Post by gaiamuse on 2012-02-05
Hi,  After some searching, it seems there is a bug in 11.04 in which is overwrites with fat16 instead of keeping fat32. Since I had to install 11.04 before upgrading to 11.10, must have done it then.This is a very unfortunate bug for those who really wish to keep both operating systems using EFI. I am testing on the netbook and trying to learn Ubuntu to eventually dual boot on our desktop. I was hoping to be able to solve this because if this happened on our desktop even if using BIOS boot it would be far more detrimental.  If this cannot be fixed, how can I at least claim the space back? If I reformat the two partitions sda1 window xp (boot) and sda3 EFI partition could this effect Ubuntu?  cheers gaiamuse

---

### Post by darkod on 2012-02-05
If your desktop is not using EFI I see no reason the same problem to happen. This is only related to the EFI issue.

I'm not sure, but I think part of the procedure to install on EFI was to backup your windows boot files from the EFI partition, and after you install ubuntu and it overwrites the EFI partition, you simply put the windows files back, without deleting grub files that are there from the ubuntu install.

---

