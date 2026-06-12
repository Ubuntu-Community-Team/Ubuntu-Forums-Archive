---
title: "Mixing apt-* and aptitude NOK?"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by littlebigman on 2010-08-25
Hello

I read somewhere that it's not a good idea to mix the use of apt-* (eg. apt-get, apt-file, etc.) and "aptitude". I guess they're not using the same database to keep track of things.

Problem is, they don't offer the same features:

"apt-get safe-upgrade" doesn't exist, so have to use "aptitude safe-upgrade".

"aptitude show/list mypackage" doesn't show the files that an uninstalled package (ie. still in depot) contains, so have to use "apt-file show mypackage".

So... what's the solution? Is it really a problem to use "apt-*" and "aptitude", depending on what we need to do?

Thank you.

---

