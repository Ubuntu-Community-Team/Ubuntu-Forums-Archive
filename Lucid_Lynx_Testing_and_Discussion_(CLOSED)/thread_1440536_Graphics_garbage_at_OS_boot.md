---
title: "Graphics garbage at OS boot"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bwallum on 2010-03-27
When I boot up, grub2 comes up fine and the grub menu. I have a background image for the grub menu screen and the text is displayed ok in a 1024x768 format.

However when the system moves beyond grub to, I presume, a splash screen, I get some graphics garbage at the top of the screen. I can't see whats going on, could be 'checking disk' I guess when the os bootstrap is delayed.

The Desktop comes up ok.

Similar garbage happens upon exit.

As well as changing the resolution for the grub menu screen I run the nVidia driver for normal graphics.

I presume that the grub menu uses the vga pass through function of the graphics card.

What does the Ubuntu entry and exit splash use? Could the splash(es) be trying to use the nVidia driver before it is loaded/after it is terminated?

---

