---
title: "Kubuntu RC won't boot"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cguy on 2010-04-26
I think the latest upgrades caused this.

The Plymouth screen shows up, the dots turn on/off and at one point everything hangs.
I can only reboot and experience this again.

Any ideas on how to get it to work?

---

### Post by cguy on 2010-04-26
I commented "show-splash" in
/etc/init/plymouth.conf
&
/etc/init/plymouth-splash.conf
I could boot up, then I uncommented them but it keeps on working.

So basically nothing is different from he state when I posted this thread but booting works now.

---

