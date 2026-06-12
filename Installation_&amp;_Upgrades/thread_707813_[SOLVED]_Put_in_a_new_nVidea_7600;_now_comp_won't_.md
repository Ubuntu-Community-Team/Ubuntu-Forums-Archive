---
title: "[SOLVED] Put in a new nVidea 7600; now comp won't start. stalls at running local boot"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by Majin Zero on 2008-02-25
I just installed a new nVidia 7600.

I have two monitors plugged in to it, apposed to one using the onboard video I had before.

recovery mode can't startx; gives me the error: no screens found.

The install/live CD works fine; haha that's how I'm here posting.

---

### Post by taurus on 2008-02-25
Make sure you turn off the onboard graphic card controller first.  Then boot into recovery mode and reconfigure your X server for the new graphic card.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by Majin Zero on 2008-02-26
> **taurus said:**
> Make sure you turn off the onboard graphic card controller first.  Then boot into recovery mode and reconfigure your X server for the new graphic card.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

Thank you so much! That fixed it.

^_^

---

