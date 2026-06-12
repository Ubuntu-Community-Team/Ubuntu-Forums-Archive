---
title: "Upgrade errors on new install"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by finlost on 2010-11-13
I was having problems getting 9.10 to mount SDA1.  I had been contemplating moving to 10.04 and this was the extra push I needed.  Do note that I think I am having some hardware problems because every once in a while, my computer just shuts off as if the power was disconnected.  I am thinking bad RAM or bad motherboard.  Back in July, I removed a GB of RAM because I was having problems and then seemed to take care of the problem.  I am now running just one GB of RAM (previously had 2 GB)

I ran the LiveCD, setup the partitions, and installed 10.04.  I was doing some work in another room during the install.  I came back and my machine was off.  IIRC, the install prompts you to remove the CD from the drive and reboot.  I didn't get that this time.  The computer was off when I checked on the install.

When I rebooted the machine, the install seemed successful.  Ubuntu then prompted me to install the upgrades/patches.  I did so.  I received this error message during the upgrade:
```
E: libkdecorations4: subprocess installed post-installation script returned error exit status 2
E: libkephal4: subprocess installed post-installation script returned error exit status 2
E: libkwineffects1: subprocess installed post-installation script returned error exit status 2
E: libkworkspace4: subprocess installed post-installation script returned error exit status 2
E: kde-window-manager: dependency problems - leaving unconfigured
E: kdepimlibs-data: subprocess installed post-installation script returned error exit status 2
E: libboost-program-options1.40.0: subprocess installed post-installation script returned error exit status 2
E: libakonadiprivate1: dependency problems - leaving unconfigured
E: kdepimlibs5: dependency problems - leaving unconfigured
E: libqt4-assistant: subprocess installed post-installation script returned error exit status 2
E: libqt4-help: subprocess installed post-installation script returned error exit status 2
E: libqt4-scripttools: subprocess installed post-installation script returned error exit status 2
E: libqt4-test: subprocess installed post-installation script returned error exit status 2

```

I have installed additional packages since receiving that error.  The packages seem to install correctly and then that error messages pops up at the end.

I cannot run any desktop effects.  Some of the packages in the error message seem to indicate decoration packages.

Any ideas on how to correct my error message?  Did the shutdown during the install corrupt some files and thusly I should just do a clean install again?

---

### Post by mörgæs on 2010-11-15
What happens if you run memtest from the live CD? Might take all night...

---

