---
title: "Maverick installation display problem on Dell Optiplex 960"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by deesto on 2010-11-03
I've just installed 10.10 on a brand new Dell Optiplex 960 machine via the x86_64 live CD.  After installation and reboot, the screen(s) are completely blank and the system does not respond.  I've seen some complaints about this and saw a solution to add `i915.modeset=1` to the boot parameters, but this has no effect in my case.

Graphics are an NVIDIA Quadro PCIe card.  Not sure what else to try.

---

### Post by deesto on 2010-11-03
Unfortunately, the answer seems to be that Linux NVIDIA GPU support still sucks, for reasons not necessarily attributed to Linux.  What worked for me:
- Get a recovery session, either via console or the live CD
- Modify the GRUB_CMDLINE_LINUX line in /etc/grug/default to include the "nomodeset" option
- Add the line "blacklist nouveau" to /etc/modprobe.d/blacklist.conf
- Reboot and get into a VGA session. Booting from grub at this point should get you the option to run a single "failsafe" X session.
- Click "System -> Administration -> Additional Drivers" and activate the recommended NVIDIA driver for your hadrware (probably the "version current" version)
- Reboot.  If necessary after reboot, adjust your NVIDIA settings ("System -> Administration -> NVIDIA X Server Settings")

Also unfortunate: this fix does not help address the VGA display stuff that appears during boot and shutdown, which still looks really bad.

---

