---
title: "No panels after upgrade from 10.10 to 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Kerish on 2011-04-29
Hi

When I did my upgrade and logged into Unity I had no panels at all.
Turns out it was:

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

I had this to get smoother HD playback but it seems it wasn't needed anymore. Video playback was just as good as before even when I removed this.

/Chris

---

### Post by tsint on 2011-05-12
Same happened to me when upgrading to 11.04, but unlike you I need to keep Composite Disable for smooth playback. So I'm stuck with no panels, will probably need to reinstall 10.10.

---

