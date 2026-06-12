---
title: "What image do I use for ARM926?"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by compiz addict on 2012-06-26
I have an E700 Wince series Easy PC. It has an ARM926 processor.

It was running Windows CE (YUK!), which wasn't even booting, so now I want Ubuntu on it.

So, on the instructions for installing Ubuntu on an ARM system ([https://wiki.ubuntu.com/ARM/OmapDesktopInstall](https://wiki.ubuntu.com/ARM/OmapDesktopInstall)), it asks me to choose between OMAP3 and OMAP4.

Which should I use? Either of them? This netbook has the Tim Hortons logo on it, so I really want to get it working :D

---

### Post by Cheesemill on 2012-06-26
From the specs I have just looked at the ARM926 uses a v5 architecture.
[http://www.arm.com/products/processors/classic/arm9/arm926.php?tab=Specifications+](http://www.arm.com/products/processors/classic/arm9/arm926.php?tab=Specifications+)

As Ubuntu is only compiled for v7 and above then you won't ever be able to run Ubuntu on an ARM926 processor.

---

### Post by compiz addict on 2012-06-27
Heh, well that's a shame. It really doesn't have to be Ubuntu though (any Linux distro is better than Wince). Is there any other distro that I can get working?

---

### Post by dino99 on 2012-06-27
> **compiz addict said:**
> Heh, well that's a shame. It really doesn't have to be Ubuntu though (any Linux distro is better than Wince). Is there any other distro that I can get working?

Seems that the only choice is to compile the kernel source for this proc

---

### Post by compiz addict on 2012-06-27
Hmm... that actually sounds like fun.

I'm going to try these instructions:

[http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.faqs/ka4134.html](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.faqs/ka4134.html)

So, it's safe to build the image on my own desktop computer, right?

Also, will it be a pain in the *** to get this to boot of of an SD card?

I might just try to find an Android image for it instead, but I think I'll try this just for the learning experience.

---

