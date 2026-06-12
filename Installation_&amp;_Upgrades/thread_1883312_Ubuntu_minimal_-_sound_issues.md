---
title: "Ubuntu minimal - sound issues"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by matt3839 on 2011-11-18
I've recently installed Ubuntu from the minimal installation disc for a light Openbox setup, and audio output has been my only issue. I've been trying to get it to work for hours, but to no avail.

I have alsa-base, alsa-utils and alsamixergui all installed, along with the proprietary Flash plugin, and I've double-checked that both my hardware and my software output are properly configured. I have used full-featured distributions in the past on the same exact computer, and sound worked perfectly then, so I know my sound device is supported.

Does anybody have any tips for setting up audio output from scratch?

---

### Post by mikewhatever on 2011-11-19
It might be obvious, but the first thing I'd check, is that none of the output channels is muted. It can be done with alsamixer, the 'm' key mutes/unmutes channels.

---

