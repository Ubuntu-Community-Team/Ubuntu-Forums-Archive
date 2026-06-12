---
title: "Can't start x after running ubuntu update - 9.1"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by purplegrog on 2010-05-16
I recently (yesterday) did a clean install of 9.1 (karmic koala) on my system.  After having struggled with various video driver issues with my 7800GT and getting the proprietary nvidia drivers installed, everything seemed to be working fine.  Today I ran some updates and now when the system boots, it crashes down to a text login prompt.

when I try to run startx from the command prompt, I get:
```

FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the Nvidia kernel module.  Please check your
(EE) NVIDIA:      system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error,0)
(EE) No drivers available.

Fatal server error:
no screens found
```

When I check the grub menu, I see that there it is defaulting to kernel 2.6.31-21-generic.  if I tell grub to boot to 2.6.31-14-generic (what I assume was the kernel prior to the update) the system boots back up into X, but when I try to start XBMC I get a message saying "xbmc needs hardware accelerated OpenGL rendering" and to install an appropriate graphics driver.  Any suggestions as to what I need to do?  is this symptomatic of me not blacklisting something critical when switching to the nvidia proprietary driver?

Any help would be much appreciated.

---

### Post by purplegrog on 2010-05-16
Update:  I logged in from the text login and attempted to reinstall the nvidia driver package I had previously downloaded from Nvidia (195.36.24, iirc) by running ```
 sudo sh NVIDIA-Linux-x86-195.36.24-pkg1.run 
``` from the directory where the download was stored.  during the installation process, I get the message that it appears the driver may already be installed, so it needs to uninstall it first.  I say ok, and during the uninstallation process, I get the message 
```

File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic link.

```
I proceed, and shortly after I also get the following message: 
WARNING:  Your driver installation has been altered since it was initially installed; this may happen, for example, if you have since installed the NVIDIA driver through a mechanism other than nvidia-installer (such as your distribution's native package management system).  nvidia-installer will attempt to uninstall as best it can.  Please see the file '/var/log/nvidia-installer.log' for details.


It the prompted me whether I wanted it to try to recreate the xorg.conf for me.  I tell it yes, then when the installation is done, I rebooted the system.  the system boots back up into X with seemingly no problem and I can run XBMC again.  


Now.  the good news is everything seems to be working again, but I'm wondering if anyone knows what happened and what I can do to prevent this in the future?

---

