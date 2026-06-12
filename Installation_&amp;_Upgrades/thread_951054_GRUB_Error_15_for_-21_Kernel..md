---
title: "GRUB Error 15 for -21 Kernel."
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by ShinobiTeno on 2008-10-17
Hello!!=)

This week I got the kernel update to -21 appear under Updates and performed it. It went flawlessly, and added -21 to menu.lst, but the problem is: every time I try boot into it(by selecting it in GRUB menu,its marked as default), I get Error15: File not found. -19 boots no problem!
Menu.lst is ok, i checked it three times. File locations(/boot, and symlinks in /) are ok. I force reinstalled -21 kernel as well. No change. I suspect that 1024 cylinder makes it happen... I suspect that the new kernel got behind 8Gb and GRUB cannot access it... Does we have to do a separate /boot partition right on the start of the disk? Any ideas it happenz?


Additional info:
Ubuntu Studio(Hardy), GNOME.

2x500GB(WD5000AAKS) sata on sil3152. One work, one 1:1 backup. One old PATA disk, with very known OS, that is going to be dd`ed very soon, for it looks quite useless contra linux)

System is set to boot from SATA, hd0(GRUB) is sdb. Because of libata mixing Pata and Sata, it gets placed second, behind old Pata drive.

Partiton Map for 500Gb disks(sdb,sdc) is the following
<sdb1="/"> <sdb2 <sdb5="~/DataDisk"> > <sdb3=swap>

Rest hardware: AMD AthlonXP Barton2.2ghz, 1Gb ddrram, Nforce2ultra400(Abit NF7-S v2, g6800.

fdisk -l:
```

Disk /dev/sda: 120.0 &#1043;&#1041;, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3dc3f511

Device Boot     Begin       End       Blocks   Id  System
/dev/sda1   *           1        2617    21021021    7  HPFS/NTFS
/dev/sda2            2618       14593    96197220    5  Extended
/dev/sda5            2618       14593    96197188+  83  Linux


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89a27d47

Device Boot     Begin       End       Blocks   Id  System
/dev/sdb1   *           1        5107    41021946   83  Linux
/dev/sdb2            5108       60546   445313767+   5  extended
/dev/sdb3           60547       60801     2048287+  82  Linux swap / Solaris
/dev/sdb5            5108       60546   445313736   83  Linux

Disk /dev/sdc: 500.1 &#1043;&#1041;, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89a27d47

Device Boot     Begin       End       Blocks   Id  System
/dev/sdc1   *           1        5107    41021946   83  Linux
/dev/sdc2            5108       60546   445313767+   5  extended
/dev/sdc3           60547       60801     2048287+  82  Linux swap / Solaris
/dev/sdc5            5108       60546   445313736   83  Linux

```

menu.lst: 
Note, l have tried to boot -21 with "/sda" and "UUID" modes as well, no change. -19 woeks. Its identical to -21, if not including "-21" number.

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system. 
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/disk/by-id/scsi-1ATA_WDC_WD5000AAKS-22TMA0_WD-WCAPW3802922-part1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
## If I plan change disk, edit menu, and fstab! read new hwid and replace!
## scsi-..WCAPW is TMAO disk.
## scsi-..WMASY is A70 disk.
##UBUNTU NAMING scsi-1ATA_WDC_WD5000AAKS-22TMA0_WD-WCAPW3802922-part1  note"22tmao"
##KNOPIX NAMING scsi-SATA_WDC_WD5000AAKS-_WD-WCAPW3802922-part1

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=/dev/disk/by-id/scsi-1ATA_WDC_WD5000AAKS-22TMA0_WD-WCAPW3802922-part1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-rt
quiet

title		TESTING SDB Ubuntu 8.04.1, kernel 2.6.24-21-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=/dev/disk/by-id/scsi-1ATA_WDC_WD5000AAKS-22TMA0_WD-WCAPW3802922-part1 ro single
initrd		/boot/initrd.img-2.6.24-21-rt

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=/dev/disk/by-id/scsi-1ATA_WDC_WD5000AAKS-22TMA0_WD-WCAPW3802922-part1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=/dev/disk/by-id/scsi-1ATA_WDC_WD5000AAKS-22TMA0_WD-WCAPW3802922-part1 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, Perform memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

lspci:
```
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:08.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
01:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
01:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800] (rev a1)

```

UPDATE:

ls -alh /boot
```

