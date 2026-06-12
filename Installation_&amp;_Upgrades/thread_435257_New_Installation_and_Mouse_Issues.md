---
title: "New Installation and Mouse Issues"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by sh1zy on 2007-05-06
I originally installed Ubuntu x64, but then realized that I wasn't intense enough to live without 32-bit programs. After installing x32, however, I've been having mouse issues.

Specifically, the mouse moves very slowly across the screen. Seems like a hardware problem, as if too many processes are running or something. Odd part is that whenever I download something, whether through update, or using firefox, while it's downloading, the mouse movement becomes smooth and normal again. As soon as the downloading stops, it's back to being slow and sticky.

I thought the problem may have something to do with my network card, but I'm not sure. I've updated my graphics drivers to the latest ones provided by ATI, but that didn't make a difference. I also made some change to xorg.conf making my Logitech MX510 use all 5 buttons. Nothing has helped, and this "functionality" also showed up when I was running it off LiveCD and persisted after I actually installed it, but never came up when I was using x64.

Any help would be greatly appreciated.

---

### Post by skeetlz on 2008-05-25
Wow... I'm having the exact opposite problem. My mouse moves fine so long as I'm not downloading anything. As soon as I initiate a download (through firefox, synaptic, etc) the mouse slows to a crawl. I think it might have something to do with wireless interference since I am using wifi and a wireless mouse.

Has anyone else experienced this? Anyone find a workaround?

Thanks!

---

### Post by soxs on 2008-05-25
@skeetlz:
I guess your PC is really low-end? Or you always run like ~100apps at a time or some really memory/CPU intense like blender etc..

@sh1zy:
This has NOTHING (NONE, NADA!) to do with x86_64 vs ix86 to do. There shouldn't be any difference. You may attach your /bar/log/Xorg.0.log so we can check wether your mousedrivers are loaded properly or not.

---

