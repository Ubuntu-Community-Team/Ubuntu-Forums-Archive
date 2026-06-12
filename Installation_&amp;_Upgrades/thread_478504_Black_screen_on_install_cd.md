---
title: "Black screen on install cd"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by knyfer on 2007-06-19
Whenever I try to run (K)ubuntu 7.04, after the LiveCD loads the Linux kernel, the splash screen fails to load and the screen goes black.  I can't get to the desktop to install it, and the CD has no defects.  Versions before 6.06 worked fine.

Comp: M7674N HP MC TV

OS: Windows Vista Home Premium 32-bit

Video Card: (I think this is the issue) ATI Radeon X1900 GT

CD/DVD Drive: TSSTcorp CD/DVDW TS-H653L

HD: 2 X 200 GB in Bios Raid 0

Processor: Intel Core 2 Duo E6400 @ 2.13 Ghz

---

### Post by merlinus on 2007-06-19
Have you tried Safe (Video) Mode?

You might also try this:

At the command prompt, type sudo dpkg-reconfigure -phigh xsever-xorg

Then select vesa as your video driver and use the space bar to select the resolution.

-merlin

---

### Post by knyfer on 2007-06-19
> **merlinus said:**
> Have you tried Safe (Video) Mode?

You might also try this:

At the command prompt, type sudo dpkg-reconfigure -phigh xsever-xorg

Then select vesa as your video driver and use the space bar to select the resolution.

-merlin



It won't even go to the command prompt.  It's ctrl + 1, right?

---

### Post by Widodh on 2007-06-21
I have exactly the same problem with my desktop.

My desktop:
- Intel Core2Duo E6600
- 4GB DDR2
- Asus P5 Mainboard
- Asus nVidia 8800GTS

I tried both Ubuntu and Kubuntu, but they both get to a black screen.

The safe (video) mode doesn't work either.

I am trying to install the AMD64 btw.

---