total 21M
drwxr-xr-x  3 root root 4,0K 2008-10-15 20:57 .
drwxr-xr-x 21 vova root 4,0K 2008-10-15 23:13 ..
-rw-r--r--  1 root root  84K 2008-08-21 06:58 config-2.6.24-19-rt
-rw-r--r--  1 root root  84K 2008-08-25 23:12 config-2.6.24-21-rt
drwxr-xr-x  2 root root 4,0K 2008-10-15 21:26 grub
-rw-r--r--  1 root root 7,7M 2008-08-26 08:25 initrd.img-2.6.24-19-rt
-rw-r--r--  1 root root 7,4M 2008-10-15 20:40 initrd.img-2.6.24-21-rt
-rw-r--r--  1 root root 101K 2007-09-28 12:06 memtest86+.bin
-rw-r--r--  1 root root 907K 2008-08-21 06:58 System.map-2.6.24-19-rt
-rw-r--r--  1 root root 907K 2008-08-25 23:12 System.map-2.6.24-21-rt
-rw-r--r--  1 root root 1,9M 2008-08-21 06:58 vmlinuz-2.6.24-19-rt
-rw-r--r--  1 root root 1,9M 2008-08-25 23:12 vmlinuz-2.6.24-21-rt

```

ls -alh /
```

total 104K
drwxr-xr-x  21 vova root 4,0K 2008-10-15 23:13 .
drwxr-xr-x  21 vova root 4,0K 2008-10-15 23:13 ..
drwxr-xr-x   2 root root 4,0K 2008-08-08 15:43 bin
drwxr-xr-x   3 root root 4,0K 2008-10-15 20:57 boot
lrwxrwxrwx   1 root root   11 2008-08-16 04:18 cdrom -> media/cdrom
drwxr-xr-x  12 root root  14K 2008-10-18 10:55 dev
drwxr-xr-x 137 root root  16K 2008-10-18 10:55 etc
drwxr-xr-x   3 root root 4,0K 2008-09-22 14:29 home
drwxr-xr-x   2 root root 4,0K 2008-07-25 19:40 initrd
lrwxrwxrwx   1 root root   28 2008-10-15 14:59 initrd.img -> boot/initrd.img-2.6.24-21-rt
lrwxrwxrwx   1 root root   28 2008-08-16 04:19 initrd.img.old -> boot/initrd.img-2.6.24-19-rt
drwxr-xr-x  15 root root  12K 2008-10-14 23:40 lib
drwx------   2 root root  16K 2008-07-25 19:40 lost+found
drwxr-xr-x   4 root root 4,0K 2008-10-18 10:55 media
drwxr-xr-x   3 root root 4,0K 2008-10-01 10:04 mnt
drwxr-xr-x   3 root root 4,0K 2008-09-19 13:43 opt
dr-xr-xr-x 136 root root    0 1970-01-01 01:00 proc
drwxr-xr-x  28 root root 4,0K 2008-10-15 21:27 root
drwxr-xr-x   2 root root 4,0K 2008-10-15 14:59 sbin
drwxr-xr-x   2 root root 4,0K 2008-07-25 19:40 srv
drwxr-xr-x  11 root root    0 2008-10-18 12:54 sys
drwxrwxrwt  12 root root 4,0K 2008-10-18 10:57 tmp
drwxr-xr-x  12 root root 4,0K 2008-08-08 15:43 usr
drwxr-xr-x  15 root root 4,0K 2008-09-10 09:18 var
lrwxrwxrwx   1 root root   25 2008-10-15 14:59 vmlinuz -> boot/vmlinuz-2.6.24-21-rt
lrwxrwxrwx   1 root root   25 2008-08-16 04:26 vmlinuz.old -> boot/vmlinuz-2.6.24-19-rt

```

---

### Post by Neo_The_User on 2008-10-18
```

cd /boot
ls

```

Post all output here. It should tell you that it at least found the linux kernel image.

---

### Post by ShinobiTeno on 2008-10-18
Sorry, >>`ed it to the tail of the first post. ):/

---

### Post by Neo_The_User on 2008-10-18
You might have to do some compiling. It's pretty complicated and requires a lot of typing on my part. I'm asking ahead to prevent frustration.

I'll get you started a little bit for now then let me know if your ready for the hard long complicated stuff. Might take 35 mins or it can be an hour and 30 mins.

not sudo apt-get install
```

sudo apt-get source linux-image-2.6.24-21-generic

```

and the rest is something I rather not get into unless you want me to.

---

