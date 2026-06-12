---
title: "How to force downgrade installation of gcc and core libs 'on top' of newer version?"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by Roobert on 2006-04-06
Hi,

I think I may have inadvertently installed Dapper core libraries like gcc-4.0-base 4.0.3-1, lisstdc++6 4.0.2-4, libpoppler1 0.5.1 and others that broke many of my Breezy dependencies. In order to 'resolve' the dependencies, I stupidly allowed Synaptic to remove many (180) packages that it thought were in conflict with the Dapper libs - which included most of my gnome desktop and programs.

Now if I try to re-install my old Breezy libraries to get my gnome-desktop, nautilius, etc, back, Synaptic complains that it can't because there's already a newer version installed. And I can't uninstall the new Dapper libs because doing so might leave me with a completely unusable system!

How can I pull the rug out from under the Dapper libs and get Breezy re-installed without destoying my system?

---

### Post by ranf on 2006-04-07
There is a mechanism called "pinning". 
But I never did that.
```

man apt_preferences
```

---

