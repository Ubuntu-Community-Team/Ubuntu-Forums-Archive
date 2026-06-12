---
title: "Can i get my vista back after ubuntu 10.10 is installed?"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by jacarandansw on 2011-04-01
hello friends 
i had Windows Vista Ultimate SP2 
160 GB HDD, 1GB RAM,INTEL DUAL CORE 
One of my friend told that UBUNTU is also a better OS and is an open source programme and u can use alternately both Ubuntu or VISTA,so i downloaded the disk image for Ubuntu 10.10 and burned it on a CD. i played it first on Windows Vista so it asked some 3 options of that i chose an option which downloaded Ubuntu Cd helper ,then i selected the first option something 'demo and install' it said to reboot the computer i reboooted it by selecting option reboot now and finishing it,after the computer was restarted.it asked me options for selecting Ubuntu or Windows Vista,i selected Ubuntu, i saw ubuntu is started which was the least time i could see a new Os is started, then i tought i should install it ,after selecting install it ,there came an option to drag option window's vertical line to right or left to increase or decrease the partition for ubuntu and on another side where something 'NTFS' was written i thought it must be for windows i dragged Ubuntu to maximum(5.23GB) left 37.3 GB for NTFS dev and i continued forward, left it for some process going on, the ubuntu was installed i think ,it also asked for some softwares to be installed i let them be installed and let all process finish after looking some featuers of Ubuntu ,i wanted to go back to windows vista but when i restarted computer it didnt asked me an option for selecting OS 'Ubuntu' or 'Vista' as it had asked me before. it directly started Ubuntu and asked for same options of software to installed ,i removed th CD and Tried again but still i couldnt see anything for Vista,when i checked properties of 'File System' it was written that 2.3 GB is covered and rest 157 GB is free,i m scared that i have deleted all the data of VIsta and Vista OS too,Can i get my VISTA BACK?,it is ok if i dont get anything of Ubuntu,i had many of important files too in my vista.is really my pc been formatted completely,? 
from last week i m searching for its solution on internet i m frustrated a lot, many of the contain particular solution but for before versions of Ubuntu,i just want My vista and vista files back .One of the solutions also contained inserting DVD of vista and some procedure but my DVD player isnt working but CD player is working.i hope some of my inernet friends come to me as a saviour please. 
and one note i don't know what is GRUB or all other stuffs as i m knowing very bit of installing OS

---

### Post by Thund3rstruck on 2011-04-01
I'll do my best to make sense on this jumbled mess of a comment :).

Open the terminal and run the command:

```

sudo fdisk -l

```

There should be a line that says NTFS: (something like this)
```

/dev/sda1   *           1        9729    78145494    7  HPFS/NTFS

```

Which indicates that I have a 75GB Windows partition on device /dev/sda1. 

If you don't see any NTFS/FAT32 partitions in your partition list then yea, Vista is gone. 

Not to preach here but installing an Operating System is major surgery and it should be done first on virtual machines or spare computers lying around; not on your primary production system. 

Live and learn :)

---

### Post by Quackers on 2011-04-01
In Ubuntu, open up a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run. Is a Windows Loader found? If so reboot and you should get a grub menu this time.
If the Windows loader is not found please  go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by jacarandansw on 2011-04-15
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055a04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37419008   83  Linux
/dev/sda2            4659        4864     1648641    5  Extended
/dev/sda5            4659        4864     1648640   82  Linux swap / Solaris
jimmylee@jimmylee-A3L:~$ 


hi there, what does this mean? sorry about the late reply. 
busy on work. does the above message mean i lost my Windows?

---

### Post by Grenage on 2011-04-15
> **jacarandansw said:**
> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055a04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37419008   83  Linux
/dev/sda2            4659        4864     1648641    5  Extended
/dev/sda5            4659        4864     1648640   82  Linux swap / Solaris
jimmylee@jimmylee-A3L:~$ 


hi there, what does this mean? sorry about the late reply. 
busy on work. does the above message mean i lost my Windows?

That means that Vista is gone; unfortunately.

---

### Post by jacarandansw on 2011-04-15
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

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,840,063    74,838,016  83 Linux
/dev/sda2          74,842,110    78,139,391     3,297,282   5 Extended
/dev/sda5          74,842,112    78,139,391     3,297,280  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1ac6a640-69c0-4597-9f03-ea2ea3c62eac   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8e422bb5-d50b-45a0-af1f-f22058b8bef4   swap                                     
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
search --no-floppy --fs-uuid --set 1ac6a640-69c0-4597-9f03-ea2ea3c62eac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 1ac6a640-69c0-4597-9f03-ea2ea3c62eac
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
    search --no-floppy --fs-uuid --set 1ac6a640-69c0-4597-9f03-ea2ea3c62eac
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=1ac6a640-69c0-4597-9f03-ea2ea3c62eac ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1ac6a640-69c0-4597-9f03-ea2ea3c62eac
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=1ac6a640-69c0-4597-9f03-ea2ea3c62eac ro single  splash
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
    search --no-floppy --fs-uuid --set 1ac6a640-69c0-4597-9f03-ea2ea3c62eac
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1ac6a640-69c0-4597-9f03-ea2ea3c62eac
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
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/core.img
  11.0GB: boot/grub/grub.cfg
  11.4GB: boot/initrd.img-2.6.35-28-generic-pae
   2.4GB: boot/vmlinuz-2.6.35-28-generic-pae
  11.4GB: initrd.img
   2.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  30 2e ee c9 0d 89 93 d6  c0 97 41 d8 43 db 8f 3e  |0.........A.C..>|
