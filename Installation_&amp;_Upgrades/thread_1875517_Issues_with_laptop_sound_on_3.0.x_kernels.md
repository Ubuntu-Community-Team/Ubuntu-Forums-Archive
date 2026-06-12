---
title: "Issues with laptop sound on 3.0.x kernels"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by seanlano on 2011-11-04
Since upgrading to the new 3.0.x kernel series (via an upgrade to Oneiric), the sound in my Thinkpad R61i laptop has started to have problems. 
Specifically:
[INDENT][LIST=1]
[*]**Headphones**. The headphones socket doesn't have any output. The computer speakers are muted, but I can't hear anything through the headphones. I have checked that the volume levels in ALSA Mixer haven't gone to zero (as I have read this is/was a problem for some). The computer appears to be playing the sound just fine, and if no headphones are plugged in then I can hear the sound, but the headphones don't work.
[*]**Volume level**. The volume scale seems to be wrong - below about 85% I can hear nothing, the sound is completely muted. It only works between 85-100%.
[/LIST][/INDENT]

Neither of these occurred in Natty with the 2.6.x kernels. I also tried using a 3.0.x realtime kernel before upgrading, and if I booted the 3.0.x kernel then these issues would appear in Natty as well - so I believe this is a kernel issue and not something to do specifically with Oneiric.

What should I try and do to establish the cause of the problem? What changed in the new kernels with respect to sound?

---

