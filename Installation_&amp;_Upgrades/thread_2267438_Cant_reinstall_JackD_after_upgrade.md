---
title: "Cant reinstall JackD after upgrade"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by madtom1999 on 2015-03-01
My system upgraded to 3.16.0-23-generic #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux last night
and ditched a load of programs in the process.
I cant re-install Jack as this would require googleearth (????) and a load of other stuff to be uninstalled.

---

### Post by madtom1999 on 2015-03-04
Done some digging and it seems to be libasound2-plugins:386 causing all the conflict. Removed that and I can install the things I had again!

---

