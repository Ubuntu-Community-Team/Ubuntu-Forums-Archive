---
title: "usplash: Setting mode 1152x864 failed"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2009-10-23
For a few weeks now, I've noticed the following console output during boot.
```
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
```

My computer has a native resolution of 1440x900. The card is an NVidia GeForce 8400M GT.

My usplash.conf file does have 1440x900 set, so it should be trying to set that resolution. Judging by the console message above, it isn't.

Because usplash starts at 1024x768 on my widescreen display, I am greeted with a blurred, _slightly_ horizontally stretched Ubuntu icon, prior to Xsplash taking over (Xsplash has no problem with the resolution).

Is anybody else having this issue? The only bug report I could find on the subject is: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/67826](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/67826)

Thanks in advance.

---

### Post by ranch hand on 2009-10-23
I would find the image and change the resolution of it to fit your system but I don't have a clue where it is.

A nautilus search for .jpg and .png should turn it up after a bit and then you would have to wade through them.

Or you could easily be better at me  in picking where they should be.

---

### Post by wnelson on 2009-10-23
Change /etc/usplash.conf xref=1024 yref=768

---

### Post by wnelson on 2009-10-23
xres, yres

---

### Post by cyberkilla on 2009-10-24
> **wnelson said:**
> xres, yres

While that would solve the console output problem, it would still give me an awful resolution for the splash image.

Do you know of any reason that it would fail to set 1440x900? I mean, where does it set the bit depth or refresh rate?

Here is the output of "sudo hwinfo --framebuffer"

```
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.464]
  Unique ID: rdCR.7ayFuy4p6eE
  Hardware Class: framebuffer
  Model: "NVIDIA G86 Board - e415h01 "
  Vendor: "NVIDIA Corporation"
  Device: "G86 Board - e415h01 "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xcd000000-0xcddfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  [B]Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits[/B]
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

I notice that 16bits is missing for the 1440x900 resolution. Could this be the source of the problem? I'm grasping at straws here.

---

### Post by cyberkilla on 2009-10-24
I wonder how I can test my theory. Perhaps if I tried each resolution with no 16bit, then the ones _with_ 16bit listed.

If all of the resolutions with 16bit work, and all of the resolutions without 16bit listed as a valid mode fail, then it's pretty much certain.

I'll be back in a few minutes with the result.

EDIT:

I am no further forward here. Setting it to 1280x800 seemed to work, but it was obviously still rather blurred. I cannot get 1440x900 to work, so I've set it to 1024x768 to avoid any console error messages.

If anybody has a solution, please let me know. Vesa reports that 1440x900 is a valid display mode, so I can't understand why usplash can't use it.

---

