---
title: "Upgrade from Ubuntu 10.04 to 10.10 failed"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by lunar1225 on 2010-10-27
I just tried to upgrade my laptop from Ubuntu 10.04 to 10.10 (both were 64 bit versions). I used the upgrade manager. During the process, it said there was some sort of error, but I'm sorry, I don't remember what it was. I just ignored it. When I rebooted my laptop to finish the installation, it got stuck on a black screen with white type. It said "laptop-login:   ". I couldn't figure out what was happening, so I turned off my laptop, then try to reboot. This time it got to the log in screen, and played the little ubuntu "drum" sound, but all the screen displayed was random vertical red, green, and blue lines of varying lightness, and a small mass of little blue green and red dots that moved when I moved the mouse. I don't know what failed where, so I booted up the safe mode, and tried repairing broken packages. It ran through the prosess, though at the end it said "errors were encountered while processing:   fglrx   E: sub process /use/bin/dpkg  returned error code (1)". I don't know if this has anything to do with the failure of the upgrade. I don't know a lot about ubuntu, so I am lost as to what I need to try next.

My laptop is a Dell Studio XPS 1640, Intel Core 2 Duo CPU P8700 @2.53 GHz, 4 GB RAM, ATI Mobility Radeon HD 3670. I have it dual booting with windows 7, so I know that it can't be a problem with broken hardware.

Thanks in advance for any help.

---

### Post by oldfred on 2010-10-28
I have nvidia, so you setting may be different:

On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

All drivers: nomodeset - this will disable the kernel modesetting feature and drop the user back to the old X.org infrastructure and behaviour. 
nouveau.modeset=1

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)

---

