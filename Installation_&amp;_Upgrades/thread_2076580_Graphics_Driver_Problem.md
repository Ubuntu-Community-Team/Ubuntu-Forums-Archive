---
title: "Graphics Driver Problem"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by Dai777 on 2012-10-26
Getting this error message:

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

How do I sort this out.

Thanks in advance 
Dai

---

### Post by dino99 on 2012-10-26
sudo lshw -c  video

---

### Post by Dai777 on 2012-10-26
> **dino99 said:**
> sudo lshw -c  video

-display UNCLAIMED     
       description: VGA compatible controller
       product: RV610 video device [Radeon HD 2400 PRO]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:fdce0000-fdceffff ioport:be00(size=256) memory:fdc00000-fdc1ffff
dai@dai-Aspire-M5600:~$ 


Not sure it is sorted but will keep you informed.

---

### Post by Dai777 on 2012-10-26
nope still not working.
Any way to uninstall and re-install to get them working

---

### Post by arpanaut on 2012-10-26
Have you seen this:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

