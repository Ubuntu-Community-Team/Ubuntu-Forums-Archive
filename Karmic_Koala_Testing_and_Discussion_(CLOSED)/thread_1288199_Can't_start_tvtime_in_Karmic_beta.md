---
title: "Can't start tvtime in Karmic beta"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by paulhurleyuk on 2009-10-11
Hello,

I've installed mythbuntu karmic beta on an HP Compaq Evo D530,

```
uname -a
Linux mythb 2.6.31-13-generic #44-Ubuntu SMP Sat Oct 10 15:27:55 UTC 2009 i686 GNU/Linux
```

When I try to run tvtime I get this error about hardware overlays
 
```
paul@mythb:/dev/dvb$ tvtime -v
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/paul/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/paul/.tvtime/tvtime.xml: Permission denied.
cpuinfo: CPU Intel(R) Pentium(R) 4 CPU 2.66GHz, family 15, model 2, stepping 9.
cpuinfo: CPU measured at 2660.193MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10604000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1024x768.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Xfwm4 and is EWMH compliant.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
```

The Evo has an Intel 82865G onboard graphics chip;

```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

Any Ideas ?

Paul.

---

### Post by paulhurleyuk on 2009-10-13
I've installed 8.04 LTS on this same box to confirm, and yes, tvtime and xawtv both run with no problems, so this is due to silly beggers playing about with the intel driver !

OOOOhhhhhhhh....

---

