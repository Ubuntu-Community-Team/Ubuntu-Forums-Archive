---
title: "Need help removing NVIDIA Beta drivers"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by Zeroangel on 2006-11-07
Hey all, I somehow managed to break my xorg by installing the NVIDIA Beta drivers. However they are not working, and I can't seem to uninstall them.

If I uninstall xserver-xorg, nvidia-glx, and linux-restricted-modules-`uname -r`, remove additional repos and try to install the stock edgy modules, I *still* get the NVIDIA beta screen and an immediate crash on my X-Server.

Does anyone know how to completely purge these drivers from my system so I can start normally? I really have tried everything I can think of to work around that problem to no avail.

---

### Post by Zeroangel on 2006-11-07
Barring that, can anyone tell me how to fix the existing drivers?

I keep getting errors about font paths missing, NVIDIA driver not being found (even though the driver is set to "nvidia" in xorg) and no usable screens being found. Even right after a dirty reinstall of the beta drivers.

---

### Post by Zeroangel on 2006-11-07
I managed to somehow repair my drivers by a full purge of all nvidia-related drivers (except for the beta that I couldnt remove), reinstall of the beta drivers using the shell script on the nvidia website. Tracking down of the script called the missing sbin files. Stopping KDM, and rebooting.

---

