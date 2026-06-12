---
title: "System freeze at startup with ATI driver after upgrade to 7.10/8.04"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by Walldorf2000 on 2008-04-07
My system did run fine with 7.04. 3D acceleration etc. worked. 

After the upgrade to 7.10 it freezes during start up (even keyboard does not react on caps lock).

Changing driver from ATI to VESA fixed the problem but system is awfully slow.

Thus I upgraded to 8.04 but with exactly the same result.

When I boot from a 7.10 CD it shows the same result, too. When I dual boot to Win98 SE everything works still fine. Thus I guess my customizing is not relevant and the system does not have a hardware issue.

This is what I tried so far without any change in the symptoms:
 - use 7.04 kernel from my previously running system
 - update to the new driver from 04/04/2008 from here [https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)
 - delete xorg.conf or use old xorg.conf
 - remove the higher screen resolutions from my monitor settings
 - ati driver options in xorg.conf[INDENT]- Option "BusType" "PCI"
- Option "LVDSBiosNativeMode" "FALSE"
[/INDENT]

My system spec:
 - ATI Radeon 9250 AGP with 128 MB
 - Athlon 500
 - 512 MB

Which information is missing? What else can I try? Should I file a bug report?

---

### Post by Walldorf2000 on 2008-04-17
I filed a bug for this problem [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/214105](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/214105) and it was found that I was hit from two regressions.

[LIST=1]
[*]The radeon driver crashes with the default AGB Mode. A workaround is the following line in the device section for the ati driver
Option "AGPMode" "4"
[*]The new radeon driver does not like the monitor information in the xorg.conf which was built up in 7.04. The workaround was to remove the monitor section in xorg.conf. There is a bug filed in upstream for this problem [https://bugs.freedesktop.org/show_bug.cgi?id=15526](https://bugs.freedesktop.org/show_bug.cgi?id=15526)
[/LIST]

---

### Post by taita on 2008-04-21
Hi, I've had the same problem .. but if this happens while booting the live-cd/dvd ?!?!?! ...
I've also another pc using the same card, I've tested to add the 
    Option "AGPMode" "4"
    Option "DRI" "off"
    
and also some friends suggested me to try to add 
   Option  "MonitorLayout" "NONE:CRT"
and tested also:
   Option  "MonitorLayout" "CRT,NONE"
and 
   Option "CRT2Position" "Clone"
   Option "MonitorLayout" "CRT,CRT"

.. I've a CRT MOnitor   (a Sony G200 that works at 1600x1200)  ... the video card is an Ati Radeon 9250  AGP with 128Mb
I've removed the Monitor section as someone suggested
but none of the solutions worked: the system freezed.
I've also recompiled the xf86-video-ati-6.6.3  drivers  (my pc worked perfectly with them)  but using them too the system freezed. So It's possible this is not just an ati driver problem but an xorg problem too.
As Walldor2000 reported just the vesa driver works but with a 1024x768 resultion.

Thanks for al infos you'll be able to furnish me

Nicola

---

### Post by wmgobuffs on 2008-04-21
I have an ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] and was able to use Beryl in 7.04.  I know there have been other threads about these driver issues, so I won't spam about my particular problem.  However, I would like to know if, once these xorg.conf issues are ironed out by the experts, will someone be so kind as to add the necessary changes to the wiki?  I can live without the cube for a few weeks, but I don't want to waste anyone's time on the messageboard if the problem has been solved elsewhere.

Thanks!

---

### Post by sebos69 on 2008-04-26
Hi!

in my case the line:
Option "AGPMode" "1"

fixed my problems, with a loss of performance, though...

---

### Post by taita on 2008-04-27
hi, I've just tested the new 8.04 and horrible I can't boot it: after starting the cd booting the system freezes. :confused:
I've had the same problem also testing other new distros like fedora9-preview, opensuse, Slackware-current. There are problems also using old xf86-video-ati-6.6.3 drivers  ... I see that all ones not working have the new xorg-server-1.4.x   it's possible there's a problem xorg-server with xf86-ati drivers?? My base versions is the recent debian4.0r3 my ati card worked perfectly with it.

---

