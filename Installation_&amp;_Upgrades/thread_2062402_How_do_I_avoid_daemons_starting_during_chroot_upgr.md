---
title: "How do I avoid daemons starting during chroot upgrade?"
date: 2012-09-24
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-09-24
I'm doing upgrades on a root filesystem while that root filesystem is in a non-running state under chroot.  This is so I can capture a template from it for distribution to other machines that are replicas.  The problem I'm running into is SOMETIMES some daemons start running inside chroot.  And it's not always the same one.  I'm looking for an option to be sure they don't get started in the first place.

And at least one won't go away.  When it is killed, it comes back.

---

