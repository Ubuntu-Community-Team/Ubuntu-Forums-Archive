---
title: "Latest Karmic update kicks X out from under &amp; breaks gnome cpufreq-applet"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Blueshell on 2009-10-12
I've been running Karmic from the beta at the beginning of the month in the AMD64 alternate install.  I just upgraded an hour ago.  Halfway through the upgrade, it apparently restarted X in the middle of the upgrade, hence shooting itself in the foot.  It did -not- reboot, nor did it break an ssh I had from elsewhere.  When X autorestarted, it came up with (a) some error message about the Gnome Power Monitor's configuration that vanished after a couple seconds so I couldn't read it, and (b) no response to keyboard or mouse.  I ssh'ed in and reran update-manager; it completed this time, though I had to reboot at least twice to really finish.

At this point, things look okay EXCEPT that I'd had the gnome cpufreq applet in my taskbar, and post-update, it was now stuck at my CPU's maximum rate, and set to "performance" whereas it was at "ondemand" pre-update.  I clicked on it and set it to "ondemand", but nothing changed---my cpu is still at maximum clock.  As far as I can see, this applet is now broken.

Anyone else seen this?  Anyone know of any relevant bugs or should I just file one?

Thanks...

---

### Post by Blueshell on 2009-10-12
Huh.  I tried another reboot (the machine again came up set to "performance"), but this time setting it to "ondemand" actually -did- modify the CPU frequency, instead of claiming it was ondemand but still having the CPU at max rate (and I'd checked that rate by looking in sys/devices/...etc).  This reboot was from poweroff and not just "sudo reboot"; I don't know if that has anything to do with it.

Unfortunately, rebooting once again comes up -again- in "performance" and needs manual resetting to "ondemand" (which at least works).  I could have sworn that, before I took the update an hour ago, repeated reboots -stuck- in ondemand!  Did this change?  Am I hallucinating?  How do I make this stick?

[Still doesn't address the update kicking X out from under itself, but I assume that's a short-term bug and won't exist in the final release.]

---

