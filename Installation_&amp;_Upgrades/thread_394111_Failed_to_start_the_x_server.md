---
title: "Failed to start the x server"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by arijarot on 2007-03-26
Hello I just upgraded to fiesty. during the installation i unwittingly replaced my gdm file and now it "failed to start the x server"... 

any suggestions would be appreciated as to what can be done...


thanks

---

### Post by floke on 2007-03-26
Not sure if this is entirely what you would want to do, but you could reinstall gdm.

From the terminal, first remove what you have (which doesn't work).
sudo apt-get remove gdm

then reinstall

sudo apt-get install gdm

Once done you can try: sudo /etc/init.d/gdm restart   to get it going

Not sure if this will work, or if it's the best way to do it, but maybe worth a go?

---

### Post by arijarot on 2007-03-26
Ok, I will try this... thank you.

---

### Post by arijarot on 2007-03-26
It didn't work...

---

### Post by floke on 2007-03-26
So what happened exactly?
Have you tried 'sudo startx'?

---

### Post by arijarot on 2007-03-26
i tried what you said as well as start x which gave the following:

fatal server error no screens found giving up

plus a bunch of other errors, but this seems to be the main point...

---

### Post by floke on 2007-03-26
A 'buch of other errors' might mean something to someone, so you should really post the output in full if you can. The 'no screens' indication indicates that something might be wrong with your xorg.conf file. So you could try this. From the terminal.

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by xueg0i on 2007-03-26
Don't panic

Please post your /etc/X11/xorg.conf and your error logs. Then we might be able to help out ;)

---

### Post by kellemes on 2007-03-27
/var/log/Xorg.0.log
This is the log that tells it al...

---

### Post by arijarot on 2007-03-27
the printout for the xorg.0.log is extremely long, too long for me to type it from my desktop's screen to another computer...

error output is now:

(EE) no devices detected

fatal screen error:
no sreens found
giving up
xinit:  connection reset by peer (errno 104): unable to connect to x server
xinit: no such process (errno 3): server error
xauth: error in locking authority file /home/.../.Xauthority

---

### Post by arijarot on 2007-03-27
> **Steve.K said:**
> A 'buch of other errors' might mean something to someone, so you should really post the output in full if you can. The 'no screens' indication indicates that something might be wrong with your xorg.conf file. So you could try this. From the terminal.

sudo dpkg-reconfigure -phigh xserver-xorg

thank you for the suggestion. i tried it. same errors as before.

---

### Post by swan on 2007-03-27
i had same/similar problem, i tried dpkg-reconfigure xserver-xorg twice, it worked when i didnt pick use frame buffer as an option

maybe somethingto do w/ nv, or that i dont have frame buffer in the kernel or something *shrug*

---

### Post by arijarot on 2007-03-27
> **swan said:**
> i had same/similar problem, i tried dpkg-reconfigure xserver-xorg twice, it worked when i didnt pick use frame buffer as an option

maybe somethingto do w/ nv, or that i dont have frame buffer in the kernel or something *shrug*

do you also have nvidia? i'll give it a go...

thanks for the suggestion. it didn't work, however. the error remains the same:confused:

---

### Post by xueg0i on 2007-03-29
I would like to help you out arijarot, but I need some more info.

Let's first try to get X working with VESA drivers. You can manually edit the configuration file for X. Just type:
```
sudo vi /etc/X11/xorg.conf
```
There are three area's that are important.
* The screen area, which defines the screen you are using.
* The device area, which defines which video driver to use.
* The ServerLayout area, which defines which of the screens and devices mentioned are used for X.

First look for something like this:
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```
Replace the line with Driver to:
```
Driver         "vesa"
```
If you don't know how to use vi, just type "man vi" in another terminal. It will explain the basic functionality of vi.

Now try to start X. If it doesn't work pm me.

Xueg0i.

---

### Post by arijarot on 2007-03-29
> **xueg0i said:**
> I would like to help you out arijarot, but I need some more info.

Let's first try to get X working with VESA drivers. You can manually edit the configuration file for X. Just type:
```
sudo vi /etc/X11/xorg.conf
```
There are three area's that are important.
* The screen area, which defines the screen you are using.
* The device area, which defines which video driver to use.
* The ServerLayout area, which defines which of the screens and devices mentioned are used for X.

First look for something like this:
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```
Replace the line with Driver to:
```
Driver         "vesa"
```
If you don't know how to use vi, just type "man vi" in another terminal. It will explain the basic functionality of vi.

