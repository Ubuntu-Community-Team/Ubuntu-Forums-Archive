---
title: "Video Driver AMP/ATI Rage 3 (Rage XL PCI)"
date: 2019-03-09
forum: Installation &amp; Upgrades
---

### Post by electrosteam on 2019-03-09
My hp ML110 G1 server is running 18.04.2 just fine, with the monitor at 640 x 480.
Searching for a video driver reveals that ATI stopped support some time ago and recommend finding a free driver.
My searches shows up advice only for much earlier kernels.

Can anyone suggest a driver ?

As I really need dual screen, my next step would be an adapter card.

John

---

### Post by QIII on 2019-03-09
Hello.

If you run 

```
lsmod | grep radeon
```

my guess is that you would find the Radeon module loaded.  That is the driver that is available for your hardware and it would have been used by default on installation.

I'm not sure what the capabilities of that ancient card are.  How many output ports are there?

---

### Post by electrosteam on 2019-03-09
Nil response to query for Radeon.

Tried $ inxi -F:
```

Graphics:  Card: Advanced Micro Devices [AMD/ATI] Rage 3 [Rage XL PCI]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,ati (unloaded: modesetting,vesa)
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 7.0, 128 bits)
           version: 3.3 Mesa 18.2.2

```

John

---

### Post by electrosteam on 2019-03-10
Call to EDID not successful, VBE reported ATI Mach 64.

Followed method reported by asearle in "Screen is 640x480", Post #10 on 9Mar19.
On my system needed ESC to get to GRUB.

xrandr reports display as 1024x768 - 61Hz, and it looks fine.

(just to clarify, I am running Lubuntu Desktop, not Server - just using an old hp server as the silicon)
John.

---

