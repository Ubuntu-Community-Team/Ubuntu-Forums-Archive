---
title: "Live CD wont load"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by Norrit on 2007-02-18
Okay, I've been trying to install off a 6.06 live cd for like 2 days now. I finally fixed my first error by taking the cd drive out of this system and using it to run the live cd on my other system because there were problems between the drive and cd when trying to run it on start up.

The specs of the system im trying to install on are:

CPU: Celeron 366 mhz
Ram: sd 128 mb
HD: 4.5 gig

It reads on startup of the live cd:

Uncompressing Linux... Ok, booting the kernel.
[17179569.184000] ACPI: Unable to locate the RSDP

It goes to the screen with the ubuntu logo and the status bar reads out:

Loading essential drivers... ok
mounting root files system... ok
moving mount points... ok
adding live CD user...

At this point it hangs up for a few minutes and then shuts down to the screen that reads:

Uncompressing Linux... Ok, booting the kernel.
[17179569.184000] ACPI: Unable to locate the RSDP

And just sits there until I reboot.

The CD works fine, I've used it on this system:

2200 amd athlon +
768 mb ram

I'm just not sure why the cd isn't loading up.

---

### Post by Kateikyoushi on 2007-02-18
To run the installer from the live CD you need at least 192MB of ram, so try the alternate install CD.

---

### Post by Norrit on 2007-02-18
I found an old stick of 32 mb sd ram laying around, installed it for 160 mb sd ram, it's running now, slowly, but its working. Thanks a lot Kateikyoushi.

Edit: Nevermind, still moving too slowly, Gonna have to pick up some new cds

---

### Post by matt_risi on 2007-02-19
Norrit: I'd really REALLY recommend downloading and burning the Xubuntu Alternate cd, and installing it on that computer. using straight Ubuntu will have you dipping into swap space pretty much the whole time you use your computer, and that's not fun at all.

Aside: I recently gave out my first Live CD to my friend's dad who has a very recent, very capable desktop PC by HP. Of course they didn't work, and his first impressions of Linux are tarnished as it is. I've used those same CD's numerous times to install on my machines, so it's not a problem with them. Any ideas?

---

