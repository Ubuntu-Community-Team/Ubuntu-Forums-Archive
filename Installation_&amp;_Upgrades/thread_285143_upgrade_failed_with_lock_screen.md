---
title: "upgrade failed with lock screen"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by streeto on 2006-10-26
OK, I wanted to upgrade to edgy, so I ran 'gksudo "update-manager -c"'.
It started, said a couple expected things, an then asked to download ~700MB of stuff. I confirmed and went to lunch.

Then I made the terrible mistake: lock the screen (xscreensaver-command -lock). You know, I did not want any of the brainiacs here at the office "make me a favor" and click OK or cancel in anything.

When I returned, I was unable to unlock the screen, it did not accept my password. Ctrl+Alt+FN was a no-go too. I tried "switch user", it hung loading the greeting screen. Eventually I ended having no other alternative except rebooting the system.

Gdm was broken. So I made a 'aptitude dist-upgrade', it asked me to 'apt-get install -f'. It complained about the package x11-common not having success unpacking.

So, I edited /etc/apt/sources.list, replaced every instance of "edgy" for "dapper", then 'aptitude update' and 'aptitude dist upgrade'. Thing went OK. Happilly, after rebooting, I had (sort of) dapper again.

Started the upgrade again, using 'gksudo "update-manager -c"'. The upgrade  happened smoothly.

This is my question, did this happen to anyone? I think the upgrader should ask a confirmation to the user after the download finished, just to avoid this kind of problem.

---

### Post by fakie_flip on 2007-04-22
You could have pushed control alt f1, logged in, and killed the screensaver lock process. Then you would have been able to get back in by pushing control alt f7.

---

