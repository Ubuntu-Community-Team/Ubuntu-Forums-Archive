---
title: "firefox broken after Hardy install"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by mudman on 2008-06-08
I did a recent installation of Hardy but firefox will not run. I get a dialog box the says firefox is already running and that I should restart firefox or reboot. I did a ps aux and a ps -A. There was no sign of firefox there otherwise I would have killed the process. anyone else have this problem?

---

### Post by aysiu on 2008-06-08
Firefox 3 is particularly buggy this way if Firefox isn't quit cleanly. With Firefox 2, all you had to do was ```
killall firefox-bin
```

Theoretically, you can delete ~/.mozilla/firefox/*profilename*/.parentlock

In my experience, you're better off rebooting.

---

