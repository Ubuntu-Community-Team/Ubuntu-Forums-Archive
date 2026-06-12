---
title: "ABI workaround no longer needed."
date: 2009-02-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-02-02
If this has been cleared before please disregard.

Updated this morning. Reset xorg to its default. Rebooted and compiz etc all very good. In fact compared to Intrepid miles better. Very smooth rotate and the random stuff has gone now on opening apps.
Jaunty looking V good.

---

### Post by vikrant82 on 2009-02-02
Ya, It happened yesterday morning. Everything else seems smooth enough, but glxgears is stuck on 60FPS!!!?? :O

On intel 915GM

---

### Post by Kevbert on 2009-02-02
New Nvidia 180 driver works well for me (no workarounds previously used, just waited for fix) on 7600GS adapter. Compiz works a dream. Driver from repos as opposed to Nvidia site.

---

### Post by philinux on 2009-02-02
> **vikrant82 said:**
> Ya, It happened yesterday morning. Everything else seems smooth enough, but glxgears is stuck on 60FPS!!!?? :O

On intel 915GM

Same here on nVidia.

[edit] Desktop effects had somehow got disabled. Re-enabling got me 3500 fps.

---

### Post by jfernyhough on 2009-02-02
I would assume that would be down to syncing to VBlank (I bet your screen is running a 60Hz refresh rate).

---

### Post by vikrant82 on 2009-02-02
> **jfernyhough said:**
> I would assume that would be down to syncing to VBlank (I bet your screen is running a 60Hz refresh rate).

Yes, indeed its 60Hz.

---

### Post by Starks on 2009-02-02
> **vikrant82 said:**
> Ya, It happened yesterday morning. Everything else seems smooth enough, but glxgears is stuck on 60FPS!!!?? :O

On intel 915GM

Wait. Why would an Intel user need to use the workaround?

I had to enable UXA to get Compiz working again.

---

### Post by vikrant82 on 2009-02-03
> **Starks said:**
> Wait. Why would an Intel user need to use the workaround?

Yes, he doesnt have to. But the Intel driver itself was completely broken (atleast on 915GM, some could use it with NoAccel). That got fixed with the same set of updates which fixed the ABI workaround.

---

