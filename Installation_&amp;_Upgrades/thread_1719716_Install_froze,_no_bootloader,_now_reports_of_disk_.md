---
title: "Install froze, no bootloader, now reports of disk errors."
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by ferdij on 2011-04-02
My girlfriend decided to be funny by performing an install of Ubuntu over my current install of it so that my data would be gone as part of an April's Fool joke. She tells me that everything was fine until a pop up message came on saying that bootloader could not be installed. She tried to choose all options but got no response and manually shut down the computer. Now when I went in ... I got a SMART prediction of disk failure. Ubuntu won't install either. And I haven't been able to reformat. We are both fairly new at Ubuntu so I have no idea how to fix this. Any ideas?

My hard drive was working fine and had no errors before.

---

### Post by Dutch70 on 2011-04-02
Hi and welcome to the forums

Well, with the info you've given (very few details) it sounds like you may need to back up anything you can manage to save & get yourself a new hard disk. You may also want to check to see if it's still under warranty.

---

### Post by Rubi1200 on 2011-04-02
Hi,
please do the following:

1. stop writing to the disk immediately

2. run the boot info script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ferdij on 2011-04-02
This is what I got:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ? 2,474,048,118 4,165,611,434 1,691,563,317  52 CP/M
/dev/sda2     ?   744,652,280 2,232,708,269 1,488,055,990  7a Unknown
/dev/sda3     ? 3,967,559,097 6,286,311,499 2,318,752,403   b W95 FAT32
/dev/sda4     ? 1,708,036,526 3,774,218,821 2,066,182,296  b4 SpeedStor

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda1 overlaps with /dev/sda3
/dev/sda1 overlaps with /dev/sda4
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda2 overlaps with /dev/sda4
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  07 5d e4 21 65 5c 70 e3  b2 19 b2 0e e4 8d e1 6f  |.].!e\p........o|
00000010  03 d3 be 98 85 0c f5 fa  07 8f 41 64 9c 12 08 c4  |..........Ad....|
00000020  ac f4 49 3e 54 c0 38 c0  ac 18 7e 0d e3 26 ef 20  |..I>T.8...~..&. |
00000030  9c a1 c6 8f ed fb cb d2  34 a4 bb da 2f 62 66 3a  |........4.../bf:|
00000040  1c 89 0f 44 1a 6c 10 95  4f d6 af fa 50 37 0d 61  |...D.l..O...P7.a|
00000050  72 b9 08 9a 12 27 1e 48  20 ec 28 25 b9 ac bb 78  |r....'.H .(%...x|
00000060  6a dd 96 c8 df f4 85 fb  bd 0a 53 5a e5 90 92 a3  |j.........SZ....|
00000070  ac e6 6e b4 5b d5 46 04  ea 55 a6 b8 71 46 2e b4  |..n.[.F..U..qF..|
00000080  09 1c b1 b1 e5 29 44 9e  79 03 fb 0c 39 2c f2 d6  |.....)D.y...9,..|
00000090  75 9f dd 1b 10 06 9b 57  2c 99 bf b3 9a 07 74 fe  |u......W,.....t.|
000000a0  57 20 05 c6 55 ad 4c f3  57 7f 6a c0 1f bc 3a d9  |W ..U.L.W.j...:.|
000000b0  9e 14 88 b1 a7 ce a9 83  d5 d7 d1 45 cb f1 b0 f9  |...........E....|
000000c0  5d 71 4d 49 02 2e 85 6d  99 a1 5b 27 bb cb 9d 05  |]qMI...m..['....|
000000d0  80 f3 86 2e 4b 21 bc e3  1a 3e 1e 39 18 66 4c c4  |....K!...>.9.fL.|
000000e0  ea 7e 62 d0 b1 1f ba a4  fe de 90 1c c1 9b e0 91  |.~b.............|
000000f0  52 c5 3b 75 9e 17 b5 cd  86 24 da 89 59 e2 18 68  |R.;u.....$..Y..h|
00000100  37 3f 2e 26 b5 a9 e8 4c  f3 7d 88 ee a6 03 89 9f  |7?.&...L.}......|
00000110  c8 df d0 95 c8 ce 0c f9  31 c2 94 f2 8e 58 72 8a  |........1....Xr.|
00000120  3d 9c 00 b9 2d f5 82 5e  80 27 06 aa 11 4d 70 51  |=...-..^.'...MpQ|
00000130  ff 30 89 3a 23 02 1a 55  9d 05 6b f8 ed 3f 53 7a  |.0.:#..U..k..?Sz|
00000140  09 ce bc c2 6c 15 03 bd  b6 db b5 42 d0 cf ca 7a  |....l......B...z|
00000150  f0 2a 79 b0 ca f9 d5 54  71 3b 9e 35 32 a1 f9 a8  |.*y....Tq;.52...|
00000160  14 ed f6 59 93 82 ee 53  ef 46 e9 ed cf 7d 35 58  |...Y...S.F...}5X|
00000170  e1 e8 fb 71 3f 47 cf 31  f6 fd ec 51 03 64 fc 87  |...q?G.1...Q.d..|
00000180  1e dc 45 c3 85 1c 22 67  c2 ed 33 9f 59 f0 db dd  |..E..."g..3.Y...|
00000190  1b 75 86 19 95 c6 4f 68  64 8a cb a9 19 fa fa dc  |.u....Ohd.......|
000001a0  83 21 ce 37 65 ea 26 8a  f9 23 97 9b 36 fb ac 74  |.!.7e.&..#..6..t|
000001b0  63 f5 0f d7 d9 14 fc bd  fd 67 a2 03 29 0f 8d 3a  |c........g..)..:|
000001c0  68 aa 52 0c 35 cb 76 fa  76 93 35 35 d3 64 9d af  |h.R.5.v.v.55.d..|
000001d0  b7 51 7a e6 42 e2 f8 7d  62 2c b6 ee b1 58 03 f9  |.Qz.B..}b,...X..|
000001e0  88 8e 0b 83 ec 5c b9 25  7c ec 93 5a 35 8a 2d 33  |.....\.%|..Z5.-3|
000001f0  98 a3 b4 57 11 26 ae 91  ce 65 98 70 27 7b 7f 58  |...W.&...e.p'{.X|
00000200

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
```

---

### Post by Rubi1200 on 2011-04-02
The results do not look good.

Even without knowing much about this, take a look and you will see what I mean.

You could try and recover the partitions with Testdisk, but I wouldn't hold my breath on that one either.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

It is, at least, worth a try.

There is also a program called Photorec which might be able to get some of your data back:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by ferdij on 2011-04-02
Thanks for your quick responses and help. You're right... I couldn't get anything done with the steps you mentioned. The curious part about all this is that my hard drive never had problems before this. 

What I did now.

1. Ran DBAN
2. Installed Ubuntu 10.10

This worked. I was able to boot and get in no problems. I ran that same script you gave me again and got these results:
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
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   600,565,759   600,563,712  83 Linux
/dev/sda2         600,567,806   625,141,759    24,573,954   5 Extended
/dev/sda5         600,567,808   625,141,759    24,573,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        26c74792-d5b9-45eb-9b4e-539df990293b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f6a66ad8-74c7-4669-80b6-fe9ae11dea74   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 26c74792-d5b9-45eb-9b4e-539df990293b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 26c74792-d5b9-45eb-9b4e-539df990293b
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 26c74792-d5b9-45eb-9b4e-539df990293b
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=26c74792-d5b9-45eb-9b4e-539df990293b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 26c74792-d5b9-45eb-9b4e-539df990293b
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=26c74792-d5b9-45eb-9b4e-539df990293b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 26c74792-d5b9-45eb-9b4e-539df990293b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 26c74792-d5b9-45eb-9b4e-539df990293b
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
UUID=26c74792-d5b9-45eb-9b4e-539df990293b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f6a66ad8-74c7-4669-80b6-fe9ae11dea74 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 171.9GB: boot/grub/core.img
 264.3GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.35-28-generic-pae
 171.9GB: boot/vmlinuz-2.6.35-28-generic-pae
    .4GB: initrd.img
 171.9GB: vmlinuz
```

Now the hard drive thing does concern me. Two errors show up:

Reallocated sector count = Assessment: Failing 
Current pending sector count = Assessment: Warning

There was no issues before her trying to install Ubuntu over Ubuntu. I ran S.M.A.R.T. tests continually and never got these reports.

---

### Post by Rubi1200 on 2011-04-02
Okay, well I am glad you managed to reinstall and boot again.

However, the warnings are not good and you should prepare for the worst.

Meantime, I suggest you go to the website of the drive manufacturer and see if they have a diagnostic tool available for checking the drive.

If it confirms what the Disk Utility is reporting about a failing drive, then it might be time to consider purchasing a new one.

---

