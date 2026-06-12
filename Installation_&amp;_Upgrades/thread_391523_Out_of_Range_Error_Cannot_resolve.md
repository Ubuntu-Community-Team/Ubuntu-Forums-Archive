---
title: "Out of Range Error Cannot resolve"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by jackosh on 2007-03-23
I just installed 6.10, and everything worked fine.  I then installed the nvidia drivers for my GeForce 7600GS.

On the reboot, I got the "signal out of range" error on my monitor.

I've read every thread about this to try to resolve the error, and nothing helps.

Ive reconfigured xorg a billion times to the absolute correct settings, and still no dice.  Any help is GREATLY appreciated!

---

### Post by Polygon on 2007-03-23
i get this error when my resoultion  is set too high for my monitor to handle... so maybe try toning down the resolution in xorg.conf (if you know how to do that)

---

### Post by jackosh on 2007-03-23
my card/monitor works very well at 1280 x 1024 @ 60Hz in Windows (and not in ubuntu)

I've tried EVERY resolution from 1280 x 1024, all the way down to 640 x 480.  No luck!

---

### Post by jackosh on 2007-03-23
OK well if i set the drivers to "nv" everything works again.

Anyone know how i can get it to work with the nvidia drivers?

---

