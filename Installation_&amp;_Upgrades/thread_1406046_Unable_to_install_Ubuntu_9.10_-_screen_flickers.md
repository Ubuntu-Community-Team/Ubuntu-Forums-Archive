---
title: "Unable to install Ubuntu 9.10 - screen flickers"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by suhasrs on 2010-02-13
I am trying to install Ubuntu 9.10 but got a blank white screen with default install settings.

I changed to safe graphics mode, then I was able to see the installation screen. After 2-3 min the screen started flickering and the mouse/keyboard did not work and the system hung.

Then i tried adding the boot parameter **fb=false** (after reading about this in ubuntu troubleshoot section). Now also the screen flickers, but then as soon as the flickering starts the system reboots.

Then I tried adding the boot parameter **vga=788**, but it made no difference. Then i tried **vga=ask** and then chose a 800x600 VESA resolution, but this too made no difference.

The display adapter is NVIDIA GeFORCE 6150SE nForce 430 that is inbuilt with ASUS M2N-MX motherboard.The system has 3 GB of RAM

The problem also occurs on LiveCD boot too.

I think that the problem is that it is not recognizing the display driver.

Please guide me in solving this issue and installing Ubuntu 9.10.

---

