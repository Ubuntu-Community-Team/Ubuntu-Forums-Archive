---
title: "Problems with booting recently installed 16.04.1 LTS"
date: 2016-09-08
forum: Installation &amp; Upgrades
---

### Post by herman2286 on 2016-09-08
Hello,

I am a new Ubuntu user. I recently installed ubuntu on a formatted HDD but ran into an issue with installing in UEFI mode. In order to get around this, I did not install ubuntu in UEFI mode. Once I did this, I realized that I couldn't boot ubuntu so I booted from "try ubuntu" the USB stick I used to install ubuntu and ran the boot-repair in order to resolve the issue. However, I'm still unable to boot ubuntu as it appears there isn't a boot partition. I am following the instructions and sharing the paste link here along with my system info to resolve the booting issue. [http://paste2.org/p5bDmkH3](http://paste2.org/p5bDmkH3)

System info:
Model: ASUS x550L
CPU: Intel core I5-4200U 1.6 gig
GPU: Intel Haswell Mobile

Regards

---

### Post by oldfred on 2016-09-08
It looks like you still have UEFI Secure boot on. System will not boot in BIOS/Legacy/CSM boot mode with Secure boot on.

You have installed in BIOS/MBR configuration. 

And you booted Boot-Repair or flash drive in UEFI boot mode. Better to always boot in same mode as you have installed whether UEFI or BIOS.

Turn off UEFI Secure boot and turn on BIOS/CSM/Legacy or whatever your system calls CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

