---
title: "x1950 pro (agp) ati driver how to"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by jerjely on 2008-04-27
Few months ago I installed guttsy and i ran into a problem with my videocard, i tried to fix it many ways. Sometimes it even seemed like it was working, but still could not enable the desktop effects. Then I gave up, three days ago though i decided to install hardy and I have the same problem as before. Ive read many forums and tried many things. For example envy, manual install of the official driver from ati website, enabling the restricted driver in ubuntu, doing all these and then enabling xgl (which caused a major lag). So i guess what i would like is someone with the same video card to tell me how to install my video drivers properly. I would much apritiate it thank you.

---

### Post by xMachina on 2008-05-13
Hi Jerjely, I finally got this card going properly in Linux after owning it for 6 months+ ... some guy called Alastair over at the ATI bugzilla has figured out how to get it going! By:

1) Follow the manual install option for the Proprietary ATI drivers at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually)

EXCEPT before rebooting, you also need to make sure the AGP memory listing matches up at 3 places, to avoid the "ATI black screen of death":

2) Look up exactly how much video RAM your card has, eg from the box, receipt, or the ATI control centre in windows (it will either be 256MB or 512MB). For the instructions below I'll go with 512, but substitute as appropriate.
3) edit your /etc/X11/xorg.conf, and add the following line at the end of the fglrx device section:
>  Option      "MaxGARTSize"       "512"
4) edit your grub boot instructions for your kernel in the /boot/grub/menu.lst file, adding vmem=512 to your kernel boot line for your main kernel, e.g.:  
> 
title           Ubuntu 8.04, kernel 2.6.24-16-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16-386 root=UUID=64fa7a1b-a8d7-45fb-a891-a81f3977bc13 ro quiet splash **vmem=512**
initrd          /boot/initrd.img-2.6.24-16-386

5) Ok, now reboot, but ENTER YOUR BIOS and look for the setting related to AGP memory, for me it was in the "Advanced Chipset Features" section. Change it to the same value as the others, eg 512MB.

...and that worked for me, ~1600 FPS in fg_glxgears ;) Haven't tried Compiz etc yet

---

### Post by gary_rowe on 2008-05-21
Hi,

I've had endless problems with the ATI Radeon X1950 and Ubuntu (not that I'm critising Ubuntu which is excellent, more that ATI just don't seem to get their act together). Anyway, I've got a dual head set up based on two Xerox X74 19" monitors running with 1280x1024. 

What this gives me is essentially a main desktop (Monitor0) which has all the desktop bits and pieces, and a spare one to the right for any extras I care to put there. All windows maximize within Monitor0 so it's very similar to a standard Windows dual head situation. None of this enormous stretchy windows malarky like with Xinerama and so on, although you can use the lovely wide desktop backgrounds at 2560x1024 natural resolution.

You won't get any 3D acceleration just yet, although it is planned for the future, which means that you'll be stuck with basic desktop effects but this works well for me. If it's any consolation I tried every conceivable way to get the X1950 to work both with EnvyNG and manual attempts. Different flavours and versions of fglrx, ati, and vesa and every time the 3D stuff utterly failed, I had a crap dual head setup and the desktop effects didn't work, so you're not missing out. The fglrx driver even reported the X1950 as being an unrecognised third party knock off which was bizarre.

The way to get this to work with your trusty X1950 is not to use the ATI drivers at all and instead use radeonhd - the open source driver for ATI cards. So, uninstall fglrx and ATI (EnvyNG to the rescue) and check that you've got radeonhd installed (look in System | Administration | Synaptic Package Manager). If you're running 8.04 (Hardy) then it'll be there by default. 

Unfortunately, this setup does require a bit of system level tweaking, so I'll just assume that you're unfamiliar with Linux commands and X11 and give it to you step by step. You may want to print these instructions in case your video setup is vaped and you can't get back.

First open up a terminal window (Applications | Accessories | Terminal) and initiate an interactive root shell to avoid typing sudo all the time

```
sudo -i
```

Next navigate to the X11 configuration area:

```
cd /etc/X11
```

and make a backup of your existing setup:

```
cp xorg.conf xorg.conf-original
```

now open up a easy to use editor running with root privileges:

```
gedit xorg.conf 
```