Now try to start X. If it doesn't work pm me.

Xueg0i.

it worked, i used "vesa."  thank you, Xueg0i. but how do i get the videocard to work? the graphics are really slow now... the nvidia worked on all the other versions of ubuntu.
oh, and my hard drive labels changed from hda1,2,3... to sda1, 2, 3... what does that mean?

---

### Post by xueg0i on 2007-03-29
I'm glad it worked. Now you have your graphical environment back, which is easier to navigate then those terminals.

About the harddisk renaming, I do not know of any changes lately, but I think you shouldn't bother about them. They are probably not related to your graphics problems.

Did you use the nvidia drivers from the nvidia website or did you use the restricted drivers from the repositories?

First uninstall the drivers from the nvidia website (if you used them). Then get the latest restricted drivers:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```
If I'm not mistaken, the installer will ask you some questions. One of the questions is about changing xorg.conf. Say yes. Reboot and you should be fine.

Every next time synaptic says there are updates, look through the list. Sometimes there is a kernel update, but no update for the restricted drivers yet (it follows shortly after). In that case you should wait to update, or update and choose to boot from the previous kernel image from your grub menu till the restricted drivers are updated.

Xueg0i.

---

### Post by arijarot on 2007-03-29
Thank you, Xuegi0i, you've been most helpful :) I actually don't know what driver I have and since I'm back in X, here is a print out of my Xorg.0.log (I've put it in two posts as it is longer than the allowed 40,000 characters)

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686
Build Date: 29 March 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 29 11:45:32 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL E772c"
(**) |   |-->Device "nVidia Corporation NV17 [GeForce4 MX 420]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 1028,0142 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 01 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1028,0142 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1028,0142 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1028,0142 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1028,0142 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1028,0142 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1028,0142 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0172 card 10de,015a rev a3 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 14e4,4212 card 1028,0002 rev 02 class 07,03,00 hdr 00
(II) PCI: 02:02:0: chip 1102,0006 card 1102,1003 rev 00 class 04,01,00 hdr 80
(II) PCI: 02:02:1: chip 1102,7004 card 1102,1003 rev 00 class 09,80,00 hdr 80
(II) PCI: 02:08:0: chip 8086,1039 card 1028,0142 rev 81 class 02,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[1] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[2] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe100000 - 0xfe2fffff (0x200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 MX 420] rev 163, Mem @ 0xfc000000/24, 0xf4000000/26, 0xf3f80000/19, BIOS @ 0x80000000/17
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
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xefffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe1fe000 - 0xfe1fefff (0x1000) MX[B]
	[1] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[2] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[3] -1	0	0xfe300000 - 0xfe3003ff (0x400) MX[B]
	[4] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[5] -1	0	0xf0000000 - 0xf001ffff (0x20000) MX[B](B)
	[6] -1	0	0xf3f80000 - 0xf3ffffff (0x80000) MX[B](B)
	[7] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[8] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ec80 - 0x0000ecbf (0x40) IX[B]
	[10] -1	0	0x0000ece8 - 0x0000ecef (0x8) IX[B]
	[11] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[12] -1	0	0x0000ecf0 - 0x0000ecff (0x10) IX[B]
	[13] -1	0	0x0000dc80 - 0x0000dc9f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[20] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[21] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe1fe000 - 0xfe1fefff (0x1000) MX[B]
	[1] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[2] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[3] -1	0	0xfe300000 - 0xfe3003ff (0x400) MX[B]
	[4] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[5] -1	0	0xf0000000 - 0xf001ffff (0x20000) MX[B](B)
	[6] -1	0	0xf3f80000 - 0xf3ffffff (0x80000) MX[B](B)
	[7] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[8] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ec80 - 0x0000ecbf (0x40) IX[B]
	[10] -1	0	0x0000ece8 - 0x0000ecef (0x8) IX[B]
	[11] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[12] -1	0	0x0000ecf0 - 0x0000ecff (0x10) IX[B]
	[13] -1	0	0x0000dc80 - 0x0000dc9f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[20] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[21] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe1fe000 - 0xfe1fefff (0x1000) MX[B]
	[5] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[6] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[7] -1	0	0xfe300000 - 0xfe3003ff (0x400) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xf0000000 - 0xf001ffff (0x20000) MX[B](B)
	[10] -1	0	0xf3f80000 - 0xf3ffffff (0x80000) MX[B](B)
	[11] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000ec80 - 0x0000ecbf (0x40) IX[B]
	[16] -1	0	0x0000ece8 - 0x0000ecef (0x8) IX[B]
	[17] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[18] -1	0	0x0000ecf0 - 0x0000ecff (0x10) IX[B]
	[19] -1	0	0x0000dc80 - 0x0000dc9f (0x20) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[26] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[27] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 2.0.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	Quadro FX 5600, Quadro FX 4600
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce4 MX 420 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe1fe000 - 0xfe1fefff (0x1000) MX[B]
	[5] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[6] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[7] -1	0	0xfe300000 - 0xfe3003ff (0x400) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xf0000000 - 0xf001ffff (0x20000) MX[B](B)
	[10] -1	0	0xf3f80000 - 0xf3ffffff (0x80000) MX[B](B)
	[11] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000ec80 - 0x0000ecbf (0x40) IX[B]
	[16] -1	0	0x0000ece8 - 0x0000ecef (0x8) IX[B]
	[17] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[18] -1	0	0x0000ecf0 - 0x0000ecff (0x10) IX[B]
	[19] -1	0	0x0000dc80 - 0x0000dc9f (0x20) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[26] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[27] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]

```

