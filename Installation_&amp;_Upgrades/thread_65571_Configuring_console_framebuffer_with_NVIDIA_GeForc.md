---
title: "Configuring console framebuffer with NVIDIA GeForce Go 6200"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by med1972 on 2005-09-14
Hi all. Not sure I am posting this to the right place. I have been running 5.04 on my old laptop (Sony VAIO PCG-V505EC w/ATI Mobility Radeon 9200) since shortly after 5.04 came out. Worked great, no issues. I just got a new laptop (Sony VAIO VGN-S470P w/NVIDIA GF Go 6200 w/Turbocache up to 128MB) and I've installed the 5.10 preview release on it. Pretty much every thing is working great except 5.10 doesn't like the console very much.

During installation the installer screens were a bit messed up. Not a big deal, I still managed to get it installed. Then I realised it was probably trying to use a framebuffer console during the install and I could probably have booted the installer without the framebuffer and it would have been fine. In fact I think this is what I did with my old laptop. At any rate, X came up just fine at the "right" resolution of 1280x800. But the console is still kinda wonky.

I've tried a few "vga=" settings and "vga=791" seems to work fine, except of course 791 is 1024x768 while the laptop is capable of 1280x800. So I am trying to figure out how I can configure the console framebuffer to give me 1280x800 resolution. I am guessing I'll need to use a "video=" line in my grub configuration but I am not sure what to use. I tried a few variations and none of them worked for me.

If I am using a video= line, should I be using video=vesafb, or video=nvidiafb? I am guessing something like:

video=[vesafb|nvidiafb]:1280x800@[some refresh rate]

Of course, another question is simply, should I use the framebuffer console at all? Is there any benefit to using a framebuffer console if I am in X 99% of the time? If not, what is the easiest way to "turn off" the framebuffer? Just use "vga=ask" and then change "vga=ask" to "vga=[some value from vga=ask that works]"?

Thanks,

Mark

---