replace the contents of xorg.conf with this configuration, which assumes some kind of multi-button wheel mouse and a dual head configuration based on two monitors capable of displaying at a resolution of 1280x1024. You may need to tweak some values to suit your setup if you know what to look for.

```

Section "Monitor"
        Identifier   "Monitor0"
        Option       "RightOf" "Monitor1"
EndSection

Section "Monitor"
        Identifier   "Monitor1"
EndSection

Section "Device"
        Identifier  "Device0"
        Driver      "radeonhd"
        Option      "monitor-DVI-I_1/analog"  "Monitor0"
        Option      "monitor-DVI-I_2/analog" "Monitor1"
        Option      "RROutputOrder"           "DVI-I_2/analog"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Device0"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Virtual   2560 1024
        EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device "Device0"
	DefaultDepth 24
EndSection

Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"7"
	Option		"ButtonMapping"	"1 2 3 6 7"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonNumber"	"7"
EndSection

Section "InputDevice"
	# generated from default
	Identifier	"Keyboard0"
	Driver		"kbd"
EndSection

Section "ServerLayout"
	Identifier	"Layout0"
	Screen "Screen0" 0 0
	Screen "Screen1" RightOf "Screen0"
	Inputdevice	"Keyboard0"	"CoreKeyboard"
	Inputdevice	"Mouse0"	"CorePointer"
EndSection

```
Save the contents of the file in the usual way (CTRL+S) and close the editor. Return to the terminal screen.

It's probably best to restart now, so make sure you've closed any open windows (except the terminal) and issue the following command:

```
shutdown -r now
```

Bang - the system goes into restart. And here is where the pain may start. Either the system will reboot nicely and it'll all just work (yay!), or you'll have a crashed X11 setup and a blank screen (darn). 

Troubleshooting
---------------

If you can interact with the system, you'll need to reinstate the original xorg.conf. This can be done by one of several methods:

1) CTRL+ALT+F1 (or F2->F6) will bring up a console based terminal which will allow you to login and make changes (see later)

2) Ubuntu will present you with a lo-res Configure... option so just choose that and do the best you can with it and limp into a low grade setup. Open up a terminal like before and follow the instructions given later.

3) Total lock up. Hit the power button and restart. You'll have to stop GRUB at startup using ESC the moment the BIOS has handed over control (not possible with a USB keyboard so find a PS/2 based one) and selecting the second item down in the list (recovery mode). Eventually it'll give you a command prompt.

So you've managed to get back to a terminal and you're cursing yet another failed attempt at getting the X1950 to work. You're not alone. 

Enter the following the get back to your previous setup (one at a time):

```

sudo -i
cd /etc/X11
cp xorg.conf-original xorg.conf
shutdown -r now

```

and you should be back where you started. If not, then you're really in trouble and you'll probably need to completely re-initialise your X server. Just delete xorg.conf and Ubuntu will take of the rest at startup.

```
sudo -i
cd /etc/X11
rm xorg.conf
shutdown -r now
```

---

### Post by jerjely on 2008-05-25
Thanks everyone!!! I really appritiate all your help, ill be sure to try it and ill post here (for other ppls sake) if it worked.

---

### Post by garferi on 2008-08-01
Hi!

