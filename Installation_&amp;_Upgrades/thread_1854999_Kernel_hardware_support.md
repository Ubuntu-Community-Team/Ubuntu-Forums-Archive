---
title: "Kernel hardware support?"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by Acerbity on 2011-10-05
I am reasonably new to Ubuntu and am making good progress.  I have a question regarding hardware support.

My company sells a network product using an OEM "black box" we'll say.  It's actually a 10.04 server running some custom daemons.  Here is my issue...

We build the system using preseed, (I have that working great) then once the system is complete and customized, I will make an image of the machine using Clonezilla and imaging the rest of the like machines (also works great).

The problem comes in when the system that we order changes.  If I apply the image to a machine that is NOT hardware identical, it can sometimes lead to problems (kernel panics) and I believe I have tracked it down to any change in the chipset that controls the storage (AHCI).

My question is, is there a way for me to clone the machine, then re-install or "refresh" the kernel to recognize and support the hardware changes?  The customizations of each system take a few hours to complete, and if there was a way to do this, it would save me a great deal of time each instance there was a hardware change.

Thanks!

---

