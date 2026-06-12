---
title: "[SOLVED] Fresh Install 7.10 (Gutsy)  - GRUB Error 15"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Shampyon on 2007-11-13
**SOLVED - See first reply**

I've been using Ubuntu for a while now. I upgraded to Gutsy using the alternate install disk, but the massive amounts of changes I'd made to the system prior to upgrade resulted in a couple of tiny errors, like difficulty in changing screensaver settings. I decided it was about time to do a fresh install. I just recieved my ShipIt disc in the mail a few days ago, and today I started the fresh install.

I use two SATA hard drives. One is 160GB, which is the disc I originally used as my primary hard drive. The second is 250GB, which I used to use for XP. I decided that my fresh install would use the 250 drive as the primary hard drive, and the 160 as the secondary. Using the safe graphics mode (I have an ATI Radeon x700 Super, which works fine with VESA and great once I install the official ATI driver), I installed Gutsy from the ShipIt disc. I formatted the 160GB drive's home partition. I formatted the entirety of the 250GB drive, ensuring to place the swap partition on that drive.

When I try to boot from the hard drive, I get a GRUB ERROR 15.

I'm not sure exactly what data you need to properly analyze the problem. Let me know if you need anything else.

fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42ca42ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6080    48837568+  83  Linux
/dev/sda2            6081       30401   195358432+   f  W95 Ext'd (LBA)
/dev/sda5            6081       12160    48837568+  83  Linux
/dev/sda6           12161       18240    48837568+  83  Linux
/dev/sda7           18241       24320    48837568+  83  Linux
/dev/sda8           24321       30034    45897673+  83  Linux
/dev/sda9           30035       30401     2947896   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdec7dec7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+  83  Linux
/dev/sdb2            4865       19454   117194175    f  W95 Ext'd (LBA)
/dev/sdb5            4865        9708    38909398+  83  Linux
/dev/sdb6            9709       14592    39230698+  83  Linux
/dev/sdb7           14593       19193    36957501   83  Linux
/dev/sdb8           19194       19454     2096451   82  Linux swap / Solaris

```

After mounting (hd0) as /media/ubuntu:
**media/ubuntu/boot/grub/menu.lst**
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=73df2d01-723f-42d3-ad31-681bdbc3e81b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=73df2d01-723f-42d3-ad31-681bdbc3e81b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

**/media/ubuntu/etc/fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=73df2d01-723f-42d3-ad31-681bdbc3e81b /               reiserfs notail          0       1
# /dev/sda5
UUID=8a3a9f51-7010-4bbe-8f07-40d4b2e6f6d3 /media/sda5     reiserfs defaults        0       2
# /dev/sda6
UUID=9e3a4932-795c-41e4-b96a-4c33ba032c74 /media/sda6     reiserfs defaults        0       2
# /dev/sda7
UUID=e35621df-059d-4288-b99c-8917ba917848 /media/sda7     reiserfs defaults        0       2
# /dev/sda8
UUID=e6df3e16-1257-46a8-aa93-2718b84102a4 /media/sda8     reiserfs defaults        0       2
# /dev/sdb1
UUID=2c2b25b4-1f5c-47e8-bb04-90213dbea36e /media/sdb1     reiserfs defaults        0       2
# /dev/sdb5
UUID=c7d22494-962a-4a33-a728-7a26c37cbff6 /media/sdb5     reiserfs defaults        0       2
# /dev/sdb6
UUID=dc747f13-bd0a-4c35-8760-7916fcbd3e9d /media/sdb6     reiserfs defaults        0       2
# /dev/sdb7
UUID=4156d957-6a9d-4cdd-8e91-3cac2819dac8 /media/sdb7     reiserfs defaults        0       2
# /dev/sdb8
UUID=cd33531f-1b8d-4f90-94b6-1386e6b7afb6 /media/sdb8     reiserfs defaults        0       2
# /dev/sda9
UUID=d74e56d7-6a52-4ec9-bfeb-b9f9bec5ed99 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```
[B]
media/ubuntu/etc/X11/xorg.conf[/B]
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"BENQ V773"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"BENQ V773"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

```

---

### Post by bulldog on 2007-11-13
15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

Did you  change the boot order in your BIOS?
On which hdd did you install GRUB?

Try to boot from the other hdd and see if grub is there as well.

---

### Post by Shampyon on 2007-11-13
> **bulldog said:**
> 15 : File not found
Did you  change the boot order in your BIOS?


That idea just hit me a few minutes ago. Went into the BIOS, saw that it was booting from the 160Gb drive first. Changed it to the 250GB drive, and now I'm posting form my fresh Gutsy install.

Thanks for your help!

---

