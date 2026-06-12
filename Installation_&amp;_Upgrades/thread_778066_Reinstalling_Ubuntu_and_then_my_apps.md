---
title: "Reinstalling Ubuntu and then my apps"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by coolaj86 on 2008-05-01
How can I go about creating a list of packages that I've installed which are not part of the base ubuntu desktop setup so that I can reinstall them as well?

I know that this will give me listing of all software that has been installed, perhaps there's something else I could run to get a list of the basic packages and then run 'diff' on it?
```
dpkg --get-selections > ~/installed-software.txt
```

---

### Post by coolaj86 on 2008-05-01
(bump)

---

