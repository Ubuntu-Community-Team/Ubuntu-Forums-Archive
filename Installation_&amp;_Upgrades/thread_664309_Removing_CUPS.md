---
title: "Removing CUPS"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2008-01-11
I want to uninstall CUPS as I have XFCE installed on a really weak laptop, with a small hard drive. The laptop is purely for browsing the web. Nothing else, therefore CUPS is just wasting resources.

I tried to remove CUPS via synaptic, but then synaptic wanted to remove pretty much my entire install as a result.

It seems that the distribution creators have "done a microsoft", and hooked CUPS into absolutely everything, so that it cannot be removed.

Can anyone point me in the right direction for removing CUPS, without trashing my system?

And perhaps the devs would care to explain why they hooked CUPS into everything in such a manner, even XFCE Desktop, ffs. (Yes, I'm more than a bit irritated over this).

---

### Post by jeffus_il on 2008-01-11
No it's not tied in, it's just that so many applications are written to use the cups libraries, so there are many dependencies, most applications print. You can remove the startup script (mine is S19cupsys) from your runlevel, probably in /etc/rc2.d, so it won't run any more. Diskspace may be between 15 to 20 Mb, it you can live with that, leave it.

---

