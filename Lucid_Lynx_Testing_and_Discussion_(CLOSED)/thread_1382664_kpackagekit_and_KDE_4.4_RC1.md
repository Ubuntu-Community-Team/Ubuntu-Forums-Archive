---
title: "kpackagekit and KDE 4.4 RC1"
date: 2010-01-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by biasquez on 2010-01-16
when i try to load "software update", i have this error:

impossible loading lib /usr/lib/kde4/kcm_kpk_update.so: (/usr/lib/libkpackagekitlib.so undefined symbol.......)

according to me, kpackagekit/packagekit version is very old...why in lucid there isn't new version?

---

### Post by VMC on 2010-01-16
> **biasquez said:**
> when i try to load "software update", i have this error:

impossible loading lib /usr/lib/kde4/kcm_kpk_update.so: (/usr/lib/libkpackagekitlib.so undefined symbol.......)

according to me, kpackagekit/packagekit version is very old...why in lucid there isn't new version?
My Ubuntu packagekit version = 0.4.9+20090825-0ubuntu6. Is that the same as yours. I'll check kubuntu when I log in.

Edit: Kubuntu 10.04 A2:

kpackagekit = Version: 0.4.2-0ubuntu3
packagekit  = Version: 0.4.9+20090825-0ubuntu6

---

### Post by biasquez on 2010-01-16
sorry, i have packagekit 0.5.5 (installed from ppa for lucid), restoring your version of packagekit, this fix my problem. i hope that ubuntu/kubuntu team will update packagekit soon.

---

### Post by meborc on 2010-01-17
issues arise when using alfa system + PPA

important thing is to make a difference if the problem is with the OS or the package from PPA

when reporting issues, please state the version of the package as well as if any ppa's were used

---

