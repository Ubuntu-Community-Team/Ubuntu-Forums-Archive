---
title: "Installed Ubuntu alongside Win7 but GRUB doesn't appear; just boots Win7"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by cosmicappuccino on 2010-12-31
Just installed Ubuntu 10.10 onto my new netbook from a USB stick. 
The laptop came with Win7 Starter, which I kept on a small partition.

Installation was apparently successful, but when I start up the computer, it will go straight to Win7 and GRUB doesn't appear. I'm very inexperienced in this area so would much appreciate any advice!!

Thanks a lot (:

---

### Post by wilee-nilee on 2010-12-31
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Sometimes a thumb will show as the main HD to the installer, and grub the bootloader will get put there=the sticks mbr, have you tried just powering on the computer with the thumb booting first? If this is what has happened, and you see the grub menu boot into Ubuntu and run the script.

---

### Post by cosmicappuccino on 2010-12-31
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda6 starts at sector 479195136. According to the info 
                       in the boot sector, sda6 has 0 sectors.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,664,128   115,550,207    83,886,080   7 HPFS/NTFS
/dev/sda4         115,552,254   488,392,064   372,839,811   f W95 Ext d (LBA)
/dev/sda5         115,552,256   479,193,087   363,640,832  83 Linux
/dev/sda6         479,195,136   488,392,064     9,196,929  49 Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1993 MB, 1993342976 bytes
2 heads, 63 sectors/track, 30898 cylinders, total 3893248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,893,247     3,893,216   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BCB21DF0B21DAFBE                       ntfs       RECOVERY                      
/dev/sda2        5A561EE9561EC623                       ntfs       SYSTEM                        
/dev/sda3        ACAA212DAA20F58C                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ae5721e3-1974-4f99-93a5-a7408c8df2d6   ext4                                     
/dev/sda6        4B13-E037                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4092-4670                              vfat       SUNOO2G                       
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
search --no-floppy --fs-uuid --set ae5721e3-1974-4f99-93a5-a7408c8df2d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set ae5721e3-1974-4f99-93a5-a7408c8df2d6
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
	search --no-floppy --fs-uuid --set ae5721e3-1974-4f99-93a5-a7408c8df2d6
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ae5721e3-1974-4f99-93a5-a7408c8df2d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ae5721e3-1974-4f99-93a5-a7408c8df2d6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ae5721e3-1974-4f99-93a5-a7408c8df2d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ae5721e3-1974-4f99-93a5-a7408c8df2d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ae5721e3-1974-4f99-93a5-a7408c8df2d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set bcb21df0b21dafbe
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 5a561ee9561ec623
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
/dev/sda5       /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 171.0GB: boot/grub/core.img
  78.6GB: boot/grub/grub.cfg
  78.7GB: boot/initrd.img-2.6.35-22-generic
 171.0GB: boot/vmlinuz-2.6.35-22-generic
  78.7GB: initrd.img
 171.0GB: vmlinuz

============================= sda6/grub/grub.cfg: =============================

#
# grub.cfg for a simple text menu.
# In the current architecture, this always just boots hyperspace.
# see normal/main.c
#
set quietmenu=1
set default=0
set timeout=0

menuentry "Hypercore" {
         sethsroot
         psaloader psa0
}

=================== sda6: Location of files loaded by Grub: ===================


    ??GB: grub/core.img
    ??GB: grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  eb 4b 90 6d 6b 64 6f 73  66 73 00 00 02 04 3f 00  |.K.mkdosfs....?.|
00000010  02 00 02 00 10 f8 03 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  00 00 00 00 00 00 29 37  e0 13 4b 20 20 20 20 20  |......)7..K     |
00000030  20 20 20 20 20 20 46 41  54 31 32 20 20 20 04 00  |      FAT12   ..|
00000040  00 80 00 08 01 f0 8f 1c  00 00 00 00 80 fa eb 07  |................|
00000050  f6 c2 80 75 02 b2 80 ea  5c 7c 00 00 31 c0 8e d8  |...u....\|..1...|
00000060  8e d0 bc 00 20 fb a0 4c  7c 3c ff 74 02 88 c2 52  |.... ..L|<.t...R|
00000070  be 71 7d e8 23 01 be 05  7c f6 c2 80 74 48 b4 41  |.q}.#...|...tH.A|
00000080  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
00000090  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000a0  c7 04 10 00 66 8b 1e 44  7c 66 89 5c 08 66 8b 1e  |....f..D|f.\.f..|
000000b0  48 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |H|f.\..D..p.B..r|
000000c0  05 bb 00 70 eb 73 b4 08  cd 13 73 0a f6 c2 80 0f  |...p.s....s.....|
000000d0  84 f0 00 e9 83 00 66 0f  b6 c6 88 64 ff 40 66 89  |......f....d.@f.|
000000e0  44 04 0f b6 d1 c1 e2 02  88 e8 88 f4 40 89 44 08  |D...........@.D.|
000000f0  0f b6 c2 c0 e8 02 66 89  04 66 a1 48 7c 66 09 c0  |......f..f.H|f..|
00000100  75 4f 66 a1 44 7c 66 31  d2 66 f7 34 88 d1 31 d2  |uOf.D|f1.f.4..1.|
00000110  66 f7 74 04 3b 44 08 7d  38 fe c1 88 c5 30 c0 c1  |f.t.;D.}8....0..|
00000120  e8 02 08 c1 88 d0 5a 88  c6 bb 00 70 8e c3 31 db  |......Z....p..1.|
00000130  b8 01 02 cd 13 72 2a 8c  c3 8e 06 42 7c 60 1e b9  |.....r*....B|`..|
00000140  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 40  |....1.1.....a.&@|
00000150  7c be 77 7d e8 42 00 eb  0e be 7c 7d e8 3a 00 eb  ||.w}.B....|}.:..|
00000160  06 be 86 7d e8 32 00 be  8b 7d e8 2c 00 cd 18 eb  |...}.2...}.,....|
00000170  fe 00 00 00 00 00 00 47  65 6f 6d 00 48 61 72 64  |.......Geom.Hard|
00000180  20 44 69 73 6b 00 52 65  61 64 00 20 45 72 72 6f  | Disk.Read. Erro|
00000190  72 00 bb 01 00 b4 0e cd  10 ac 3c 00 75 f4 c3 00  |r.........<.u...|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 24 12  |..............$.|
000001c0  0f 09 00 be bd 7d 31 c0  cd 13 46 8a 0c 80 f9 00  |.....}1...F.....|
000001d0  75 0f be da 7d e8 c1 ff  eb 8d 46 6c 6f 70 70 79  |u...}.....Floppy|
000001e0  00 bb 00 70 b8 01 02 b5  00 b6 00 cd 13 72 d7 b6  |...p.........r..|
000001f0  01 b5 4f e9 e0 fe 00 00  00 00 00 00 00 00 55 aa  |..O...........U.|
00000200



```

