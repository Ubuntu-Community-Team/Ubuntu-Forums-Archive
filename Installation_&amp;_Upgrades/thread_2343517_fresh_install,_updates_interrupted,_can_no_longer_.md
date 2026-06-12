---
title: "fresh install, updates interrupted, can no longer boot"
date: 2016-11-17
forum: Installation &amp; Upgrades
---

### Post by bookherd on 2016-11-17
I just installed 16.04 on an old netbook that was previously running 12.04.  Clean install from USB, included updates, seemed to be working okay on first try.  After rebooting, I went to the software center for additional OS updates.  These updates stalled out for over 2 hours, so I rebooted.  I'm now only able to boot to a GNU GRUB screen.  Previously, pressing TAB allowed me to go to BIOS to select boot order; now it does nothing.  Selecting any version of Ubuntu from GRUB gives me a ton of scrolling error messages and dumps me into a BusyBox prompt:

[IMG]https://c6.staticflickr.com/6/5562/30929275421_968d0d530c_b.jpg[/IMG]

I want to boot from the USB and start the install over from scratch.  But how?  My command-line fu is not up to this challenge level.

---

### Post by nikefalcon on 2016-11-17
If **TAB** is the "enter BIOS setup" button, installing Ubuntu should have no effect on that - the BIOS listens for it during POST when the hardware splash screen is being shown(All this will happen before your bootloader runs.). Also, several BIOSs have a separate button that allows one to select the boot device without entering BIOS setup(Usually **F12**). Try spamming the keys.

---

### Post by bookherd on 2016-11-17
Thanks, Nikefalcon. The hardware splash screen says, "Press F2 to run setup, press TAB to display BIOS POST message."  F2 is actually what gets me into the BIOS, but changing boot order there has not allowed me to boot from USB, even before the issue I described (not sure why).  TAB is actually the "separate button that allows one to select the boot device without entering BIOS setup" you're referring to (F12 does nothing).

Anyway, for whatever reason, TAB is actually allowing me to change boot order this morning, and I was able to boot from USB.  Thanks again for your help!

---

