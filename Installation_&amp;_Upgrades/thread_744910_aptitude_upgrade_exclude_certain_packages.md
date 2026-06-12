---
title: "aptitude upgrade exclude certain packages"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by reduxtion on 2008-04-04
When running aptitude upgrade, is it possible to exclude one or two packages for this run only and not any other time?

---

### Post by brian_p on 2008-04-04
> **reduxtion said:**
> When running aptitude upgrade, is it possible to exclude one or two packages for this run only and not any other time?

Read the manual (man aptitude) and look at the 'hold/unhold' option. Does this do what you want?

---

### Post by kellemes on 2008-04-04
> **reduxtion said:**
> When running aptitude upgrade, is it possible to exclude one or two packages for this run only and not any other time?

aptitude hold packageX
aptitude unhold packageX

---

