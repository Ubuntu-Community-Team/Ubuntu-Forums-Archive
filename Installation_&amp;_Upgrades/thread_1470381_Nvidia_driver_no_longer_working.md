---
title: "Nvidia driver no longer working"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by AlpCen on 2010-05-02
I just upgraded from Kubuntu 9.10 to 10.4 and since then the driver has stopped working.

I always used to install the driver manually from the nvidia website but the script (versions 190.53 and 195.36.24) fails since I upgraded: "Unable to load module nvidia.ko"

If I just install the nvidia-current package, the module exists as "/lib/modules/2.6.32-22-generic/updates/dkms/nvidia-current.ko" but kdm or X or whatever is unable to load it after rebooting.

If I try to install the driver using jockey-kde, everything seems to work fine except that I'm thrown back to the kdm login screen whenever I try to start KDE. However, if I choose openbox as display manager, the driver actually works fine. I really don't get that at all.

---

### Post by AlpCen on 2010-05-03
Still doesn't work.

---

### Post by djurny on 2010-05-03
try appending 'nomodeset' to kernel commandline options, had the same issue, due to the nouveau driver being loaded at boottime (somehow drm/kms needs this early on)
then drop to root console at boot, install the nvidia binary drivers and reboot once more..

edit: just read that you are indeed able to graphically login (gdm/kdm) so perhaps this trick will not help you :(

---

### Post by AlpCen on 2010-05-03
Got it. :)

You're right, it had something to do with nouveau. After blacklisting the nouveau and vga16fb kernel modules (as described in [http://ubuntuforums.org/showthread.php?t=1469528](http://ubuntuforums.org/showthread.php?t=1469528)), I was able to manually compile the nvidia driver. Works fine now.

---

