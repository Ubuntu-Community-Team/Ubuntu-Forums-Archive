---
title: "Can only use graphical failsafe"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by Gavagai80 on 2008-09-05
I'm a long-time Kubuntu user and decided to install Ubuntu 8.04 on another partition (I didn't want to apt-get ubuntu-desktop, because I did that once before and the gnome it installed was broken in lots of ways and possibly responsible for subsequent KDE problems). Optical drive seems have broken so I went with USB. The live(fake)cd would bring up the login screen, but the automatic login simply flickered the monitor and returned to the login screen. I rebooted and did the install, and the (graphical) install process worked... but after the install, it again can't login to gnome.

I selected the graphical failsafe mode and that works, but it gives me a screen with just the wallpaper and with no panels, and alt+f2 doesn't do anything (it does let me create a fake html file I can then click to launch firefox, and create a directory so I can click it to launch natalus... seems a normal desktop except for not having any panels or alt+f2). I couldn't figure out how to get gnome's console to load so I had no way to attempt to reconfigure xorg or the like. Finally I tried ctrl+alt+F1, and that froze the screen so I had to do a hard reboot.

On returning to Kubuntu, I got a "Please repair the filesystem manually" message... much like [this other person's thread](http://ubuntuforums.org/showthread.php?t=461719). It had an option to bypass it so I bypassed it, and Kubuntu booted fine. I gather the only broken partition is the one Ubuntu is installed on (it displays as empty in konqueror now), due to the hard reboot.

Note on display issues: in various past attempts to install OpenSUSE, it would always end up with a "signal over range" monitor message (at which point I'd give up and go back to kubuntu each time). I've never had a problem with installing Kubuntu or Mepis (or viewing their livecd desktops) -- I recall Kubuntu ran its livecd at 800x600 resolution though, and I think it allowed me to choose my final resolution or else defaulted it to something low, whereas Ubuntu is forcing it to 1400x900. (Though 1400x900 appears to work on the login screen and in failsafe mode, just not in real gnome, so who knows if that's related to anything.)

Another note: I let ubuntu's install process select to import profile data from kubuntu. Not sure if that option can break things.

Order of priorities: 
1) Repair ubuntu's /media/sda5 from kubuntu.
2) Get ubuntu to run something other than failsafe mode.

How do I do these things?

---

### Post by Crafty Kisses on 2008-09-05
What are your system specs?

---

### Post by Gavagai80 on 2008-09-05
HP a1200e, AMD Sempron 3200+, 1.5 GB RAM, ATI graphics with an acer AL1916W monitor.

---

### Post by Gavagai80 on 2008-09-07
Just had a system freeze (in kubuntu) which may be related to the corrupt filesystem(s). Anyone have any idea? I think it should have something to do with fsck...

---

### Post by Gavagai80 on 2008-09-10
Okay, /dev/sda7 is supposed to be a swap space partition and I think it's the one causing the problem -- flashed by in a second, but I think one of the boot messaged said swap failed.

fsck /dev/sda7 results in this message:
```
fsck 1.40.8 (13-Mar-2008)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda7
```

---

