---
title: "Lost 2nd monitor in KDE upgrading to 22.04 from 20.04"
date: 2024-01-17
forum: Installation &amp; Upgrades
---

### Post by gauss on 2024-01-17
I used KDE 20.04 and my two monitors merged normally. I did a **do-release-upgrade** and now my second monitor displays correctly (merged) until the KDE icon disappears and KDE launches. At that point it goes blank. I did a fresh Ubuntu 22.04.03 install, preserving **/home** and then installed **kde-full**. Still KDE (Plasma X11 from SDDM) has the same problem with the second monitor. The first monitor displays normally. When I boot Ubuntu (GNOME) from SDDM both monitors function correctly, merged. When I boot KDE from a live USB KDE linstall ISO, both monitors are normal, merged.

Any debugging hints (e.g. logs to consult) will be gratefully received.

---

### Post by SeijiSensei on 2024-01-18
Have you tried using System Settings > Display to resolve the problem? You can also get there by right-clicking on the Desktop and choosing "Configure Display."

---

### Post by gauss on 2024-01-24
> **SeijiSensei said:**
> Have you tried using System Settings > Display to resolve the problem? You can also get there by right-clicking on the Desktop and choosing "Configure Display."
That was it. Both monitors appeared but the left one had 60 Hz refresh rate and the right one 75 Hz. When I changed the right one to 60 Hz, the right monitor displayed normally, with both monitors creating a merged desktop.

Many thanks.

---

