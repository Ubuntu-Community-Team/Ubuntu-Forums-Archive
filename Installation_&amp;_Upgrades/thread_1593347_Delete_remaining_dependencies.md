---
title: "Delete remaining dependencies?"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Blackbird++ on 2010-10-11
Hi,

I've just installed the **ubuntustudio-audio** package, but I decided I would better try to boot the original ISO.
So I deinstalled the meta-packet "ubuntustudio-audio" via Synaptic, but its dependencies weren't deinstalled.
The "computer janitor" didn't find anything.

How can I delete the remaining packets?

---

### Post by oldos2er on 2010-10-11
```
sudo apt-get autoremove
```

---

### Post by Blackbird++ on 2010-10-11
No, that affects nothing.

Update: Ok well I removed them all by hand. Not cool... :|

---

