---
title: "Just installed on new machine alongside Windows 7, no boot menu"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by kenny99 on 2011-06-09
As the title suggests, I've just installed 11.04 on a new machine, to be dual booted with Windows 7. The installation process completed, popped the disc back out, but when booting up I get no boot menu and just load Windows 7. I don't get any error messages or any sort of feedback. 

If i go into BIOS, I only have Windows 7 as a bootable option.

Can anyone help? I presumed grub or an equivalent would be installed as part of the installation.

---

### Post by Quackers on 2011-06-09
Grub is installed by default to the mbr of /dev/sda (the first hard drive). If that is the hard drive you are booting from it seems that did not happen, for some reason.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kenny99 on 2011-06-09
Hi Quackers. I tried to boot from the live CD, but got a "General error mounting filesystems" message, and am currently in a maintenance shell. I tried to run lshw, but got "cannot open shared object file: no such file or directory". Any thing i should check here?

---

### Post by Quackers on 2011-06-09
Did you change your bios settings to boot from cd/usb first?

---

### Post by kenny99 on 2011-06-09
I didn't change anything in BIOS. Initially, I got the error I mentioned in the previous post, this time i got the Ubuntu loading screen for a couple of minutes before eventually getting a message that there was a problem during installation and that the desktop will be loaded in order to troubleshoot the issue. So I'm at the desktop now. Seems like more than just a grub/boot issue now, do you think?

---

### Post by Quackers on 2011-06-09
Unless your bios is already set to boot from cd or USB first, your system will try to boot from the hard drive. Maybe it is set that way.
So are you now in the Ubuntu live desktop? Connected to the internet? If so please follow what's in post #2

---

### Post by kenny99 on 2011-06-09
No problem, results.txt contents below. Thanks for the help so far

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 707276264 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     24,578,048   249,813,508   225,235,461   7 NTFS / exFAT / HPFS
/dev/sda3         249,815,038   976,771,071   726,956,034   5 Extended
/dev/sda5         249,815,040   968,912,895   719,097,856  83 Linux
/dev/sda6         968,914,944   976,771,071     7,856,128  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CC64F01464F0034E                       ntfs       Win_RE
/dev/sda2        0EA8EF46A8EF2AC3                       ntfs       Windows7
/dev/sda5        5848d63a-f3a0-433b-8245-a9e43fefc13c   ext4       
/dev/sda6        66fdd4bc-a1a5-47ba-8ce1-0db0d708eca4   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set=root 5848d63a-f3a0-433b-8245-a9e43fefc13c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 5848d63a-f3a0-433b-8245-a9e43fefc13c
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
	search --no-floppy --fs-uuid --set=root 5848d63a-f3a0-433b-8245-a9e43fefc13c
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=5848d63a-f3a0-433b-8245-a9e43fefc13c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 5848d63a-f3a0-433b-8245-a9e43fefc13c
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=5848d63a-f3a0-433b-8245-a9e43fefc13c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 5848d63a-f3a0-433b-8245-a9e43fefc13c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 5848d63a-f3a0-433b-8245-a9e43fefc13c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 0EA8EF46A8EF2AC3
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
UUID=5848d63a-f3a0-433b-8245-a9e43fefc13c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=66fdd4bc-a1a5-47ba-8ce1-0db0d708eca4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 337.255630493 = 362.125475840  boot/grub/core.img                             1
 335.258159637 = 359.980707840  boot/grub/grub.cfg                             1
 120.548328400 = 129.437782016  boot/initrd.img-2.6.38-8-generic               2
 337.253910065 = 362.123628544  boot/vmlinuz-2.6.38-8-generic                  1
 120.548328400 = 129.437782016  initrd.img                                     2
 337.253910065 = 362.123628544  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  23 6f c8 1e f3 4a 36 02  cc 01 30 80 2d 82 aa 95  |#o...J6...0.-...|
