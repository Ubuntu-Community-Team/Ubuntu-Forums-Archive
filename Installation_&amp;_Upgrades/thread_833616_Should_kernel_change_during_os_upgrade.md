---
title: "Should kernel change during os upgrade?"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by Tomone on 2008-06-18
I've been having some problems since upgrading from gutsy to hardy and I also noticed that my computer is still using the 2.6.22 kernel. Is this something that's supposed to change? And if not, could having an older kernel cause any problems?

---

### Post by avtolle on 2008-06-18
Yes, the kernel should have changed. Most interesting. Probably, you'll need to do a clean install.

---

### Post by Tomone on 2008-06-18
Thanks. That's what I figured, but I didn't want to do a clean install without conformation.
Also, the only information on my conky display that I have for no reason is the kernel version. But good thing that was there or else I wouldn't have noticed the non-change.

---

### Post by avtolle on 2008-06-18
One thought for something you might try first```
sudo apt-get update
sudo apt-get uprade
sudo apt-get dist-upgrade
```to see if this will update your kernel (and other packages). Otherwise, if you don't want to do this, go for the clean install.

---

