---
title: "Problems after upgrade"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by koma77 on 2006-10-26
After upgrading to 6.10 from 6.06 the CAD software Eagle stopped working properly.

It has lots of graphics issues.

Also, my old installation of Google Earth hangs when I try to start it.

I've tried reinstalling Eagle via Synaptic, but it is still broken...

---

### Post by rmjb on 2006-10-26
Per chance do you have an ATi card?

- rmjb

---

### Post by koma77 on 2006-10-27
Yes, I've got an ATi Card, and I noticed that a new driver was installed in the update...
Is there a problem with the new driver?

---

### Post by randell6564 on 2006-10-27
> **koma77 said:**
> After upgrading to 6.10 from 6.06 the CAD software Eagle stopped working properly.

It has lots of graphics issues.

Also, my old installation of Google Earth hangs when I try to start it.

I've tried reinstalling Eagle via Synaptic, but it is still broken...

Personally, I would not even TOUCH 'Edgy' until I see it working!

---

### Post by ekravche on 2006-10-27
Try to reinstall google earth using automatix. That would probably fix it, as well as update it

---

### Post by rmjb on 2006-10-27
> **koma77 said:**
> Yes, I've got an ATi Card, and I noticed that a new driver was installed in the update...
Is there a problem with the new driver?

Well, for me my 3D acceleration is all software now, but for some people with ATi cards the 3D accel still works. Test it out by running fglrxinfo

If you see lines with Mesa coming up, it's software.

You can probably install the driver from ATi's site to fix this issue. Try this howto: [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

Replace all places it says dapper with edgy.

- rmjb

---

