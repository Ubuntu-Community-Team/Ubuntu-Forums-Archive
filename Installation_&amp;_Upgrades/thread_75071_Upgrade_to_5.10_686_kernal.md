---
title: "Upgrade to 5.10 686 kernal?"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by jdawdy on 2005-10-13
I have 5.04 with the 686 rebuilt kernal.  Is it possible to upgrade to 5.10 686 kernal or will I need to upgrade, then recompile?

I am leery of upgrading...I have an idea it would be better to format the linux partition and then reinstall 5.10 from a cd and then proceed to the kernel recompile.

Jim

---

### Post by mariner09 on 2005-10-13
I think just upgrading the kernel would open the door to numerous issues.  

Your best bet would be to do a fresh install and then just install the 686 kernel.

---

### Post by herot on 2005-10-13
a further question

if i have a Athlon XP processor, do i need to be running the i686 kernel instead of the i386 kernel?

if so, what are the benefits?

---

### Post by imagine on 2005-10-13
[QUOTE=herot]if i have a Athlon XP processor, do i need to be running the i686 kernel instead of the i386 kernel?[/QUOTE]
No. You can, but you don't have to. An i686-processor can also use the i386-kernel, but not vice versa.

[QUOTE=herot]if so, what are the benefits?[/QUOTE]The i686 package of the kernel should give you a better performance than the i386-version, since it can use some additional intructions which are not available to the 80386/80486 architecture.

As a general note, everything above and including the Pentium 1 Pro is a i686 processor.

---

