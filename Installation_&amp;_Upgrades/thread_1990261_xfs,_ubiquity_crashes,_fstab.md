---
title: "xfs, ubiquity crashes, fstab"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by marinara on 2012-05-29
I managed to format the ssd I'm installing to, but then ubiquity crashes with a ubi-partman crash.  I'm using xfs, because ext4 should be tweaked for use with an SSD.

Anyhow after much formatting, i managed to get past the ubiquity crash. At which point, I reboot, and my partition has errors.  I manage to fix the errors by changing the fstab line from 
```
<uuid> xfs defaults 0 1 
to <uuid> xfs defaults 0 0

```
why did this happen?

---