00000010  55 1c 26 f3 1a 7b 42 56  bb 52 a4 32 4e 9a 9f cf  |U.&..{BV.R.2N...|
00000020  74 31 c0 06 01 12 f1 00  e5 b8 b8 8b 28 6b c5 ae  |t1..........(k..|
00000030  f6 44 aa b6 13 36 6e 04  28 c9 f3 f0 1f 74 77 04  |.D...6n.(....tw.|
00000040  67 52 39 22 57 50 80 16  25 c2 af 4d f4 c4 f5 00  |gR9"WP..%..M....|
00000050  14 01 32 f0 80 83 59 41  e4 d1 2c 29 98 23 eb c4  |..2...YA..,).#..|
00000060  39 c5 32 41 2d 54 8a f0  40 57 b4 c4 71 67 a5 1e  |9.2A-T..@W..qg..|
00000070  06 e0 32 00 16 23 45 12  1f 21 ec 55 83 7a 36 54  |..2..#E..!.U.z6T|
00000080  5e 47 48 07 52 06 04 1f  45 e4 73 0d 1e 1e c1 f7  |^GH.R...E.s.....|
00000090  30 a2 4a a1 65 b5 4b 21  f2 e9 a0 0e 00 ed 3f 33  |0.J.e.K!......?3|
000000a0  73 ea 35 42 50 26 54 f4  2d 20 0f 4b a3 9d 44 ab  |s.5BP&T.- .K..D.|
000000b0  b4 b1 6c 08 5a 75 10 4c  e2 61 43 21 ec 1e a0 02  |..l.Zu.L.aC!....|
000000c0  7a c2 58 02 c0 2c 01 80  18 fd e2 fe 7a a6 16 fc  |z.X..,......z...|
000000d0  af c8 ac 23 91 42 d0 a0  61 61 ed 4f 54 a2 33 c0  |...#.B..aa.OT.3.|
000000e0  04 af e2 5f 33 69 f6 23  f3 fe 9e c2 ac 27 75 30  |..._3i.#.....'u0|
000000f0  33 c8 b2 55 07 54 55 04  f7 49 c4 0e 35 06 86 2c  |3..U.TU..I..5..,|
00000100  c7 b6 39 55 be c6 a3 54  00 cd 3e 51 21 eb 4f 41  |..9U...T..>Q!.OA|
00000110  f8 1e c7 78 00 d4 bc 72  02 80 3c f4 f9 67 41 e8  |...x...r..<..gA.|
00000120  45 4e f0 2b a0 08 52 91  22 fc 94 a3 28 64 a0 1e  |EN.+..R."...(d..|
00000130  82 fe 1f 80 19 5a f4 ba  53 e1 e4 1d f4 de 00 d4  |.....Z..S.......|
00000140  98 28 14 64 1e f5 d0 1f  a3 5e 2c 94 ba 9b 23 6e  |.(.d.....^,...#n|
00000150  1f 02 70 29 16 a3 5d eb  89 38 23 12 53 35 44 9b  |..p)..]..8#.S5D.|
00000160  21 f2 1e 85 29 50 94 f8  ca 62 46 52 86 61 4c 53  |!...)P...bFR.aLS|
00000170  82 59 50 d9 4f 82 56 95  47 22 26 d4 98 31 68 88  |.YP.O.V.G"&..1h.|
00000180  1f a1 ec e9 a7 bd 5a f6  bc a3 22 c1 6a a8 8f 5d  |......Z...".j..]|
00000190  23 0e fe b0 ba 55 b4 94  25 c1 f7 36 02 b2 95 54  |#....U..%..6...T|
000001a0  6a 7e 04 0a 87 ac 24 93  60 14 01 8b 1c 4a 02 41  |j~....$.`....J.A|
000001b0  5f c3 76 2f a3 65 56 0f  c8 79 2d 7e 2a 41 00 fe  |_.v/.eV..y-~*A..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 dc 2a 00 fe  |.............*..|
000001d0  ff ff 05 fe ff ff 02 90  dc 2a 00 e8 77 00 00 00  |.........*..w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Quackers on 2011-06-09
It appears that you have installed grub to sda1 rather than to sda. This is the problem. sda1 appears to be a recovery partition and this is unlikely to boot from grub now. It may still boot from its key press at boot though (but not sure about that).
To install grub to the proper place you should open up a terminal and run these commands, one at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
``` This should report no errors. If that is the case reboot, taking out the live cd/usb and Ubuntu should boot directly. 
If it does, open a terminal and run ```
sudo update-grub
``` when you should see the Windows Loader picked up as grub.cfg is configured. If so, reboot and you should get the grub menu giving you a choice of which system to boot.

