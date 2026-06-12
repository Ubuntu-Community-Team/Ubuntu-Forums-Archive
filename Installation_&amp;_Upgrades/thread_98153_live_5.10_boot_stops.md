---
title: "live 5.10 boot stops"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by kojak on 2005-12-02
hi all,
all booting good until:

"starting hotplug subsystem"

everything stops and then I have to shut down manually

dell desktop
P4 2.66

---

### Post by thedstro on 2005-12-02
I had the same problem!  In my case disabling the on-board sound through the BIOS setup fixed it and allowed me to boot.  This is just a workaround of course!  The solution could be replacing the sound driver (intel_snd_hda I think it was called in my case) or changing to udev instead of hotplug.

---

