---
title: "Maverick 10.10 Install Troubles"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by legendamazing on 2010-11-16
Hello I have an old computer with 1 hard drive which I thought I would install Maverick on.

I tried the live cd out and really liked it so I chose the option to install.
I chose to Format the whole drive and not deal with Dual boot. 
I went through the process and everything seemed to work out, and then it said to restart the computer.
I restarted.
Now the Computer can't find any OS on the hard drive. It doesn't think it exists. I don't see what I did wrong.

I boot up the system and it goes through it's normal BIOS and then the screen just goes blank, after a while it says "operating System Not Found" I have tried to change the boot order, just in case something got messed up, but to no avail.

The computer runs just fine in the Live CD.

Now I am a newbie to Ubuntu, so I assume it is a simple fix, but I cannot find it. Please Help!

---

### Post by Quackers on 2010-11-16
If you boot from the Live cd and choose "try Ubuntu" then go to the site below and download the boot script to your DESKTOP then open a terminal and run the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by galvatron408 on 2010-11-17
You'll get that message saying, "No operating system found" if your bios doesn't know to boot from the hard drive. So, enter your bios and make sure that hdd is included in your boot order.

---

### Post by imasynper on 2010-11-17
I don't mean to hijack the thread, but I'm having a similar problem. Installed Ubuntu 10.10 today on my girlfriends laptop with the live cd, it prompted me to restart which I did. When it got past the BIOS all i got was a black screen with a blinking _ in the top left corner. It never does anything past that point. All I can do is manually turn it off with the power button. Like the OP I can boot into the live cd and see ubuntu installed on the hard drive, it just won't boot into it. I checked the boot order and the hard drive is at the top of the list. I got the boot script and it's there below. Thanks for the help.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1007 MB, 1007681536 bytes
9 heads, 8 sectors/track, 27335 cylinders, total 1968128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *            253     1,968,127     1,967,875   6 FAT16


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   300,292,095   300,290,048  83 Linux
/dev/sdb2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sdb5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FC30-3DA9                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f3465293-3c7b-4b63-a2bc-76165805e5b8   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        18b7bca6-8815-47c0-86d9-7ff1f414d3c5   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set f3465293-3c7b-4b63-a2bc-76165805e5b8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set f3465293-3c7b-4b63-a2bc-76165805e5b8
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f3465293-3c7b-4b63-a2bc-76165805e5b8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f3465293-3c7b-4b63-a2bc-76165805e5b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f3465293-3c7b-4b63-a2bc-76165805e5b8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f3465293-3c7b-4b63-a2bc-76165805e5b8 ro single 
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
    search --no-floppy --fs-uuid --set f3465293-3c7b-4b63-a2bc-76165805e5b8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f3465293-3c7b-4b63-a2bc-76165805e5b8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
# / was on /dev/sdb1 during installation
UUID=f3465293-3c7b-4b63-a2bc-76165805e5b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=18b7bca6-8815-47c0-86d9-7ff1f414d3c5 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 116.1GB: boot/grub/core.img
  90.3GB: boot/grub/grub.cfg
  82.3GB: boot/initrd.img-2.6.35-22-generic
 116.1GB: boot/vmlinuz-2.6.35-22-generic
  82.3GB: initrd.img
 116.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  12 38 cc 70 7d 56 36 a1  30 8a 23 70 8f 9f e2 69  |.8.p}V6.0.#p...i|