---

### Post by kenny99 on 2011-06-09
Ah you are indeed a legend sir. All looks good now, many many thanks :)

---

### Post by Quackers on 2011-06-09
No sir, the work was done by drs305! I just refer everyone to it :-)
Glad it worked.
You're welcome.
Please mark the thread as solved using the Thread Tools near the top of the page.

---

### Post by shahajil on 2011-07-02
```

```                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 570110584 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   464,927,230   461,853,183   7 NTFS / exFAT / HPFS
/dev/sda3         606,904,320   625,141,759    18,237,440  17 Hidden NTFS / HPFS
/dev/sda4         464,928,766   606,904,319   141,975,554   5 Extended
/dev/sda5         464,928,768   598,851,583   133,922,816  83 Linux
/dev/sda6         598,853,632   606,904,319     8,050,688  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        94D0C3EBD0C3D1A2                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sda2        CC822286822274DC                       ntfs       
/dev/sda3        8C6CCC1C6CCC0346                       ntfs       HDDRECOVERY
/dev/sda5        7eb63769-eff6-4ee9-9627-85ae5e3ae1e8   ext4       
/dev/sda6        c3d5b21c-1932-4c29-a51f-7777d97ca93b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set=root 7eb63769-eff6-4ee9-9627-85ae5e3ae1e8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 7eb63769-eff6-4ee9-9627-85ae5e3ae1e8
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    search --no-floppy --fs-uuid --set=root 7eb63769-eff6-4ee9-9627-85ae5e3ae1e8
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7eb63769-eff6-4ee9-9627-85ae5e3ae1e8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 7eb63769-eff6-4ee9-9627-85ae5e3ae1e8
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7eb63769-eff6-4ee9-9627-85ae5e3ae1e8 ro single 
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
    search --no-floppy --fs-uuid --set=root 7eb63769-eff6-4ee9-9627-85ae5e3ae1e8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 7eb63769-eff6-4ee9-9627-85ae5e3ae1e8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root CC822286822274DC
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 8C6CCC1C6CCC0346
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
UUID=7eb63769-eff6-4ee9-9627-85ae5e3ae1e8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c3d5b21c-1932-4c29-a51f-7777d97ca93b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 271.849937439 = 291.896647680  boot/grub/core.img                             1
 237.834377289 = 255.372718080  boot/grub/grub.cfg                             1
 222.148437500 = 238.530068480  boot/initrd.img-2.6.38-8-generic               2
 271.848224640 = 291.894808576  boot/vmlinuz-2.6.38-8-generic                  1
 222.148437500 = 238.530068480  initrd.img                                     2
 271.848224640 = 291.894808576  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  f8 36 78 cf 87 76 b8 a1  68 fc 36 37 6f df 86 ec  |.6x..v..h.67o...|
