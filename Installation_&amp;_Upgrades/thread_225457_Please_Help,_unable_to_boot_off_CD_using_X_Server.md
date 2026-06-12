---
title: "Please Help, unable to boot off CD using X Server"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by norsman on 2006-07-29
I downloaded 6.06 from the Ubutnu site, the X64 version. I can boot off the cd, but after the first screen loads everything, it says there is an error with the X server and to restart GDM when the problem is resolved. The error in the log file is (EE) no devices detected. In the advancd log file it says (WW) PCI Mach 64 in slot 1:0:0 not detected, (WW)  PCI Mach 64 in slot 1:0:1 not detected, (EE) no devices detected, fatal server error: no screens found.

Any ideas greatly appreciated

My System:
Asus A8N-E
AMD Athlon64 3700+
ATI Radeon X850 Pro
1GB Corsair RAM

---

### Post by Kepler on 2006-07-29
Similar problem here with identical symptoms.  I'm also using an ATI Radeon X800 series video adapter.  I was able to use:

    sudo dpkg-reconfigure xserver-xorg

to confirm that X was set up to use the correct graphics adapter.  This only resulted in a more attractive log file (no EE entries) after the 'no screens found' crash.  Strangely enough, the log file records:

    (**) |-->Screen "Default Screen" (0)

which seems strange given the type of error.

At this point I wouldn't mind forgoing the graphical interface for a text-mode install but I can't seem to figure out how to invoke that instead.  Advice would be likewise appreciated.

---

### Post by Kepler on 2006-07-29
Replying to your own posts: Always good form... ;)

A bit more searching yielded this post:

[http://ubuntuforums.org/showthread.php?t=19013]("http://ubuntuforums.org/showthread.php?t=19013")

For my issue, using *sudo nano /etc/X11/xorg.conf* and changing the driver from 'ati' to 'radeon' did the trick.  I didn't need to make other changes because my monitor information was detected correctly and placed in *xorg.conf*.

Changing the drive to 'vesa' resulted in the dead-monitor problem referenced in the thread.

---

### Post by norsman on 2006-07-30
[http://ubuntuforums.org/showthread.php?t=190133&highlight=x850](http://ubuntuforums.org/showthread.php?t=190133&highlight=x850)

If you go to this site, there is a very good guide with two ways to solve the problem.

by using:

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

It worked for me
Thanks for the help

---

