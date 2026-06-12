---
title: "Curious Graphical Corruption (Boot/Shut Down)"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kestal on 2009-08-15
**Hardware with the problem:**

Laptop - Dell New Studio 14z laptop - Intel 9400m-g video card
Desktop - Custom Built - 4gb ram, 2.8ghz dual, Intel (XFX) 8500g 512mb Video Card

**First Question/Inquiry**

During the boot up and shut down procedure (prior to the graphical load and shutdown screens), there is a split second or two where I experience greenish (or sometimes orange) graphical corruption. Some times, its in the form of a previous screen I have experience (in desktop), or others its just randomized throughout my screen in segmented lines.

I thought that with KMS and karmic it may have changed, but it seems that this is still there (just tested Karmic Alpha 4). Its curious as I note that this only seems to happen with Ubuntu.

Is this only happening to me? Others with Intel cards maybe? or ati? I noticed that nv was switching to nouveau but it was postponed, would this maybe help?

Right now I am testing Ubuntu via Virtual Drive on laptop (I need to purchase an external DVD drive still).

**Second Problem/Inquiry:**

Also, to get my hardware to work (and accept something above 800x600 display), I had to i915.modeset=0.

What is the reason of this? Is it just because its an alpha release? Isnt modesetting supposed to be a good thing?

**Third Problem/Inquiry:**

This has been a problem only starting with Karmic alpha's. I cannot seem to boot/install from Usb. It was fine in Jaunty, but no longer. Is anyone else having this problem? (it sticks me to tty1 from live cd load up)

---

### Post by kestal on 2009-08-15
anyone?

---

### Post by VMC on 2009-08-15
I have an older Intel chip, i865. I'm not sure if its the same, but if I do vga=773, then on reboot of shutdown I get several graphic rows of multi-coloreds. I have to use use nomodeset without vga=773. Also I had to revert to previous intel driver 2.4. 

I'm not sure if the current updates will allow me to use the current Intel drivers of not. Oddly enough, Fedora doesn't have any of these issues.

---

### Post by kestal on 2009-08-15
> **VMC said:**
> I have an older Intel chip, i865. I'm not sure if its the same, but if I do vga=773, then on reboot of shutdown I get several graphic rows of multi-coloreds. I have to use use nomodeset without vga=773. Also I had to revert to previous intel driver 2.4. 

I'm not sure if the current updates will allow me to use the current Intel drivers of not. Oddly enough, Fedora doesn't have any of these issues.

I had that problem on Jaunty, but Karmic fixed it for me. However, the graphical corruption/shadow images have been there, for me, on all my desktops/laptops, since 8.04.

---

