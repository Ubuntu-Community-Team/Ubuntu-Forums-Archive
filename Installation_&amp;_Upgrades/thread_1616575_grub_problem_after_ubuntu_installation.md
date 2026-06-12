---
title: "grub problem after ubuntu installation"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by danae72 on 2010-11-08
Hi, I just reinstalled ubuntu but kept my 2 windows partitions intact. The installation went fine, except that upon the restart, the computer doesnt boot anymore - i get a grub error 15 message. I cannot boot neither windows nor ubuntu. I have tried installing again, but the problem remains. I am running a live cd ubuntu now. Can someone help me? I am an absolute beginner at linux.

---

### Post by thegod_slayer on 2010-11-08
first of all, welcome to this forum and welcome to ubuntu.

i think you should read this first.

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

first do some theory research on ubuntu or linux and then try it.
it will seem a whole lot easy.

---

### Post by kansasnoob on 2010-11-08
> **danae72 said:**
> Hi, I just reinstalled ubuntu but kept my 2 windows partitions intact. The installation went fine, except that upon the restart, the computer doesnt boot anymore - i get a grub error 15 message. I cannot boot neither windows nor ubuntu. I have tried installing again, but the problem remains. I am running a live cd ubuntu now. Can someone help me? I am an absolute beginner at linux.

Please use the Live CD and post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by danae72 on 2010-11-08
Here are the results.               

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    14,153,727    14,151,680  27 Hidden HPFS/NTFS
/dev/sda2    *     14,153,728   292,098,047   277,944,320   7 HPFS/NTFS
/dev/sda3         292,103,341   312,575,759    20,472,419   5 Extended
/dev/sda5         292,103,343   311,608,079    19,504,737  83 Linux
/dev/sda6         311,608,143   312,575,759       967,617  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4089 MB, 4089445376 bytes
33 heads, 63 sectors/track, 3841 cylinders, total 7987198 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,987,197     7,987,166   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A046B17E46B155AE                       ntfs       ServiceV002                   
/dev/sda2        6434409E34407558                       ntfs       SW_Preload                    
/dev/sda3: PTTYPE="dos" 
/dev/sda5        41a95586-e451-4883-a3e5-2f0cad9079e1   ext2                                     
/dev/sda6        4e1fa3fc-4935-49b8-8c3f-5689b33bd33f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7850-9E62                              vfat       USB                           
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 41a95586-e451-4883-a3e5-2f0cad9079e1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 41a95586-e451-4883-a3e5-2f0cad9079e1
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41a95586-e451-4883-a3e5-2f0cad9079e1
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41a95586-e451-4883-a3e5-2f0cad9079e1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
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
    search --no-floppy --fs-uuid --set 41a95586-e451-4883-a3e5-2f0cad9079e1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41a95586-e451-4883-a3e5-2f0cad9079e1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a046b17e46b155ae
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6434409e34407558
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
UUID=41a95586-e451-4883-a3e5-2f0cad9079e1 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4e1fa3fc-4935-49b8-8c3f-5689b33bd33f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/core.img
 154.7GB: boot/grub/grub.cfg
 154.4GB: boot/initrd.img-2.6.35-22-generic
 154.4GB: boot/vmlinuz-2.6.35-22-generic
 154.4GB: initrd.img
 154.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  13 01 cf 3e 23 2e d3 e0  ef 30 dd f1 f2 d1 2f 02  |...>#....0..../.|
