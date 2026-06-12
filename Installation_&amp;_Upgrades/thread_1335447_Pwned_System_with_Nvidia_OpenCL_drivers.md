---
title: "Pwned System with Nvidia OpenCL drivers"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by Buttink on 2009-11-23
Ok. I wanted to try and do some OpenCL stuff because it looks cool. So, I downloaded the driver and the SDK. I went to the recovery mode and logged into myself(so i didnt have xserver). Then, I ran the nvidia driver file. Now, my system cant do anything with graphics. When I start up, it will complain about xserver failing because of nvidia drivers.

GAR! Iv tried all sorts of stuff like ...
```
dpkg-reconfigure -phigh xserver-xorg
```
and something else that involved nvidia-kernel (i cant find the page anymore)

Iv read some stuff like in this forum there is the "Latest Nvidia Drivers" but idk if that applies to me. Well if anyone has actually done this or knows how to fix this, help would be awesome.

---

### Post by Buttink on 2009-11-23
nobody? anything just to revert after nvidia driver install

---

### Post by richiekAL on 2009-11-25
The issue here is that Ubuntu is still trying to override the Hardware Drivers settings even though you've already installed your own version. So, you've got two options:
  [B]1. Fix the custom installation
[/B]* log in with whatever graphics mode is necessary.
* Go to System -> Administration -> Hardware Drivers, and deactivate the Ubuntu-maintained driver installation.
* Now kill your xsession and re-install the custom nvidia driver. All should work!

  [B]2. Revert back to Ubuntu-maintained driver
[/B]Any of these steps may be redundant, but this worked for me.
Firstly, uninstall the nvidia driver (be sure to kill the xserver first)
  % [COLOR=Blue]sudo sh {nvidia-driver-installation-file}.run --uninstall[/COLOR]
Now, in my case I used to be runnint v185 of the drivers, but this has recently upgraded to v190.
Try:
  % [COLOR=Blue]sudo apt-get --reinstall install nvidia-glx-190-dev[/COLOR]
and hopefully it will work.
Next do:
  % [COLOR=Blue]sudo nvidia-xconfig -A[/COLOR]
  % [COLOR=Blue]sudo reboot

[COLOR=Black]And hopefully now you're back in business... either way![/COLOR]
[/COLOR]

---

