---
title: "How well is power consumption going on your laptop?"
date: 2008-07-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dgf on 2008-07-15
hi,
yesterday I looked with powertop how much Watts it is using, and I was shocked. When it was with hardy still 12.4W with darkest display, sound off, cd off and wifi on, it is with intrepid 10.0W. That is less than I have got with Windows, which got the drivers from Sony.

So, how well is this going on your mashines? I don't want it to be a failure of powertop on my laptop, it HAS to be true.

The only thing that annoys me now is that the hard disc is too often on. Even when in piding someone comes online it has too load his picture from disk, instead of having it in RAM already.
Oh and hibernate and suspend, which naturerally aren't really working...

---

### Post by vikrant82 on 2008-07-15
Hardy it was 13-14watts, with wireless in power save mode. This is a 15.4 inch widescreen.

With intrepid, well its almost same.

---

### Post by olskar on 2008-07-15
It should get better. This is the third highest voted idea on brainstorm, [http://brainstorm.ubuntu.com/idea/81/](http://brainstorm.ubuntu.com/idea/81/) and it is "marked as being in development the 18 March 08. "

---

### Post by Amaranth on 2008-07-15
I don't remember the specific numbers but with wifi and such on intrepid uses 1W more than OS X (macbook) so we're doing pretty good. Heck, the 1W difference could even be because I have to use ndiswrapper since this is a broadcom 4328.

---

### Post by psyke83 on 2008-07-15
This may be a crazy idea, just bear with me. Since the recent Xorg and Mesa updates, 2D rendering seems to have improved immensely. The intel driver still uses the EXA acceleration method by default, but the driver no longer forces the "greedy" Migration Heuristic (the default is "always", and in the past it was causing slow 2D rendering for many users). In other words, 2D rendering seems a lot snappier.

What's even more surprising, though, is that my system uses less CPU when compiz is enabled! I have the CPU Frequency Scaling applet and System Monitor running, and I notice that many operations use much less CPU in compiz. 

For example: if you frantically scroll a webpage while compiz is enabled, the CPU scales between 600Mhz to 1200Mhz (usually stays at around 800Mhz). Without compiz, it usually maxes out at 1500Mhz. This is incredibly surprising for me, as I'm using an internal Intel 855GM chipset, pretty old by today's standards. Switching between tabs in Firefox uses less CPU with compiz. Scrolling a window uses ~7% CPU with compiz, and ~50% CPU without (admittedly, compiz always helped in this case). The only time I notice increased CPU usage with compiz is from intensive Flash videos and some animations, but the increase is negligible.

So... give compiz a try and see if it helps reduce your power consumption (although CPU usage does not equate power consumption, as compiz may prevent your graphics card from entering a power saving state). You have nothing to lose by trying ;).

---

