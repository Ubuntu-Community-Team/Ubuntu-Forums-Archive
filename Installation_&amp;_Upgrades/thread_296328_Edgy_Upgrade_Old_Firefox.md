---
title: "Edgy Upgrade Old Firefox"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by the_0ne on 2006-11-09
Just finished a dist-upgrade to Edgy from Dapper.  First thing I couldn't wait for was FF 2.0.  Well, clicked on the Firefox icon and got the old version 1.5.0.  If I go to the package manager, it shows that FF 2.0 is indeed installed.  How do I get to it?  Or do I need to re-install?

---

### Post by the_0ne on 2006-11-09
> **the_0ne said:**
> Just finished a dist-upgrade to Edgy from Dapper.  First thing I couldn't wait for was FF 2.0.  Well, clicked on the Firefox icon and got the old version 1.5.0.  If I go to the package manager, it shows that FF 2.0 is indeed installed.  How do I get to it?  Or do I need to re-install?

Found the problem.  Apparently I had installed a version of firefox that wasn't in the repositories a long time ago.  I found that in /usr/bin/ there were 2 symlinks to 2 versions of firefox.  One was to /opt/firefox and the other to /usr/lib/firefox, which was called firefox.ubuntu.  I changed my gnome icons to point to the firefox.ubuntu link and that fixed the problem.

---

