---
title: "Partial Upgrade this morning.?"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-10-15
I saw the sticky about "partial upgrades", but as far as I know unless you click the partial upgrade button, you cannot see what updates are being installed, or am I wrong?  Im trying to be cautious.

---

### Post by philinux on 2009-10-15
> **sox fan Matt said:**
> I saw the sticky about "partial upgrades", but as far as I know unless you click the partial upgrade button, you cannot see what updates are being installed, or am I wrong?  Im trying to be cautious.

When you see partial just click the cancel button.

---

### Post by sports fan Matt on 2009-10-15
Ok, that worked ..:)  In the past though did that not cancel everything and you had to start with the update manager again?

---

### Post by DougieFresh4U on 2009-10-15
Remember, you can always check via terminal what it really wants to do(remove)

```
The following packages are BROKEN:
  libavcodec-extra-52 libpostproc-extra-51 
The following packages will be REMOVED:
  libavformat-unstripped-52{a} rtkit{u}
```

and
```
The following packages have unmet dependencies:
  libpostproc-extra-51: Conflicts: libpostproc-unstripped-51 but 4:0.5+svn20090706-2ubuntu2 is to be installed.
  libavcodec-extra-52: Conflicts: libavcodec-unstripped-52 but 4:0.5+svn20090706-2ubuntu2 is to be installed.
```

---

