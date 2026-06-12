---
title: "Ubuntu 13.10 LiveUSB Low Graphics Mode Error"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by PurpleSack on 2013-12-04
I am currently using a Lenovo S410, with Windows 8.1 preinstalled, and am trying to get Ubuntu 13.10 to be dual booted alongside Windows. 


The hardware would be:
i5-4200
Switchable graphics: Intel HD Graphics Family/AMD Radeon HD 8570M
the
I have been having trouble doing an installation of Ubuntu 13.10 using a LiveUSB created with pendrive. After selecting "Try Ubuntu", I end up with the error "The system is running in low-graphics mode".


I have tried "nomodeset", "i915.modeset=0", "radeon.modeset=0", "acpi_backlight=0" , running in compatibility mode and disabling switchable graphics in the BIOS, but the same error still appears. Fast Startup in Windows has been disable, as is secure boot. I have also tried running the LiveUSB in another computer and tried installing ```
sudo apt-get install fglrx
```as well as ```
sudo apt-get update
``` which didn't work either.


MD5 checksums have returned correctly, and I have tried recreating the LiveUSB as well.


Any help would be appreciated. Thanks!

---

