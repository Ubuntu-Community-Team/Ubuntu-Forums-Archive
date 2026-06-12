---
title: "Ubuntu 18.04 Install freezes"
date: 2018-09-01
forum: Installation &amp; Upgrades
---

### Post by harperic on 2018-09-01
Hello, 
I have been having trouble installing Ubuntu on my recent custom built PC. I begin the install and it goes through
 as normal but once it gets to the Ubuntu loading splash screen it stops. Although the orbs continue to flash it doesn't
load. Trust me I have left it on overnight. Here are my system specs:
CPU: Ryzen 3 2200g with Raedon Vega 11 Graphics, 3.50ghz
RAM: 8gb DDR4
GPU: Nvidia GEFORCE GTX 1050 w/ 2gb vram
MOTHERBOARD: ASUS Prime B35M-A

I have already tried nomodeset and acpi=off and gotten the same results. Any Ideas? 
Thanks?

---

### Post by steven-openmedia on 2018-12-23
Looks like you've hit the same AMD GPU issues as me.

Edit the boot command line for the installer and add
 * modprobe.blacklist=amdgpu

---

### Post by oldfred on 2018-12-24
Have you updated UEFI?
With nVidia, you will need nomodeset. But some have posted this works better?         nouveau.modeset=1 
    

       Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)

---

