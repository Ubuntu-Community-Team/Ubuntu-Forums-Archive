---
title: "Ubuntu 16.10 desktop live cd cannot boot to graphical desktop?"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by shamsat on 2016-10-16
Hi,
I just tried to boot the ubuntu-16.10-desktop-amd64.iso, there is first for while console login prompt then error message "the graphics is not detected", the live cd cannot boot to graphical desktop, i tried two different DELL laptops but no success, is there any way to install this live cd  from it's console prompt?

---

### Post by howefield on 2016-10-16
Try setting the nomodeset option when booting from the Live media, if it works you can add it to the grub menu for use when installed.

After selecting your language when booting the Live media, press the F6 button and scroll down to and select the nomodeset option. Enter and continue the boot process,.

---

### Post by shamsat on 2016-10-16
Thanks for the reply, i boot with the nomodeset option there is some changes, booted with the low resolution and there is for seconds pink screen but still no succes, cannot start the desktop.

---

### Post by howefield on 2016-10-16
Can you provide the full specifications for the machine that you are currently trying ?

---

### Post by shamsat on 2016-10-16
These are some details:
> 
DeLL leptop Inspiron 15 3000 series 
Processor: Intel® Core&#8482; i7-4510U CPU @ 2.00GHz × 4 
Graphics:  Intel® Haswell Mobile
OS type:   64-bit


Is there any alternate installation option.

---

