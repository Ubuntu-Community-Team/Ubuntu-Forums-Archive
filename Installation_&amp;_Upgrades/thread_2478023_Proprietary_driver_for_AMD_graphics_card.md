---
title: "Proprietary driver for AMD graphics card?"
date: 2022-08-14
forum: Installation &amp; Upgrades
---

### Post by peyre on 2022-08-14
I recently went back to my old 2-core desktop from 2009 so my son could have a decent gaming computer.  Xubuntu runs great on it, but of course it's a slow machine, especially for graphical things includingLOTRO--so anything I can do to optimize this thing would be welcome.  I thought maybe graphics performance could be improved by using the proprietary driver.  I pulled up Additional Drivers in Settings, but it says none are available.  Plus I don't see any drivers for this model on AMD's support site.  Does this mean there aren't any for this one?  It's a:

Yeston AMD Video Card Radeon RX550 4G D5 LP Gaming Graphics Card GPU, 4G/128bit/GDDR5 PCI-Express 3.0x8 DirectX 12,DVI+HDMI+VGA Desktop Graphics Card

---

### Post by mikewhatever on 2022-08-14
Here it is: [https://www.amd.com/en/support/graphics/radeon-500-series/radeon-rx-500-series/radeon-rx-550](https://www.amd.com/en/support/graphics/radeon-500-series/radeon-rx-500-series/radeon-rx-550)
Note that it is for 22.04 HWE and 22.04 releases.

---

### Post by peyre on 2022-08-14
Hey thanks!  I've downloaded and installed it, but Additional Drivers still says none are available or in use.  Am I missing something?

---

### Post by mikewhatever on 2022-08-16
Well, you haven't installed it with the Additional Drivers utility, so why should it say anything?

---

### Post by QIII on 2022-08-16
Depending on the hardware (bleeding edge hardware may be an issue still), when Ubuntu is installed on a machine with AMD graphics, either the open source amdgpu driver module or the open source radeon driver module is activated.  There is no need to add a "proprietary driver".  The modules are already part of the kernel, so there is no "additional driver" to be sought.  AMD works with the Linux kernel developers to make the driver module work out of the box -- but that may take a while for the very latest hardware.  nVidia is a different kettle of fish.

The only thing that might be useful, depending on what you are using your GPU for, would be the proprietary AMDGPU-PRO overlay for the amdgpu module.  But that is not required for the vast majority of users.

Don't be confused.  AMD went back to the "Radeon" branding, but you were still re-installing the amdgpu driver.  [https://amdgpu-install.readthedocs.io/en/latest/](https://amdgpu-install.readthedocs.io/en/latest/)

---

### Post by peyre on 2022-08-16
> **mikewhatever said:**
> Well, you haven't installed it with the Additional Drivers utility, so why should it say anything?

That's a thing?  It doesn't offer an option anywhere in the Additional Drivers screen to add or install anything.

---

### Post by peyre on 2022-08-16
> **QIII said:**
> Depending on the hardware (bleeding edge hardware may be an issue still), when Ubuntu is installed on a machine with AMD graphics, either the open source amdgpu driver module or the open source radeon driver module is activated.  There is no need to add a "proprietary driver".  The modules are already part of the kernel, so there is no "additional driver" to be sought.  AMD works with the Linux kernel developers to make the driver module work out of the box -- but that may take a while for the very latest hardware.  nVidia is a different kettle of fish.

The only thing that might be useful, depending on what you are using your GPU for, would be the proprietary AMDGPU-PRO overlay for the amdgpu module.  But that is not required for the vast majority of users.

Don't be confused.  AMD went back to the "Radeon" branding, but you were still re-installing the amdgpu driver.  [https://amdgpu-install.readthedocs.io/en/latest/](https://amdgpu-install.readthedocs.io/en/latest/)

Ah.  Thanks, I think.  I selected AMD because I understand the open-source drivers are better than those for nVidia, but I've read in various places that AMD does make proprietary ones that can sometimes improve performance.  Maybe that was for older hardware or something.

---

