---
title: "X server not starting: failed to open DRM connection"
date: 2008-12-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hardhu on 2008-12-04
Hello everybody,
after yesterday upgrade, my notebook (Acer 5024, AMD Turion ML-24, Ati Mobility Radeon X700, using fglrx) doesn't start anymore in graphical mode. Looking at Xorg.0.log, the last line says:

```
(WW) fglrx(0): Failed to open DRM connection
```

Any help is appreciated.

---

### Post by hardhu on 2008-12-04
> **hardhu said:**
> Hello everybody,
after yesterday upgrade, my notebook (Acer 5024, AMD Turion ML-24, Ati Mobility Radeon X700, using fglrx) doesn't start anymore in graphical mode. Looking at Xorg.0.log, the last line says:

```
(WW) fglrx(0): Failed to open DRM connection
```

Any help is appreciated.

Update: the X server starts correctly using radeon driver, so it appears to be a fglrx related problem.

---

### Post by hardhu on 2008-12-04
> **hardhu said:**
> Update: the X server starts correctly using radeon driver, so it appears to be a fglrx related problem.

Update again: but also with radeon driver I get problems with DRM; here's the line form Xorg.0.log:

```
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
```

---

### Post by ScislaC on 2008-12-04
Same problem here. :(

---

### Post by ]FT[ on 2008-12-05
Same problem here :(

---

### Post by jarkko23 on 2008-12-08
There's directory dri in dev;

me@gandalf:/dev$ ls -l /dev/dri
ls: cannot access /dev/dri: No such file or directory
me@gandalf:/dev$ 

(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
...
(WW) fglrx(0): Failed to open DRM connection


Maybe there's some kernel module not being loaded?

Found other post about the issue here [http://www.linuxquestions.org/questions/slackware-14/ww-fglrx0-failed-to-open-drm-connection-2.6.27.8-688861/](http://www.linuxquestions.org/questions/slackware-14/ww-fglrx0-failed-to-open-drm-connection-2.6.27.8-688861/)

---

### Post by NCLI on 2008-12-13
You're not alone, the fglrx driver doesn't work for me either, but the open radeon driver works perfectly, compiz enabled.

[http://ubuntuforums.org/showpost.php?p=5795292&postcount=25](http://ubuntuforums.org/showpost.php?p=5795292&postcount=25)

---

### Post by danf_1979 on 2008-12-13
I'm using fglrx and X is ok, but I have no 3D acceleration (Xorg log says so).

For example, executing glxgears, glxinfo, warzone2001, etc, result in:

```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

I don't use compiz, so I really don't care, but its a bug anyway.

What version of fglrx are you using? and could you please provide /etc/X11/xorg.conf ? I wonder why you're without X using fglrx.

---

### Post by ]FT[ on 2009-01-28
UP
Fglrx still isn't working well!!!

```

ft@deadware:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

```

(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0                                                                                                 
(WW) Video driver ABI version of the X server is 4.1                                                                                                                                                  
(WW) fglrx(0): Failed to open DRM connection                                                                                                                                                          
(EE) fglrx(0): [FB] Can not get FB MC address range.                                                                                                                                                  
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): No DRM connection for driver fglrx.
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

---

