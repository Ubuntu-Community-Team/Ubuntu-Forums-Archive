---
title: "Update manager - removing unwanted updates"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by RegUB on 2010-02-09
If Update Manager presents updates that I do not want, I do not install them - but they are still presented for selection the next time Update Manager runs. Is there any way of permanently removing them from the list of available updates?

---

### Post by phillw on 2010-02-09
> **RegUB said:**
> If Update Manager presents updates that I do not want, I do not install them - but they are still presented for selection the next time Update Manager runs. Is there any way of permanently removing them from the list of available updates?

From how I understand the workings of Update Manager..

Updates are often bug-fixes and some times security patches - you should really install them. However, under Synaptics Packages Manager you can select a package and 'lock' it so no further updates will take place.

highlight the package you want to lock, Click Package and select Lock Version. This will prevent the package being updated. There may be specific reasons for doing this, but the majority of the time - let it update !!

Just be aware that the lock doesn't apply to apt-get. aptitude can be locked also, however. --> [http://ubuntuforums.org/showthread.php?t=1157330](http://ubuntuforums.org/showthread.php?t=1157330)

Regards,

Phill.

---

