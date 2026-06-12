---
title: "Ubuntu Installer - &quot;failed to start GNOME display manager&quot;"
date: 2024-04-06
forum: Installation &amp; Upgrades
---

### Post by zenon222 on 2024-04-06
I'm trying to install Ubuntu on a Dell Latitude 5480.
The install USB can't get past the splash screen logo.
Pressing escape to see what might be the error showed the following:
```
[FAILED] Failed to Detect the available GPUs and deal with any system changes.
See 'systemctl status gpu-manager.service' for details.
[FAILED] failed to start GNOME display manager
See 'systemctl status gdm.servive' for details.
```

I have no command line available to do anything.

Thanks in advance.

---

### Post by zenon222 on 2024-04-19
anyone?

---

### Post by MAFoElffen on 2024-04-21
That laptop has an NVidia GPU & Intel i915 iGPU:
> 
Intel HD Graphics 620. Intel HD Graphics 630. NVIDIA GeForce 930MX

Start from the grub menu by selecting the "Safe Graphics" Option.

At the screen where it asks full Install options for Full or Minimal, in the lower portion of that panel, below the option to check for and install updates, select the checkbox for Installing third party drivers for media files and such...

---

