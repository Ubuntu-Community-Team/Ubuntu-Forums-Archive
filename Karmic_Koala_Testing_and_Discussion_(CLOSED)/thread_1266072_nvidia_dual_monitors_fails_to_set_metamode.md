---
title: "nvidia dual monitors fails to set metamode"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougEdey on 2009-09-14
FIXED with latest libc updates


Since the latest batch of updates (including reverting to libc6-ubuntu9) I can no longer set dual monitors (this was fine beforehand) and appears to be a regresssion. Has anyone seen this/fixed it or are people still fixing libc?

from disper output:

could not find nor create MetaMode:  :: DFP-0: 1920x1200 +1920+0, DFP-1: 1920x1200 +0+0

Nvidia-settings is the same message but slightly different syntax, probably just formatting differences.

---

