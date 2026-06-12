---
title: "upgrade 10.04 to 10.10: Screen goes black with newest kernel"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by japsai on 2010-12-03
Recovery mode doesn't work, same problem. Taking the older kernel gives no problem. I have no 3rd party graphics driver installed. 10.04 was a fresh install on this machine. I cannot get a commandline, the screen just shuts down because of a lack of input.

Thanks for your thoughts!

---

### Post by Rubi1200 on 2010-12-03
Hi,
could you please tell us how much RAM you have and what graphics card is installed?

Thanks.

---

### Post by japsai on 2010-12-07
Memory: 8GB
Graphics: GeForce 8600 GT (according to lshw -C video)

---

### Post by Rubi1200 on 2010-12-07
Thanks for the information.

The RAM should not be an issue, but the graphics card might be.

However, to make sure this is not some other issue, please run the boot info script linked at the bottom of my post.

Get the results back here and we will see if we can rule out bootloader/booting issues.

Thanks.

---

### Post by japsai on 2010-12-07
Thanks for your help, I have attached the RESULTS.txt file. 

What may be good to know is that if I start (from GRUB) the recovery mode of the problematic kernel, it seems like a normal boot procedure starts, i.e. several lines of output appear before the screen goes black.

---

### Post by Rubi1200 on 2010-12-07
Thanks; well a cursory glance seems to indicate that the results are normal.
Next time you boot, when the GRUB menu comes up and the entry for Ubuntu is highlighted press "e" to edit.
Navigate using the cursor to the line that ends with quiet splash and add nomodeset so that it looks like this: quiet splash nomodeset (note the space). Then "Ctrl" + "x" to boot. If this gets you in, try reinstalling the drivers and/or downloading additional drivers via the Proprietary Hardware menu.
Let us know if this helps.

