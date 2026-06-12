---
title: "Feisty + GeForce 8600GTS"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by mukiex on 2007-05-28
So, here's a quick rundown of my system :
Core 2 Duo E4300 (1.8ghz, 800mhz FSB)
1 GB PC667 RAM
GeForce 8600GTS

Ubuntu Feisty 32-bit

So here's my problem. I've found Envy to be the easiest way to install an Nvidia card. However, Envy doesn't have an option to download the latest beta driver, which currently is the only driver that supports the GeForce 8600GTS. So here's my jimmy rigged solution :

1.a Run :  envy -t  
1.b. Select manual installation and install latest Nvidia driver
1.c. Envy then installs the build environment for the driver and installs the driver.

2.a. Run the beta driver binary.
2.b. Binary compiles and installs.

3. run : startx

Now, this worked great, but the problem is that every time I boot into ubuntu, kdm or gdm won't load. As such, I need to redo steps 1-3 on another terminal (Ctrl+Alt+F4 is the one I usually use) for the environment to load.

Anyone come across this issue? Any solutions in mind?

Note : I allowed Envy to modify my xorg.conf and haven't touched the file since.

---

