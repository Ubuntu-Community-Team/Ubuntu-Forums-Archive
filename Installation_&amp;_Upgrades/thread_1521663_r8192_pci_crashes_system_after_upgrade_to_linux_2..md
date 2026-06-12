---
title: "r8192_pci crashes system after upgrade to linux 2.6.32-23-generic"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by scotty64 on 2010-07-01
I installed the latest updates (that included the 2.6.32-23 kernel and linux-firmware updates) on my Samsung NB30 netbook yesterday. I used to use ndiswrapper for the built in RTL wireless because the native kernel modules did not work. I tried it with the latest 2.6.32-23 kernel again and noticed that things got much worse: The whole system freezes when the driver is loaded.
As a consequence I blacklisted these modules again and I am back to ndiswrapper now...

---

