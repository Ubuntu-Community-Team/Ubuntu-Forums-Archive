---
title: "Unable to boot from Installation CD (Lucid/Beta2)"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Antenne on 2010-04-15
Hi. 
After running Gentoo for years, I decided to take a hard disk failure as chance to try something else. Downloaded Lucid Beta2 from the mirror, burned it on MacOSX (verified ok) and tried to boot the machine. No Joy.

All I get is a somewhat purplish screen with UBUNTU and red/white alternating dots. A some point, the dots stop all red. There seems to be no way to get any console window to check log for messages. I removed all pieces of hardware I could sensibly remove as I assumed that device may not be recognized. What's left now: DVD, HD and an NVIDIA grafics card (dual head). Still the same.

Is this a known problem? An ideas on how to proceed? Maybe how to obtain some log info?

Thanks.

---

### Post by Antenne on 2010-04-15
To reply to myself:
It appears that pressing [SPACE] on grub loading opens a selection menu. In this menu, press F6 and remove the *splash* option (to get more output, remove *silent* as well).

With this, I could boot into the live image without further issues. Oh my.

---

