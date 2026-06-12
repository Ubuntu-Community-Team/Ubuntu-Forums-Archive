---
title: "Dual Boot Option gone"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by chew725 on 2011-01-21
Hello

I'm new to this, but yesterday I installed Ubuntu on my laptop for a class. I already have Windows 7 on my computer, and would like to keep that operating system as well. I have installed Ubuntu in the past with no problem, and was able to have a dual boot option. When I restarted my computer yesterday, however, the default setting I guess sent me straight to Ubuntu. I'm pretty nervous since EVERYTHING is on Windows 7 and I really need that stuff. 

I tried pressing ESC during the startup, but I couldn't find anything in there to make a dual boot option. After looking a bit online for help, I put startupmanager in and tried to make the bootloader menu come up. This also did not work. First, I tried getting to startupmanager through System... and it was missing the option to enable the bootloader menu. Getting a bit frantic, I tried just typing startupmanager into a terminal, and this is what I got: 

heather@heather-HP-G62-Notebook-PC:~$ startupmanager
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Grub2 detected
Usplash not detected
Splashy not detected
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)


It was my understand that Usplash and Splashy should already be there with Ubuntu?

Finally, I saw another suggestion to press SHIFT during the startup, and that did not give me any menus either...

I would greatly appreciate any help.

---

### Post by Quackers on 2011-01-21
From your Ubuntu desktop, open up a terminal and run
```
sudo update-grub
``` then watch as grub.cfg is run, to see if the Windows Loader is picked up. If it is, reboot and try booting Windows from the grub menu.

---

### Post by Rubi1200 on 2011-01-21
Hi and welcome to the forums chew725 :)

If the advice posted by Quackers does not help, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by chew725 on 2011-01-21
Thanks...I tried Quackers advice, and windows wasn't so I'm trying your way, Rubi1200. I'm pretty new to this stuff so here's a pretty dumb question...if Ubuntu is already installed on my hard disk, how can I run  Ubuntu Live CD/USB, and where can I choose the option "Try Ubuntu without any changes."?

Thanks

---

### Post by Rubi1200 on 2011-01-21
You can run a LiveCD no matter what is installed to the hard-drive. In BIOS, set the boot priority so that you can use the CD/DVD drive as first device.

BIOS can be accessed via F2, F12, Esc, Del etc. (depends on the make/model of computer). There should be a screen there called Boot (or similar) where you can change device priority.

When you put the CD in it should start Ubuntu and you can choose the option to try not install.

After that, follow the instructions I posted.

---

### Post by drs305 on 2011-01-21
Insert the LiveCD, make sure your BIOS is set to boot from the CD first, and it will boot to the "Try/Install" selection screen. Click on "Try Ubuntu" and it will take you to the Desktop, where you can open Firefox to download the script and a terminal (Applications, Accessories, Terminal) to run it.

---

### Post by chew725 on 2011-01-21
Ok I think I did it right...here is the RESULTS.txt file 

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   952,197,119   952,195,072  83 Linux
/dev/sda2         952,199,166   976,771,071    24,571,906   5 Extended
/dev/sda5         952,199,168   976,771,071    24,571,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        be51c960-6a83-42d2-8768-5777089d9c16   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d40ebb54-c1ba-45c2-bf24-7b29be706ad0   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


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
search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=be51c960-6a83-42d2-8768-5777089d9c16 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=be51c960-6a83-42d2-8768-5777089d9c16 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=be51c960-6a83-42d2-8768-5777089d9c16 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=be51c960-6a83-42d2-8768-5777089d9c16 ro single  splash
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
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d40ebb54-c1ba-45c2-bf24-7b29be706ad0 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 317.9GB: boot/grub/core.img
 476.9GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
    .8GB: boot/initrd.img-2.6.35-24-generic
 317.9GB: boot/vmlinuz-2.6.35-22-generic
 317.9GB: boot/vmlinuz-2.6.35-24-generic
    .8GB: initrd.img
    .8GB: initrd.img.old
 317.9GB: vmlinuz
 317.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2b 2a cc 0b 9b 46 9d 0d  99 59 47 9e 7e 0a 32 f1  |+*...F...YG.~.2.|
