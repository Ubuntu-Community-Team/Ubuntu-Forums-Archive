---
title: "ati card (fglrx driver) with multiple monitors crashes when xinerama enabled"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by jetpeach on 2010-10-13
One change, using "sudo aticonfig --xinerama=on" causes the xserver to crash when completing the boot. Unlike most cases, I can't identify the cause in my X log file. The xorg.conf works fine when I run "sudo aticonfig --xinerama=off" (of course, one of the monitors sits black in this case though), and my exact xorg.conf file from Lucid (which worked with xinerama and both monitors) also crashes now with Meerkat.

Link to Xorg.0.log
[http://dl.dropbox.com/u/1229450/Xorg.0.log]("http://dl.dropbox.com/u/1229450/Xorg.0.log")

Link to xorg.conf
[http://dl.dropbox.com/u/1229450/xorg.conf]("http://dl.dropbox.com/u/1229450/xorg.conf")

Could it be a KDE problem? Not sure, it's strange because both monitors look good while the pretty KDE boot screen is being shown on the left monitor, and it's not until KDE is finishing booting and about to normally display the desktop that it crashes.

XRandR1.2 problem? I've heard people having trouble with this, so I tried two things:
adding 	to xorg.conf device section
Option	    "EnableRandR12" "false"

and 
Edit /etc/ati/amdpcsdb
In the section labeled [AMDPCSROOT/SYSTEM/DDX]
EnableRandR12=Sfalse

Neither of these seemed to fix the problem.

Any help is greatly appreciated! 

Thanks!!!! jetpeach

---

### Post by bjtuna on 2010-10-13
A number of bugs are making their way into Launchpad related to this. I've been tracking this same problem.  I have an ATI card, dual monitors, running fglrx driver with xinerama. I can trigger a segfault in X by running certain apps, like VLC, nevernote, and amdcccle while xinerama is enabled.  If xinerama is disabled, these apps don't segfault X.

---

### Post by gleu on 2010-10-30
I finally managed to work fglrx in dual screen mode (without kwin effects).
```

1. Move every xorg.conf.XXX out of the /etc/X11 directory except xorg.conf.failsave
2. Copy xorg.conf.failsave to /etc/X11/xorg.conf
3. Run aticonfig --initial=dual-head
4. Restart X11
5. Enable in amdcccle Xinerama

```
I am using fglrx drivers from ati (10-10-x86) but I suppose the driver from ubuntu will work too.

---

