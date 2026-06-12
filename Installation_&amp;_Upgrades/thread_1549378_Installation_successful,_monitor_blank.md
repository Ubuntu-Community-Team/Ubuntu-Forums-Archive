---
title: "Installation successful, monitor blank"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by kdhmiles on 2010-08-09
I've just installed Ubunto 10.04 onto my wifes Samsung V25 laptop. When booting from CD no problems at all. 
Installed to disk, and at boot up it makes all the sounds, I can log in (though can't see the screen) and still no screen once logged in. Just blank.

Any ideas?

---

### Post by CPL2010 on 2010-08-09
Scan rate on the monitor I'm guessing is set wrong during setup during the hardware detection.  I've had that happen with HP pavillion laptops.  Can you post the xorg.conf file?  Or quickly scan through it and look for the monitor section and if it's set to higher than 60 mhz.

[http://ubuntuforums.org/showthread.php?t=307716](http://ubuntuforums.org/showthread.php?t=307716)

link to the steps to check it out.

---

### Post by kdhmiles on 2010-08-10
CPL,

Thanks for taking the time to respond. I will take a look when I am at home.

As for the xorg.conf - not sure how I'd get this from the system as I am unable to see anything once it boots.

Is it possible to get it to boot without a window manager? perhaps that would allow me access?

---

