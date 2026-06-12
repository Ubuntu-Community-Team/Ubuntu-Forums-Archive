---
title: "No boot option for Windows 7"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by mattycarmad on 2010-12-17
I'm in exactly the same sticky state.

Was running my new Ubuntu 10.10 build alongside my original Windows 7 partition, but now the Windows 7 boot option has disappeared following a trip to the update manager

Tried the Update Grub2 command to no avail. (e.g. sudo update-grub)

What is weird is that I now have two Ubuntu boot options i.e.

"Ubuntu, with linux 2.6.35-23-generic"
"Ubuntu, with linux 2.6.35-23-generic" (Recovery Mode)
"Ubuntu, with linux 2.6.35-22-generic"
"Ubuntu, with linux 2.6.35-22-generic" (Recovery Mode)
"Memtest86+"

I ran the same boot_info_script from as per a similar post (and above) in the hope you wizened peeps may see something I clearly can't.

p.s. I'm as noob as they come and fearful of most areas of linux at this point.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

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

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   288,183,200   287,976,353   7 HPFS/NTFS
/dev/sda3         288,184,318   488,396,799   200,212,482   5 Extended
/dev/sda5         288,184,320   480,165,887   191,981,568  83 Linux
/dev/sda6         480,167,936   488,396,799     8,228,864  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,769,023   976,766,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        CCB08C45B08C37CA                       ntfs       System Reserved               
/dev/sda2        4048AAAE48AAA260                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b6771ea5-7f5b-4d3c-adad-bdda21caa97e   ext4                                     
/dev/sda6        27e020e5-3a4e-45c3-9d6a-40695ae67a7e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8CA00A6CA00A5CD8                       ntfs       HOTSWAP                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/4048AAAE48AAA260  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b6771ea5-7f5b-4d3c-adad-bdda21caa97e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b6771ea5-7f5b-4d3c-adad-bdda21caa97e
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b6771ea5-7f5b-4d3c-adad-bdda21caa97e
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b6771ea5-7f5b-4d3c-adad-bdda21caa97e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b6771ea5-7f5b-4d3c-adad-bdda21caa97e
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b6771ea5-7f5b-4d3c-adad-bdda21caa97e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b6771ea5-7f5b-4d3c-adad-bdda21caa97e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6771ea5-7f5b-4d3c-adad-bdda21caa97e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b6771ea5-7f5b-4d3c-adad-bdda21caa97e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6771ea5-7f5b-4d3c-adad-bdda21caa97e ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b6771ea5-7f5b-4d3c-adad-bdda21caa97e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b6771ea5-7f5b-4d3c-adad-bdda21caa97e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b6771ea5-7f5b-4d3c-adad-bdda21caa97e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=27e020e5-3a4e-45c3-9d6a-40695ae67a7e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 197.0GB: boot/grub/core.img
 197.0GB: boot/grub/grub.cfg
 148.5GB: boot/initrd.img-2.6.35-22-generic
 148.6GB: boot/initrd.img-2.6.35-23-generic
 197.0GB: boot/vmlinuz-2.6.35-22-generic
 197.0GB: boot/vmlinuz-2.6.35-23-generic
 148.6GB: initrd.img
 148.5GB: initrd.img.old
 197.0GB: vmlinuz
 197.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  e6 76 02 c7 ac 2d 7e 20  13 51 b0 3d 16 94 bc 53  |.v...-~ .Q.=...S|
