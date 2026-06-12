---
title: "[SOLVED] system can not update"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by sneeks on 2008-02-04
i have check the threads for other similer probs but to no avail.
after trying to install the dvd codecs for the player(totem)
the system froze for a bit then i got this error message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repor
after this the system will not update atall,or install anything.
any idea's chaps....

---

### Post by OffAxis on 2008-02-04
A package is halfway installed.
Literally, run that command.

```
sudo dpkg --configure -a
```

and all will be well again.

---

### Post by sneeks on 2008-02-04
> **OffAxis said:**
> A package is halfway installed.
Literally, run that command.

```
sudo dpkg --configure -a
```

and all will be well again.

will give it a go,ta mate

---

### Post by zvacet on 2008-02-04
If you didn´t do it yet do it now

```
sudo apt-get install ubuntu-restricted-extras
```

---

