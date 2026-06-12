---
title: "Dropbox upgrade stuck at 97% unpacking?"
date: 2018-10-07
forum: Installation &amp; Upgrades
---

### Post by zachalexy on 2018-10-07
Hi, since a few days Dropbox notifies me with the screen below. Then I start this update, everything seems fine but somehow Dropbox unpacking stops at 97%. Then, things finish without warning/error and I've got two icons in the topbar. Everything works, I can access my Dropbox folder via Nautilus, etc. Next boot I'm confronted with this upgrade again? Any help, thx, Zach
[ATTACH=CONFIG]281273[/ATTACH]

[ATTACH=CONFIG]281274[/ATTACH][ATTACH=CONFIG]281275[/ATTACH]

---

### Post by westie457 on 2018-10-07
What happens if you install the package suggested in your first picture? 
Or run in a terminal ```
 sudo apt install - f
```

---

### Post by zachalexy on 2018-10-07
Hi, runs just fine.

 Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Dropbox upgrade pop-up keeps showing every reboot?

Thx, Zach

---

### Post by westie457 on 2018-10-12
Did you install dropbox via the repos or their website?

---

### Post by zachalexy on 2018-10-20
Hi westie457,
Tried both, still no luck. Dropbox works fine, but every reboot I still get the upgrade popup again. Thx, Zach

---

### Post by zachalexy on 2018-10-21
Hi, performed a so called advanced reinstall: [https://www.dropbox.com/help/desktop-web/advanced-reinstall](https://www.dropbox.com/help/desktop-web/advanced-reinstall).
Annoying popup at boot gone.
Thx, Zach

---