00000010  71 94 18 1d 2b 4d 70 28  43 bc b0 a0 3e 82 74 91  |q...+Mp(C...>.t.|
00000020  f8 77 29 d3 8d 45 fe c0  d2 51 16 07 07 1d d2 d0  |.w)..E...Q......|
00000030  7b 79 48 ff 81 50 d5 ea  10 0a 18 0d 0d 9e 69 2e  |{yH..P........i.|
00000040  64 58 cf 9b d7 54 c3 7b  50 21 fb 92 ff ac 41 81  |dX...T.{P!....A.|
00000050  8d 13 1a 62 d9 04 a2 03  8c 9b 55 0d 12 fd 99 83  |...b......U.....|
00000060  21 9c d0 a8 43 c0 01 43  23 75 d3 05 ea 17 82 d4  |!...C..C#u......|
00000070  bc 14 18 f2 89 ba f6 ff  63 00 58 e8 f9 76 0d 02  |........c.X..v..|
00000080  78 32 a0 a8 85 01 4c 69  bc 9b 6f 16 ee 37 e3 01  |x2....Li..o..7..|
00000090  ea a6 84 3a 34 4e 2e a3  0e f4 68 80 2a 04 89 80  |...:4N....h.*...|
000000a0  1c d1 f4 41 0f b9 47 27  e9 15 85 91 f0 b0 9a 41  |...A..G'.......A|
000000b0  85 2b 44 44 bc 6f b5 15  df db c8 c7 91 c7 3a 3b  |.+DD.o........:;|
000000c0  0c 1a 5c c0 40 a5 1a f1  a0 b3 f9 d7 0b 85 0f 41  |..\.@..........A|
000000d0  a0 f8 70 48 49 c7 1a 71  a5 be 41 a8 0f 42 37 4c  |..pHI..q..A..B7L|
000000e0  74 a2 72 96 02 a0 86 09  04 66 8c 3b 21 e2 44 05  |t.r......f.;!.D.|
000000f0  f0 25 f7 0c dd 55 42 21  84 51 d0 f2 f5 ec 42 bd  |.%...UB!.Q....B.|
00000100  0e 49 1d 4f 9a 61 3d 50  0c fd 57 41 66 ac 07 16  |.I.O.a=P..WAf...|
00000110  f0 c4 cf 24 b4 e2 50 ae  ac d0 c8 32 da 04 1f f0  |...$..P....2....|
00000120  46 7e 9f d1 d7 41 50 68  48 73 da d0 04 fb 05 58  |F~...APhHs.....X|
00000130  68 f0 b2 05 bb 1e 21 8d  03 62 9e 15 aa 43 85 46  |h.....!..b...C.F|
00000140  68 fb 05 46 dc 0a e1 0c  05 37 7b 96 04 c9 e0 75  |h..F.....7{....u|
00000150  21 a8 f8 fc 90 c2 85 83  57 75 35 5c c3 1c 93 85  |!.......Wu5\....|
00000160  e6 9d 02 c1 af 43 92 ef  95 a1 51 c8 e5 05 83 6d  |.....C....Q....m|
00000170  f6 20 3d 88 03 a1 e3 ed  cc f6 7a 23 33 1c 40 08  |. =.......z#3.@.|
00000180  e8 f3 73 0d 14 1a 24 1d  09 a4 45 98 44 a9 a1 23  |..s...$...E.D..#|
00000190  11 dc 0a 11 93 e5 84 9a  d4 5a 33 b5 3d 24 03 d7  |.........Z3.=$..|
000001a0  e1 b3 d9 4e 94 8e 6b 9f  5b a4 dc 35 28 23 c3 56  |...N..k.[..5(#.V|
000001b0  a3 3e 27 71 c0 28 00 e8  f6 fe b8 89 f2 51 00 fe  |.>'q.(.......Q..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 76 01 00 00  |............v...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 



```

---

### Post by chew725 on 2011-01-21
Wait don't look at the file I just posted...its wrong...I'm almost done with the right one

---

### Post by chew725 on 2011-01-21
Ok this is the correct file:

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   952,197,119   952,195,072  83 Linux
/dev/sda2         952,199,166   976,771,071    24,571,906   5 Extended
/dev/sda5         952,199,168   976,771,071    24,571,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        be51c960-6a83-42d2-8768-5777089d9c16   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d40ebb54-c1ba-45c2-bf24-7b29be706ad0   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

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
search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=be51c960-6a83-42d2-8768-5777089d9c16 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=be51c960-6a83-42d2-8768-5777089d9c16 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=be51c960-6a83-42d2-8768-5777089d9c16 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=be51c960-6a83-42d2-8768-5777089d9c16 ro single  splash
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
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be51c960-6a83-42d2-8768-5777089d9c16
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d40ebb54-c1ba-45c2-bf24-7b29be706ad0 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 317.9GB: boot/grub/core.img
 476.9GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
    .8GB: boot/initrd.img-2.6.35-24-generic
 317.9GB: boot/vmlinuz-2.6.35-22-generic
 317.9GB: boot/vmlinuz-2.6.35-24-generic
    .8GB: initrd.img
    .8GB: initrd.img.old
 317.9GB: vmlinuz
 317.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2b 2a cc 0b 9b 46 9d 0d  99 59 47 9e 7e 0a 32 f1  |+*...F...YG.~.2.|
00000010  71 94 18 1d 2b 4d 70 28  43 bc b0 a0 3e 82 74 91  |q...+Mp(C...>.t.|
00000020  f8 77 29 d3 8d 45 fe c0  d2 51 16 07 07 1d d2 d0  |.w)..E...Q......|
00000030  7b 79 48 ff 81 50 d5 ea  10 0a 18 0d 0d 9e 69 2e  |{yH..P........i.|
00000040  64 58 cf 9b d7 54 c3 7b  50 21 fb 92 ff ac 41 81  |dX...T.{P!....A.|
00000050  8d 13 1a 62 d9 04 a2 03  8c 9b 55 0d 12 fd 99 83  |...b......U.....|
00000060  21 9c d0 a8 43 c0 01 43  23 75 d3 05 ea 17 82 d4  |!...C..C#u......|
00000070  bc 14 18 f2 89 ba f6 ff  63 00 58 e8 f9 76 0d 02  |........c.X..v..|
00000080  78 32 a0 a8 85 01 4c 69  bc 9b 6f 16 ee 37 e3 01  |x2....Li..o..7..|
00000090  ea a6 84 3a 34 4e 2e a3  0e f4 68 80 2a 04 89 80  |...:4N....h.*...|
000000a0  1c d1 f4 41 0f b9 47 27  e9 15 85 91 f0 b0 9a 41  |...A..G'.......A|
000000b0  85 2b 44 44 bc 6f b5 15  df db c8 c7 91 c7 3a 3b  |.+DD.o........:;|
000000c0  0c 1a 5c c0 40 a5 1a f1  a0 b3 f9 d7 0b 85 0f 41  |..\.@..........A|
000000d0  a0 f8 70 48 49 c7 1a 71  a5 be 41 a8 0f 42 37 4c  |..pHI..q..A..B7L|
000000e0  74 a2 72 96 02 a0 86 09  04 66 8c 3b 21 e2 44 05  |t.r......f.;!.D.|
000000f0  f0 25 f7 0c dd 55 42 21  84 51 d0 f2 f5 ec 42 bd  |.%...UB!.Q....B.|
00000100  0e 49 1d 4f 9a 61 3d 50  0c fd 57 41 66 ac 07 16  |.I.O.a=P..WAf...|
00000110  f0 c4 cf 24 b4 e2 50 ae  ac d0 c8 32 da 04 1f f0  |...$..P....2....|
00000120  46 7e 9f d1 d7 41 50 68  48 73 da d0 04 fb 05 58  |F~...APhHs.....X|
00000130  68 f0 b2 05 bb 1e 21 8d  03 62 9e 15 aa 43 85 46  |h.....!..b...C.F|
00000140  68 fb 05 46 dc 0a e1 0c  05 37 7b 96 04 c9 e0 75  |h..F.....7{....u|
00000150  21 a8 f8 fc 90 c2 85 83  57 75 35 5c c3 1c 93 85  |!.......Wu5\....|
00000160  e6 9d 02 c1 af 43 92 ef  95 a1 51 c8 e5 05 83 6d  |.....C....Q....m|
00000170  f6 20 3d 88 03 a1 e3 ed  cc f6 7a 23 33 1c 40 08  |. =.......z#3.@.|
00000180  e8 f3 73 0d 14 1a 24 1d  09 a4 45 98 44 a9 a1 23  |..s...$...E.D..#|
00000190  11 dc 0a 11 93 e5 84 9a  d4 5a 33 b5 3d 24 03 d7  |.........Z3.=$..|
000001a0  e1 b3 d9 4e 94 8e 6b 9f  5b a4 dc 35 28 23 c3 56  |...N..k.[..5(#.V|
000001b0  a3 3e 27 71 c0 28 00 e8  f6 fe b8 89 f2 51 00 fe  |.>'q.(.......Q..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 76 01 00 00  |............v...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb
```

---

### Post by drs305 on 2011-01-21
The RESULTS.txt shows only Ubuntu, which means that it either overwrote Windows or you have another drive that is not connected or recognized.

If the former, don't write anything further on the drive, as you will have to try to recover files using data recovery tools. 

You can tell us how you installed Ubuntu but it doesn't really matter unless you have two drives. There are apps such as TestDisk that can help you explore your drive and possibly recover files. I'm not a data recovery expert but perhaps I'm getting ahead of the situation...

---

### Post by Quackers on 2011-01-21
Are you sitting down?
It appears that Ubuntu has over-written your Windows installation.
When using the installer, did you choose the "install alongside" option? Unfortunately many people have had their operating systems over-written using that option. It is a fault that has been logged at Launchpad and some changes are on the way. Sadly, that doesn't do a lot for you, I'm sure.
It may be possible to get some files back using testdisk/PhotoRec from the live cd desktop. Sorry for this bad news.

---

### Post by chew725 on 2011-01-21
I did use that option as it has worked in the past...this is so bad...
I will try to use TestDisk to try to get some stuff back I guess if possible...any suggestions?

---

### Post by Quackers on 2011-01-21
Here is one link. There are other guides available, some quite detailed. Good luck!
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by drs305 on 2011-01-21
Herman's Test Disk page has information and a lot of links:
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")

PhotoRec is not easy to use. If you can get to the 'green' line and press 'p' at the correct point in the following link you can view and copy files from Test Disk. It is probably much easier than PhotoRec.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

You have to enable the *universe* repository to install TestDisk if you are using the LiveCD, which I'd recommend so you don't write to the drive. And if you can get to the point where you can copy files, try to copy them to another device if possible to make sure you don't overwrite any other data on the (former) Windows partition.

---

