---
title: "ATI Catalyst &amp; 'Hardware Drivers'"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by al111 on 2011-11-16
My PC hung at a blank or black screen after updating with 'Update Manager'-

So booting into 'safe-mode' and re-installing the ATI Driver did resolve the screen issue... but then I found other things that didn't work, that did before updating...so I decided to just re-install 10.04 (Lucid Lynx)-

After re-installing 10.04 (and ATI), the same issues appeared, leading me to conclude that updating via 'Update Manager' breaks linux on my pc-

I think I fixed everything, but even though ATI looks like it's installed and seems to be working, 'Hardware Drivers' reports that 'NO proprietory drivers are in use in this system'-

I checked 'FGLRX' in Terminal, and got:

      pc@PC1:~$ fglrxinfo
      display: :0.0 screen: 0
      OpenGL vendor string: Advanced Micro Devices, Inc.
      OpenGL renderer string: ATI Radeon HD 4800 Series
      OpenGL version string: 3.3.11251 Compatibility Profile Context


ATI Catalyst information reports 'Catalyst Version' is 11.11-

I can configure 'Extra' Visual Effects in 'Appearance Preferences' successfully-

_Question_: *Is 'Hardware Drivers' in error reporting that 'NO proprietory drivers are in use in this system', or is there something else that needs to be checked, installed, or configured?* Thanks-

---

### Post by Mark Phelps on 2011-11-17
ATI restricted video drivers are tied to specific kernel versions.  When you do an update that upgrades the kernel version, that "breaks" the video drivers -- and you have to reinstall them.

If you obtained the drivers from the AMD site and installed them, you will have to do this replacement every time you upgrade the kernel.

However, if you remove those, and reinstall them using the Additional Drivers, it is able to then update the drivers itself whenever you update the kernel.

---

### Post by al111 on 2011-11-17
Thanks-

---

