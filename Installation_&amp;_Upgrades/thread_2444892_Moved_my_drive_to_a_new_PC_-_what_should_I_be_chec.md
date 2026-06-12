---
title: "Moved my drive to a new PC - what should I be checking?"
date: 2020-06-05
forum: Installation &amp; Upgrades
---

### Post by NotQuiteSU on 2020-06-05
I took my Ubuntu 18 LTS SSD and moved it to a new chassis. Everything booted up no problem, but I'm wondering if there is something I should be checking to make sure I'm using the fell capabilities of the new chip. I know in Windows, I could check device manager and a few other things, but I'm not sure if anything needs to be checked on Ubuntu

---

### Post by Tadaen_Sylvermane on 2020-06-05
Normally one wouldn't search for a problem without a symptom. It will show up somewhere obvious if the problem exists at all.

---

### Post by TheFu on 2020-06-06
For CPUs, not really. There are some settings to disable certain security bug fixes for still supported CPUs. Some of those fixes reduce performance by 10-30% depending on the workload.  i don't have a clue how to do that.  i figure that if a security fix/mitigation is important enough to be a default, then i want it.

For any specialized HW, just check that drivers are loaded and working with the expected performance.  A GPU or GigE performing below normal would be were i started.  i'd not get drivers outside the Ubuntu ecosystem unless something is broken.

Some storage needs to be tuned too when the controller changes. That's more important for RAiD setups.

---

