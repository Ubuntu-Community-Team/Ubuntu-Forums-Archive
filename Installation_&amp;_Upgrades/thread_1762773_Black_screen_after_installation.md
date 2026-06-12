---
title: "Black screen after installation"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by sydpolk on 2011-05-19
I installed 11.04 Desktop disk on my HP wx8000 workstation. When I rebooted, it gave me the black screen with a blinking caret.

- I have tried reinsalling grub2.
- I have tried adding "nomodeset" to the load command line
- I have tried setting grub to use only text mode.

I would appreciate some futher pointers, as I am stuck.

---

### Post by jerrrys on 2011-05-20
read this

[http://ubuntuforums.org/showthread.php?t=1756110](http://ubuntuforums.org/showthread.php?t=1756110)

---

### Post by sydpolk on 2011-05-27
I have tried everything I could except downgrading the kernel and grub that was references from that page and all pages that it references. I am still getting a black screen even with most of the workarounds I see in the massive threads on the subject.

I have never seen anything but a black screen despite setting GRUB_GFXMODE to 640x480 or text. The Live CD works fine.

All of the flowcharts say something like "If you see a grub menu, go to Step 2. If you don't, reinstall grub." I have done that several times.

I would appreciate some hand-holding here. I am running a HP wx8600 workstation with an NVIDIA card. I am enclosing the output from "hwinfo --framebuffer".

```
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.464]
  Unique ID: rdCR.dT2SpPKHP90
  Hardware Class: framebuffer
  Model: "NVIDIA G84 Board - p588h500"
  Vendor: "NVIDIA Corporation"
  Device: "G84 Board - p588h500"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xf1000000-0xf1dfffff (rw)
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
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

I must say that I am quite disappointed with this experience.

---

### Post by Sumstah on 2011-05-28
I was having the same problem.

Have you tried, on the GRUB screen where you choose what OS you want to load.

Be clicked on the Ubuntu OS, then press 'e'.

where it says 'quiet splash', delete them and type 'nomodeset' then press CTRL+X.

I only started using Ubuntu a few days ago so what I have suggested may not help.

Hopefully this will work for you.

---

### Post by sydpolk on 2011-05-28
> **Sumstah said:**
> I was having the same problem.

Have you tried, on the GRUB screen where you choose what OS you want to load.

Be clicked on the Ubuntu OS, then press 'e'.

where it says 'quiet splash', delete them and type 'nomodeset' then press CTRL+X.

I only started using Ubuntu a few days ago so what I have suggested may not help.

Hopefully this will work for you.

I never get a grub screen. I just get a black screen with a blinking caret.

---

### Post by Sumstah on 2011-05-28
Oh, I was getting a black screen with a blinking caret in the top left hand corner, after I was choosing Ubuntu from the Grub screen.

Sorry I don't know anything else to suggest, as I am new to Ubuntu.

Regards.

---

### Post by sydpolk on 2011-06-01
Turns out this beast has a RAID controller that Ubuntu does not like. Disabling it and setting the drives to IDE emulation fixed the problem.

---

