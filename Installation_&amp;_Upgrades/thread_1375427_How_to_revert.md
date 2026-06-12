---
title: "How to revert?"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by goldfish2 on 2010-01-07
Is there an easy way to revert to a previous installation of programs?

I installed a couple things and upgraded a couple things that my system didn't like... I could probably try to use /var/log/apt/term.log to try and do it by hand, but is there an automated way to do it?

Thanks

---

### Post by Mark Phelps on 2010-01-08
Depends on what you're trying to revert ...

If you have a newer version of an app and want to replace it with an older version, you can do that by either (1) downloading an older .deb file and installing that, or (2) downloading an older tarball containing the source, compiling and making that, and using that.

If you want to go back to an older version of Ubuntu, no, there is no easy way to "revert" -- you have to do a reinstallation.

---

