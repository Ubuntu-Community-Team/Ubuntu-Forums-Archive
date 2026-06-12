---
title: "After install nvidia-current driver,i cant get into untiy."
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by edwardsli on 2012-04-28
my video card is nvidia go6150 in hp3431au.
just can get into untiy2d.
if remove nvidia-current that is ok.
what should i do?

---

### Post by JedV on 2012-04-28
I had a similar issue; compiz was VERY laggy after the upgrade.  Removing the nvidia proprietary drivers things went back to normal (i.e. 11.10 performance) for me.

This post helped:  [http://ubuntuforums.org/showpost.php?p=11878577&postcount=2]("http://ubuntuforums.org/showpost.php?p=11878577&postcount=2")

---

### Post by edwardsli on 2012-04-28
Thank you very much.

---

### Post by Bluphx on 2012-04-28
So suggestion is to try to remove the driver from "additional drivers" or startup?

---

### Post by JedV on 2012-05-01
> **Bluphx said:**
> So suggestion is to try to remove the driver from "additional drivers" or startup?

System Settings -> Additional Drivers

I de-activated the proprietary drivers from nVidia, and things are now fine.

---

