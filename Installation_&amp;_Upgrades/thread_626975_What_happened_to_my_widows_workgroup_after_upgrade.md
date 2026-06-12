---
title: "What happened to my widows workgroup after upgrade"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by jerryz on 2007-11-29
I upgraded to 7.10 everything works great except for one small problem. Everyone else run windows and all printers are connected to windows machined and were shared. Previously I was able to access and these printers and print. Now I can't even see the workgroup let alone print. What did the upgrade change?

---

### Post by cmnorton on 2007-11-29
It sounds like your cups definitions were overwritten. During the upgrade, you have a choice of overwriting certain system files or leaving them alone. I found keeping copies of my configurations like cups printers, and letting the config files upgrade was a better move than not having them upgrade.

---

### Post by jerryz on 2007-11-29
OK... So how do I fix it at this point?

> **cmnorton said:**
> It sounds like your cups definitions were overwritten. During the upgrade, you have a choice of overwriting certain system files or leaving them alone. I found keeping copies of my configurations like cups printers, and letting the config files upgrade was a better move than not having them upgrade.

---

### Post by twist2b on 2007-11-29
im thinking synaptic, but if i were you i would re-install the old ubuntu if you dont have to much to re-install... and then GET in ADD/REMOVE whats called KEEP
then whenever something goes bad you can just reset to your previous state.

---

### Post by jerryz on 2007-11-30
And why would I want to go back? I just want to print

> **twist2b said:**
> im thinking synaptic, but if i were you i would re-install the old ubuntu if you dont have to much to re-install... and then GET in ADD/REMOVE whats called KEEP
then whenever something goes bad you can just reset to your previous state.

---

