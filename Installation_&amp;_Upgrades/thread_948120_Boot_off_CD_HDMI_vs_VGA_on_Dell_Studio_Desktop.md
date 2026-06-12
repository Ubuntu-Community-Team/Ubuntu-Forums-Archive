---
title: "Boot off CD: HDMI vs VGA on Dell Studio Desktop"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by rujith on 2008-10-14
I'm trying to run Ubuntu 8.0.4 off a CD on a Dell Studio Desktop.  The
start-up goes fine, but when it's about to start X (or thereabouts),
the VGA display just goes blank.

The Dell Studio Desktop has an Integrated Intel GMA X4500HD graphics
card, with two outputs at the back: HDMI and VGA.  I've connected a
VGA monitor; I don't have an HDMI-capable display.  I'm wondering
whether Ubuntu is trying to output just HDMI via the graphics card?
That does seem unlikely, however.

Here's more details of what I'm doing:

Machine: Dell Studio Desktop
	 Intel Core 2 Duo Processor E7200
	 Integrated Intel GMA X4500HD Graphics

Booting Ubuntu 8.0.4, x86, normal desktop off a CD.  

Boot parameters: deleted "quiet splash --" and added
"all_generic_ide".

Boot using the option "Try Ubuntu without changing
your computer."

I also tried various other options, such as Safe Graphics display,
noapic, nolapic, aic7xxx.aic7xxx=no_probe.  None of those helped.

Anyway, Ubuntu starts booting, spits out a whole bunch of messages,
upto:

   Starting GNOME display manager
   Starting atd
   Starting crond
   Checking battery state 

And then my VGA display just goes blank.

Any help would be appreciated on how to complete the boot.  Somebody's
got to have figured out how to run Ubuntu on these new Dell Studio
Desktop machines!

Thanks,
Rujith de Silva.
[http://rujith.com/](http://rujith.com/)

---

