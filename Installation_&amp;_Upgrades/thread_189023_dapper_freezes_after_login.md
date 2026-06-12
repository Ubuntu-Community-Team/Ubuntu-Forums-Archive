---
title: "dapper freezes after login"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by beatgeek on 2006-06-04
I upgraded to dapper from breezy last night, and when I rebooted (into the new 2.6 kernel, I think it's version 23?), the login screen comes up fine, and it looks like my computer is going to give me my desktop - it even goes so far as to show me my desktop background - but then it freezes before the taskbars can come up. No keyboard commands work.

I tried booting into the old 2.6-10 and 2.6-9 kernels, and those work fine. I heard dapper integrated smp into the new kernel, so i wonder if that has anything to do with it, since I have an intel 4 HT processor. One note though is that I have not installed any smp kernels, even back with breezy.

I also wondered if my wireless pmcia card (I have a laptop) might be causing problems in the new kernel, since when the computer's frozen, the card has one unblinking light, as opposed to the usual two blinking lights that tell me it's working. However, when I booted without the card in my laptop, it still froze.

I'm considering wiping everything and doing a clean install since there might be some detritus left over from previous struggles with trying to get ubuntu to work, unless anyone has any suggestions.

(edit) Also, I have an ATI mobility 9600.

---

### Post by garba on 2006-06-04
[QUOTE=beatgeek]I upgraded to dapper from breezy last night, and when I rebooted (into the new 2.6 kernel, I think it's version 23?), the login screen comes up fine, and it looks like my computer is going to give me my desktop - it even goes so far as to show me my desktop background - but then it freezes before the taskbars can come up. No keyboard commands work.
[/QUOTE]

you mean you get a hard lock? can you switch back to the console through ctrl-alt-f1 at least? if you can, login at the console and try a "killall gnome-panel", this helps when you have a faulty gnome-session

---

### Post by crowdofone on 2006-06-04
been having the same problem .. see my post [here]("http://ubuntuforums.org/showthread.php?t=145709") for a possible fix

---

### Post by beatgeek on 2006-06-06
ctrl-alt-f1 works, bringing me back to the command line, but kill-all-gnome-panel didn't do anything.

i also tried doing what crowdofone recommended, as well as other suggestions from that thread, and none of them worked.

startx returned an error about the server already being active for display 0. "If this server is no longer running, remove /tmp/.X0-lock and start again." So I did. I run startx again, and it starts doing things, but then I get an error:

(EE) failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) failed to load module "GLcore" (loader failed, 7)
(EE) fglrx(0): hardware already been looked
waiting for xserver to shut down Synaptics Deviceoff called .FreeFontPath "FPE" usr/share/X11/fonts/misc", refcount is 2, should be 1; fixing

i've also noticed that when i upgraded to dapper, my 3D acceleration ceased to work. fglrxinfo tells me things about mesa now. i tried installing linux-restricted-modules, xorg-driver-fglrx, etc, according to the ati ubuntu wiki. those first steps didn't work, so now i'm going to try the troubleshooting steps as according to the wiki. perhaps if i can get 3D acceleration back, my problem will go away.

---

### Post by beatgeek on 2006-06-06
ok, so i did the troubleshooting steps from the wiki: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

and i'm getting really weird problems now. now fglrxinfo isn't even telling me about mesa anymore- it's just giving me an error that says:
[4294791.302000]NET:Registered protocol family lo
[4294791.302000]lo: Disabled Privacy Extensions
[4294791.303000]ADDRCONF(NETDEV.UP): eth0: link is not ready
[4294791.302000]IPv6 over IPv4 tunneling driver
Error: unable to open display :0

also, xorg.conf is totally blank, as if i were trying to create a new file called xorg.conf (yes, i double checked the path).
"dmesg | grep fglrx" gives me nothing.
"nano /var/log/xorg.0.log" also gives me nothing but a blank file.

i guess i'll try "method 2" now...

---

### Post by beatgeek on 2006-06-06
ok, now that i'm in the gui (of the pre-dapper kernel), i'm getting useful error messages. dmesg | grep fglrx gives:

[4294716.816000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294716.818000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294716.819000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294719.312000] [fglrx:firegl_unlock] *ERROR* Process 4358 using kernel context 0

the first part of /var/log/Xorg.0.log, before it goes on ad infinitum, is as such:
```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux badger 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST $Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun  5 23:18:42 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 ($(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.$        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:un$(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1558,0500 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1558,0500 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1558,0500 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1558,0500 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1558,0500 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1558,0500 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1558,0500 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1558,0500 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1558,0800 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24d6 card 1558,0800 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e50 card 1558,0500 rev 00 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 1524,1410 card 4400,0000 rev 00 class 06,07,00 hdr 02
(II) PCI: 03:01:0: chip 104c,8026 card 1558,0500 rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:03:0: chip 10ec,8169 card 1558,0500 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
        [0] -1  0       0x00003000 - 0x000030ff (0x100) IX[B]
        [1] -1  0       0x00003400 - 0x000034ff (0x100) IX[B]
        [2] -1  0       0x00003800 - 0x000038ff (0x100) IX[B]
        [3] -1  0       0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xe8100000 - 0xe81fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
        [0] -1  0       0x00004000 - 0x000040ff (0x100) IX[B]
        [1] -1  0       0x00004400 - 0x000044ff (0x100) IX[B]
        [2] -1  0       0x00004800 - 0x000048ff (0x100) IX[B]
        [3] -1  0       0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
        [0] -1  0       0xe8200000 - 0xe82fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:0:0), (3,4,7), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 4 I/O range:
        [0] -1  0       0x00004400 - 0x000044ff (0x100) IX[B]
        [1] -1  0       0x00004800 - 0x000048ff (0x100) IX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] rev 0, $(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffff$(II) Active PCI resource ranges:
        [0] -1  0       0xe8204800 - 0xe82048ff (0x100) MX[B]
        [1] -1  0       0xe8200000 - 0xe8203fff (0x4000) MX[B]
        [2] -1  0       0xe8204000 - 0xe82047ff (0x800) MX[B]
        [3] -1  0       0xe8000800 - 0xe80008ff (0x100) MX[B]
        [4] -1  0       0xe8000c00 - 0xe8000dff (0x200) MX[B]
        [5] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [6] -1  0       0xe8000000 - 0xe80003ff (0x400) MX[B]
        [7] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [8] -1  0       0xe8100000 - 0xe810ffff (0x10000) MX[B](B)
        [9] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [10] -1 0       0x00004000 - 0x000040ff (0x100) IX[B]
        [11] -1 0       0x00001c00 - 0x00001c7f (0x80) IX[B]
        [12] -1 0       0x00001800 - 0x000018ff (0x100) IX[B]
        [13] -1 0       0x00001c80 - 0x00001cbf (0x40) IX[B]
        [14] -1 0       0x00001400 - 0x000014ff (0x100) IX[B]
        [15] -1 0       0x00002040 - 0x0000205f (0x20) IX[B]
        [16] -1 0       0x00002060 - 0x0000206f (0x10) IX[B]
        [17] -1 0       0x00002020 - 0x0000203f (0x20) IX[B]
        [18] -1 0       0x00002000 - 0x0000201f (0x20) IX[B]
        [19] -1 0       0x00001ce0 - 0x00001cff (0x20) IX[B]
        [20] -1 0       0x00001cc0 - 0x00001cdf (0x20) IX[B]
        [21] -1 0       0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xe8204800 - 0xe82048ff (0x100) MX[B]
        [1] -1  0       0xe8200000 - 0xe8203fff (0x4000) MX[B]
        [2] -1  0       0xe8204000 - 0xe82047ff (0x800) MX[B]
        [3] -1  0       0xe8000800 - 0xe80008ff (0x100) MX[B]
        [4] -1  0       0xe8000c00 - 0xe8000dff (0x200) MX[B]
        [5] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [6] -1  0       0xe8000000 - 0xe80003ff (0x400) MX[B]
        [7] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [8] -1  0       0xe8100000 - 0xe810ffff (0x10000) MX[B](B)
        [9] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [10] -1 0       0x00004000 - 0x000040ff (0x100) IX[B]
        [11] -1 0       0x00001c00 - 0x00001c7f (0x80) IX[B]
        [12] -1 0       0x00001800 - 0x000018ff (0x100) IX[B]
        [13] -1 0       0x00001c80 - 0x00001cbf (0x40) IX[B]
        [14] -1 0       0x00001400 - 0x000014ff (0x100) IX[B]
        [15] -1 0       0x00002040 - 0x0000205f (0x20) IX[B]
        [16] -1 0       0x00002060 - 0x0000206f (0x10) IX[B]
        [17] -1 0       0x00002020 - 0x0000203f (0x20) IX[B]
        [18] -1 0       0x00002000 - 0x0000201f (0x20) IX[B]
        [19] -1 0       0x00001ce0 - 0x00001cff (0x20) IX[B]
        [20] -1 0       0x00001cc0 - 0x00001cdf (0x20) IX[B]
        [21] -1 0       0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe8204800 - 0xe82048ff (0x100) MX[B]
        [5] -1  0       0xe8200000 - 0xe8203fff (0x4000) MX[B]
        [6] -1  0       0xe8204000 - 0xe82047ff (0x800) MX[B]
        [7] -1  0       0xe8000800 - 0xe80008ff (0x100) MX[B]
        [8] -1  0       0xe8000c00 - 0xe8000dff (0x200) MX[B]
        [9] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [10] -1 0       0xe8000000 - 0xe80003ff (0x400) MX[B]
        [11] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [12] -1 0       0xe8100000 - 0xe810ffff (0x10000) MX[B](B)
        [13] -1 0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x00004000 - 0x000040ff (0x100) IX[B]
        [17] -1 0       0x00001c00 - 0x00001c7f (0x80) IX[B]
        [18] -1 0       0x00001800 - 0x000018ff (0x100) IX[B]
        [19] -1 0       0x00001c80 - 0x00001cbf (0x40) IX[B]
        [20] -1 0       0x00001400 - 0x000014ff (0x100) IX[B]
        [21] -1 0       0x00002040 - 0x0000205f (0x20) IX[B]
        [22] -1 0       0x00002060 - 0x0000206f (0x10) IX[B]
        [23] -1 0       0x00002020 - 0x0000203f (0x20) IX[B]
        [24] -1 0       0x00002000 - 0x0000201f (0x20) IX[B]
        [25] -1 0       0x00001ce0 - 0x00001cff (0x20) IX[B]
        [26] -1 0       0x00001cc0 - 0x00001cdf (0x20) IX[B]
        [27] -1 0       0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXL$
[B](EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)[/B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
 compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"

       compiled for 7.0.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.0.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4

(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 6.8.99.8, module version = 8.25.18
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
 Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 6.99.99.904, module version = 1.0.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) ATI Radeon/FireGL: The following chipsets are supported:
        RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
blah blah blah
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.25.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.25g1
(II) ATI Proprietary Linux Driver Build Date: May 18 2006 09:54:44
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.25.1-driver-lnx-268237
(--) Chipset MOBILITY RADEON 9600/9700 (M10/M11 4E50) found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe8204800 - 0xe82048ff (0x100) MX[B]
        [5] -1  0       0xe8200000 - 0xe8203fff (0x4000) MX[B]
        [6] -1  0       0xe8204000 - 0xe82047ff (0x800) MX[B]
        [7] -1  0       0xe8000800 - 0xe80008ff (0x100) MX[B]
        [8] -1  0       0xe8000c00 - 0xe8000dff (0x200) MX[B]
        [9] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [10] -1 0       0xe8000000 - 0xe80003ff (0x400) MX[B]
        [11] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [12] -1 0       0xe8100000 - 0xe810ffff (0x10000) MX[B](B)
        [13] -1 0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x00004000 - 0x000040ff (0x100) IX[B]
        [17] -1 0       0x00001c00 - 0x00001c7f (0x80) IX[B]
        [18] -1 0       0x00001800 - 0x000018ff (0x100) IX[B]
 [19] -1 0       0x00001c80 - 0x00001cbf (0x40) IX[B]
        [20] -1 0       0x00001400 - 0x000014ff (0x100) IX[B]
        [21] -1 0       0x00002040 - 0x0000205f (0x20) IX[B]
        [22] -1 0       0x00002060 - 0x0000206f (0x10) IX[B]
        [23] -1 0       0x00002020 - 0x0000203f (0x20) IX[B]
        [24] -1 0       0x00002000 - 0x0000201f (0x20) IX[B]
        [25] -1 0       0x00001ce0 - 0x00001cff (0x20) IX[B]
        [26] -1 0       0x00001cc0 - 0x00001cdf (0x20) IX[B]
        [27] -1 0       0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81db850
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe8204800 - 0xe82048ff (0x100) MX[B]


[5] -1  0       0xe8200000 - 0xe8203fff (0x4000) MX[B]
        [6] -1  0       0xe8204000 - 0xe82047ff (0x800) MX[B]
        [7] -1  0       0xe8000800 - 0xe80008ff (0x100) MX[B]
        [8] -1  0       0xe8000c00 - 0xe8000dff (0x200) MX[B]
        [9] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [10] -1 0       0xe8000000 - 0xe80003ff (0x400) MX[B]
        [11] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [12] -1 0       0xe8100000 - 0xe810ffff (0x10000) MX[B](B)
        [13] -1 0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [14] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [15] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [16] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [17] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [18] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [19] -1 0       0x00004000 - 0x000040ff (0x100) IX[B]
        [20] -1 0       0x00001c00 - 0x00001c7f (0x80) IX[B]
[21] -1 0       0x00001800 - 0x000018ff (0x100) IX[B]
        [22] -1 0       0x00001c80 - 0x00001cbf (0x40) IX[B]
        [23] -1 0       0x00001400 - 0x000014ff (0x100) IX[B]
        [24] -1 0       0x00002040 - 0x0000205f (0x20) IX[B]
        [25] -1 0       0x00002060 - 0x0000206f (0x10) IX[B]
        [26] -1 0       0x00002020 - 0x0000203f (0x20) IX[B]
        [27] -1 0       0x00002000 - 0x0000201f (0x20) IX[B]
        [28] -1 0       0x00001ce0 - 0x00001cff (0x20) IX[B]
        [29] -1 0       0x00001cc0 - 0x00001cdf (0x20) IX[B]
        [30] -1 0       0x00003000 - 0x000030ff (0x100) IX[B](B)
        [31] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [32] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "MOBILITY RADEON 9600/9700 (M10/M11 4E50)" (Chipset = 0x4e50)
(--) fglrx(0): (PciSubVendor = 0x1558, PciSubDevice = 0x0500)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xf0000000
(--) fglrx(0): MMIO registers at 0xe8100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON 9600
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: P10
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 6.8.99.8, module version = 8.25.18
        ABI class: X.Org Server Extension, version 0.2
(EE) fglrx(0): Fail to initialize ASIC in kernel.
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MS_  Model: 6  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:Serration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 60  vid: 16497
(II) fglrx(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #5: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 162.0 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1600  h_sync: 1656  h_sync_end 1848 h_blank_end 2160 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1200  v_sync_end 1200 v_blanking: 1250 v_border: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 344/236MHz @ 60Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1656 1848 2160  1200 1202 1205 1250
(**) fglrx(0):  Default mode "1280x1024": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  162.00  1280 1496 1688 2160  1024 1113 1116 1250
(**) fglrx(0):  Default mode "1152x864": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz

blah blah blah, that gets through all the warnings before it talks about endless "no such device"s for drmOpenMinor


```

fglrxinfo once again gives:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by beatgeek on 2006-06-06
i ran into a snag with "method 2".
under "compiling the kernel module", when i do this:
sudo module-assistant build,install fglrx
i get an error message saying:
Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use.
If the running kernel has been shipped with the Debian  
           &#9474; distribution, please install the package
           &#9474; linux-headers-2.6.12-9-386. If your kernel source tree (or
           &#9474; headers) is located in some non-usual location, please set the
           &#9474; KERNELDIRS environment variable to the path of this directory, or
           &#9474; (alternatively) specify the source directory we build for with
           &#9474; the --kernel-dir option in module-assistant calls. 
 Package fglrx-kernel-source was not built successfully, see
           &#9474; /var/cache/modass/fglrx-kernel-source*buildlog* for details!

i assume it's trying to do things for the only kernel that works right now, 2.6.12-9-386. that's not what i want. i installed the kernel headers for the dapper kernel, and i still get this error message. where is this KERNELDIRS environment variable? is that what i need to change to get it to recognize the new kernel headers?

---

### Post by beatgeek on 2006-06-06
ok, i've read the post that says ati's dapper drivers are bugged. i'll give up on this for now.

---

