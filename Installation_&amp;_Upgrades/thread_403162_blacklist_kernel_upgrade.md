---
title: "blacklist kernel upgrade"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by lonely.numb on 2007-04-06
ok, i do not want to upgrade my kernel, kernel resctricttedmodules and headers as it will break down my installed nvidia driver, and its very irritating to deselect those packages manually...is there any config to do it or adning some "blacklist" thing into some config file?
thank you

---

### Post by yabbadabbadont on 2007-04-06
Select the packages in Synaptic and then go to the Packages menu and choose, "Lock Version".  From then on those packages will not be upgraded.  However, you will want to check updates to see if they come from the Security repository.  If they do, you should update to them for obvious reasons.  :D

---

