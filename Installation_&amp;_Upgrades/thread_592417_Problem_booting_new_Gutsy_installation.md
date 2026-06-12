---
title: "Problem booting new Gutsy installation"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by kappa01 on 2007-10-26
I did a clean install of Gutsy on a Thinkpad T41, but now I'm having a problem booting it.

Grub correctly reports only the Gutsy installation and presents two options to boot into it, normal and recovery mode.

When I try the normal mode, the system hangs immediately after clearing the Grub screen.  The screen is backlit, but otherwise blank.

In contrast, when I try recovery mode, everything goes fine, the system taking me to the CL, logged in as root.  When I log out of root (CTRL-D), X starts followed by the display manager and then I'm able to work normally.

What's going on and how to diagnose and fix?

---

### Post by Fire_Chief on 2007-10-26
What symptoms are you seeing which lead you to the conclusion that the system is hanging during regular boot up?

---

### Post by kappa01 on 2007-10-26
It's completely frozen.

---

### Post by Pumalite on 2007-10-26
'IBM offers the Thinkpad T41 in a range of options, with processors ranging from a 1.7GHz Pentium M down to the 1.4GHz Pentium M that powered our review sample. This is supported by a disappointing 256MB of PC2700 memory (333MHz DDR). 512MB is nearer the norm for a notebook these days, but there is an additional SODIMM slot should you need more, up to a maximum of 2GB.

The graphics are a little surprising, in that they are of a standard above what your normal corporate user requires. ATI's Mobility Radeon 7500 chip provides the horsepower for the graphics and while the Thinkpad T41 certainly isn't a gaming notebook, the graphics controller lets you have a stab at all but the most recent games.'
With ATI, you probably need to configure xserver. With 256 MB of RAM, you'd be better off with Xubuntu Alternate CD

---

### Post by Fire_Chief on 2007-10-26
Does the splash screen appear with the loading bar? Does the loading bar reach a certain fill percentage across the screen? Do your caps lock or num lock keys still light when pressed? Does the hard drive light flicker, stay solid on, or completely off? What sort of network connection are you using (wired, wireless)?

In recovery mode, you can view the /var/log/messages file to see if there is any information from the previous startup which may indicate a problem. 

Any other information you can share about the problem will be helpful. :)

---

### Post by kappa01 on 2007-10-26
After the Grub screen disappears, there is nothing...just a backlit black screen.
I haven't checked CapLock or NumLock (on another machine now).
The drive light is dark.
Using wireless, but by the speed of failure (nearly instantaneous after Grub clears), I doubt that any drivers have loaded.  In anycase, the wireless connection works fine in recovery mode.
I'll try checking the boot log, but again, it seems to crash to soon for anything linux to be happening...it all dies in the instant after Grub blanks.
P

---

### Post by Fire_Chief on 2007-10-26
You could edit your GRUB menu.lst file in /boot/grub and remove the quiet and splash options to see everything that is happening behind the scenes. This will let you see exactly how far the boot process is getting beyond GRUB.

---

### Post by kappa01 on 2007-10-26
After editing menu.lst, do I need to do anything to get grub to recognize the changes?
P

---

### Post by Fire_Chief on 2007-10-26
No, when you save the changes and reboot, GRUB re-reads the file (actually reads it every time the system boots).

---

