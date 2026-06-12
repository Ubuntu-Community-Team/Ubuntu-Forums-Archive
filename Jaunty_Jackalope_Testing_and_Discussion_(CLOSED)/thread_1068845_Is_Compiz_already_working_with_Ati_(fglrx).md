---
title: "Is Compiz already working with Ati (fglrx)?"
date: 2009-02-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-02-13
Hardware Drivers shows "Ati Fire GL" as activated - (although it's acutally a "Radeon Mobility X700"), but Compiz isn't working on my machine.

I tried reinstalling the fglrx drivers,
"dpkg-reconfigure xserver-xorg", editing xorg.conf - but still:

```
$  compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/usr/bin/compiz: line 421: 12366 Segmentation fault      ${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS

```

```
$ grep EE /var/log/Xorg.0.log
	[    0.036562] (WW) warning, [    0.036579] (EE) error, [    0.036595] (NI) not implemented, [    0.036612] (??) unknown.
[    0.552947] (II) Loading extension MIT-SCREEN-SAVER
[    0.553797] (EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
[    0.553814] (EE) Failed to load module "glx" (loader failed, 7)
[    0.581530] (EE) module ABI major version (1) doesn't match the server's version (2)
[    0.581556] (EE) Failed to load module "dri" (module requirement mismatch, 0)

```

```
$ LIBGL_DEBUG=verbose fglrxinfo 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault

```

```
$ dmesg | grep fglrx
[   19.909133] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   20.017049] [fglrx] Maximum main memory to use for locked dma buffers: 1885 MBytes.
[   20.017389] [fglrx]   vendor: 1002 device: 5653 count: 1
[   20.017856] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   20.018761] [fglrx] Driver built-in PAT support is enabled successfully
[   20.018912] [fglrx] module loaded - fglrx 8.57.2 [Jan 14 2009] with 1 minors
[  478.215516] fglrxinfo[11833]: segfault at 540 ip b7f4b9ad sp bf8bcb6c error 4 in libX11.so.6.2.0[b7f0a000+ea000]

```

```
$ dmesg | grep glxinfo
[   90.652409] glxinfo[5504]: segfault at 18 ip b800cc3a sp bfba09b8 error 4 in libGL.so.1.2[b7fdb000+83000]
[   90.668901] glxinfo[5508]: segfault at 18 ip b7f81c3a sp bff16508 error 4 in libGL.so.1.2[b7f50000+83000]
[   90.730565] glxinfo[5517]: segfault at 18 ip b800bc3a sp bfa9e0b8 error 4 in libGL.so.1.2[b7fda000+83000]
[   91.277454] glxinfo[5541]: segfault at 18 ip b7fe7c3a sp bfe7a488 error 4 in libGL.so.1.2[b7fb6000+83000]
[  145.690323] glxinfo[6658]: segfault at 18 ip b7efec3a sp bfd92728 error 4 in libGL.so.1.2[b7ecd000+83000]
[  507.929518] glxinfo[12353]: segfault at 18 ip b7f28c3a sp bf9bab48 error 4 in libGL.so.1.2[b7ef7000+83000]
[  507.936541] glxinfo[12356]: segfault at 18 ip b7ff6c3a sp bf8889f8 error 4 in libGL.so.1.2[b7fc5000+83000]
[  507.946881] glxinfo[12358]: segfault at 18 ip b7fd2c3a sp bff648f8 error 4 in libGL.so.1.2[b7fa1000+83000]
[  508.034159] glxinfo[12362]: segfault at 18 ip b8047c3a sp bfbd9568 error 4 in libGL.so.1.2[b8016000+83000]

```

---

### Post by excogitation on 2009-02-14
Is nobody with an Ati graphics card on Jaunty?

---

### Post by Gina on 2009-02-14
I have ATI graphics in a couple of my machines, one of which is running Jaunty (laptop) but I'm not using Compiz.

---

### Post by inportb on 2009-02-14
Here I am, but I use the radeon driver which works nicely.

---

### Post by jocko on 2009-02-15
Compiz works just fine with fglrx, it's fglrx which doesn't work with the xserver version in jaunty, which is why you get these errors:
```
[    0.553797] [COLOR=Red](EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so[/COLOR]
[    0.553814] [COLOR=Red](EE) Failed to load module "glx" (loader failed, 7)[/COLOR]
[    0.581530][COLOR=Red] (EE) module ABI major version (1) doesn't match the server's version (2)[/COLOR]
[    0.581556] [COLOR=Red](EE) Failed to load module "dri" (module requirement mismatch, 0)[/COLOR]
```
You could try this:
```
gksudo gedit /etc/X11/xorg.conf
```And add this line to the serverflags section:
```
Section "ServerFlags"
[COLOR=Blue]Option "IgnoreABI" "True"[/COLOR]
EndSection
```This option should make xorg try to load modules even if they are not built on the correct xorg version. Note that I'm not sure if fglrx work with this option and if it does there's probably no guarantee that it will be stable.

---

