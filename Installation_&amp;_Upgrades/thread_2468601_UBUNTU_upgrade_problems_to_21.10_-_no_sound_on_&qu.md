---
title: "UBUNTU upgrade problems to 21.10 - no sound on &quot;firefox.real&quot; &amp; no CTRL.TAB &amp; more"
date: 2021-11-04
forum: Installation &amp; Upgrades
---

### Post by nicolasdiogo on 2021-11-04
Hello,

Just upgraded to Ubuntu 21.10

There were a few silly problems that i encountered, and solved.

Below, I post the simple solution found

```

rm -R ~/.config/gnome-session/
rm ~/.config/pulse/*

```

Perhaps, this information may be useful to others.

---

