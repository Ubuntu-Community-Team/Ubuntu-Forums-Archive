---
title: "[SOLVED] Broken openoffice.org-hyphenation-en-us"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by CptPicard on 2008-10-03
My removal of ubuntu-desktop removed pretty much everything else too and now I'm trying to get this Hardy box back to normal. However, I've got a broken package (openoffice.org-hyphenation-en-us), and apt is stuck on it and I really don't know what to do. The error that causes the failure is "update-openoffice-dicts: not found" in the postinst/postrm script.

Seems like it's the same issue as here:

[http://ubuntuforums.org/showthread.php?t=698140](http://ubuntuforums.org/showthread.php?t=698140)
[http://ubuntuforums.org/showthread.php?t=92365](http://ubuntuforums.org/showthread.php?t=92365)

But I haven't managed to resolve it. Any kind of forcing options I can think of passing to dpkg don't have an effect either.

Would hate to have to completely reinstall from scratch... :(

---

### Post by Bluebell392 on 2008-10-03
Can you get into a terminal window? If so, try to install any package with the option --fix-broken.

---

