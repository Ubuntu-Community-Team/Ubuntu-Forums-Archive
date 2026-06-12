---
title: "do-release-upgrade, option to exclude packages/drivers?"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by bartgrefte on 2016-04-30
A while ago I read that apt has the option to exclude packages from an apt-get upgrade. But what about do-release-upgrade, does that command have a similar option? do-release-upgrade --help didn't show such an option.

To be a bit specific, there are a couple of packages and a driver that (unless something has changed) don't have certain options I need enabled before compiling, meaning that when those packages get updated, I have to recompile those again.

Is there a way to prevent that with a do-release-upgrade?

---

