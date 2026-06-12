---
title: "Laptop is not charging via USB-C after upgrade from 22.04 to 22.10"
date: 2022-11-24
forum: Installation &amp; Upgrades
---

### Post by mariyo2 on 2022-11-24
Laptop is not charging via USB-C after upgrade from 22.04 to 22.10. Any suggestions what to do?

uname -a
Linux 5.19.0-23-generic #24-Ubuntu SMP PREEMPT_DYNAMIC Fri Oct 14 15:39:57 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

Update: 
- charging works using charging adapter, 
- however it does not work with USB-C dock (HP USB-C Dock G5), 
- before upgrade to 21.10 it worked without issues. 
- Other dock features like multiple displays works.

It might be related to Thunderbolt, because in `Settings -> Privacy -> Thunderbolt` shows: "No devices attached", "Direct Access" is enabled. `boltctl list` returns nothing

Thx

---

### Post by f-muetsch on 2023-02-06
Same problem here! Did you manage to solve this?

---

