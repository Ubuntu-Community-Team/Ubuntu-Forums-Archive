---
title: "Poor Framerates with ATI 9800"
date: 2005-06-20
forum: Installation &amp; Upgrades
---

### Post by Spikey on 2005-06-20
Hi,

I recently installed my ATI driver on my Ubuntu system and i am not really noticing a good difference. When i run glx gears i get:

2373 frames in 5.0 seconds = 474.600 FPS
1582 frames in 5.0 seconds = 316.400 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1582 frames in 5.0 seconds = 316.400 FPS
1469 frames in 5.0 seconds = 293.800 FPS

These numbers jump up and down. It apears as though i installed the Drivers correctly as i followed the tut at [HTML]http://ubuntuforums.org/showthread.php?t=24557[/HTML] 

and the ATI Control Pannel shows this:

Display Adapter

Card Name: Radeon 9800
Bios Version: 8.17
Chip Type: ATI Radeon 9800 (R350 NH)
Chip Revision: A13
DAC Speed 400MHz
Memory Type: DDR SDRAM
Memory Size: 128 MByte
Transfer Mode: PCI 

Display Driver
Driver version: 8.14.13
Open GL
Open GL Verdor StringMesa project: [www.mesa3d.org](www.mesa3d.org)
Open GL renderer strirMesa GLX Indirect
Open GL Version String 1.2 (1.5 Mesa 6.2.1)





When i run fgl_gears i get this error.

celliott@ell-tech:~$ fgl_glxgears
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  161 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32

Does anyone have any ideas what is wrong with my Driver install???

Thanks
Spikey

---

### Post by afonic on 2005-06-21
It has not installed correctly. You should get Ati as OpenGL Verdor and not Mesa.

Post your xorg.conf file, it may help finding the problem.

---

