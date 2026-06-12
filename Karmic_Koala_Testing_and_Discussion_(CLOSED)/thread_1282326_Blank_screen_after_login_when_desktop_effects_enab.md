---
title: "Blank screen after login when desktop effects enabled, slow system"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wireless on 2009-10-04
With a suggestion from a post here to fix speed issue, I disabled NEW_FAIR_SLEEPERS and rebooted, and not only speed is totally back to normal, it also seem to fix blank screen after logon when desktop effects are enabled. i enabled NEW_FAIR_SLEEPERS just to recheck and confirm and indeed i got blank screen and slow system again! so please try and post back.
> sudo su
echo NEW_FAIR_SLEEPERS > /sys/kernel/debug/sched_features # to enable it
echo NO_NEW_FAIR_SLEEPERS > /sys/kernel/debug/sched_features # to disable it

And thanks for MarkusThielmann for posting the suggestion! 
Cheers

---

