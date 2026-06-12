---
title: "Second monitor not recognised (Mint 18.1)"
date: 2017-01-03
forum: MINT
---

### Post by ogp on 2017-01-03
Hi, 

I'm trying to make a second monitor work on my machine but with no success. The details are as follows; 

- First monitor is plugged into a graphics card (GeForce 6600GT) and is a Hyundai 1680x1060, which works fine
- Second monitor (newly-added) is plugged into the on-board graphics of the motherboard and doesn't work
- Machine is running Mint 18.1 64-bit. 

$ inxi -G gives the following; 

```
ogp@Desktop ~ $ inxi -GGraphics:  Card-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
           Card-2: NVIDIA NV43 [GeForce 6600]
           Display Server: X.Org 1.18.4 drivers: nvidia,intel (unloaded: fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.95hz
           GLX Renderer: GeForce 6600/PCIe/SSE2 GLX Version: 2.1.2 NVIDIA 304.134



```

If I look at 'Control Centre > Displays' it only tells me that there is one display plugged in. 

The second monitor does some things (it will show the Mint logo on shut-down, for instance) but when the first monitor is up and running then it just shows what looks like a small underscore in the top left hand corner. 

On board graphics is enabled in the BIOS. 

If anyone can help me understand what to do to make the second display work then I'd be very grateful - thanks.

---

### Post by coffeecat on 2017-01-03
*Thread moved to the **MINT** sub-forum.*

---

