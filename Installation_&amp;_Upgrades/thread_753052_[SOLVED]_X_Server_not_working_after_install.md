---
title: "[SOLVED] X Server not working after install"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by mgw854 on 2008-04-12
I just installed Ubuntu 7.10 on my PC, but X Server refuses to start.  I just get a blank screen.  I had to install Ubuntu in Safe Graphics mode.  I have a Dell E207WFP monitor connected to a NVIDIA 8800GT graphics card.  I have run dpkg-reconfigure xserver-xorg.  These are the pertinent settings I used:
Driver: vesa
Bus: PCI:4:0:0
Amt of memory: -blank-
Kernel framebuffer: Yes
Attempt monitor autodetection: No
Video modes to be used: 1600x1200
Monitor settings mode: Medium
Monitors best video mode: 1600x1200 @ 60 Hz
Write sync ranges to conf file: Yes
Default color depth: 24 bits

When I try to start X from the safe mode terminal, it flashes a bit, and then says:
```

(II) Module already built-in
(EE) AIGLX: Screen 0 is not DRI capable

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc"
refcount ia 2, should be 1; fixing.

```

And then I just return to the prompt.  Anyone have any suggestions to get this setup working?

By the way, here is the information for the monitor from Dell (refresh rates, sizes, etc). [Dell 20" Widescreen Flat Panel]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=320-5123")

---

