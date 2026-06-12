---
title: "cannot install nvidia driver on laptop"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by first-in-charge on 2018-10-19
i'm trying to install nvidia drivers for a geforce 820m laptop running ubuntu 16.04, had no success installing version 410 from 
ppa:graphics-drivers/ppa and prime-select nvidia and prime-select query returned "unknown", also tried version 340 from additional drivers and it caused thesystem to run 
on low graphics mode,popOS(nvidia version) didn't work either, also it returned this installing the driver from the ppa
[INDENT]W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915
[/INDENT]

---

### Post by ubfan1 on 2018-10-20
Those files are in the linux-firmware package.  Install that with  
sudo apt-get install linux-firmware

---

### Post by first-in-charge on 2018-10-21
> **ubfan1 said:**
> Those files are in the linux-firmware package.  Install that with  
sudo apt-get install linux_firmware

that package was already installed in the system and both the warning and driver problem still unchanged

---

### Post by first-in-charge on 2018-11-12
i just gave up and installed mint, in which i was able to install the package on nvidia website and after completely disabling nouveau (blacklisting it), and trying running it on the root terminal on the other boot options, in resume it was a pain in the ass.

---

