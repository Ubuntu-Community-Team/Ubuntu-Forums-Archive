---
title: "Jaunty to Karmic problems"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by CremeBrulee on 2010-01-21
I recently upgraded from Jaunty to Karmic and now firefox keeps crashing and chrome isn't much better, on top of this my computer wont hibernate or suspend anymore.  Someone told me the browser problems were an ipv6 thing but disabling ipv6 in firefox didn't help. Any ideas?

---

### Post by dstew on 2010-01-22
Did you re-install Firefox after you upgraded? I think if you install fresh, that is, from a Live CD onto a new partition, you get a new Firefox that is optimized for whatever kernel you have. If you upgrade, you may still have the old version, or perhaps an old configuration or [profile]("http://support.mozilla.com/en-US/kb/Profiles") that is causing some problems. Also, a plugin could be the problem.

I would recommend a new Firefox install, and a new profile. See if that works OK. Then, start putting in your plugins, and note if and when the bad behavior returns.

If the behavior is truly more widespread than just Firefox, as suggested by no-suspend and Chrome crashing, you might have a more serious system issue. You might try installing a fresh Ubuntu from a Live CD.

---

