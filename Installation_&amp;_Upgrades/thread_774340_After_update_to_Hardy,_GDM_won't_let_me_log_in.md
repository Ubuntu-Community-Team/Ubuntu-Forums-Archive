---
title: "After update to Hardy, GDM won't let me log in"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Poilar on 2008-04-29
I just updated to Hardy. GDM loads up and I see the graphical login screen.

I enter my username and hit enter. The screen immediately turns black, shows me the log for an instant, and then I'm back at GDM and it's asking me for my username again. I guess GDM is restarting. The same thing happens regardless of what session type I'm using, including failsafe gnome terminal.

If I switch to a text-based login, I'm able to login.

Ideas?

Things of note:
1) I see an error during boot that I don't think I used to get before upgrading: "intel_rng: FWH not detected" I looked this error up though and people seemed to think it was connected to wireless issues so not sure that it's relevant.
2) Typically, after I enter my username a tiny prompt pops up asking me to swipe my finger on my attached fingerprint scanner. When I login via the text-based login, the scan of fingerprint goes through without a hitch though.
3) If I glance at the log for a second as it flashes, I believe I see something about Xmodmap being unable to open display.

Thanks!

**EDIT: As it turns out BioAPI (my fingerprint scanning software) was causing the problem. I disabled BioAPI at login and it let me login completely. Haven't tried yet to scan my finger for sudo, nor have I tried to figure out what's wrong with it yet.**

---

