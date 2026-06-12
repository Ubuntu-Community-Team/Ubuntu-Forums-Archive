---
title: "What happens to my beta graphics drivers when I do an in-place upgrade?"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by tabarnak on 2013-02-11
I installed them from the AMD website because the fglrx in the repositories breaks X server on my laptop. I've never installed drivers without going through apt-get, so I wonder if going through the upgrade process would break anything. I'm on 12.10 right now, so I'm anticipating 13.04.

---

### Post by tabarnak on 2013-02-11
Anyone with experience with this?

---

### Post by Mark Phelps on 2013-02-11
Been a while since I did this, but when I used such drivers, if I installed them through Additional Drivers, they automatically got updated when I upgraded to a new version; but if I installed them from the AMD site, not only did they NOT get updated, but that trashed the display.

To be safe, you should remove them and replace with the open-source Radeon driver before you do the update.

Besides, do you really want to jump into using an Alpha version?

If you're determined to do that, since there is no easy "rollback" feature, I would first image off your current setup with Clonezilla -- that way, you could restore it if the upgrade is a disaster.

---

