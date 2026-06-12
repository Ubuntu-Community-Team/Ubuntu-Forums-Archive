---
title: "Compaq presario install problems"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by BiggoCharley on 2012-02-20
I have an old (6yrs) Compaq Presario with a sempron 3200 processor.  I am not able to install from the live cd. I have dried jaunty, karmic, maverick and mint Lisa. None of these will boot from the live cd. Everything looks ok at first --the initial splash screens show up but after that the boot hangs up and the screen goes blank.  I am able to boot up from the knoppix cd ok and I have recently installed Windows XP on this machine so I'm convinced that the CD drive is ok. Could there be a compatibility issue with the sempron processor?

---

### Post by ajgreeny on 2012-02-20
Not likely; more likely with the graphics card.

Try again, but at the first screen you see, hit enter, then choose language, and then hit F6 for boot options worth trying.  I would try **nomodeset** first and if that is no good try the others one by one.

---

### Post by BiggoCharley on 2012-02-23
> **ajgreeny said:**
> Not likely; more likely with the graphics card.

Try again, but at the first screen you see, hit enter, then choose language, and then hit F6 for boot options worth trying.  I would try **nomodeset** first and if that is no good try the others one by one.

We never get to the point where we get the "choose Language" screen on the newer versions.  If I were doing this for myself I would try an older version and if I got that to install then upgrade.  But I'm doing this for someone else and i'm afraid that that would be above their paygrade.

---