00000010  42 1f 21 23 2f f3 b0 d0  0f ed 02 f0 1f 3f 03 10  |B.!#/........?..|
00000020  00 1f 24 2f d0 0d d3 e0  ee 10 6d 41 d4 f2 20 de  |..$/......mA.. .|
00000030  f0 25 11 b1 dc 70 4f 1a  11 4f c2 d3 25 3f 1f d5  |.%...pO..O..%?..|
00000040  23 1f ff f1 0e 1e f1 e1  0e ff 26 e2 1d 53 2f 24  |#.........&..S/$|
00000050  ee ff 0b fc d0 a2 f3 2a  03 44 fd 21 33 ef 24 3f  |.......*.D.!3.$?|
00000060  f3 0e 11 de ff 2c f9 02  eb 11 35 e1 44 24 63 e2  |.....,....5.D$c.|
00000070  10 00 db 1d ee fe e3 ee  23 f2 0e 44 24 d0 0f 32  |........#..D$..2|
00000080  ee 30 f0 f1 d1 eb e1 00  12 a3 50 24 50 f0 14 ef  |.0........P$P...|
00000090  2d 1e f2 d4 dd 10 01 e0  f1 20 23 01 00 00 2e 0f  |-........ #.....|
000000a0  0f e1 ff 0d 15 d4 1d 5f  30 24 2f b0 0d 2c cf d2  |......._0$/..,..|
000000b0  f0 2d 10 14 01 f0 13 1f  23 20 e2 f2 f0 fe 2f ff  |.-......# ..../.|
000000c0  0e f1 e0 fe 0e 26 d2 23  3c 66 00 e1 f2 fb 0f fc  |.....&.#<f......|
000000d0  f0 02 ed 13 12 e1 24 25  f1 2f 2f 0e 10 0e e0 f0  |......$%.//.....|
000000e0  1a e3 c3 c0 21 24 1e 24  4f 01 34 fc 11 0d ef 1f  |....!$.$O.4.....|
000000f0  cf f2 2e f0 33 ed fd e0  e0 1f 01 2f 10 10 0e ee  |....3....../....|
00000100  1f c0 d0 24 31 2f e0 e0  1f 1c 01 01 30 d0 20 20  |...$1/......0.  |
00000110  ee 11 13 00 01 00 00 11  1f ff ff 0d ed de cf ff  |................|
00000120  50 24 25 26 0e d2 3d cf  e1 cf f1 3c 0e 34 0f e2  |P$%&..=....<.4..|
00000130  24 f3 1d 4f f2 1e 50 d0  0e 4f bf d1 df cf c6 24  |$..O..P..O.....$|
00000140  1f 6d 51 64 f3 f0 1e 0d  f0 92 ef 0d 0f 11 24 10  |.mQd..........$.|
00000150  f3 f3 20 01 1f 2e 2d 1e  e0 2f d0 0e 4e 14 b4 01  |.. ...-../..N...|
00000160  ff 42 41 e2 23 11 20 2f  12 f2 ed ee 25 3d 1c 15  |.BA.#. /....%=..|
00000170  02 d4 b6 1a 6e f0 d0 4e  cd ed bf 24 20 50 b3 34  |....n..N...$ P.4|
00000180  5d ee 4f ff d1 ef f1 3f  f0 e3 24 3f d1 e1 2f f0  |].O....?..$?../.|
00000190  21 f1 02 3c 0e 3f fd c2  ee 23 0e 20 04 c4 2f 11  |!..<.?...#. ../.|
000001a0  1f 00 e1 e0 ff 1e 20 f0  24 11 10 00 0f 1f 11 10  |...... .$.......|
000001b0  e2 2f 21 ff 1e 10 ed 23  f0 ff ff f0 50 f2 00 ef  |./!....#....P...|
000001c0  ff ff 83 ef ff ff 02 00  00 00 61 9e 29 01 00 ef  |..........a.)...|
000001d0  ff ff 05 ef ff ff 63 9e  29 01 00 c4 0e 00 00 00  |......c.).......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by danae72 on 2010-11-08
> **thegod_slayer said:**
> first of all, welcome to this forum and welcome to ubuntu.

i think you should read this first.

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

first do some theory research on ubuntu or linux and then try it.
it will seem a whole lot easy.

Thank you for the welcomes. I am not generally used to asking for help on forums (this is my first post here and i have been using ubuntu for over a year), but i have tried googling for solutions and nothing helps, or i dont understand it (including the link to the topic above).

---

### Post by kansasnoob on 2010-11-08
For some reason grub2 is failing to install so copy-n-paste the following commands using the Live CD:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

Note: If for some reason "grub-install /dev/sda" should return any errors you may also have to run:

```
grub-install --recheck /dev/sda
```

I should also point out a discrepancy, the boot info script shows Vista OS on sda2:

> sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /bootmgr /boot/bcd

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe

But the grub menu shows sda2 as "Windows Recovery Environment":

> menuentry "Windows Vista (loader) (on /dev/sda1)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a046b17e46b155ae
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 6434409e34407558
drivemap -s (hd0) ${root}
chainloader +1
}

So I'm not quite sure what to think of that. I'd like to see the output of:

```
sudo parted /dev/sda print
```

Before you attempt booting Windows :)

---

### Post by danae72 on 2010-11-08
Yay! It works! :D thank you so much you are the best :D

here is the output of the windows thing:

