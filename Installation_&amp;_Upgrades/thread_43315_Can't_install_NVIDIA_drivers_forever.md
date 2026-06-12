---
title: "Can't install NVIDIA drivers forever"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by juantxorena on 2005-06-21
Greetings. I'm going to the point:
I'm trying to install NVIDIA drivers, (1.0-7664). The installer says that I haven't got a precompiled kernel. Then he starts to compilig a kernel (I use 2.6.10-5-k7). He compiles it. He installs the drivers.
After that, I reboot, and everithing is going OK, y can login in the graphic moce, I can use Firefox, etc.
The next time I boot my computer, I can't start X. No info, only "Can't start X server. Xserver will be desactivated this sesion", or something like that. Y I reboot, happens the same.
If I re-install NVIDIA drivers, the same as above happens, although the installer uninstall the previous drivers after compiling the kernel.
The same again: I can use X server only in one session. After that, I must reinstall NVIDIA drivers again.
Help, please?

---

### Post by Lunde on 2005-06-21
[QUOTE=juantxorena]Greetings. I'm going to the point:
I'm trying to install NVIDIA drivers, (1.0-7664). The installer says that I haven't got a precompiled kernel. Then he starts to compilig a kernel (I use 2.6.10-5-k7). He compiles it. He installs the drivers.
After that, I reboot, and everithing is going OK, y can login in the graphic moce, I can use Firefox, etc.
The next time I boot my computer, I can't start X. No info, only "Can't start X server. Xserver will be desactivated this sesion", or something like that. Y I reboot, happens the same.
If I re-install NVIDIA drivers, the same as above happens, although the installer uninstall the previous drivers after compiling the kernel.
The same again: I can use X server only in one session. After that, I must reinstall NVIDIA drivers again.
Help, please?[/QUOTE]

Many others have the same problem. There are no fix that I know of for this yet. 

Even the first time you boot and everything looks great, most likely the frame rate of glxgears drops drasticly the first 5 minutes. It's better to use an older driver until the 7664 is more stable.

Some links:
[http://www.ubuntuforums.org/showthread.php?postid=214636](http://www.ubuntuforums.org/showthread.php?postid=214636)
[http://www.nvnews.net/vbulletin/showthread.php?t=50254&page=1&pp=15](http://www.nvnews.net/vbulletin/showthread.php?t=50254&page=1&pp=15)

---

### Post by juantxorena on 2005-06-21
Thanx, I'll try with another drivers. For example, 1.0-7167. Are they good, or better something older?
Edit: I unistall the actual drivers previously, or the installer will uninstall them properly?

---

### Post by Lunde on 2005-06-21
[QUOTE=juantxorena]Thanx, I'll try with another drivers. For example, 1.0-7167. Are they good, or better something older?
Edit: I unistall the actual drivers previously, or the installer will uninstall them properly?[/QUOTE]

There is an uninstall flag you can use when you start the installer, don't remember exactly what it is (--uninstall) or something, I dont think that an older driver will remove the new one. 

**Some links for setting up an older Nvidia driver: **

[http://ubuntuforums.org/showthread.php?t=26568](http://ubuntuforums.org/showthread.php?t=26568)

[http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713)

[https://wiki.ubuntu.com//BinaryDriverHowto](https://wiki.ubuntu.com//BinaryDriverHowto)

---

### Post by juantxorena on 2005-06-21
I just downloaded and installed 1.0-7167 drivers. They unistalled the previous drivers OK, but there was a problem with a syslinks, or something. The installer itself tells how to solve it. I rebooted a couple of times and everything's OK.
Thanks for the help anyway.

---

