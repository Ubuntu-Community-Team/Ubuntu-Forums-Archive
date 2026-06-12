---
title: "repository refresh"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by HugoNotte on 2012-05-09
Ubuntu 11.10 64 bit & Ubuntu 12.04 64 bit
I have noticed that the repository refresh done by the update manager is taking quite a long time. Somewhere in March or February the amount of data downloaded for that refresh went up to 30 MB. It seems that a couple of I386 repositories take 5-6 MB each in order to refresh. The problem with this is, that each time the system does a refresh, it either blocks the (slow) ADSL line (flat rate) for around 8 minutes per computer (X3) or when connected to the faster mobile broadband, eats a hefty data chunk and that becomes expensive.

Until some time early this year it hasn't been like that, the update manager's refresh would take less than half the time (=data). Even when I exit the update manager after boot up, the system still does what seems like a repository refresh within the first 40 minutes of running.

Any idea, how to get around this?
Any idea why the data amount has escalated? Many updates only need a fraction of the amount of data downloaded for the refresh itself.

Do other, non ubuntu based ditros have the same problem?

---

### Post by HugoNotte on 2012-05-10
bump

---

### Post by PaulW2U on 2012-05-10
I've noticed that too using both 32-bit and 64-bit Kubuntu.

There's already another thread about this but I can't find it at the moment. I don't think any cause was found for the increased amount of data downloaded each time the repositories are refreshed but I would certainly recommend turning off source code and may be proposed updates.

I download a maximum of 15MB each time by the way, often much less.

Edit: I've just refreshed - 6.5MB downloaded.

Edit: [http://ubuntuforums.org/showthread.php?t=1972335](http://ubuntuforums.org/showthread.php?t=1972335) is the thread that I couldn't find earlier.

---

