---
title: "Help, Grub-rescue error: invalid arch-independent ELF magic"
date: 2016-12-22
forum: Installation &amp; Upgrades
---

### Post by ozzman530 on 2016-12-22
Thank you for taking the time to read this. I'm pretty new to Linux and Ubuntu. I am running 16.10 on an old repurposed Dell Laptop (I5 ssd,etc). I received updated two days ago, and the kernel version went from 4.8.0.30 to 4.8.0.32. It hasn't booted properly since. I must have destroyed what little was left because now I get to "Grub rescue" without using the Live cd, which boots fine and everything is still there. I tried to re-install yesterday but after 24 hours of it trying I gave up and force restarted. Back to live cd working fine. 

I tried several answers in thread that looks like they pointed at fixing UEFI, I learned that I have Legacy boot enabled, but not sure what all that means.

---

### Post by oldfred on 2016-12-22
Elf magic is often trying to boot in wrong mode.
Did you change from BIOS/CSM/Legacy to UEFI or vice-versa in UEFI?

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