> **wilee-nilee said:**
> Sometimes a thumb will show as the main HD to the installer, and grub the bootloader will get put there=the sticks mbr, have you tried just powering on the computer with the thumb booting first? If this is what has happened, and you see the grub menu boot into Ubuntu and run the script.

I used Unetbootin to make my USB stick bootable, and when I insert the stick and start the computer, it just goes to the Unetbootin menu. (I used Unetbootin because it was mentioned here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)) If you think it might help to use usb-creator.exe instead, I'm happy to try that...

Thanks a lot, again....

---

### Post by Crazedpsyc on 2010-12-31
There are several guides for this (although I can't find them right now) but the basic principal is:
run the following from the live CD:
 ```
sudo mount /dev/[UBUNTUPARTITION] /mnt
```this one I can't remember the details of:
```
sudo grub2-install /mnt/
```I have actually done this when I encountered a similar problem
I will continue to look for those guides for you!

EDIT:
I found one that sounds like what I remember:
> 
sudo -i 
mount /dev/sda7 /mnt 
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition 
grub-install --root-directory=/mnt/ /dev/sda
see the rest at: [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by cosmicappuccino on 2010-12-31
> **Crazedpsyc said:**
> There are several guides for this (although I can't find them right now) but the basic principal is:
run the following from the live CD:
 ```
sudo mount /dev/[UBUNTUPARTITION] /mnt
```
this one I can't remember the details of:
```
sudo grub2-install /mnt/
```
I have actually done this when I encountered a similar problem
I will continue to look for those guides for you!

Thanks Crazedpsyc - I appreciate your help! (:

In fact I found a thread on the forums from a few months ago with a similar problem, but the solution that worked there didn't work for me. Their solution was:

```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

```

...I've tried this several times - it even says installation was successful - but when I reboot, there's no change. I noticed that your version said "grub2-install" rather than "grub-install", so I just tried that too, but got this:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub2-install --root-directory=/mnt/ /dev/sda
sudo: grub2-install: command not found

```

:confused: ...

---

### Post by Quackers on 2010-12-31
I don't see anything wrong with the boot script output, as such. I would ask, though, if you intended to hav a 4GB swap partition?
I ask this as sda6 looks strange, and you have no swap space.

---

### Post by cosmicappuccino on 2010-12-31
> **Quackers said:**
> I don't see anything wrong with the boot script output, as such. I would ask, though, if you intended to hav a 4GB swap partition?
I ask this as sda6 looks strange, and you have no swap space.

No, I didn't make a swap partition... the netbook came with 4 partitions already allocated. I took over the "recovery" partition for Ubuntu but didn't want to get rid of too many of the original partitions so figured I'd make a swap file later, to be safe...

EDIT: In fact sda4 confuses me... it didn't show up at all in the Ubuntu installation partitioning step, but does in the boot script output... wondering if there's any way to make use of it / why it's there....

---

### Post by cosmicappuccino on 2010-12-31
In case this helps:

When I type this:

```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

```

The output I get is this:

```

Probing devices to guess BIOS drives. This may take a long time.
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect, fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb

```

Two things that caught my eye are:

```
This is the contents of the device map /mnt//boot/grub/device.map.
```
Should there be two slashes there?

```
(hd1)   /dev/sdb
```
I think this is my USB stick. Should it be there?

---

### Post by drs305 on 2010-12-31
cosmicappuccino,

I would first try booting and holding down the SHIFT key to see if the Grub2 menu appears. I don't think it will as the RESULTS.txt does not include the code for a keystatus check, but it won't hurt to try.

Next, if you can't get into your normal Ubuntu installation via the Grub2 menu, boot to the Desktop via Unetbootin or however you did to install Ubuntu. Select "Try Ubuntu" if necessary.

The next step depends on what is running when you get to the Desktop - a "LiveCD/Try" version, or your real Ubuntu installation.

In either case, I would confirm you have an Internet connection and then purge and reinstall Grub2. The instructions are found in this guide:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

From a normally-running Ubuntu, you don't need to accomplish the 'chroot' but you should run steps 2-5 of that section to purge and reinstall G2.

If you are in a LiveCD/Try It version of Ubuntu, run all the commands in the chroot section of the guide.

The partition to mount should be sda5 (hd0,5). When it comes time to select where to install G2, select only sda and not the partition. You might also confirm that your Ubuntu drive is actually "sda" and not "sdb" before running any of the commands. "sudo fdisk -l" should help you decide which is your Ubuntu drive.

---

### Post by Quackers on 2010-12-31
sda is your hard drive
sda4 is an extended partition which holds sda5 and sda6

Your second command is wrong here
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=[COLOR="Red"]/mnt/[/COLOR] /dev/sda[COLOR="Black"][/COLOR]
```
It has one too many / in it
It should be ```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by cosmicappuccino on 2010-12-31
Thanks for your suggestions, all!

> **drs305]
In either case, I would confirm you have an Internet connection and then purge and reinstall Grub2. The instructions are found in this guide:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
[/QUOTE]

Holding the SHIFT key doesn't work. I followed the instructions at the link you provided (from the "trial" environment booted from USB), but unfortunately reached the following error when trying to reinstall GRUB after having uninstalled it:

```

root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 200 not upgraded.
Need to get 0B/2,204kB of archives.
After this operation, 5,804kB of additional disk space will be used.
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub-common.
(Reading database ... 118006 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98+20100804-5ubuntu3_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.98+20100804-5ubuntu3) ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...

Creating config file /etc/default/grub with new version
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

```

[QUOTE=Quackers said:**
> sda is your hard drive
It has one too many / in it
It should be ```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Oh right, thank you. Shall I try this straight away now, then? I'm just concerned because of my failed attempt at uninstalling/reinstalling GRUB as described above - will it be ok just to try the corrected command now?

Thanks so much again!

---

### Post by Quackers on 2010-12-31
You can try it, yes.
It may be necessary to purge/re-install grub as drs305 suggests. If it is in fact necessary, drs305's guide is the one to follow, I have used it several times myself :-)

---

### Post by cosmicappuccino on 2010-12-31
> **Quackers said:**
> You can try it, yes.
It may be necessary to purge/re-install grub as drs305 suggests. If it is in fact necessary, drs305's guide is the one to follow, I have used it several times myself :-)

Ok, I tried the corrected command and rebooted, but it's just gone straight into Win7 again.

I guess the next step is to try purging/reinstalling grub, but then I don't know what I can do about the error that I quoted in my previous post...?

:confused:

---

### Post by drs305 on 2010-12-31
cosmicappuccino,

If the "--root-directory" commands don't work, you can try the purge/reinstall commands again. You got into the 'chroot' environment (as shown by the "root" prompt), but the error messages show that all the system files weren't mounted or available when you ran the purge/reinstall commands.

If you were running a normally-booted Ubuntu, it would mean some of the system files are missing. If you booted via the LiveCD/Try It method, it means that the system files weren't properly mounted before chrooting. The system files are mounted by running the "for i in ....." command. You must first mount your real Ubuntu partition, then run the "for i ..." commmand. Take a look at the chroot guide. 

If you try running all the steps again, it's easiest to copy/paste the commands into a terminal. You copy by highlighting and then CTRL-c. To paste into a linux terminal, you must paste with CTRL-SHIFT-v. An even faster way is to highlight with the mouse, then middle click to paste in the terminal.

---

### Post by Quackers on 2010-12-31
When you tried following drs305's guide, did you leave out this line
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
```
I ask because others have done so, and it leads to needed files not being mounted.

---

### Post by cosmicappuccino on 2010-12-31
> **drs305 said:**
> cosmicappuccino,

If the "--root-directory" commands don't work, you can try the purge/reinstall commands again. You got into the 'chroot' environment (as shown by the "root" prompt), but the error messages show that all the system files weren't mounted or available when you ran the purge/reinstall commands.

If you were running a normally-booted Ubuntu, it would mean some of the system files are missing. If you booted via the LiveCD/Try It method, it means that the system files weren't properly mounted before chrooting. The system files are mounted by running the "for i in ....." command. You must first mount your real Ubuntu partition, then run the "for i ..." commmand. Take a look at the chroot guide. 

If you try running all the steps again, it's easiest to copy/paste the commands into a terminal. You copy by highlighting and then CTRL-c. To paste into a linux terminal, you must paste with CTRL-SHIFT-v. An even faster way is to highlight with the mouse, then middle click to paste in the terminal.

Okay, I did the purge/reinstall again, and this time it worked... not sure what I did wrong last time. However, I then rebooted my computer, and it went straight to Win7 again! ... Any thoughts, please...?

---

### Post by drs305 on 2010-12-31
> **cosmicappuccino said:**
> Okay, I did the purge/reinstall again, and this time it worked... not sure what I did wrong last time. However, I then rebooted my computer, and it went straight to Win7 again! ... Any thoughts, please...?

The one thing that comes to mind is that part of the MBR (or the area just outside the MBR) is being write-protected by a Windows product. These include Dell DataSafe/Recovery, HP ProtectTools, Adobe FlexNet, etc. If you can remove these from your Windows installation it may allow G2 to write to that portion of the MBR. 

If you have any of these products you can do a search of the Ubuntu forums for more information on how to deal with them.

If you rerun the boot info script see if there is now a section for "keystatus" (just search the text for that term). If it is mentioned, you can try holding down the SHIFT key during boot to see if the Grub2 menu now displays.

---

### Post by cosmicappuccino on 2011-01-01
> **drs305 said:**
> The one thing that comes to mind is that part of the MBR (or the area just outside the MBR) is being write-protected by a Windows product. These include Dell DataSafe/Recovery, HP ProtectTools, Adobe FlexNet, etc. If you can remove these from your Windows installation it may allow G2 to write to that portion of the MBR. 

If you have any of these products you can do a search of the Ubuntu forums for more information on how to deal with them.

If you rerun the boot info script see if there is now a section for "keystatus" (just search the text for that term). If it is mentioned, you can try holding down the SHIFT key during boot to see if the Grub2 menu now displays.


Awesome, thank you so much!!! It works now - it started working after I uninstalled some recovery software that the computer came with (: (: (:

Happy new year!

---