00000010  ff ad 62 1f e8 27 9b 75  88 17 55 78 26 8c b4 eb  |..b..'.u..Ux&...|
00000020  ca 8e d1 9e 8c e5 31 89  7b a4 fe eb 63 c1 a7 cd  |......1.{...c...|
00000030  e3 07 b2 a5 f8 92 bd 32  de 81 f4 1d f8 2f f1 01  |.......2...../..|
00000040  f5 ac 2d ad c2 39 d9 cd  cb dd 96 c4 26 2e ba 3f  |..-..9......&..?|
00000050  6a 9a 27 ec 8c 1a 51 2d  a7 1d ca 5a a5 cf 6e 8b  |j.'...Q-...Z..n.|
00000060  94 48 bd 23 5d 00 5d 4d  95 dd 03 f9 84 9a 66 7b  |.H.#].]M......f{|
00000070  dd d3 ca 56 74 d0 07 7f  80 2c b5 0e 10 dc 40 b2  |...Vt....,....@.|
00000080  85 8c fe 7d 6b e5 7f 05  52 75 62 f5 44 01 59 a2  |...}k...Rub.D.Y.|
00000090  5f 0f 31 b7 1c ef d4 14  24 b0 64 af 4d 9e cc d9  |_.1.....$.d.M...|
000000a0  3b 05 aa 71 50 e7 29 c3  63 5d 7a c0 31 b4 59 ba  |;..qP.).c]z.1.Y.|
000000b0  9d 9d 2d e2 c8 55 fe 14  a6 e8 19 f8 a1 ff 5f 01  |..-..U........_.|
000000c0  61 0a 8f ff a9 34 05 ab  a5 2a 7b 66 5b b1 78 59  |a....4...*{f[.xY|
000000d0  fe 17 37 fc 36 b5 85 34  39 f0 4a 12 64 fe 0d eb  |..7.6..49.J.d...|
000000e0  b7 24 3e 73 f4 71 99 74  86 7d 48 c1 79 4f e0 3f  |.$>s.q.t.}H.yO.?|
000000f0  11 1e 0b 4c e7 60 d8 94  06 5e 97 11 ae a8 55 ee  |...L.`...^....U.|
00000100  03 32 07 b5 32 cf d1 5e  a8 60 b4 81 55 8a dc 59  |.2..2..^.`..U..Y|
00000110  00 00 54 fd 30 b0 88 b9  45 e0 12 c9 ab 60 f2 76  |..T.0...E....`.v|
00000120  a1 22 f5 8c 56 20 4d 28  a9 8e 92 1e 0b 7a 1a c2  |."..V M(.....z..|
00000130  cb 9d 8a f3 18 fd 53 d0  b8 2f 13 b6 5b fe ec 51  |......S../..[..Q|
00000140  6a 49 d1 e2 74 8a f4 4c  d5 2a 0b 4c 80 dd 8d 5f  |jI..t..L.*.L..._|
00000150  e1 56 e0 5a 42 72 a5 a0  3f cf 9a bf 9a c7 62 ea  |.V.ZBr..?.....b.|
00000160  c2 27 d6 90 73 21 d9 55  03 1e a0 e0 cc 3f c2 69  |.'..s!.U.....?.i|
00000170  ea 20 ed 5f d4 17 f2 34  51 d4 13 b0 61 11 55 26  |. ._...4Q...a.U&|
00000180  f7 3a 43 b6 f3 aa 3e 1d  eb 0e 70 5c 2a a8 e4 15  |.:C...>...p\*...|
00000190  e5 26 f2 cd 28 b7 51 de  7c 2f f2 83 dd 83 24 72  |.&..(.Q.|/....$r|
000001a0  63 d2 2f ec c3 e6 79 07  fe 0f 14 4e 3e cd a9 00  |c./...y....N>...|
000001b0  9a 26 60 5b 1e 9a 86 69  70 fd 57 fc e2 29 00 fe  |.&`[...ip.W..)..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 fb 07 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  fb 07 00 e0 7a 00 00 00  |............z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

```









pls help me with this .. i have the same problem ...thank u in advance .. m a new user of ubuntu

---

### Post by shahajil on 2011-07-02
pls help me .. i have the same problem .. i have posted result file. pls tell me wat shu d do . m a new user of ubuntu .. :)

---

### Post by Quackers on 2011-07-02
Grub has been installed to sda1 whereas it should have been installed to the mbr of the hard drive (sda).
If you boot from the Ubuntu live cd/usb and select "try Ubuntu" then open up a terminal you can copy/paste these two commands into the terminal, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
``` Which should report "Finished. No errors".
If it does you can reboot and you should then see Ubuntu boot directly. If it does, open up a terminal in your new Ubuntu system and run ```
sudo update-grub
``` and you should see the Windows Loader picked up as grub.cfg is run.
If you do, reboot and you should see a grub menu which will give you the choice of which operating system to boot.

If sda1 is a recovery partition, it may not work now because grub has been installed there.
If you can make a set of recovery dvd's from within Windows I would recommend that you do so - if you haven't done that already.

---