### Post by earth_walker on 2005-10-13
I had 5.04 with the 686 kernel on a dell optiplex gx260, and had no issues upgrading to breezy through apt-get (other than having to reconfigure my xorg display settings, but that's another issue).

---

### Post by ProPilot on 2005-10-13
I have the i386 on an i686 machine and would like to ubgrade but being a nOOb would like the assistance of a comprehensive HowTo to ensure all the right steps are taken. Is there one?

---

### Post by AgenT on 2005-10-13
If you currently have the 686 kernel then this will be replaced by the newer version of the 686 kernel if you UPGRADE. If you do a clean install, all you will have to do is just install the 686 kernel. You don't have to edit anything since all that is done for you. After you reboot, your new kernel will be used.

The package you want to install is: ```
linux-686
```

After reboot, make sure you are booted into your new kernel by using this command: ```
uname -r
``` And if everything works correctly, you can remove your 386 kernel packages if you wish to (it's not manditory and you can always have the 386 kernel for backup).

---

### Post by vladuz976 on 2005-10-13
[QUOTE=herot]a further question

if i have a Athlon XP processor, do i need to be running the i686 kernel instead of the i386 kernel?

if so, what are the benefits?[/QUOTE]

if you have an amd athlon xp, why don't you use the k7 kernel instead of the regular 686?

---

### Post by ProPilot on 2005-10-13
I have Breezy installed with the 386 kernel since Sep. I will not be doing a clean install but do wish to upgrade the kernel to the 686 which this computer is capable of.

A howto would be nice but failing that complete instructions here would be great as well.

Thanks - Breezy works great (except sound)

---

### Post by vladuz976 on 2005-10-14
[QUOTE=ProPilot]I have Breezy installed with the 386 kernel since Sep. I will not be doing a clean install but do wish to upgrade the kernel to the 686 which this computer is capable of.

A howto would be nice but failing that complete instructions here would be great as well.

Thanks - Breezy works great (except sound)[/QUOTE]


Didn't you read AgenT's instructions above?

do 
```
uname -r
```

if it says i686 then use synaptic or apt-get or aptitude to insall the package "linux-686" which will AUTOMATICALLY pull all the packages needed for you!  from then on when you update/upgrade with apt-get or synaptic both kernels will be updated.  If you see that the i686 kernel works ok, then you could remove the i386 kernel even, using synaptic.  Also, if you know you have an AMD Athlon XP rater than some pentium 4.  you can get the "linux-k7" package instead of the "linux-686" one. that matches the amd architecture closer.
hope this helps.

---

### Post by herot on 2005-10-14
i have just upgraded my kernel from *-386 to *-k7

i did:
```
apt-get install linux-k7
```
it updated my grub menu and added the k7 kernel as my top choice...
when i booted everything seems to work great!!
it seems a decent bit more responsive as well!
thanks for the help guys!

would i benefit from REcompiling my kernel now??
```

herot@slasheru:~$ uname -r
2.6.12-9-k7
herot@slasheru:~$

```

---

### Post by ProPilot on 2005-10-14
valduz976 - Thank you for the clarification - yes I did read however I did not understand that by selecting just the one item that all of the other required items would be automatically selected for me.

I appreciate the patience that is shown so that this nOOb can come up to speed on such a great system.

---

### Post by haddog on 2005-10-14
What about the AMD Sempron processor? I have the 3000+ and 1.5G meg of DDR ram.  What is the best/optmized kernel to use?

---

### Post by ProPilot on 2005-10-14
I have just upgraded to the 686 kernel successfully. Thank you everyone.

---

### Post by ProPilot on 2005-10-14
haddog
It looks like the sempron is a K8 equivalant chip. I do not know if the K7 kernel will work with this processor.

---

### Post by LongTooth on 2005-10-16
I'm running a AMD processon on my PC, a Sempron 2800+. I too have questions about a kernal upgrade. Would an upgrade to a 'k7' be of any benefit? Should I upgrade to a 'k7' or wait? These are questions I'd like to know the answer to. If I'm not mistaken, there are a lot of AMD user here. Maybe I'm not the only one who wnat to know. 

Thanks.

---

### Post by AgenT on 2005-10-16
Just use the 686 kernel! Installing the K7 kernel or whatnot will not give you much, if any, noticable speed increase. The reason why is too technical and complex to bother explaining here. Not to mention one would need someone more qualified to explain it. There was a nice article made for (or by) Debian that explained this. Maybe someone can find it. Similar for upgrading from 386 to 686, except that the 686 kernel has some major advantages for some hardware like ability to use 1GB memory and above. The difference speed wise is very minimal, if anything at all.

---

### Post by jdawdy on 2005-10-17
I should have  mentioned I was using a custom kernal, not the stock kernal, so I figured upgrading wouldnt  do the trick anyway.  I had recompiled the kernal so my webcam woul work.


I ended up deleting the 5.04 installation, installing 5.10, and then using synaptic to install the 686 kernal.


5.10 is running much better on my HP compaq laptop!

---

### Post by vladuz976 on 2005-10-17
[QUOTE=AgenT]Just use the 686 kernel! Installing the K7 kernel or whatnot will not give you much, if any, noticable speed increase. The reason why is too technical and complex to bother explaining here. Not to mention one would need someone more qualified to explain it. There was a nice article made for (or by) Debian that explained this. Maybe someone can find it. Similar for upgrading from 386 to 686, except that the 686 kernel has some major advantages for some hardware like ability to use 1GB memory and above. The difference speed wise is very minimal, if anything at all.[/QUOTE]


So you are saying that the k7 kernel doesn't support 1GB memory or more?

---

### Post by AgenT on 2005-10-17
[quote=vladuz976]So you are saying that the k7 kernel doesn't support 1GB memory or more?[/quote]

No, I am only saying that the 386 kernel does not support high amounts of memory. I have no idea about the k7 kernel but my guess would be that it has all the advantages of 686.

---

### Post by zingibong on 2005-10-17
I have AMD Sempron 2800+ and Ubuntu 5.10
I have just installed both 686 and k7, one after another to see what will be chosen automatically by the system after rebooting. It has chosen k7 and so far it is running well.

---

### Post by herot on 2005-10-17
> I have just installed both 686 and k7, one after another to see what will be chosen automatically by the system after rebooting. It has chosen k7 and so far it is running well.

zingibong, the system does not automagically choose which kernel you want to run. you have to do that. it just picks the last one that was just installed and/or possibly the latest version number at the very least but im not sure about that last part

---

### Post by AgenT on 2005-10-19
Unless something goes wrong, the last kernel you install will be the one that will be booted by grub. Everytime you install a kernel it installs its own entry in grub as the first entry to try and boot. If you wish to choose a different kernel, you would either have to edit the grub configuration file, uninstall the other kernels, reinstall the kernel you wish to have booted first or just manually choose a different kernel at boot.

---

### Post by anonOmus on 2005-10-19
wow!

Huge difference in video performance for me! when i switched over the kernal! :KS  What happens when I tune the kernal?! even more?!

Yee haaa

I wish it was thin easy to swap out a kernal in solaris!

---

### Post by haddog on 2005-10-27
Installed the k7 kernel. Don't notice any speed increase but no decrease either.

---

### Post by Felipe_U on 2005-11-03
Hello,
      I just installed the 686 kernel and now the X won't start, it says that te NVIDIA module won't load, I'll post the Xorg log below. I have GFORCE 2 MX 200 with the Nvidial legacy package installed and worked properly with the 386 kerne.

```


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux wolverine 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-686 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:25:32 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  3 19:59:18 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1130 card 8086,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 8086,2442 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 8086,2442 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 8086,2442 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 8086,2442 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2445 card 8384,7608 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0111 card 0000,0000 rev b2 class 03,00,00 hdr 00
(II) PCI: 02:0a:0: chip 1317,0985 card 1113,1216 rev 11 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
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
	[0] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xde000000 - 0xdfffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] rev 178, Mem @ 0xdc000000/24, 0xd0000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdbffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdf000000 - 0xdf0003ff (0x400) MX[B]
	[1] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[2] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[3] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[4] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[5] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[6] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[7] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[8] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[9] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdf000000 - 0xdf0003ff (0x400) MX[B]
	[1] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[2] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[3] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[4] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[5] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[6] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[7] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[8] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[9] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf0003ff (0x400) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[15] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(WW) Ignoring request to load module GLcore
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7174
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7174
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7174  Tue Mar 22 06:48:37 PST 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf0003ff (0x400) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[15] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf0003ff (0x400) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[18] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[22] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xDC000000
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

Greetings,
Felipe

---

### Post by jetpeach on 2006-02-18
is this really worth it?  can anybody link to benchmarks showing noticable differences in the speed of things?  I am worried about something like in Felipes post happening where I can't get it working right again, and also that certain applications might fail after I install the 686 or k7 kernel because they are meant only for the 386...

---

### Post by Tibor60 on 2006-02-18
I was using the 686 kernel, and it there was not any problem for a while. But the last automatic update trashed my 686 kernel and now I had to return to the 386 kernel with a lot of programs not working. So if you installed the 686 kernel I think it is wise to turn off the automatic update...

---

### Post by angkor on 2006-02-18
[QUOTE=jetpeach]is this really worth it?  can anybody link to benchmarks showing noticable differences in the speed of things?  I am worried about something like in Felipes post happening where I can't get it working right again, and also that certain applications might fail after I install the 686 or k7 kernel because they are meant only for the 386...[/QUOTE]

If it's worth it I don't know. MY system *felt* a bit more responsive after installing the k7 kernel (old sempron 2800+). It is however worth it if you have +1G of ram, because using the newer kernel it will be used fully in stead of 900MB something with the standard 386 kernel.

Don't worry about apps not working, they're all 386 kernels except for the k8 which are meant for amd64 procs. Felipes problem has to do with the installed nvidia-drivers. If you install a new kernel you need to reinstall the nvidia packages for the driver to work again (note that you don't have to do this with the usual kernel updates, those are just different versions of the same kernel).

So you can just give it a go, your old kernel will be available from the grub menu in case the new one doesn't work as you expected. And remember to reinstall the nvidia packages if you already have these installed.

---

### Post by angkor on 2006-02-18
[QUOTE=Felipe_U]Hello,
      I just installed the 686 kernel and now the X won't start, it says that te NVIDIA module won't load, I'll post the Xorg log below. I have GFORCE 2 MX 200 with the Nvidial legacy package installed and worked properly with the 386 kerne.
[/QUOTE]

as posted above:

reinstall the nvidia-packages and try again.

---

### Post by Mustard on 2006-02-18
[QUOTE=Felipe_U]Hello,
      I just installed the 686 kernel and now the X won't start, it says that te NVIDIA module won't load, I'll post the Xorg log below. I have GFORCE 2 MX 200 with the Nvidial legacy package installed and worked properly with the 386 kernel.
Greetings,
Felipe[/QUOTE]

This is due to the linux-restricted-module for your kernel version not being installed.

If I recall correctly the command to install is this..
```
sudo apt-get install linux-restricted-module-`uname -r`
```

..where uname -r is the version of your currently running kernel.

---

### Post by tekwarren on 2006-02-21
I had an issue upgrading to the 686-smp kernal where gnome wouldn't start either. Do I run run the restricted modules command and then try the upgrade? I am currently on the default 386 kernal WITH the latest nvidia drivers.



-newb :-k

---

### Post by tekwarren on 2006-02-21
when running the command above I get:

E: Couldn't find package linux-restricted-module-2.6.12-10-386

---

### Post by angkor on 2006-02-21
[QUOTE=tekwarren]when running the command above I get:

E: Couldn't find package linux-restricted-module-2.6.12-10-386[/QUOTE]

Try again with:

```
sudo apt-get install linux-restricted-module**s**-2.6.12-10-386
```

;)

---

### Post by Mustard on 2006-02-21
Ah ok, my recollection was not as good as I thought. :)

It's linux-restricted-**modules**..  not linux-restricted-**module**... I forgot the 's' on modules.

---

### Post by tekwarren on 2006-02-21
ok I'll give that a shot on my laptop in the morning. So I just need to do this and THEN do the normal kernal upgrade to 686-smp ?


Thanks again

---

