---
title: "GeForce 7 Doesn't Like Ubuntu 7.1."
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by mdintzis on 2007-12-23
Ubuntu 7.1 was my sixth attempt to install a Linux OS on a desptop PC. I installed Ubuntu on a generic minitower PC with an nForce 650i Ultra motherboard (made by nVidia), a GeForce 7 video card (made by nVidia), and an Intel core duo 2 processor.

----------------------------------------------------------------------------
I've previously experimented with Mandriva, Fedora Core, Centos, and Debian---including:
* Three Gateway Pentium PCs. Two of them with nVidia graphics cards and one with an ATI card.
* A Compaq Presario minitower (AMD-based) PC with an nVidia graphics card
-------------------------------------------------------------------------------

In each case, the main problem has been the graphics card. I can never go beyond 800 x 600 resolution. Some dialog boxes under Administration and Preferences are so large that I can't reach the OK button at the bottom. Therefore, I can't make any changes to system settings.

Ubuntu is different in that it recognizes the Geforce (nVidia) graphics card model automatically. It even offers to load nVidia-provided extensions that support 3D viewing features. However, the PC began to freeze up after a couple of minutes of work. And the graphics driver got completely corrupted after just 3 or 4 restarts. After that, no further work was possible. Without graphics capability, I cannot learn anything more about Linux and troubleshoot the problem. I have no choice but to reluctantly go back to MS Windows.

---

### Post by logos34 on 2007-12-24
I wonder if compiz-fusion (enabled by default) could be part of the problem.  

to turn it off go to >system>prefs>appearance>visual effects tab

have you tried 

sudo nvidia-settings

?

There is one last thing you could try--the official proprietary nvidia driver (or beta version).

Use **Envy** to install:

[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