---

### Post by arijarot on 2007-03-29
cont.

```
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe1fe000 - 0xfe1fefff (0x1000) MX[B]
	[5] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[6] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[7] -1	0	0xfe300000 - 0xfe3003ff (0x400) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xf0000000 - 0xf001ffff (0x20000) MX[B](B)
	[10] -1	0	0xf3f80000 - 0xf3ffffff (0x80000) MX[B](B)
	[11] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000ec80 - 0x0000ecbf (0x40) IX[B]
	[19] -1	0	0x0000ece8 - 0x0000ecef (0x8) IX[B]
	[20] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[21] -1	0	0x0000ecf0 - 0x0000ecff (0x10) IX[B]
	[22] -1	0	0x0000dc80 - 0x0000dc9f (0x20) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) NV(0): Initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce4 MX 420"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF4000000
(--) NV(0): MMIO registers at 0xFC000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: DEL  Model: d002  Serial#: 808464728
(II) NV(0): Year: 2003  Week: 11
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.631 redY: 0.328   greenX: 0.275 greenY: 0.600
(II) NV(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) NV(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) NV(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) NV(0): Serial No: 6418033D001X
(II) NV(0): Monitor name: DELL E772c
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff0010ac02d058313030
(II) NV(0): 	0b0d0103682018782e8aa9a154469924
(II) NV(0): 	0e484ca442003159455961598180714f
(II) NV(0): 	010101010101c31e0020410020301060
(II) NV(0): 	130036e61000001e000000ff00363431
(II) NV(0): 	3830333344303031580a000000fc0044
(II) NV(0): 	454c4c2045373732630a2020000000fd
(II) NV(0): 	0032a01e460b000a20202020202000fc
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) NV(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) NV(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) NV(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) NV(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) NV(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(--) NV(0): VideoRAM: 65536 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): DELL E772c: Using hsync range of 30.00-70.00 kHz
(II) NV(0): DELL E772c: Using vrefresh range of 50.00-160.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (mode clock too high)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (mode clock too high)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1152x864 (pitch 1152)
(**) NV(0): *Driver mode "1152x864": 104.0 MHz, 67.7 kHz, 74.8 Hz
(II) NV(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 56.8 MHz, 53.7 kHz, 84.9 Hz
(II) NV(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(**) NV(0): *Driver mode "640x480": 35.0 MHz, 42.9 kHz, 84.6 Hz
(II) NV(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(**) NV(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) NV(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) NV(0):  Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 84.9 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(**) NV(0):  Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) NV(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) NV(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0):  Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(**) NV(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(**) NV(0): Display dimensions: (320, 240) mm
(**) NV(0): DPI set to (91, 91)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf3f80000 - 0xf3ffffff (0x80000) MX[B]
	[1] 0	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B]
	[2] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfe1fe000 - 0xfe1fefff (0x1000) MX[B]
	[8] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[9] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[10] -1	0	0xfe300000 - 0xfe3003ff (0x400) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xf0000000 - 0xf001ffff (0x20000) MX[B](B)
	[13] -1	0	0xf3f80000 - 0xf3ffffff (0x80000) MX[B](B)
	[14] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[15] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000ec80 - 0x0000ecbf (0x40) IX[B]
	[22] -1	0	0x0000ece8 - 0x0000ecef (0x8) IX[B]
	[23] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[24] -1	0	0x0000ecf0 - 0x0000ecff (0x10) IX[B]
	[25] -1	0	0x0000dc80 - 0x0000dc9f (0x20) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[32] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[33] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xf4000000,0x4000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

---

### Post by arijarot on 2007-03-29
Oh, and in System, Administration, Restricted Drivers Manager, there is one driver: "NVIDIA accelerated graphics driver (legacy card)", not enabled.

---

### Post by xueg0i on 2007-03-29
your log looks ok, the driver used (NV) is the default for X. Did you try to update to the restricted drivers? With these you'll have accelerated graphics. Because you fiddled around with the xorg.conf file manually, the Restricted Drivers Manager might not work (just try it). If not try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And try again to switch on the restricted drivers in the Restricted Drivers Manager.

---

### Post by arijarot on 2007-03-29
> **xueg0i said:**
> your log looks ok, the driver used (NV) is the default for X. Did you try to update to the restricted drivers? With these you'll have accelerated graphics. Because you fiddled around with the xorg.conf file manually, the Restricted Drivers Manager might not work (just try it). If not try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And try again to switch on the restricted drivers in the Restricted Drivers Manager.

OK>... I enabled it through the Restricted drivers manager, then an update manager popped up and downloaded a "nvidia-glx-legacy" package... restarting system.... 

It worked (I think :confused: )... problem is that now my screen resolution is capped at 800x600; 60mhz ???:confused: 

Also, no matter how many times I restarted the computer the status of the driver would always say "computer needs to be rebooted" unless I disabled it, the status would simple be a red ball.

---

### Post by xueg0i on 2007-03-29
Linux is full of surprises :)

Did you already try:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```
System>Administration>Screen resolution might help, don't forget to restart X after the changes (Ctr-Alt-Backspace).

