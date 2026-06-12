---
title: "Resolution Problem with Ubuntu"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by Joorik on 2012-03-10
Hello guys,

I've recently bought an Asrock ION 3D 152D HTPC. I installed Ubuntu on it, but the resolution was really low and parts of the desktop were offscreen.

I have a 32" Philips 32pfl7605, connected the HTPC via HDMI. It only lists 640x480 and lower as possible resolutions.

I did some checking on my own, and "Upscaling" was turned on on the TV. So I turned that off, and now it just looks silly. It only uses 640x480 pixels on the center of the screen, the rest is black.

I currently have XBMC Live installed (packaged with ubuntu), and the problem is still here!

Anyone know what the problem could be?

Thanks!

---

### Post by Joorik on 2012-11-16
Anyone? I still haven't figured it out :(

---

### Post by cortman on 2012-11-16
What are the outputs of

```
xrandr
lshw -C | grep video
lspci | grep -i vga
```

---

### Post by Joorik on 2012-11-16
> **cortman said:**
> What are the outputs of

```
xrandr
lshw -C | grep video
lspci | grep -i vga
```

I'm currently at work, so I can't check that.

I do have the output of Xorg.0.log, this looks a bit wrong:

> 
(WW) Mar 13 21:30:32 NVIDIA(GPU-0): The EDID read for display device DFP-1 is invalid:
(WW) Mar 13 21:30:32 NVIDIA(GPU-0):     unrecognized EDID Header.
(--) Mar 13 21:30:32 NVIDIA(GPU-0): 
(--) Mar 13 21:30:32 NVIDIA(GPU-0): Raw EDID bytes:
(--) Mar 13 21:30:32 NVIDIA(GPU-0): 
(--) Mar 13 21:30:32 NVIDIA(GPU-0):   1d 7b fd 9f ff ff ff 00  41 0c 00 00 01 01 01 01
(--) Mar 13 21:30:32 NVIDIA(GPU-0):   03 14 01 03 80 80 48 78  0a e6 92 a3 54 4a 99 26
(--) Mar 13 21:30:32 NVIDIA(GPU-0):   0f 4a 4c 21 08 00 8b c0  81 80 a9 40 01 01 01 01
(--) Mar 13 21:30:32 NVIDIA(GPU-0):   01 01 01 01 01 01 02 3a  80 18 71 38 2d 40 58 2c
(--) Mar 13 21:30:32 NVIDIA(GPU-0):   45 00 00 d0 52 00 00 1e  02 3a 80 d0 72 38 2d 40
(--) Mar 13 21:30:32 NVIDIA(GPU-0):   10 2c 45 80 00 d0 52 00  00 1e 00 00 00 fc 00 50
(--) Mar 13 21:30:32 NVIDIA(GPU-0):   68 69 6c 69 70 73 20 46  54 56 0a 20 00 00 00 fd
(--) Mar 13 21:30:32 NVIDIA(GPU-0):   00 30 3e 0f 46 11 00 0a  20 20 20 20 20 20 01 c9
(--) Mar 13 21:30:32 NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 


Edit: It's connected via HDMI.

---