I have ATi X1950 PRO 512 MB 8x AGP card and now tried [xMachina's solution]("http://ubuntuforums.org/showpost.php?p=4947573&postcount=7") without success, again got Black screen after reboot, same as with all 8.X ATi driver, also tried envy.
I installed the newest ATi 8.7 driver on base of [Ubuntu Hardy Installation Guide Manual Method]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29").

Here is my **xorg.conf**, **menu.lst** and **Xorg.0.log** file after the crash:

**xorg.conf**
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "hu"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option      "MaxGARTSize" "512" 
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

**menu.lst**
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
timeout		10

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
# kopt=root=UUID=5C304EBF304E9FBE loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5C304EBF304E9FBE loop=/ubuntu/disks/root.disk ro quiet splash vmem=512
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5C304EBF304E9FBE loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
root		(hd0,0)
savedefault
chainloader	+1

```

**Xorg.0.log**
```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux feri-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  1 17:06:51 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1043,80f2 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1043,80a6 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1043,80a6 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1043,80a6 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1043,80a6 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1043,80a6 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1043,80f3 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7280 card 174b,e190 rev 9a class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,72a0 card 174b,e191 rev 9a class 03,80,00 hdr 00
(II) PCI: 02:05:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 11c1,048f card 1848,0001 rev 02 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbff00000 - 0xdfefffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV570 [Radeon X1950 Pro] rev 154, Mem @ 0xc0000000/28, 0xfe9f0000/16, I/O @ 0xc000/8, BIOS @ 0xfe9c0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) rev 154, Mem @ 0xfe9e0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeafbc00 - 0xfeafbcff (0x100) MX[B]
	[1] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[8] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[9] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[12] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[16] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[17] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[18] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[19] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[20] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[21] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[28] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[29] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[30] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafbc00 - 0xfeafbcff (0x100) MX[B]
	[1] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[8] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[9] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[12] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[16] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[17] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[18] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[19] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[20] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[21] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[28] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[29] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[30] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafbc00 - 0xfeafbcff (0x100) MX[B]
	[5] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[12] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[18] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[22] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[23] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[24] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[25] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[26] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[27] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[34] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[35] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[36] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.51.3
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.51.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.512                    
(II) ATI Proprietary Linux Driver Build Date: Jul  3 2008 22:50:40
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7280) found
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafbc00 - 0xfeafbcff (0x100) MX[B]
	[5] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[12] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[18] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[22] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[23] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[24] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[25] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[26] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[27] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[34] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[35] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[36] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820c650
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafbc00 - 0xfeafbcff (0x100) MX[B]
	[5] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[12] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[21] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[27] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[28] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[29] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[30] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[37] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[38] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[39] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[40] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(**) fglrx(0): Option "MaxGARTSize" "512"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "Radeon X1950 Series" (Chipset = 0x7280)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0xe190)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xfe9f0000
(--) fglrx(0): I/O port at 0x0000c000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.13
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV570
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.51.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x20000000)
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 18f  Serial#: 1296707895
(II) fglrx(0): Year: 2005  Week: 31
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) fglrx(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HMEY817569
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004c2d8f0137314a4d
(II) fglrx(0): 	1f0f01036c221b782aaaa5a654549926
(II) fglrx(0): 	145054bfef808180714f010101010101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300520e1100001e000000fd00384b1e
(II) fglrx(0): 	510e000a202020202020000000fc0053
(II) fglrx(0): 	796e634d61737465720a2020000000ff
(II) fglrx(0): 	00484d45593831373536390a202000ad
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 581/702MHz @ 0Hz [enable load balancing]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 32 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (340, 270) mm
(--) fglrx(0): DPI set to (95, 96)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): Illegal ATI GART size: 512 MB, acceptable range: 64 MB - 255 MB. 
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f004a1b bridge: 0x8086/0x2570
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f004b1a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0x3758096384)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfeafbc00 - 0xfeafbcff (0x100) MX[B]
	[7] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[8] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[9] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[10] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[11] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[14] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[15] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[24] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[26] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[28] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[29] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[30] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[31] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[32] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[33] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[34] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[40] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[41] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[42] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[43] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.90
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.51.3
(II) fglrx(0):     Date: Jul  3 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-19-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00005000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface

```

Thanks any help!

---

### Post by jmacdallas on 2008-08-12
Jerjely, this is what did it for me.

[http://ubuntuforums.org/showthread.php?p=5505853#post5505853](http://ubuntuforums.org/showthread.php?p=5505853#post5505853)

---

### Post by garferi on 2008-10-18
ATi driver version 8.10 sooolved the problem on my Ubuntu Hardy Heron 8.04.1 system! :) 6 months needed to solve this, lol :D
Download it from [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run").
Put it to your home folder and copy the code to the terminal, than follow the instructions of the graphical installer.
```
sudo sh ati-driver-installer-8-10-x86.x86_64.run
```
After the installation paste these to terminal:
```
sudo aticonfig --initial -f
```
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

Restart your computer.

The newest driver in every month is [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html").
I also have Compiz-Fusion working, and about 4000 FPS in glxgears. :)
Now I have just one problem, the videos are blinking in the players. I have waiting for the solutions...
Thx!

Good luck All!

---