00000010  ce 03 14 05 e0 60 77 08  59 25 50 c7 92 41 f9 d6  |.....`w.Y%P..A..|
00000020  02 26 5c 5b f9 90 c0 49  21 27 cc ab 74 c7 55 29  |.&\[...I!'..t.U)|
00000030  54 9b bf 63 0e c1 55 28  b2 b8 50 56 b8 c6 c7 66  |T..c..U(..PV...f|
00000040  83 6e f7 6f 30 78 36 40  f7 f2 4d 18 64 1e 24 54  |.n.o0x6@..M.d.$T|
00000050  ff 8b 09 ad 59 7a 37 0e  70 3d 03 50 3e 1a fb e3  |....Yz7.p=.P>...|
00000060  03 2f 05 5e d9 ff 4e 68  c4 0d 45 e5 5e c7 94 14  |./.^..Nh..E.^...|
00000070  86 a2 da d6 43 5a d7 3d  fb e4 10 d9 66 be 64 b8  |....CZ.=....f.d.|
00000080  07 b2 36 56 24 ad dc 5b  de df c1 f8 e0 42 11 77  |..6V$..[.....B.w|
00000090  db 2f ad 8c fd 84 79 43  3c 2f ec 4f 8d aa 89 0c  |./....yC</.O....|
000000a0  4f e0 ed e2 ae 2a e6 f4  40 d4 e6 e8 b4 75 be 66  |O....*..@....u.f|
000000b0  38 0e a4 7c 57 a4 2b 20  6c 6b 94 ff ac c9 ff fd  |8..|W.+ lk......|
000000c0  84 f7 6e 0f 5e 66 14 97  3c 2e 25 f3 93 9d c7 53  |..n.^f..<.%....S|
000000d0  31 6a 19 53 0d 66 fe 9f  0a 20 f9 aa f9 bd 29 0e  |1j.S.f... ....).|
000000e0  89 c6 06 0c 41 92 b5 54  6e 76 f0 8c dd 4e 72 16  |....A..Tnv...Nr.|
000000f0  42 40 25 67 a0 41 f3 67  f5 fd 6b 0d 60 41 db f4  |B@%g.A.g..k.`A..|
00000100  cb db d7 ea ea 5e e0 29  c0 2c a0 9a 20 3f 1e bb  |.....^.).,.. ?..|
00000110  97 6e 9c f2 6c 1b 89 0c  9f 10 8a 06 3d 4d 33 de  |.n..l.......=M3.|
00000120  e7 11 c7 e2 b4 b7 be fc  53 81 20 a4 1b d5 37 b0  |........S. ...7.|
00000130  04 7b e5 13 d2 f7 4a fc  1d 00 42 10 f1 f1 c7 18  |.{....J...B.....|
00000140  e4 c6 c3 0e 3c bf fe fd  3f 96 b0 ff 0e ae 12 d4  |....<...?.......|
00000150  cf 8e 66 11 c3 3f a5 ff  61 e0 27 00 82 08 8e e0  |..f..?..a.'.....|
00000160  59 30 49 5a 74 42 93 92  64 aa c1 fd 3c 7c c4 42  |Y0IZtB..d...<|.B|
00000170  ce 22 c5 d0 09 89 95 97  cc 2d d6 1f fc 97 79 33  |.".......-....y3|
00000180  4d 77 98 92 8e e0 90 10  68 64 f6 db fc c3 05 2e  |Mw......hd......|
00000190  4f ff db 91 0f b6 b0 36  47 cf 1c 03 5d 2c 17 2d  |O......6G...],.-|
000001a0  f7 03 0f 18 d1 c7 fb 93  e1 70 30 33 82 8b 3d 75  |.........p03..=u|
000001b0  3f be 1e a1 af c2 9c e8  af 82 c0 30 d1 fc 00 fe  |?..........0....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by legendamazing on 2010-11-17
Hello OP here,
No problem, I do not consider this hijacking, but another guy who needs help. I ran the code and here are my results: 
```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 36.4 GB, 36420075520 bytes
255 heads, 63 sectors/track, 4427 cylinders, total 71132960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    68,116,479    68,114,432  83 Linux
/dev/sda2          68,118,526    71,131,135     3,012,610   5 Extended
/dev/sda5          68,118,528    71,131,135     3,012,608  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8a9bacb4-40f7-4a72-818b-906fcdf39cf1   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        919769e4-acb4-474d-a761-b63f3e46faa1   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 8a9bacb4-40f7-4a72-818b-906fcdf39cf1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 8a9bacb4-40f7-4a72-818b-906fcdf39cf1
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8a9bacb4-40f7-4a72-818b-906fcdf39cf1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8a9bacb4-40f7-4a72-818b-906fcdf39cf1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8a9bacb4-40f7-4a72-818b-906fcdf39cf1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8a9bacb4-40f7-4a72-818b-906fcdf39cf1 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8a9bacb4-40f7-4a72-818b-906fcdf39cf1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8a9bacb4-40f7-4a72-818b-906fcdf39cf1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8a9bacb4-40f7-4a72-818b-906fcdf39cf1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=919769e4-acb4-474d-a761-b63f3e46faa1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  19.4GB: boot/grub/core.img
  25.9GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-22-generic
  19.4GB: boot/vmlinuz-2.6.35-22-generic
    .6GB: initrd.img
  19.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  3d dd bc dc bd d9 39 d9  61 d6 db d5 a2 d3 08 d3  |=.....9.a.......|
00000010  66 d1 c2 d0 88 cf ec ce  40 ce 98 cd 6f cd ce cc  |f.......@...o...|
00000020  76 cd cd cc bf cd 1b cd  c3 ce 26 ce fd cf 56 cf  |v.........&...V.|
00000030  c8 d1 36 d1 f7 d3 6c d3  80 d6 f0 d5 29 d9 a0 d8  |..6...l.....)...|
00000040  34 dc a7 db 3d df cd de  b5 e2 3e e2 c0 e5 58 e5  |4...=.....>...X.|
00000050  10 e9 ae e8 60 ec 07 ec  c2 ef 6e ef d0 f2 89 f2  |....`.....n.....|
00000060  f8 f5 bf f5 c9 f8 89 f8  6a fb 27 fb e4 fd ba fd  |........j.'.....|
00000070  e0 ff b5 ff c4 01 a2 01  60 03 47 03 b8 04 99 04  |........`.G.....|
00000080  d6 05 ba 05 b6 06 a3 06  4c 07 37 07 d1 07 c8 07  |........L.7.....|
00000090  f7 07 db 07 0c 08 f3 07  d4 07 c1 07 91 07 82 07  |................|
000000a0  fe 06 ee 06 a0 06 81 06  be 05 97 05 11 05 ef 04  |................|
000000b0  2c 04 13 04 85 03 6c 03  9f 02 83 02 00 02 e0 01  |,.....l.........|
000000c0  2a 01 05 01 32 00 16 00  5c ff 37 ff 58 fe 19 fe  |*...2...\.7.X...|
000000d0  53 fd 21 fd 62 fc 35 fc  0f fb d8 fa af f9 6b f9  |S.!.b.5.......k.|
000000e0  72 f8 33 f8 df f6 ad f6  46 f5 fc f4 c8 f3 7d f3  |r.3.....F.....}.|
000000f0  fb f1 a9 f1 85 f0 34 f0  aa ee 50 ee 06 ed bb ec  |......4...P.....|
00000100  7a eb 1b eb ba e9 5b e9  2a e8 c0 e7 a5 e6 4a e6  |z.....[.*.....J.|
00000110  31 e5 cd e4 d7 e3 76 e3  8c e2 24 e2 58 e1 ef e0  |1.....v...$.X...|
00000120  15 e0 ac df 01 df 8d de  d9 dd 6b dd bf dc 4e dc  |..........k...N.|
00000130  e0 db 63 db 10 db 8c da  86 da 10 da d4 d9 4f d9  |..c...........O.|
00000140  64 d9 d5 d8 39 d9 a9 d8  2d d9 a0 d8 37 d9 bb d8  |d...9...-...7...|
00000150  a4 d9 25 d9 6c da ec d9  2e db af da 89 dc 0e dc  |..%.l...........|
00000160  6f dd f1 dc 04 df 95 de  67 e0 f6 df da e1 64 e1  |o.......g.....d.|
00000170  9d e3 34 e3 4c e5 ea e4  2c e7 bd e6 f0 e8 86 e8  |..4.L...,.......|
00000180  9e ea 44 ea 43 ec ee eb  fc ed a6 ed 76 ef 35 ef  |..D.C.......v.5.|
00000190  10 f1 cf f0 84 f2 43 f2  d8 f3 90 f3 0f f5 d3 f4  |......C.........|
000001a0  30 f6 f4 f5 64 f7 1f f7  87 f8 56 f8 95 f9 5d f9  |0...d.....V...].|
000001b0  b7 fa 84 fa f3 fb b9 fb  ef fc b3 fc 0a fe 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 2d 00 00 00  |............-...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by legendamazing on 2010-11-22
Hello I was hoping that someone could give me a hand? No one has responded, no big deal, but I would appreciate some help. I am just pushing this to the top.
God Bless

---

### Post by legendamazing on 2010-11-22
Hey it's me again. I was just hoping someone would help... please.

---

### Post by legendamazing on 2010-11-22
Hey it is working, I don't know why, but I reset all defaults on the computer and reinstalled, and it worked. Thanks!

---

### Post by Quackers on 2010-11-22
Hi, I'm sorry I've been away mostly as I've had some computer problems myself :-)
I'm glad to see things are now working :-) I suspect you had a dodgy bios setting perhaps.

---

