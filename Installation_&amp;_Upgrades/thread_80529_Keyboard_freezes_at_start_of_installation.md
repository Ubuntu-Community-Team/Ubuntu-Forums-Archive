---
title: "Keyboard freezes at start of installation"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by Gen. Lee poor on 2005-10-22
Hi, 

This is actually my second attempt at installing Ubuntu on my old laptop, and being as I got the same error this time, I thought I may try to get it fixed, rather than waste another cd.... 

I have an old HP laptop (UK keyboard), and after booting the Breezy install cd, I get to the language selection screen, but the keyboard is dead (tab, space, enter do not do anything). 
I have tried changing a few parameters as a test (keyboard works fine to type parameters), but no luck. 
I tried setting the keyboard map at startup with a few test parameters (gb, dk and even the example es), but that just led to a freeze before I got to the language selection screen. I also tried disabling the frameset. The result of this was that although the language screen came up, the cursor is flashing, just confirming that the pc is alive. The keyboard is still dead). 
Funnily enough, this is exactly the same error I got when I tried installing 5.04 on the same machine. That time, I guessed the cd had screwed up while downloading and didn't look any further into it. 

If anyone has got any solutions to this, I'd be most grateful.

Thanks

---

### Post by Gen. Lee poor on 2005-10-24
Well, I can answer my own problem here because when I disabled acpi using acpi=off, then the install worked. I say "worked", but actually it didn't. 

After installing, I never got any further than the reboot. The system always hung at the "starting hotplug subsystem" line, and never made it any further. 
I even tried installing 5.04, using the acpi=off line and this crashed at the reboot at the same spot. 

So after reinstalling 3 times, with usb=false, and checking that acpi was off, I gave up (never had any hair to pull out anyway), and went back to a good old Suse 9.1 disc (acpi worked fine, and no hotplug issues). 

I'm a bit disappointed actually, as I really did want to see what everyone was raving about ubuntu for, and liked what I'd seen from the screenshots.

Never mind. I shall maybe try again at the next release.

---

