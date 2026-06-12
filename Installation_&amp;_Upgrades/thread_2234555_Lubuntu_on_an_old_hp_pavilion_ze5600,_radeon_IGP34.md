---
title: "Lubuntu on an old hp pavilion ze5600, radeon IGP340M X11 configuration problem"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by Netrunner on 2014-07-15
Hello everyone, 
I recently tried to install lubuntu alternate 14.04 on an old hp pavilion ze5600 of mine.
To get the installation done I used an usb with flashed this image: 
[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)
[https://wiki.ubuntu.com/IconsPage?action=AttachFile&do=get&target=pc32_iso_semirounded.png](https://wiki.ubuntu.com/IconsPage?action=AttachFile&do=get&target=pc32_iso_semirounded.png)
and the always good "super grub disk" on a cd.
Everything went fine, and with that I mean I couldn't notice any error message during the lovely old fashion installation process.
But after the reboot X11  doesn't show up.
The messages I am investigating are the foolowing:

(--) RADEON(0): Chipset: "ATI Radeon IGP330M/340M/350M (U2) 4337" (ChipID = 0x4337)
(EE) RADEON(0): [drm] Failed to open DRM device for pci:0000:01:05.0 No such file or directory
(EE) RADEON(0): Kernel modesetting setup failed
(II) UnloadModule: "radeon"
(EE) Screen(s) found but none have a usable configuation.
(EE) Fatal server error:
(EE) no screens found(EE)

i am sorry but the quickest solution was to change distro.

---