### Post by ShinobiTeno on 2008-10-18
So you think its not that kernel image is unreachable for GRUB?.. -19 runs fine, -21 always gets "File not found". If you think theres a possibility to solve this with recompiling, lets give it a shot=) I`m ready.

---

### Post by Neo_The_User on 2008-10-20
It is reachable by GRUB. Most likely, The -21 kernel config has a different setup that the -19 kernel. I think they tried making the kernel smaller for faster boot-ups etc etc. Anyway... Now that you have the source code, CD to the kernel source folder. If you did it in your home folder (most likely) then type in

```

cd (kernel source folder goes here except without parenthesis)

```

Now for the dev tools.

```

sudo apt-get install linux-kernel-devel fakeroot build-essential makedumpfile qt3-dev-tools libqt3-mt-dev

```

Make sure your using the -19 kernel when doing this :lolflag:

Now that you have the dev tools you need and the kernel source, now its time for the compiling and configuring.

To get the -21 kernel using the same config file as the -19 kernel, type in the following command.

```

cp -vi /boot/config-`uname -r` .config

```

Now to graphically edit the config file (just a few things)

```

make xconfig

```

Now... go all the way to the bottom of the list located at the left side of the kernel config window. Look for kernel hacking. Turn off kernel debugging (unless you want to wait a million years for it to compile) which should then turn off "compile with kernel debug info"

Now click the save icon located at the top left of the kernel config window or hit Control S to save it.

Making the kernel:

```

make-kpkg clean

```

Compile the kernel:

```

fakeroot make-kpkg --initrd --append-to-version=-ultimate-killer-kernel kernel-image kernel-headers

```

Replace ultimate-killer-kernel with whatever you want. If you want it to say 2.6.24-21-generic then change it to generic. I personally thinks it cool in the grub menu when it says 2.6.24-21-ultimate-killer-kernel

Wait a long long time. WHEN IT SAYS DONE FOR A LONG TIME BUT IT DOESN'T GIVE YOU THE INTERACTIVE TERMINAL LIKE "neo@neo-desktop" (thats mine because its my name) THEN SCROLL UP AND DOWN THE TERMINAL TO WAKE IT UP AGAIN! THE TERMINAL FALLS ASLEEP KIND OF AT THE END!

Figure out what processor you have and how many cores it has.

If you have an AMD Phenom X4 64-bit Quad-core then after it compiles, type in
echo fbcon | sudo tee -a /etc/echo fbcon | sudo tee -a /etc/initramfs-tools/modulesinitramfs-tools/modules
```

export CONCURRENCY_LEVEL=5

```

I have a K7 AMD Athlon XP 2000+ and have no idea how many cores I have so I don't do the concurrency_level thing.

Load frame buffer

```

echo vesafb | sudo tee -a /etc/initramfs-tools/modules
echo fbcon | sudo tee -a /etc/initramfs-tools/modules

```

Now open up a file browser to where you had your kernel source or whatever. Inside the directory (not the folder of the kernel) of which the kernel source folder is in, find the kernel image and the kernel headers. It will say Custom-10.00 or something like that. It will be a very long .deb file. After you find them, go back in terminal and type in

```

sudo dpkg -i (kernel image goes here so drag it in via nautilus or something)

sudo dpkg -i (kernel headers)

```

In terminal, type in

```

sudo update-grub

```

If you still have problems type this in

```

fsck -y /dev/hda0

```

replace hda0 with hda1 or whatever if it doesn't work. Post output of fsck -y /dev/hda0 here.

---

### Post by ShinobiTeno on 2008-10-23
Much thanks for the guide!

I`ve been hacking in the kernel for some time and got it to work.
But the most important thing is after I installed it and did update-grub, stock -21 kernel magically started to boot... I did try update-grub before all this(right after kernel got installed thru automatic sys-update), and it didnt change anything...

Customized kernel that I built works, but I get PulseAudio warning-"unable to get connection(or something)" and the X server fails to start>complained on NVIDIA not integrated(I use them for 3D). Are there possibilities to make nvidia work using ubuntu reps, or I need to go to nvidia and get their drivers there and recompile the kernel with their script?..

What's on PulseAudio(in the case you're using it or know about)?

Other strange thing: In xconfig, I noticed ALSA to be turned off completely according to -19 stock .config... But it works in -19 nevertheless...

Im just currious about turning on PAE and (especially) recompiling for K7(I have 3200+ athlon(2,2ghz)) :)

---

