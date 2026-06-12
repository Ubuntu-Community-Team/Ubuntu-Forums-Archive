---
title: "Add/Remove program error"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by sk8cheez120 on 2008-04-04
I was in the middle of installing programs then my laptop froze and i had to reboot. AFter rebooting, i tried to reinstall the programs using synaptic or add/remove, It sends me this error that reads:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



PLease help? I don't know what to do or what this message means.

Danny

---

### Post by reyhan on 2008-04-04
type this at the terminal ```
sudo dpkg --configure -a
``` or
```
sudo dpkg -reconfigure -a
```

---

### Post by satanic-yobbo on 2008-04-04
open a terminal by going to applications>accessories> terminal and type in sudo dpkg --configure -a and then your password when prompted for it and it should correct the problem

hahahaha beaten to the punch lol ahh well at least you got a quick response lol

---

