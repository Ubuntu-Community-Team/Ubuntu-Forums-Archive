---
title: "Ubuntu 11.10 Installation Issues on Custom Hardware"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by Stevetronics on 2012-01-22
Hey all,
Hopefully you can help me out with this. I've been having troubles installing Ubuntu 11.10 x64 on my computer. I built it myself, and I know it has far more "oompf" than Ubuntu needs to run. I am installing into a 60GB OCZ Vertex2 SSD, and I give the installation 56GB for / and 4GB swap, and then I have a 2TB data drive. I've tried five clean installs today, and only one has worked, and then it was broken when trying to use ndiswrapper to wrap drivers for the netgear WNDA3100v2 Wireless-N adapter. When the install doesn't work, here's what I see: First, the install itself (the actual act, when the disc is in the tray) works fine, no errors. Then, When I boot without the disc, it starts to boot (I get that ubuntu purple background) then two of my screens go black (the ones the install had been using) and my third lights up, but displays nothing. ?

Here's my setup:

Intel Core i5 2500k
16GB G.Skill Ripjaws X DDR3 RAM
ASRock Z68 Xtreme3 Gen3 Motherboard
64GB Crucial SSD (Windows Drive)
60GB OCZ Vertex2 SSD (Ubuntu Drive)
2TB Western Digital Caviar Green (Data Drive)
2x XFX ATI Radeon HD 6950 2GB graphics cards in Crossfire
3x Acer G235H monitors

[LIST]
[*]Monitors 1 and 2 are on the first 6950
[*]Monitor 3 is on the motherboard's integrated graphics
[*]Crossfire will only let you drive monitors from the top card, which is why there is a monitor on IG even though I have a second card.
[/LIST]
When I boot the liveCD, (as in right now) it boots just fine, runs off the monitors on my graphics card, and ignores the one on integrated. It even lets me extend the desktop over both - I have a dual-monitor liveCD. What's going on?

Thanks,
Steve

---

### Post by Quackers on 2012-01-22
Have you tried booting with the nomodeset option? If it boots with that you can install the video drivers.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

EDIT
Actually there may be a problem with crossfire. Can you disable one video card and see what happens?

---

### Post by Stevetronics on 2012-01-22
Sure. Any other diagnostic info that would help out?

---

### Post by Quackers on 2012-01-22
Are there 2 graphics cards AND an onboard graphics too?
Ubuntu will struggle with more than one graphics chip. Try disabling all but one and then try booting. If you still get a blank screen try the nomodeset boot option from that link. See how that goes.

EDIT
To get to the grub menu you will need to tap the shift key during boot (or the Esc key).

---

### Post by Stevetronics on 2012-02-16
Hey all,
Sorry to resurrect an old thread, but I have this problem still. I have bought and installed an AMD-certified Mini-Displayport to single-link DVI active adapter, and I am having issues with using my monitors in a non-mirrored setup. When I make display changes, the screen goes to hell. The system responds, and teh cursor and windows render correctly, but any text looks like there's an inch of water between my eyes and the screen.. Any suggestions?

---

