---
title: "Sparkle nVidia GeForce 8400 GS breaking 11.04 Install"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by skunk.grunt on 2011-05-05
I read a couple similar threads relating to my problem but neither had a solution that worked for me.

I tried an 11.04 install through WUBI, and after the first part of the installation in the ubuntu environment, it restarts fine, but then never gets past the grub loader.  A blinking cursor is all I get, then it restarts.  This is an infinite loop if I choose ubuntu every time.  Plugging in my monitor the onboard video works like a charm.  It's just the card that's causing problems.  

I have the latest BIOS update for my Dell e310 (Yeah, I know it's ancient), the current drivers for the card and the video works great in Win XP.

I even installed 10.10 through WUBI and it installed with the card just fine.  I figured I'd just do a distro upgrade and bypass the problem.  Nope.  Same problem.  As soon as it restarted, it hit the same boot loop.  This is scrictly and issue between the graphics card and 11.04 as far as I can see.

I will mention that before the bios screen, the nvidia info pops up on the screen and it states pcie, but it's not.  Regular old PCi card.

---

### Post by skunk.grunt on 2011-05-06
Well, I fixed the problem.

I installed Linux Mint with mint4win.

Bye bye ubuntu.

---

### Post by amolvaidya06 on 2011-08-14
I have the same forward with a geforce 8400.  Interestingly I also have Dimension E310.  Going to try Mint.

---

### Post by amolvaidya06 on 2011-08-15
Linux Mint was also a no-go.  Just looped booting the computer.  Could never get past the boot-loader.  I was wondering if I should try and install Linux using the integrated graphics card (which seems to work fine) and then try and download drivers, or something else for the Geforce 8400?  Any ideas on how I may proceed.

---

### Post by amolvaidya06 on 2011-08-15
I'm wondering if this could be due to an insufficient power supply?  Someone on another forum suggested this, and after checking the power supply in my computer it only deliver a 240 watt output, whereas the minimum required by the graphics card is 300 watts.

---

