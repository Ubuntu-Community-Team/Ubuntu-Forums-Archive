---
title: "Grub Bootloader"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by devninja on 2012-08-08
After I install Ubuntu 12.04 and reboot, the boot loader starts then a bunch of colors fill the screen like static. Then when i go to run windows booting from the hard drive with windows on it it tells me missing operating system. Note: Before selecting to install Ubuntu from the boot options screen on the disk i pressed f6 and selected nomodeset because if i did not select that the screen would just be a blinking cursor after pressing "Install Ubuntu".

P.S

Before putting in my GTX 570 I was able to install and run Ubuntu without any problems.

Specs
MoBO: MSIH61-E33M
CPU: Intel core i5 2300
RAM: 4GB 1333MHZ
GPU: EVGA GTX 570 1GB

---

### Post by darkod on 2012-08-08
If you needed nomodeset to start the install, you also need it on first boot.

When the grub2 menu shows, highlight the ubuntu entry and press 'e' for edit. It will show the boot lines.

Use the arrows and go towards the end of the line starting with linux. Add nomodeset after the 'quier splash'. Press Ctrl + X or F10 to boot.

This is also a one time option, it doesn't get saved. Usually if you boot once, go into Additional Drivers and activate the video driver, you don't need the nomodeset again.

If you continue to need it, there is another procedure to make it permanent. Untill then you will need to add it manually on each boot.

---

### Post by devninja on 2012-08-10
The Thing is when i load into grub 2 the whole screen goes static with random colors.

---

