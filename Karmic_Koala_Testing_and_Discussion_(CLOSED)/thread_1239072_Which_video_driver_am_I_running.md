---
title: "Which video driver am I running?"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Stochastic on 2009-08-13
It's been ages since I've needed to sort this out, but the latest RT kernel doesn't want to play nice with my video driver.  How do I report which one I'm using?  I know it's an ATI Radeon XPRESS 200m card if that helps at all.

---

### Post by taavikko on 2009-08-13
> **Stochastic said:**
> It's been ages since I've needed to sort this out, but the latest RT kernel doesn't want to play nice with my video driver.  How do I report which one I'm using?  I know it's an ATI Radeon XPRESS 200m card if that helps at all.

If haven't made any adjustements, then it's "radeon"
You can check by looking "/var/log/xorg.0.log"

---

