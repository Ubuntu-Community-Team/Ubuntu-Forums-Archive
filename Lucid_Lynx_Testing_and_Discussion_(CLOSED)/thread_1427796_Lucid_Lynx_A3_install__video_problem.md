---
title: "Lucid Lynx A3 install : video problem"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kqr2 on 2010-03-12
Hi,

I'm trying to do a CD install of Lucid Lynx Alpha 3 Desktop on a mini-itx x86 system with a 24-bit 640x480 LVDS (LCD) display.

I can get to the initial install screen, however, when I try to either run the live cd or install to disk, the video then goes haywire -- appearing as garbled stripes.

I've added the option 'vga=ask' and it correctly shows the video modes:

Mode 0x301 : 640x480, 8 bits
Mode 0x311 : 640x480, 16 bits
Mode 0x312 :  640x480, 24 bits

When I try entering any of the modes, however, the video is still garbled.  

For comparison purposes, I can run the Ubuntu 8.04 install CD without any problems and when I do 'hwinfo --framebuffer', it correctly lists the above video modes.

Is there a way I can troubleshoot this on the Lucid Lynx installer?  It seems to me that the video mode isn't getting set properly even if I manually set the 'vga=<mode>' kernel option.

Even if I try to go to a virtual terminal, the video is still messed up.

Thanks.

---

### Post by cariboo on 2010-03-12
Try the nomodeset option available by pressing F6.

---

### Post by kqr2 on 2010-03-12
Thanks for the suggestion.

I tried the F6/nomodeset option with both the live cd and install commands, but no luck.  The screen is still out of sync with scrolling garbled stripes.

I forgot to mention that the board is actually a VIA nano with via vx800 integrated graphics chipset.  Older versions of ubuntu, however, don't seem to have a problem with that.

Any other suggestions for debugging or dropping into a fail safe mode.

---