00000010  23 50 69 00 e4 34 b1 e8  ed 34 7e 37 22 4f c3 78  |#Pi..4...4~7"O.x|
00000020  17 1b f7 82 36 55 37 f9  01 8e e2 d6 d5 f5 70 5a  |....6U7.......pZ|
00000030  71 14 2e 8e 1b 86 a7 09  f6 33 73 b1 13 da c9 5e  |q........3s....^|
00000040  d4 5b 12 33 70 5e 5d 0d  59 8d 7b a3 b6 8d dc 52  |.[.3p^].Y.{....R|
00000050  78 20 75 aa fe 71 57 31  a5 8b 13 7b dc f0 3f b9  |x u..qW1...{..?.|
00000060  87 bc 99 2d 3a d2 42 7a  b6 91 a8 05 56 c9 47 d7  |...-:.Bz....V.G.|
00000070  ea 1c 64 ee 31 85 03 c2  ac 8d 1b c2 5a fc 8b 6d  |..d.1.......Z..m|
00000080  25 6e 23 9f af 28 05 b6  ca 52 e0 26 52 1c 1f 32  |%n#..(...R.&R..2|
00000090  98 09 3e e0 02 01 32 bc  b0 95 ac e5 16 d0 5b d5  |..>...2.......[.|
000000a0  6a a6 91 ed f3 80 39 59  f3 1b bd 7c 80 12 1d 4b  |j.....9Y...|...K|
000000b0  44 5d 57 4e ff 8d ad 5e  bc d0 ef 9a 08 9f 90 cd  |D]WN...^........|
000000c0  d1 c3 15 66 9e d6 e7 1a  2b f7 cd 1b b1 45 49 f0  |...f....+....EI.|
000000d0  09 df c6 59 26 32 e6 72  86 1b 97 5f 8e 9e 99 06  |...Y&2.r..._....|
000000e0  c1 fc b8 57 78 50 3f 2d  8e 23 d2 a9 d7 a9 66 70  |...WxP?-.#....fp|
000000f0  cf db 3c d0 67 75 37 1f  71 8c f8 9b 66 f1 21 9e  |..<.gu7.q...f.!.|
00000100  93 60 2e 30 a0 e4 48 7e  86 20 9b 3d 81 1a 4d 0f  |.`.0..H~. .=..M.|
00000110  a8 5b de 2c 2c be 46 03  d6 4d f8 13 61 75 e4 c5  |.[.,,.F..M..au..|
00000120  1f 49 4b 03 7c 88 ea 4d  e5 de f9 ee a7 e3 93 d3  |.IK.|..M........|
00000130  f8 b8 db bc 2d e8 5c 0b  dd d6 e0 ff 8f 7c 50 9a  |....-.\......|P.|
00000140  8b 31 4b 2a f2 4e 43 97  7c 0d 5f fa 11 3e 39 b3  |.1K*.NC.|._..>9.|
00000150  7f fe 11 4b 27 ac 69 96  37 f1 a1 58 9a b8 3b d4  |...K'.i.7..X..;.|
00000160  00 53 89 98 00 8e f8 b0  ef 86 93 bd e0 b8 c7 d1  |.S..............|
00000170  58 d5 e2 4c 9b ac 1f 95  8e ea ea b4 f0 67 25 c2  |X..L.........g%.|
00000180  b2 03 95 8b d6 39 3a d4  18 a8 69 31 f7 a7 90 dc  |.....9:...i1....|
00000190  b0 62 e7 49 3c 9b 3a fd  18 e7 05 f7 61 fb 6a c3  |.b.I<.:.....a.j.|
000001a0  75 d9 35 be 99 3e 04 6b  15 39 e0 9b 10 51 ff ab  |u.5..>.k.9...Q..|
000001b0  9c ee 3f 8a 3c e6 46 60  1f d3 c0 25 67 dd 00 fe  |..?.<.F`...%g...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 68 71 0b 00 fe  |...........hq...|
000001d0  ff ff 05 fe ff ff 83 6b  71 0b 7f 94 7d 00 00 00  |.......kq...}...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by cariboo on 2010-12-17
Moved to a separate thread, as the original was about a pendrive installation.

---

### Post by Quackers on 2010-12-17
From your booted Ubuntu install open a terminal and run ```
sudo update-grub
``` then watch as grub.cfg is configured to see if the Windows Loader is picked up.

---

### Post by coffeecat on 2010-12-17
> **Quackers said:**
> From your booted Ubuntu install open a terminal and run ```
sudo update-grub
``` then watch as grub.cfg is configured to see if the Windows Loader is picked up.

+1 to that.

However, I was helping out on a thread on another forum and it turned out that - quite bizarrely - os-prober was not installed. Quite why, I have not a clue, since os-prober is part of a default install. So, if update-grub doesn't put Windows on the menu, go to System > Administration > Synaptic and see if os-prober is installed. If it isn't, install it and run 'sudo update-grub' again.

**EDIT** by the way, having those several Ubuntu choices isn't weird at all. Have a look at the numbers. The update brought down a newer kernel. You still have the option to boot into the older kernel in case the newer one has any issues on your hardware.

---

### Post by Quackers on 2010-12-17
coffeecat, I suspect that involved Lubuntu? I have seen it before with that.

---

### Post by coffeecat on 2010-12-17
> **Quackers said:**
> coffeecat, I suspect that involved Lubuntu? I have seen it before with that.

That's interesting; I'll bear it in mind. However, the OP of the thread in question was clear that it was Ubuntu - I've just checked. Very curious.

---

### Post by Quackers on 2010-12-17
Something else to watch for then :-) Make a mental note to self to look at the os-prober output in boot script :-)

---

### Post by mattycarmad on 2010-12-17
> **coffeecat said:**
>  if update-grub doesn't put Windows on the menu, go to System > Administration > Synaptic and see if os-prober is installed. If it isn't, install it and run 'sudo update-grub' again.
 

coffeecat - you legend!!  It was exactly that.

Had tried update grub several times, but needed os-prober to detect Windows 7 instance.

Thanks v.much to all:D

---

### Post by Quackers on 2010-12-17
That's good to know :-)
It's interesting as os-prober is started in your boot script output, though doesn't list an output.
Thanks for the feedback.

---

### Post by coffeecat on 2010-12-18
Yes, thanks for confirming what was the problem, mattycarmad. I wonder if a bug is causing os-prober to be uninstalled during an update since, clearly, you had a Windows entry to start with and must have had os-prober installed originally.

---

