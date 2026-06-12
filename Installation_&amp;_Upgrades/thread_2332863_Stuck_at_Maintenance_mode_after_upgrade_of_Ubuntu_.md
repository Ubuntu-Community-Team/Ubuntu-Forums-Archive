---
title: "Stuck at Maintenance mode after upgrade of Ubuntu 14.04-&gt;16.04"
date: 2016-08-04
forum: Installation &amp; Upgrades
---

### Post by Vladislav_Roussino on 2016-08-04
Hello,
I have a home server running Ubuntu 14.04. I'va played a lot to set it up, since i use it for tons of different tasks. I wanted to try the "new" 16.04 so i quickly made a clone of my ssd to another empty drive, booted and did a sudo do-release-upgrade. The upgrade passed with no errors or issues. I've intentionally unplugged all other drives from my server before the upgrade to avoid any "unexpected" issues. After the restart i'm getting only into the maintenance console and i get no error or warning - the system just enters maintenance mode and that's it.
I need to mention that i was specifically running my 14.04 with a 4.2 kernel because i want my main video output to be on my tv with Kodi as default desktop environment. I'm having a Nvidia 630 graphics card installed on the server and with every other newer kernel i cannot get it to load Kodi directly, that's why i use 4.2. now when Ubuntu 16.04 tries to start i see that it's still launching the 4.2 kernel. Could this be the problem? or is it a failing Nvidia driver? I saw several advises here and on other forums/blogs suggesting to reinstall the Nvidia driver, to try to reinstall the desktop environments etc, but i prefer to ask here first before crashing everything up to a point that i have to restartthe whole operation with cloning my main drive etc.

---

### Post by QIII on 2016-08-04
Hello!

Had you uninstalled the video driver and disabled all PPAs prior to upgrade?

---

### Post by Vladislav_Roussino on 2016-08-04
no i haven't and this might be partially the problem. i have a progress - i managed to get the network running under maint. mode and after apt-get update/upgrade i was prompted to install GRUB since something has changed - this i think was because i'm using a cloned version of my installation. ok, i installed GRUB but after a restart i was in maint. mode again. so i purged nvidia* and installed nvidia-364 driver. i noticed that during the installation there was info for kernel 4.4.0.31, but nothing for the one i use - 4.2.*.*. now when i restart i'm stuck at the boot logo which at some point stops and freezes without any other thing happening. i guess i need to change the kernel which is booting? any idea how to do that in maint mode? i used to tweak the kernel selection using ubuntu tweak.

---

