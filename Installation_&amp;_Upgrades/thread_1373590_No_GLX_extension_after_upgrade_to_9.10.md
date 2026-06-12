---
title: "No GLX extension after upgrade to 9.10"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by Keith_Beef on 2010-01-05
I upgraded a little over a week ago, and had noticed that I had no desktop effects. I wasn't really bothered by that, but tonight I tried to rn Blender, only to see this message.
```

$ blender
Compiled with Python version 2.6.4rc2.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:177: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x6e697274
  Serial number of failed request:  12
  Current serial number in output stream:  13
```

So I tried to find out why.
```
$ glxinfo 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault (core dumped)
```

Hey! What happened?

```
$ cat /var/log/Xorg.0.log | grep [EW][EW]
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(EE) open /dev/fb0: No such file or directory
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

No NVIDIA driver? OK, let's fix that.

```
$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G92 [GeForce 9800 GTX+] (rev a2)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
```

So, up pops a dialog telling me there are no proprietary drivers on the system. OK, that's not a great surprise. The dialog proposes verion 185 (recommended) or version 177. So I try to download and install version 185. This fails, with an alert "SystemError: installArchives() failed".

I opened up Synaptic, and found that the nvidia-185 packages were already installed. I chose to re-install them and also to remove an nvidia-180 package that was still around.

```
E: nvidia-185-kernel-source: subprocess installed post-installation script returned error exit status 127
E: nvidia-glx-185: dependency problems - leaving unconfigured
```

and

```
(Reading database ... 322950 files and directories currently installed.)
Removing nvidia-180-libvdpau ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 322943 files and directories currently installed.)
Preparing to replace nvidia-185-libvdpau 185.18.36-0ubuntu9 (using .../nvidia-185-libvdpau_185.18.36-0ubuntu9_amd64.deb) ...
Unpacking replacement nvidia-185-libvdpau ...
Preparing to replace nvidia-185-modaliases 185.18.36-0ubuntu9 (using .../nvidia-185-modaliases_185.18.36-0ubuntu9_amd64.deb) ...
Unpacking replacement nvidia-185-modaliases ...
Setting up nvidia-185-kernel-source (185.18.36-0ubuntu9) ...
/var/lib/dpkg/info/nvidia-185-kernel-source.postinst: 39: /usr/lib/dkms/common.postinst: not found
dpkg: error processing nvidia-185-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of nvidia-glx-185:
 nvidia-glx-185 depends on nvidia-185-kernel-source (>= 185.18.36); however:
  Package nvidia-185-kernel-source is not configured yet.
dpkg: error processing nvidia-glx-185 (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-185-libvdpau (185.18.36-0ubuntu9) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Setting up nvidia-185-modaliases (185.18.36-0ubuntu9) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nvidia-185-kernel-source
 nvidia-glx-185
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nvidia-185-kernel-source (185.18.36-0ubuntu9) ...
/var/lib/dpkg/info/nvidia-185-kernel-source.postinst: 39: /usr/lib/dkms/common.postinst: not found
dpkg: error processing nvidia-185-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of nvidia-glx-185:
 nvidia-glx-185 depends on nvidia-185-kernel-source (>= 185.18.36); however:
  Package nvidia-185-kernel-source is not configured yet.
dpkg: error processing nvidia-glx-185 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-185-kernel-source
 nvidia-glx-185
```


What am I doing wrong? I really want to get back GLX so I can run blender and an evaluation version of Varicad.

K.

---

