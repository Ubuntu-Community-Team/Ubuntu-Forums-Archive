---
title: "Any way to fix my installation?"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by lemonoid on 2012-05-01
I have been running Ubuntu 11.10 since its release and I have very important files, not only in my home folder but I have a lot of other tools and documents that I need. The software center told me that I could upgrade, which I had forgot about until it told me, so I chose to install my upgrade, and when my computer rebooted - Linux does not fully work. There are a few issues. Where icons should be on my notification bar there is an x as if the icon image did not load correctly, the home screen is black and all applications are black, except for the lens. Then my keyboard functionality is on and off, and the mouse does not work. So I made a live usb to test 12.04 on my system, and the live version runs fine with no problems at all. I am actually using it to post this right now. I really don't want to have to delete my old Ubuntu installation to have my upgrade because I thought I was past this inconvenience. Is there any way to fix my installation without having to wipe my current system? Thank you in advance for any help or answers you provide.

---

### Post by VMC on 2012-05-01
First off, I would backup your files, using either Clonezilla or tar or something else.

Download bootinfoscript(see my blue label) and run it. Then copy the RESULTS.txt back here so we can see how your computer is setup.

---

### Post by lemonoid on 2012-05-01
> **VMC said:**
> First off, I would backup your files, using either Clonezilla or tar or something else.

Download bootinfoscript(see my blue label) and run it. Then copy the RESULTS.txt back here so we can see how your computer is setup.
should I run the script while in live?

---

### Post by darkod on 2012-05-01
Yes, you can do it in live mode.

---

### Post by lemonoid on 2012-05-01
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 7369864 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,265,024    27,469,823       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,469,824   536,785,943   509,316,120   7 NTFS / exFAT / HPFS
/dev/sda4         536,786,942   976,771,071   439,984,130   5 Extended
/dev/sda5         968,689,664   976,771,071     8,081,408  82 Linux swap / Solaris
/dev/sda6         536,786,944   960,604,159   423,817,216  83 Linux
/dev/sda7         960,606,208   968,687,615     8,081,408  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,856,126     7,856,064   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        100E6A700E6A4F32                       ntfs       PQSERVICE
/dev/sda2        40526ABE526AB7F4                       ntfs       SYSTEM RESERVED
/dev/sda3        E69C6C219C6BEB0F                       ntfs       Gateway
/dev/sda5        38067550-f293-4c3e-9af0-a9b5f2495bed   swap       
/dev/sda6        6a6071a7-3276-4268-b567-38dfd7cc7796   ext4       
/dev/sda7        2401f9da-91c2-4a66-899d-fbd000b67768   swap       
/dev/sdb1        E86F-6017                              vfat       PINKSANDISK

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/SYSTEM RESERVED   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /media/Gateway           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6        /media/6a6071a7-3276-4268-b567-38dfd7cc7796 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    linux    /boot/vmlinuz-3.2.0-24-generic root=/dev/sda6 ro   quiet splash vt.handoff=7
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=/dev/sda6 ro recovery nomodeset 
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=6a6071a7-3276-4268-b567-38dfd7cc7796 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    echo    'Loading Linux 3.0.0-17-generic ...'
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=6a6071a7-3276-4268-b567-38dfd7cc7796 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=6a6071a7-3276-4268-b567-38dfd7cc7796 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=6a6071a7-3276-4268-b567-38dfd7cc7796 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=6a6071a7-3276-4268-b567-38dfd7cc7796 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=6a6071a7-3276-4268-b567-38dfd7cc7796 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6a6071a7-3276-4268-b567-38dfd7cc7796 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6a6071a7-3276-4268-b567-38dfd7cc7796 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6a6071a7-3276-4268-b567-38dfd7cc7796
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 100E6A700E6A4F32
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 40526ABE526AB7F4
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=6a6071a7-3276-4268-b567-38dfd7cc7796 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda7 during installation
UUID=2401f9da-91c2-4a66-899d-fbd000b67768 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic              10
               =                boot/initrd.img-3.0.0-15-generic               2
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/initrd.img-3.0.0-17-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-15-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                boot/vmlinuz-3.0.0-17-generic                  2
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

============================== sdb1/syslinux.cfg: ==============================

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
 
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

---

### Post by lemonoid on 2012-05-01
any luck through that bootscript?

---

### Post by darkod on 2012-05-01
I don't see anything rare. It looks like the upgrade was done but some things don't work as expected. That can happen during any upgrade unfortunately.

That's why I have my system set up with separate /home partition so I can always do a clean install on / and keep my /home untouched.

---

### Post by lemonoid on 2012-05-01
> **darkod said:**
> I don't see anything rare. It looks like the upgrade was done but some things don't work as expected. That can happen during any upgrade unfortunately.

That's why I have my system set up with separate /home partition so I can always do a clean install on / and keep my /home untouched.

well I have my /home backed up that's not really the problem. I just have some changes in etc/udev and various other places, along with android source code for compiling, which for some reason has never transferred without corruption, and I just have that I'm going to hate to set up all my repos again, it takes SOO long to download that source code, at least I have my builds backed up. I guess I'll just let the installer delete my ubuntu and re-install it. thanks anyways friends.

---

### Post by darkod on 2012-05-01
If you are doing a clean install, you might wanna consider setting up a separate /home too. That way you have it separated from /.

It's not complicated, but you have to use the manual partitioning. The automatic methods don't create separate /home. Once you have it, you can do any future clean install much easier. Up to you.

---

### Post by VMC on 2012-05-01
Actually you can do another "clean" install, and leave your "/home" intact. Just don't format the partition and use the same user name. I do it all the time. It will come back will a mild warning, but just proceed. Everything under your "/home" will remain intact. That's why I said to backup first before any attempt.

What won't be left is anything outside your home environment. So if you , for example, installed Google, which resides under "/opt", it will need re-installing.

---

### Post by The Rnegade on 2012-05-02
> **lemonoid said:**
> I have been running Ubuntu 11.10 since its release and I have very important files, not only in my home folder but I have a lot of other tools and documents that I need. The software center told me that I could upgrade, which I had forgot about until it told me, so I chose to install my upgrade, and when my computer rebooted - Linux does not fully work. There are a few issues. Where icons should be on my notification bar there is an x as if the icon image did not load correctly, the home screen is black and all applications are black, except for the lens. Then my keyboard functionality is on and off, and the mouse does not work. So I made a live usb to test 12.04 on my system, and the live version runs fine with no problems at all. I am actually using it to post this right now. I really don't want to have to delete my old Ubuntu installation to have my upgrade because I thought I was past this inconvenience. Is there any way to fix my installation without having to wipe my current system? Thank you in advance for any help or answers you provide.

you can backup anything from live cd by loading your filesystem and the copying on to some removable media drive. 

and my suggestion for the future is to never to an upgrade, they never work right. luckily ubuntu 12.04 is a long term service release, which means it will be supported for a long time, you wont need to upgrade for a long time

---

