---
title: "kickstart problem with kickseed-common"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by pjrp on 2008-06-18
Hi All

I'm trying to set up a Hardy kickstart installation from a local mirror.  It fails downloading installer components with a message "Failed to load installer components.  Loading kickseed-common failed for unknown reasons.  Aborting."

On closer inspection it seems that kickseed-common cannot load because it depends on di-utils, which doesn't exist.

I've also tried using gb.archive.ubuntu.com as the mirror and hit the same problem.

Any ideas?

Phil

---

### Post by dstew on 2008-06-18
There is a bug in the network installer. Check [this thread]("http://ubuntuforums.org/showthread.php?t=824576"), post #8.

---

### Post by pjrp on 2008-06-18
Thanks - that does look like exactly the problem

Phil

---

