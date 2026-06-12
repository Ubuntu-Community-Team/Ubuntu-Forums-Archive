---
title: "Upgraded from Feisty, Nvidia drivers missing."
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by karloscarweber1 on 2007-10-25
I've been using Feisty for about six weeks, upgraded to Gutsy in OS and now the Nvidia drivers are missing or don't work.  I can't even boot into the operating system, it gives me an error that the X-windows system can't initialize. 

Very strange to remove the drivers that I have installed when the OS is upgraded.  

How do I solve this problem and boot into my now upgraded OS?

---

### Post by gtdaqua on 2007-10-25
Had the same issue. 
You need to configure X Server with 'vesa' driver to have the GUI. Then download the latest NVIDIA driver, linux-restricted-modules and kernel-source. Install the NVIDIA driver. Then remove the linux-restricted-module so that NVIDIA works without interruption.

You need the linux-restricted-module and kernel-source to have it installed. And you have to remove the restricted-module later to have it working continuously! bizarre!

---

### Post by Steve1961 on 2007-10-25
Boot up and when you get the error message hit ctrl-alt-f2 to open a virtual terminal.  Login and type:

sudo nano /etc/X11/xorg.conf

Change the "nvidia" driver to "vesa" and save and close.  Then type:

sudo shutdown -r now

This should at least get you back into a graphical environment so that you can troubleshoot.  I suspect that the linux restricted modules package for your new kernel might not be installed.

---

### Post by Skweek on 2007-10-25
You could try the new version of Envy.. [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
It worked perfectly for me last night.

---

### Post by kennedyjch on 2007-10-25
I second the effacacy of the ENVY ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))  scripts in getting both Feisty and Gutsy to function with my NVidia card.

---

