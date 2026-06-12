---
title: "Back to Edgy..."
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by imatwork on 2007-04-26
Feisty problem 01:
installed nvidia-glx for a GeForce4 4200Ti / ran the 'sudo nvidia-glx-config enable' bit / edited xorg.conf like usual to configure refresh + resolution, but the system is stuck at 800x600 @ 50hz. I'm expecting 1280x1024 @ 85h as configured.


Feisty problem 02:
added an internal, secondary, misc storage drive formatted ext3 back into the system which contains existing data. i edited fstab as usual (/dev/hdb1  /media/data  ext3  defaults,errors=remount-ro  0 1), and created the usual mount point (/media/data). Oddly, after reboot, I may or may not have immediate access to the drive. Meaning that on some start-ups I would be asked for a root password. When this situation is true, the system had renamed the drive to something other than "data". On other start-ups the drive will appear as I created it; "data", and I can click straight in. I'm puzzled by this behavior.


Having gone back to Edgy, neither of these problems exist. In both cases, Feisty vs Edgy, the configurations are identical (hardware included). I have seen far too many unresolved posts roll by regarding Nvidia issues with Feisty, so clearly there is a problem. Hopefully it will be resolved.

---

### Post by Wight_Rhino on 2007-04-26
I too went back to Edgy last night , did a quick check by putting dvd/cd/usb/floppy in and they all automounted! All readable, no problems. How and why did they stop working in Feisty?

Oh well. I'm back on a working Ubuntu. Lesson learned is to wait a month or so after the final release before upgrading to Gutsy. Or load the beta on another partition and give the testers some much needed help.

---

