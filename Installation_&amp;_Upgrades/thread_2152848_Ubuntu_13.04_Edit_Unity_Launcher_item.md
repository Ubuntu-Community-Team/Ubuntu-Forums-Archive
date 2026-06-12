---
title: "Ubuntu 13.04: Edit Unity Launcher item"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2013-06-09
Since upgrading to 13.04 my Launcher for Chromium, for instance, still has options such as "Launch with Bumblebee" (for Nvidia laptops) and "Launch Incognito" but they no longer work. Ie clicking on these selections does nothing at all.

How can I edit the Launcher so that the selections work again? I have looked at /usr/share/applications/chromium-browser.desktop but that doesn't seem to be the correct file to edit as, for example, the Bumblebee/optirun selection doesn't even appear there but "Launch with Bumblebee" still appears when the icon is right clicked.

---

### Post by Frogs Hair on 2013-06-09
One thing you might try is remove the launcher and then add again.

---

### Post by stepheny on 2013-06-09
Tried that, but to no avail :-(

---

### Post by stepheny on 2013-06-10
I fixed it by editing ~/.local/share/applications/chromium.browser.desktop. I was also informed that Ubuntu Tweak has the ability to edit Quicklists (which is what the launcher right click menus are called).

Thanks to 25tom and stinkeye.

---