I'm going to bed now, for I have an exam tomorrow. I'll be available for support on saturday again.

---

### Post by arijarot on 2007-03-30
> **xueg0i said:**
> Linux is full of surprises :)

Did you already try:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```
System>Administration>Screen resolution might help, don't forget to restart X after the changes (Ctr-Alt-Backspace).

I'm going to bed now, for I have an exam tomorrow. I'll be available for support on saturday again.

It sure is. If I want accelerated graphics I have to have a ridiculusly slow refresh rate and a terribly low resolution. 
here is the results:
linux-restricted-modules-2.6.20-13-generic is already the newest version.
I should go and study for my finals too!

---

### Post by arijarot on 2007-03-31
see also [http://www.ubuntuforums.org/showthread.php?t=359367&page=8,#73](http://www.ubuntuforums.org/showthread.php?t=359367&page=8,#73)

---

### Post by Rich_li_ny on 2007-04-03
New install and having a couple problems.  I just installed Xbuntu 6.10 using the alternate CD ISO. This is what I get when I boot.


System Boots. 
I get error message: [COLOR="RoyalBlue"]"[17179569.184000] ACPI: Unable to locate RDSP[/COLOR]" and system contiunes with boot process. When it comes time for the Xbuntu logo and gui to display the monitor goes dead and LED on monitor goes from green to flashing amber (no video). 

When I press: "Control + Alt + Backspace" the LED on the monitor turns green for a sec and it attempts to do display something but then just goes back into a dead state.



To try to solve the problem I exited to a command prompt to try to manually set my video mode. This is what I did: 

Pressed "Control + ALT + F1 to get to a command prompt. On exit to a command prompt this is what is displayed:

Starting up ...
[17179569.184000] ACPI: Unable to Locate RSDP

usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600

Ubuntu 6.10 ubuntu tty1

Ubuntu login: _ 


Ok So it seems the 1024x768 isnt working with this and the 800x600 is fine (for a command prompt anyway) So I log in and try to make a change but I am a total noob and having some problems. This is what I tried to do next 

---------------------------------------------------------------------------------------
Attempted to create a new Xorg.config file.

Ran xorgconfig 

It did some kind of auto config and said my mouse failed.
While Running Config file this is what what displayed on the monitor:


Module Loader present

Markers: 
(--) probed, (**) from config file, (= =) default setting, (++) from command line, (!!) notice, 
(II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown


(= =) Log File "/varlog/Xorg.0.log"
(++) Using Config File: "root/xorg.conf.new" 
error opening security policy file /usr/lib/xserver/SecurityPolicy

(EE) xf86OpenSerial: Can not open device /dev/mouse
	No such file or directory.
(EE) Mouse 0 cannot open input device
(EE) PreInit failed for input device "Mouse0"

xkb_keycodes	 	{ include "xfree86+aliases(qwerty)" };
xkb_types		                { include "complete" };
xkb_compatability        	{ include "complete" };
xkb_symbols		{ include "pc(pc105)+us" };
xkb_geometry		{ include "pc(pc105: };
No core pointer

Fatal Server error:
failed to initialize core devices

OK.. So what do I have to do to get my Xorg config file right?  And why would my mouse fail?   This is an older machine and I did have a puppy distro working on it with 800x600. 
Can someone please tell me what I am doing wrong? There has to be a command I can use to get a selection of video modes/resolutions, test them out and save them.. 


Here are some notes of what works running live CD with Xorg on another distro.
800x600 24
Horizontal frequency 53.7214 Khz
Refresh Frequency   85.1369 Hz


I hope this is posted in the right place.  I am really new at this so if I made a mistake please forgive me.  


Any help is greatly appreciated 

Rich

---

### Post by xueg0i on 2007-04-03
Arijarot, It seems you have everything up and running now. I didn't know about "not relying on DPMS". Nice you found that one out!

Rich_li_ny, you should have posted a new thread I suppose, but since it is here I will try to help you anyways ;)

First some sugestions:
Try the non alternate CD first (if you hadn't before) to get rid of the error.
Post the error and warning messages from /var/log/Xorg.0.log (lines start with (EE) and (WW))

Xueg0i.

---

### Post by Rich_li_ny on 2007-04-03
[QUOTE=xueg0i;2395298]Arijarot, It seems you have everything up and running now. I didn't know about "not relying on DPMS". Nice you found that one out!

Rich_li_ny, you should have posted a new thread I suppose, but since it is here I will try to help you anyways ;)

First some sugestions:
Try the non alternate CD first (if you hadn't before) to get rid of the error.
Post the error and warning messages from /var/log/Xorg.0.log (lines start with (EE) and (WW))

Xueg0i.[/QUOTE

I cant run the non alternate CD cause my system specs are to low.
Current system Specs are:
PII 300
192 mb ram

Matrix 16 mb AGP Video card.  

Trying to get log now. But am a total noobie at Linux.  Will post it once iI figure out how to get it.    

Thanks,
Rich

This is also second install. First was with text installation.  After running into problems reinstalled using OEM selection in hopes of better results but wound up with the same thing in the end. 
Rich

---

### Post by jrmartin on 2007-06-05
When starting my computer to reconfigure the x server stuff, I have to log in as root to change files.  How can I do this?  I tried typing root as the login and my usual password, but it's not working.

---

### Post by jrmartin on 2007-06-07
nevermind, got it.

---

