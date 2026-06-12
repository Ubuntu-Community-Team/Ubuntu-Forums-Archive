---
title: "upgrade to 10.10 = desktop lockups"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by xenus on 2010-11-18
Thought this was a sound issue as trying to play a sound file guarantees a desktop freeze/lockup and disk thrash after a couple of seconds playback.
Posted the issue in the multimedia forum:

[http://ubuntuforums.org/showthread.php?t=1624212](http://ubuntuforums.org/showthread.php?t=1624212)

However all the diags look ok.  Everything worked fine in 10.04.
Looking for advice on how to troubleshoot further to identify the root cause.

---

### Post by xenus on 2010-11-18
Looks like this is the return of an old bug that was patched some time ago.
Realised I changed the Bios to enable C1E after reading this was a good thing (it should enable power saving modes better).  Having disabled it again, so far the lockups have ceased.

The gory details of the bug/patch are in a post at this link:

[http://lwn.net/Articles/286432/](http://lwn.net/Articles/286432/)

I'd suggest someone who knows the code take a look at this as it appears to be a regression.  I was ok on 2.6.32 but hit the problem with 2.6.35-22  Lucid -> Meercat upgrade.

---

