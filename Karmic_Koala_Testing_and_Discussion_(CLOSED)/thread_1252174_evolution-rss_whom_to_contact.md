---
title: "evolution-rss: whom to contact?"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2009-08-28
I'm following this bug ([https://bugs.launchpad.net/ubuntu/+source/evolution-rss/+bug/406332](https://bugs.launchpad.net/ubuntu/+source/evolution-rss/+bug/406332)) which basically describes why the RSS plugin can't be installed for Evolution. Who would be correcting this problem - the person that maintains this in the Ubuntu repo?

---

### Post by 23meg on 2009-08-28
We don't have per-package maintainers in Ubuntu, except de facto ones for a small number of packages; anyone (even non-developers, via sponsorship) can fix it.

---

### Post by Enigmatic on 2009-08-28
I see. I unfortunately don't know anything about this, otherwise I'd gladly try to fix it. All that needs to be done is to load the previous, stable, non-dev version without the Evolution requirements into the repo, from what I can tell.

---

### Post by 23meg on 2009-08-28
Looks like a packaging bug to me; probably just needs a change in the control file.

---

