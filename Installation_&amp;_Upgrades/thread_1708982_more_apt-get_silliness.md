---
title: "more apt-get silliness"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-03-17
Usually I just use "apt-get remove" to remove a package.  I guess I need to now get in the habit of using "apt-get purge" instead.

Consistently I find the issue that SOMETIMES a package will not completely be removed.  It still shows with a status of "rc" from "dpkg -l".  Supposedly "apt-get purge" should remove the remaining config files.  But it always (this is why I say "consistently, because of this always) fails.  The message say the package cannot be removed because it is not installed.

Now if I had used "apt-get purge" instead, to begin with, it completely gets rid of the package (except for broken packages such as "nsd3").  But it fails if I first do it partially with "apt-get remove" then follow that with "apt-get purge".

---

### Post by dabl on 2011-03-17
```
man apt-get
``` seems pretty clear on the difference in "remove" and "purge".  "Remove" only removes the named package.  "Purge" removes associated dependent packages and configuration files.

---

### Post by Skaperen on 2011-03-17
> **dabl said:**
> ```
man apt-get
``` seems pretty clear on the difference in "remove" and "purge".  "Remove" only removes the named package.  "Purge" removes associated dependent packages and configuration files.Right.  That's as it should be.  But as I described, it doesn't work with apt-get if you do the purge after doing the remove.  OTOH, "dpkg --purge" does work, so this cannot be blamed on the remove step having removed the info needed for the purge step.  It's apparently apt-get doing things wrong.

---

