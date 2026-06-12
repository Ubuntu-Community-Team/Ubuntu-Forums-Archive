---
title: "Missing driver Intel HD graphics 3000 on x64 Ubuntu 20.04"
date: 2020-05-30
forum: Installation &amp; Upgrades
---

### Post by semyuel on 2020-05-30
After installing **x64 Ubuntu 20.04** the driver for the integrated video card was not installed. The OS hands after login. Hard reboot or power off is required. Changing linux** 'grub' 'nomodeset' load option** is a temporary solution, the OS is loaded in low resolution without graphics driver. The device is laptop '_Hewlett-Packard HP Pavilion dv7 Notebook PC_', video adapter is '_Intel(R) HD Graphics 3000 (2108 MB)_', 3D Accelerator: '_AMD Radeon HD 7690M XT (Whistler)_'

GPU:

1) Integrated: Intel Sandy Bridge-MB - Integrated Graphics Controller (MB GT2)
2) PCI Express 2.0 x16: AMD Radeon HD 7690M XT (HP)

[IMG]https://i.stack.imgur.com/lnPxU.png[/IMG]
when the OS was installing and loaded for the first time, I noticed error message that the video driver for the radeon video card was not installed.

**[radeon]] *ERROR* No UMS support in radeon module!**

'Software & UpdateS -> Additional Drivers' dialog shows no results (zero options).

after reading through forums and discussion boards, I learned that installing Intel tools, 'intel-driver' for graphical card under '**x64 Ubuntu 20.04**' is causing even more trouble, so that people are looking how to rollback that or purge. The ***'Intel® Graphics Tool for Linux'*** is not helpful and causes same frozen screen as default one.

[SIZE=2][B]My questions is why the OS is trying to use Radeon card if there is fully functional integrated Intel video card? Is there Intel HD 3000 driver for the x64 Ubuntu 20.04?
[/B][/SIZE]
How can I switch to use only integrated Intel video adapter in Ubuntu 20.04?

I've changed BIOS option to use FIXED graphics card mode, so that the OS can't switch cards dynamically. Though there might be Ubuntu or linux configuration setting, which defines the exact video adapter in use. I'd like to set it to Intel ( there are no drivers yet for the Radeon under Ubuntu 20.04 )

Why video driver for the same video card '**Intel(R) HD Graphics 3000**' that works fine for the Ubuntu 19.04 or 18.04 or 16.04 is not compatible with Ubuntu 20.04? Are there any breaking changes that make drivers incompatible?

---

### Post by dino99 on 2020-05-30
A thread about igpu/amd switch [https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04](https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04)

---