EDIT: this link should also help:
[http://ubuntuforums.org/showpost.php?p=10191728&postcount=6](http://ubuntuforums.org/showpost.php?p=10191728&postcount=6)
(courtesy of oldfred)

You may want to also boot an older kernel and then try the settings in the link above.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   929,523,711   929,316,864   7 HPFS/NTFS
/dev/sda3         929,523,712 1,953,521,663 1,023,997,952   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1       1,937,713,152 1,953,523,711    15,810,560  82 Linux swap / Solaris
/dev/sdb2               2,048   878,905,343   878,903,296  83 Linux
/dev/sdb3         878,907,390 1,937,711,103 1,058,803,714   5 Extended
/dev/sdb5         878,907,392 1,937,711,103 1,058,803,712  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        48DA7BB4DA7B9D3E                       ntfs       System Reserved               
/dev/sda2        0A989A27989A10F5                       ntfs       WINSYS                        
/dev/sda3        08D4915BD4914C36                       ntfs       WINHOME                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        10e5fd8a-dfa8-425e-852d-8dd941445b51   swap                                     
/dev/sdb2        60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9   ext4       LINSYS                        
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        4e818e75-0b64-4265-9978-8f7a322a51b6   ext4       LINHOME                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        5826E33326E310B4                       ntfs       DATA                          
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb5        /home                    ext4       (rw,commit=0)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9
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
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 48da7bb4da7b9d3e
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=60c09b3f-e69b-4ce1-b1d9-03c4d85b01e9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=4e818e75-0b64-4265-9978-8f7a322a51b6 /home           ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=10e5fd8a-dfa8-425e-852d-8dd941445b51 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


  90.3GB: boot/grub/core.img
 400.0GB: boot/grub/grub.cfg
  90.5GB: boot/initrd.img-2.6.32-25-generic
    .4GB: boot/initrd.img-2.6.35-23-generic
  90.4GB: boot/vmlinuz-2.6.32-25-generic
  90.4GB: boot/vmlinuz-2.6.35-23-generic
    .4GB: initrd.img
  90.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  48 71 69 d2 2e 96 6c 3f  17 24 15 e0 f4 b1 70 3f  |Hqi...l?.$....p?|
00000010  ba a1 93 e3 8c f3 69 3f  76 ec 2f 1d 74 0d 70 3f  |......i?v./.t.p?|
00000020  5f bb e8 f7 7f 62 79 3f  4d b9 b5 0a 72 df 76 3f  |_....by?M...r.v?|
00000030  43 d8 e9 78 66 46 78 3f  3d ac 53 3f fe ca 77 3f  |C..xfFx?=.S?..w?|
00000040  aa 1e d8 ee 45 bd 75 3f  80 ee b3 9d aa 65 73 3f  |....E.u?.....es?|
00000050  58 a6 78 39 f3 82 72 3f  d6 39 c4 a5 b9 a3 77 3f  |X.x9..r?.9....w?|
00000060  0e 65 90 3f 44 5f 7b 3f  a1 4c 43 d2 de d7 76 3f  |.e.?D_{?.LC...v?|
00000070  f6 c6 cd e7 7d c0 74 3f  53 52 5d 0b a0 6e 7b 3f  |....}.t?SR]..n{?|
00000080  35 f7 5c 21 44 d0 78 3f  e7 f0 36 5d 9f 1c 7d 3f  |5.\!D.x?..6]..}?|
00000090  0f 2f d3 0b b6 8d 75 3f  56 4e 25 1d 96 61 81 3f  |./....u?VN%..a.?|
000000a0  96 12 10 bd 14 6c 79 3f  56 db 73 dd f3 f4 7a 3f  |.....ly?V.s...z?|
000000b0  06 c3 89 ee 85 8e 77 3f  95 dd 66 19 15 06 80 3f  |......w?..f....?|
000000c0  5a da 8b 67 5c a5 8d 3f  e4 13 a9 30 ec c0 6e 3f  |Z..g\..?...0..n?|
000000d0  bf 13 ff 0a d1 1a 76 3f  18 ea df 91 69 9f 7b 3f  |......v?....i.{?|
000000e0  06 d0 b4 ab fc 7f 7a 3f  36 81 a2 c3 ed 00 80 3f  |......z?6......?|
000000f0  52 8b c0 5c 90 51 81 3f  f8 94 76 30 b0 6b 90 3f  |R..\.Q.?..v0.k.?|
00000100  53 3c 09 7e a1 4c 7d 3f  9a 4c 4d ed 65 8c 7c 3f  |S<.~.L}?.LM.e.|?|
00000110  06 30 5e 41 20 da 74 3f  9d 5f d4 cd bb bf 7f 3f  |.0^A .t?._.....?|
00000120  b6 86 71 79 e6 b3 80 3f  24 a0 ab 72 6f 5b 84 3f  |..qy...?$..ro[.?|
00000130  a0 ce af ae 7c 3b a3 3f  e6 99 b0 7d d2 1c 76 3f  |....|;.?...}..v?|
00000140  19 7a 32 ad 85 dd 7b 3f  dd 74 1a 9f 42 74 7e 3f  |.z2...{?.t..Bt~?|
00000150  75 c5 7a e1 05 af 83 3f  c5 0f 14 37 7a b0 82 3f  |u.z....?...7z..?|
00000160  a1 02 6f 7e 32 13 91 3f  e8 12 77 95 b6 9a a3 3f  |..o~2..?..w....?|
00000170  72 30 5c 5f e3 ad 6a 3f  46 d6 ac 34 05 59 68 3f  |r0\_..j?F..4.Yh?|
00000180  61 f2 1e 6c 84 cb 67 3f  c3 87 c6 61 33 b4 73 3f  |a..l..g?...a3.s?|
00000190  7d b9 90 e5 33 22 69 3f  e1 f8 bb 18 01 69 6d 3f  |}...3"i?.....im?|
000001a0  c3 d8 67 2a fe a2 78 3f  7f 90 55 7d fc 63 6d 3f  |..g*..x?..U}.cm?|
000001b0  df 45 9a b9 2d 81 69 3f  72 2a 14 4b 6e 0e 00 fe  |.E..-.i?r*.Kn...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 1c 3f 00 00  |.............?..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

