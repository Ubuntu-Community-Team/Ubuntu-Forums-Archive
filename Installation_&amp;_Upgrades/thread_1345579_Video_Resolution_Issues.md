---
title: "Video Resolution Issues"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by mawiles on 2009-12-04
Installed 9.10, presented with 800x600 or 640x480 resolutions, a far cry from previous Ubuntu versions.  Enabled the NVidia drivers, and resolution went DOWN to 640x480 or lower.  No conf file to edit in X11. Operating systems utilities of no use. The LCD I use is capable of 1440x900.  What has happened to X? and its files?  What is replacing it, and how do I resolve this issue.

---

### Post by coffeecat on 2009-12-04
It sounds as though the xserver is not detecting the EDID information from the monitor, or the monitor is not putting out correct EDID information.

Have you tried System > Preferences > Display? If you choose 'yes' at the yes/no window, you are taken to the proprietary nvidia settings utility. Some people are reporting a 'failed to parse existing Xconfig file' when saving settings with that. I haven't tried this myself, but it's being suggested that invoking 'gksudo nvidia-settings' from the terminal gets around that.

Alternatively, choosing 'no' from the yes/no window gives you the standard gnome display preferences utility, where you should be able to set the resolution. Have you tried that?

Last question. Is the monitor switched on when you boot up? If the xserver cannot detect a display it defaults to 640x480. Are you using a kvm switch?

---

### Post by mawiles on 2009-12-04
The monitor is on, everything works fine in XP and Win 7, and the monitor was on during installation.  There are no files found for X to edit manually.  The O/S utilities (System > Preferences > Display) only offer 2 resolutions as previously stated. After the installation of the Nvidia drivers two choices of lower resolution were presented by the utility. There was never a reporting of an error. When one attempts to use the NVidia utilities, it is unable to write to the correct files (never has worked in any version of ubuntu that I can remember). It almost appears that X server is no longer used, or is using some other method to configure the video.  A google search revealed the utility xrandr, which is interesting.  This is a standard westinghouse 19" wide screen capable of 1440x900, with a Nvidia 8800GT vid card. I am using a DVI cable to connect the monitor to the vid card.

---

### Post by mawiles on 2009-12-04
Anyone know where I can get the iso for an older version, this one is just plain broken!

---

