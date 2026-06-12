---
title: "[SOLVED] 8.10 Beta LiveCD Booting Problems"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by snoguy986 on 2008-10-18
Everytime I try and boot the live beta, it hangs on me.  More specifically, when the splash screen first appears, the progress bar (the one that bounces back and forth initially) gets halfway though and then stops.  There is no disc activity that I can see, and it does not progress past this point.

I attempted to check the disc for errors, but that requires an initial boot apparently and the same thing stated above happens before it can check the disc.

I tried a few boot options (noapic, text to at least see where in the boot process it hangs, but no luck), and I've downloaded and burned multiple copies of the beta.

I'm trying to run it on a Compaq Presario V2424NR laptop.  I'm running a 1.8GHz Turion with 1.5GB of memory and an ATI Xpress 200M vid card.  I've had plenty of success with past ubuntu editions and other flavors of linux on this machine without this happening.

If anyone has any ideas of what's going on I would greatly appreciate some feedback.


Thanks.

---

### Post by overdrank on 2008-10-18
Moved to Intrepid :)

---

### Post by inportb on 2008-10-18
You could also remove the "splash" option to see text instead of the splash.

---

### Post by snoguy986 on 2008-10-18
I gave that a shot, and something I edited (besides the "splash" option) caused it to cooperate.  I deleted everything after the "splash" option, which included "--" and I'm now sitting at the liveCD desktop.

---

### Post by inportb on 2008-10-18
Ah, that's great. Now if you run into the same issue after installing, you might need to do the same thing (or edit your /boot/grub/menu.lst for a more permanent solution)

---

### Post by wwusnobrdr on 2008-10-18
I think the problem is due to acpi.  I have a Compaq Presario laptop as well and when I am not plugged into AC power I have to press the power button ~4 times while the splash screen is loading due to no response.  When I am plugged into AC I only have to do this once.  This happened with LiveCD and continues with an updated Intrepid.  When you put acpi=off in the kernel boot line, it will load just fine.  This never happened with Hardy.

---

