---
title: "Acer AL1916W display vertically shifted"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2010-11-28
Hi,
I've just installed 10.10 and the screen is shifted down (meaning, there is a black bar at the top of the Acer AL1916W monitor and the bottom menu bar is hidden - the accessible). The Acer controls seem to have no effect on this.
Does anyone have an idea what I'm doing wrong?
Thanks,
David

---

### Post by dino99 on 2010-11-28
might be an xorg.conf issue

if you are using one of the latest ubuntu release, you can rename or delete it, then reboot

---

### Post by dbclinton on 2010-11-28
Thanks. I'll try that tomorrow (when I'm back in the office).
David

---

### Post by dbclinton on 2010-11-28
Wait a second, 10.10 has no xorg.conf file...what exactly should I rename?
Or, to put a different way: how can I reset x settings to restore my proper display?
Thanks

---

### Post by dbclinton on 2010-12-20
Xwindows must have failed to configure properly so I forced it by booting the computer with an old CRT monitor attached. Then I booted again with the Acer and everything was fine.

---