00000010  f8 ba e8 44 fa b4 d0 d8  3e 17 f0 80 72 96 82 c8  |...D....>...r...|
00000020  fb d6 cc 82 13 dd c6 03  5e 95 89 86 40 53 a0 98  |........^...@S..|
00000030  c6 0e 0f 48 79 bf 92 ed  8c e3 71 d5 27 1f 28 1e  |...Hy.....q.'.(.|
00000040  2f 2e bb 63 79 15 46 fe  f8 3f dc c3 2a 09 c1 0e  |/..cy.F..?..*...|
00000050  95 09 b1 28 1b 66 78 0f  78 7a 8f 10 f1 e3 a5 76  |...(.fx.xz.....v|
00000060  4d ed 20 f6 fe 63 aa ab  07 d9 4c 64 c7 0c c9 84  |M. ..c....Ld....|
00000070  19 e1 fd 92 28 97 59 d7  80 78 f8 4a 06 cb 53 b2  |....(.Y..x.J..S.|
00000080  b2 2a 39 1a 89 34 7f 9c  97 eb 1a 2f 53 f3 74 e8  |.*9..4...../S.t.|
00000090  14 f1 21 11 98 f8 18 7e  5c 25 c2 f8 25 8f bb 15  |..!....~\%..%...|
000000a0  cc f8 f1 90 2b 9a 7b 73  f3 77 76 76 3f bb a7 cb  |....+.{s.wvv?...|
000000b0  a7 ac b2 48 07 22 16 f3  b5 93 76 58 cf a5 74 fc  |...H."....vX..t.|
000000c0  b8 3a fe 3c 29 a8 50 58  d8 9c fa 50 25 5b 39 64  |.:.<).PX...P%[9d|
000000d0  e1 2c e9 00 29 fd 94 9d  7a 49 7b 8e 79 30 51 12  |.,..)...zI{.y0Q.|
000000e0  ee 19 39 72 ec 76 3b 5e  0a 31 2e bb cb d8 f2 fd  |..9r.v;^.1......|
000000f0  f8 21 4a ae 73 d6 c8 ae  77 2d 85 55 cf 3c de 75  |.!J.s...w-.U.<.u|
00000100  8c 50 49 92 f3 07 09 03  21 5a 59 83 dc c5 d2 34  |.PI.....!ZY....4|
00000110  49 99 f1 dc ef 9e e2 7b  b4 f9 27 ae 91 0e 9e c5  |I......{..'.....|
00000120  92 87 21 6a 98 23 32 52  34 4a 03 54 d9 4b 4c 82  |..!j.#2R4J.T.KL.|
00000130  cd 85 e1 e0 a4 c9 46 ab  24 80 ed 47 48 42 33 02  |......F.$..GHB3.|
00000140  1e 88 17 38 40 6e 1e 63  29 e1 6f 40 6a ba 70 4c  |...8@n.c).o@j.pL|
00000150  5c e8 2b f5 bb 8f 87 a7  88 9e df dd 35 f9 83 bf  |\.+.........5...|
00000160  f7 62 8e 4a 86 a2 b1 a8  44 a6 e4 91 91 ec e2 d2  |.b.J....D.......|
00000170  af 0a 0c 85 3e b7 a9 50  9f 4f 98 d1 6d 75 6a be  |....>..P.O..muj.|
00000180  59 dd 4a 11 b6 42 03 93  ca 31 9e 54 74 4d 8b 12  |Y.J..B...1.TtM..|
00000190  62 1c e8 b8 a1 2a 1e 23  17 a7 af d3 db 84 2c eb  |b....*.#......,.|
000001a0  2c 9f 1a 25 c1 c8 86 92  23 70 d5 26 92 11 69 c5  |,..%....#p.&..i.|
000001b0  93 d2 c3 c9 ec 69 53 23  09 8d 44 f1 e9 99 00 fe  |.....iS#..D.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Rasa1111 on 2011-04-16
Yep, No windows OS in there. 
Im sorry you lost your data. :(
I have lost all my data to once before, and it's not fun. 
I feel for you. 

 Maybe it is a blessing in disguise though! lol
Have you been using the ubuntu thats installed?
If so, how do you like it?

Good luck. <3

---

### Post by jacarandansw on 2011-04-28
i didn't use it much. but the interface is good. not quite familiar with the system, it's a bit different from windows. don't like it for some aspect. firstly, when new user try to install ubuntu, it should provide a better protection for the existing system, like windows 7 does. the installation procedure is a bit confused. it seems like it was protecting the existing system, but actually, it does not. it delete all my old system without get my permission. i think ubuntu team should think about this, otherwise it won't attract more users, and it is not a successful product.

> **Rasa1111 said:**
> Yep, No windows OS in there. 
Im sorry you lost your data. :(
I have lost all my data to once before, and it's not fun. 
I feel for you. 

 Maybe it is a blessing in disguise though! lol
Have you been using the ubuntu thats installed?
If so, how do you like it?

Good luck. <3

---

### Post by Mark Phelps on 2011-04-28
> **jacarandansw said:**
> i think ubuntu team should think about this, otherwise it won't attract more users, and it is not a successful product.

Several folks have notified CANONICAL about this serious flaw in their new installer -- but they have yet (as far as I know) to pay any attention to our concerns.  Evidently, they are too busy using new desktop interfaces and integrating Cloud Computing.

---

