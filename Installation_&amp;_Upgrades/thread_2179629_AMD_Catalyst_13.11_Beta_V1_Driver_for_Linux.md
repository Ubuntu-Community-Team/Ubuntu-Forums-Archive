---
title: "AMD Catalyst 13.11 Beta V1 Driver for Linux"
date: 2013-10-09
forum: Installation &amp; Upgrades
---

### Post by Cogent_Pole on 2013-10-09
Could anyone please direct me to the step by step tutorial on how to implement all the updates stated below:

**System Requirements:**
Before attempting to install the AMD Catalyst™ Linux graphics driver, the following software must be installed: 

[LIST]
[*]Xorg/Xserver 7.4 and above (up to 1.14)
[*]Linux kernel 2.6 or above (up to 3.10)
[*]glibc version 2.2 or 2.3
[*]POSIX Shared Memory (/dev/shm) support is required for 3D applications
[/LIST]
*NOTE: If a Linux 2.6.11 or newer kernel was built with CONFIG_AGP enabled, the kernel AGP frontend is required to load the fglrx kernel module. To identify whether your kernel with CONFIG_AGP enabled, look for CONFIG_AGP=y in the kernel config file, or if the ‘agpgart’ module is loaded*
**System Recommendations:**
For optimal performance and ease of use, the following are available: 

[LIST]
[*]Kernel module build environment
[LIST]
[*]Kernel source code include either the Kernel Source or Kernel Headers packages
[/LIST]

[*]The RPM utility should be installed and configured correctly on your system, if you intend to install via RPM packages
[/LIST]
The following packages must be installed in order for the AMD Catalyst™ Linux graphics driver to install and work optimally: 

[LIST]
[*]gimp-help-en
[*]gimp-help-common
[*]XFree86-Mesa-libGL
[*]libstdc++
[*]libgcc
[*]XFree86-libs
[*]fontconfig
[*]freetype
[*]zlib
[*]gcc
[/LIST]

---

### Post by Mark Phelps on 2013-10-09
BEFORE you charge down this path, it would be good to know what make and model AMD video chipset you have -- since only the latest ones can support this driver.

---

### Post by Cogent_Pole on 2013-10-10
I have ASUS HD 7790

---

