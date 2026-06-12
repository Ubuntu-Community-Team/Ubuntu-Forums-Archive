---
title: "local cache for apt (/var/cache/apt/archives) ?"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by pokipoki08 on 2008-08-04
I've downloaded a lot of files during system upgrades and would like to use them on other PCs.

How do I enable them after copying to dir /var/cache/apt/archives on the new PC?

It seems Sypnatic or System Upgrade don't see those files at all and tries to download them again.

Thanks.

---

### Post by Elfy on 2008-08-04
```
sudo apt-get update
``` always does it for me

---

### Post by Jack Waugh on 2011-12-21
Thank you both for this informative thread.

Wouldn't it be cool if there were a way to configure APT to communicate with local machines to look for cached packages before going to the sources?

---

### Post by oldos2er on 2011-12-21
Closed, necromancy.

---

