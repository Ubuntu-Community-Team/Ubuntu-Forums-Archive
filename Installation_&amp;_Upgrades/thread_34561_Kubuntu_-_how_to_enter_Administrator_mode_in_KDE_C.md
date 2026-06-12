---
title: "Kubuntu - how to enter Administrator mode in KDE Contol Center"
date: 2005-05-15
forum: Installation &amp; Upgrades
---

### Post by andersno on 2005-05-15
When trying to get my wireless card working, I have to use the KDE Control Center to enable wlan0, but cannot get access to the Networks Settings.

How do I enter Administrator mode?

---

### Post by Xian on 2005-05-15
You have to expand the Network Settings module to make the "Administrator Mode" button visible. It is located on the bottom, right hand side of the dialogue window. Press that and then enter you password.

---

### Post by Xian on 2005-05-15
If for any reason that doesn't work then goto the KDE start menu, choose 'Run Command' and enter this:

kdesu kcontrol

This will make the entire KDE Control Center to behave in admin mode.

---

### Post by andersno on 2005-05-15
Thank you, that did the trick.

---