danae@danae:~$ sudo parted /dev/sda print
[sudo] password for danae: 
Model: ATA WDC WD1600BEVS-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  7247MB  7246MB  primary   ntfs            diag
 2      7247MB  150GB   142GB   primary   ntfs            boot
 3      150GB   160GB   10.5GB  extended
 5      150GB   160GB   9986MB  logical   ext2
 6      160GB   160GB   495MB   logical   linux-swap(v1)

---

### Post by kansasnoob on 2010-11-08
> **danae72 said:**
> Yay! It works! :D thank you so much you are the best :D

here is the output of the windows thing:

danae@danae:~$ sudo parted /dev/sda print
[sudo] password for danae: 
Model: ATA WDC WD1600BEVS-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  7247MB  7246MB  primary   ntfs            diag
 2      7247MB  150GB   142GB   primary   ntfs            boot
 3      150GB   160GB   10.5GB  extended
 5      150GB   160GB   9986MB  logical   ext2
 6      160GB   160GB   495MB   logical   linux-swap(v1)

OK, the Boot Info Script is correct. See sda1 is only about 7GB and parted sees it as "diag" (short for diagnostic), whereas sda2 is 142GB.

I'd fear booting sda1 could be disastrous :(

How likely is it that someone would mess up on that machine and accidentally boot sda1? If it's at all likely I'd customize the menu to get rid of that option.

You might first try running:

```
sudo update-grub
```

just to see if that changes anything but I doubt it. I'd also like to be sure that trying to boot sda2 does work.

---

### Post by danae72 on 2010-11-08
I tried updating grub but it still lists sda2 as windows recovery environment. What would happen if I booted it? As far as I knew, this partition was the one that came with the laptop instead of an installation disc for windows vista, and when I booted it before, there was only a menu for installing windows. I am the only one using the computer.

---

### Post by kansasnoob on 2010-11-08
> **danae72 said:**
> I tried updating grub but it still lists sda2 as windows recovery environment. What would happen if I booted it? As far as I knew, this partition was the one that came with the laptop instead of an installation disc for windows vista, and when I booted it before, there was only a menu for installing windows. I am the only one using the computer.

It could, at worst, do the same as running a full recovery on the machine!

Does sda2 boot Windows OK?

Ultimately I'd appreciate you filing a bug report on this. I'll explain more tomorrow, right now I'm just silly tired :)

---

### Post by kansasnoob on 2010-11-08
Oops, I'm really tired.

As far as I can see you should be OK booting sda2 but not sda1. I'm silly tired, I'll pop back in tomorrow.

This truly is a BUG, it shouldn't happen!

---

### Post by danae72 on 2010-11-09
Thanks again for all your help. Sda2 boots normally. 
I've tried filing a bug report on bugzilla, but I have no idea how to classify it. :/

---

### Post by kansasnoob on 2010-11-09
Super late responding :(

Things have just been totally crazy here.

As far as filing a bug report on that I'd suggest just booting into your now working Ubuntu and pressing Alt+F2, then typing **ubuntu-bug grub-pc**.

Then briefly explain what happened and also post the bug report link here so I can try to get involved.

Just FYI grub2 has been the default bootloader since 9.10 and it's improved a lot. However there are still issues that need to be dealt with.

Should you want to customize your boot menu to eliminate that sda1 option the easiest way is to copy-n-paste the sda2 entry from "/etc/grub.d/30_os-prober" into "/etc/grub.d/40_custom":

> menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 6434409e34407558
drivemap -s (hd0) ${root}
chainloader +1
}

In other words you'd run:

```
sudo gedit /etc/grub.d/40_custom
```

Then add the new entry. The bit between the quotation marks can be edited to your liking like:

> [QUOTE]menuentry "**[COLOR="Red"]My new Windows entry[/COLOR]**" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 6434409e34407558
drivemap -s (hd0) ${root}
chainloader +1
}[/QUOTE]

Then after making sure the new entry, which will show up at the bottom of the boot menu, boots correctly you could run:

```
sudo chmod -x /etc/grub.d/30_os-prober
```

And:

```
sudo update-grub
```

That should stop the entries in "/etc/grub.d/30_os-prober" from showing and should you ever want "/etc/grub.d/30_os-prober" to work properly again just change the "-" to "+" like this:

```
sudo chmod +x /etc/grub.d/30_os-prober
```

This is a great place to look for more info about grub2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It really is simple after you fiddle around the first few times :)

---

