---
title: "why are packages held back sometimes?"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by herot on 2007-04-12
in my package update window, there are 3 packages that have been held back from being updated: mplayer, libggi2, and kxmame.

why is this?

---

### Post by mcduck on 2007-04-12
There are many possible reasons, but the most likely one is that installing the updates would require either installing additional packages, or removing some installed packages. Update Manager is not allowed to do that, you need to update with Synaptic (or apt-get dist-upgrade) to do that kind of updates.

The other likely reason is that you are using some unofficial repositories, or repositories made for other Ubuntu versions, and that causes dependency problems that Update Manager is not able to solve.

---

