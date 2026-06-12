---
title: "Unable to identify Ubuntu after installing"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by SMOKEY989 on 2011-08-29
Hi

Any help would be greatly appreciated.


I have created new partitions for ubuntu((ext4) and share partition and installed Ubuntu.  When installation completed and system restarted, my laptop (Sony Vaio) automatically booted Windows 7.  There was no option to select operating system and on several restarts i have tried to locate Ubuntu through bios, but no luck!!  I understand GRUB2 should allow this but it doesn't seem to be working.

Anyone got any ideas as to what this might be and how to resolve it?

thanks

---

### Post by Hakunka-Matata on 2011-08-29
boot into your Ubuntu liveCD, open a Terminal and run 
```
sudo fdisk -lu
```
post output

we'll see how your hard drive is partitioned and whether Ubuntu is actually installed.

---

### Post by SMOKEY989 on 2011-08-29
I ran installation from USB, using unetbootin.  Would it still work this way?  

thanks

---

### Post by Hakunka-Matata on 2011-08-29
Yep, just boot using the flashdrive and select "try without installing"

---

### Post by SMOKEY989 on 2011-08-30
Hi 

Here's the output

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x21227c0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    19556351     9777152   27  Unknown
/dev/sda2   *    19556352    19761151      102400    7  HPFS/NTFS
/dev/sda3        19761152   393716399   186977624    7  HPFS/NTFS
/dev/sda4       393719806   625139711   115709953    f  W95 Ext'd (LBA)
/dev/sda5       393719808   618790911   112535552   83  Linux
/dev/sda6       618792960   625139711     3173376   82  Linux swap / Solaris

Disk /dev/sdb: 4111 MB, 4111466496 bytes
127 heads, 62 sectors/track, 1019 cylinders, total 8030208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e87d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3223366752  3470046675   123339962   f4  SpeedStor
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(793, 22, 13) logical=(409368, 50, 21)
Partition 1 has different physical/logical endings:
     phys=(870, 235, 61) logical=(440696, 102, 48)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   378192737   710426324   166116794   10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(48030, 72, 54)
Partition 2 has different physical/logical endings:
     phys=(870, 235, 50) logical=(90224, 41, 7)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?   225603442   225603451           5   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(367, 66, 47) logical=(28651, 88, 13)
Partition 3 has different physical/logical endings:
     phys=(370, 32, 37) logical=(28651, 88, 22)
Partition 3 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

I haven't got a clue what this means by the way, so your help will be appreciated!!

---

### Post by SMOKEY989 on 2011-08-31
Hi, sorry to be a pain. Could anyone help me with this?

---

### Post by Hakunka-Matata on 2011-08-31
Is this a Wubi install?
Please paste formatted output using code tags.  How?

[LIST]
[*]highlight and copy data to be posted, "like the output of sudo fdisk -lu"
[*]paste it into your reply, then highlight it again
[*]click on the code tags icon "**#", **if you can't see the '#', switch to 'Advanced" mode
[/LIST]

---

### Post by SMOKEY989 on 2011-08-31
No it isn't a Wubi install, I created the partitions in Windows to accommodate the Ubuntu install.  

The new drives were G: Installtion drive for Ubuntu(ext 4)  and H: swap drive.

I will try what you said above and post soon, I am very new to Linux so if i keep asking questions I apologise.

---

### Post by SMOKEY989 on 2011-08-31
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x21227c0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    19556351     9777152   27  Unknown
/dev/sda2   *    19556352    19761151      102400    7  HPFS/NTFS
/dev/sda3        19761152   393716399   186977624    7  HPFS/NTFS
/dev/sda4       393719806   625139711   115709953    f  W95 Ext'd (LBA)
/dev/sda5       393719808   618790911   112535552   83  Linux
/dev/sda6       618792960   625139711     3173376   82  Linux swap / Solaris

Disk /dev/sdb: 4111 MB, 4111466496 bytes
127 heads, 62 sectors/track, 1019 cylinders, total 8030208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e87d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3223366752  3470046675   123339962   f4  SpeedStor
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(793, 22, 13) logical=(409368, 50, 21)
Partition 1 has different physical/logical endings:
     phys=(870, 235, 61) logical=(440696, 102, 4:cool:
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   378192737   710426324   166116794   10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(48030, 72, 54)
Partition 2 has different physical/logical endings:
     phys=(870, 235, 50) logical=(90224, 41, 7)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?   225603442   225603451           5   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(367, 66, 47) logical=(28651, 88, 13)
Partition 3 has different physical/logical endings:
     phys=(370, 32, 37) logical=(28651, 88, 22)
Partition 3 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 
```

Hopefully this is what you mean!

I've attached screen grab of my partitions in Windows Computer Management.

The first (9.32gb) is a recovery partition for windows, 
the second (107.32gb) is the main Linux installation partition(ext4) i created
the third 3.03gb is the swap drive i created
fourth (178.32gb) is windows
 and the last is system reserved.

thanks

---

### Post by oldfred on 2011-08-31
You must not have gotten grub2's boot loader installed to the MBR.

To see where everything is installed:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by SMOKEY989 on 2011-08-31
HI here is the output

thanks



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 486358872 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......sE.8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7772832 of /dev/sdb for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    19,556,351    19,554,304  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     19,556,352    19,761,151       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          19,761,152   393,716,399   373,955,248   7 NTFS / exFAT / HPFS
/dev/sda4         393,719,806   625,139,711   231,419,906   f W95 Extended (LBA)
/dev/sda5         393,719,808   618,790,911   225,071,104  83 Linux
/dev/sda6         618,792,960   625,139,711     6,346,752  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        ACC843D3C8439A8A                       ntfs       Recovery
/dev/sda2        86BE321ABE32036B                       ntfs       System Reserved
/dev/sda3        448A33C78A33B470                       ntfs       
/dev/sda5        9396c375-e007-4262-b653-71f625f70660   ext4       
/dev/sda6        4db33eb5-47a0-4787-9134-dd050d1c8f96   swap       
/dev/sdb         EAC8-F1A5                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9396c375-e007-4262-b653-71f625f70660
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9396c375-e007-4262-b653-71f625f70660
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9396c375-e007-4262-b653-71f625f70660
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9396c375-e007-4262-b653-71f625f70660 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9396c375-e007-4262-b653-71f625f70660
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9396c375-e007-4262-b653-71f625f70660 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9396c375-e007-4262-b653-71f625f70660
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9396c375-e007-4262-b653-71f625f70660
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ACC843D3C8439A8A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 86BE321ABE32036B
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
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 231.914009094 = 249.015771136  boot/grub/core.img                             1
 189.881248474 = 203.883438080  boot/grub/grub.cfg                             1
 189.183872223 = 203.134636032  boot/initrd.img-2.6.38-8-generic               2
 231.912281036 = 249.013915648  boot/vmlinuz-2.6.38-8-generic                  1
 189.183872223 = 203.134636032  initrd.img                                     2
 231.912281036 = 249.013915648  vmlinuz                                        1

=========================== sdb/boot/grub/grub.cfg: ============================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb/syslinux.cfg: ===============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry6 
menu label Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry7 
menu label Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- 
 
label ubnentry8 
menu label Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- 
 
--------------------------------------------------------------------------------

==================== sdb: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================== sdb: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

=============== sdb: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  64 d8 65 d8 66 d8 67 d8  68 d8 69 d8 6a d8 6b d8  |d.e.f.g.h.i.j.k.|
00000010  6c d8 6d d8 6e d8 6f d8  70 d8 71 d8 72 d8 73 d8  |l.m.n.o.p.q.r.s.|
00000020  74 d8 75 d8 76 d8 77 d8  78 d8 79 d8 7a d8 7b d8  |t.u.v.w.x.y.z.{.|
00000030  7c d8 7d d8 7e d8 7f d8  80 d8 81 d8 82 d8 83 d8  ||.}.~...........|
00000040  84 d8 85 d8 86 d8 87 d8  88 d8 89 d8 8a d8 8b d8  |................|
00000050  8c d8 8d d8 8e d8 8f d8  90 d8 91 d8 92 d8 93 d8  |................|
00000060  94 d8 95 d8 96 d8 97 d8  98 d8 99 d8 9a d8 9b d8  |................|
00000070  9c d8 9d d8 9e d8 9f d8  a0 d8 a1 d8 a2 d8 a3 d8  |................|
00000080  a4 d8 a5 d8 a6 d8 a7 d8  a8 d8 a9 d8 aa d8 ab d8  |................|
00000090  ac d8 ad d8 ae d8 af d8  b0 d8 b1 d8 b2 d8 b3 d8  |................|
000000a0  b4 d8 b5 d8 b6 d8 b7 d8  b8 d8 b9 d8 ba d8 bb d8  |................|
000000b0  bc d8 bd d8 be d8 bf d8  c0 d8 c1 d8 c2 d8 c3 d8  |................|
000000c0  c4 d8 c5 d8 c6 d8 c7 d8  c8 d8 c9 d8 ca d8 cb d8  |................|
000000d0  cc d8 cd d8 ce d8 cf d8  d0 d8 d1 d8 d2 d8 d3 d8  |................|
000000e0  d4 d8 d5 d8 d6 d8 d7 d8  d8 d8 d9 d8 da d8 db d8  |................|
000000f0  dc d8 dd d8 de d8 df d8  e0 d8 e1 d8 e2 d8 e3 d8  |................|
00000100  e4 d8 e5 d8 e6 d8 e7 d8  e8 d8 e9 d8 ea d8 eb d8  |................|
00000110  ec d8 ed d8 ee d8 ef d8  f0 d8 f1 d8 f2 d8 f3 d8  |................|
00000120  f4 d8 f5 d8 f6 d8 f7 d8  f8 d8 f9 d8 fa d8 fb d8  |................|
00000130  fc d8 fd d8 fe d8 ff d8  00 d9 01 d9 02 d9 03 d9  |................|
00000140  04 d9 05 d9 06 d9 07 d9  08 d9 09 d9 0a d9 0b d9  |................|
00000150  0c d9 0d d9 0e d9 0f d9  10 d9 11 d9 12 d9 13 d9  |................|
00000160  14 d9 15 d9 16 d9 17 d9  18 d9 19 d9 1a d9 1b d9  |................|
00000170  1c d9 1d d9 1e d9 1f d9  20 d9 21 d9 22 d9 23 d9  |........ .!.".#.|
00000180  24 d9 25 d9 26 d9 27 d9  28 d9 29 d9 2a d9 2b d9  |$.%.&.'.(.).*.+.|
00000190  2c d9 2d d9 2e d9 2f d9  30 d9 31 d9 32 d9 33 d9  |,.-.../.0.1.2.3.|
000001a0  34 d9 35 d9 36 d9 37 d9  38 d9 39 d9 3a d9 3b d9  |4.5.6.7.8.9.:.;.|
000001b0  3c d9 3d d9 3e d9 3f d9  40 d9 41 d9 42 d9 00 fe  |<.=.>.?.@.A.B...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 6a 0d 00 fe  |...........Pj...|
000001d0  ff ff 05 fe ff ff f8 52  6a 0d 0a dd 60 00 00 00  |.......Rj...`...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

---

### Post by oldfred on 2011-08-31
It looks like you installed grub2's boot loader to sda5 not sda. It will not matter that it still is there as normally the PBR is not used by grub/Ubuntu except possibly advanced users.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by SMOKEY989 on 2011-08-31
HI Oldfred

No errors on running your code, i'm right at the end now.  When you say # If no errors on previous commands reboot into working system and run this: 

WHat do you mean by reboot into working system, how do you do this?

thanks

---

### Post by Hakunka-Matata on 2011-08-31
> **SMOKEY989 said:**
> HI Oldfred

No errors on running your code, i'm right at the end now.  When you say # If no errors on previous commands reboot into working system and run this: 

WHat do you mean by [COLOR=Red]reboot into working system[/COLOR], how do you do this?

thanks

That means to reboot normally, not using liveCD, but selecting Ubuntu from the boot menu
then run ```
sudo update-grub
```

---

### Post by SMOKEY989 on 2011-09-01
[Hakunka-Matata & oldfred, sincere thanks for all your help, Linux is now up and running on my computer!!  :smile:]("http://ubuntuforums.org/member.php?u=735950")

Can I just ask, what desktop environment you both use?

If anyone else is reading this what else do you use and why?  The reason i ask is that I am thinking of using installing Gnome or another environment other than Unity!

thank you

---

### Post by oldfred on 2011-09-01
Glad you got it working.

I still am primarily on Maverick. I changed 11.04 to not use Unity and then I do not see much difference from 10.10 anyway. But my wife has complained i update too often as I have been every 6 months doing a clean install and something is not quite the same. If I showed her Unity I think I would have huge problems.
And my 11.10 is not working at all, I just may have to reinstall. I also just installed 11.04 Kubuntu to see if I can live with it.

---

### Post by Hakunka-Matata on 2011-09-01
Yes, good job SMOKEY989, I'm always pleased when someone gets Ubuntu running correctly for the first time, especially if they have some problems installing and stick with it and fix things (learning more than those who don't have any initial problems).  I think it's a great Operating System.  I just got home after being gone all day to the bay area (CA.) for a post-op checkup.  I like to see this kind of results.

I use natty 11.04 - 32 bit (even though I could use 64 bit),  with Ubuntu-Classic Desktop
10.10 - 32
10.04 - 32 LTS

---

