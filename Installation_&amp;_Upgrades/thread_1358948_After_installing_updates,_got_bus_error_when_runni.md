---
title: "After installing updates, got bus error when running firefox"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by mashimario on 2009-12-19
a novice here.

I installed ubuntu 9.10. No any problem since the first day.
Just now, the update manager informed me some updates then I did it.
After that, the system is crashed. 
I am wondering if I can restore my system back to the point before the updates?
If yes, how to do it?

Thanks a lot

I reinstalled the xulrunner, then the porblem is gone.

---

### Post by mashimario on 2009-12-19
After completely removing the firefox```
sudo apt-get --purge remove firefox
```
The system is stable. And then I tried to reinstall the firefox, 
```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```, I still get the "Bus error".

Pleaes, anyone can help me this out?


> **mashimario said:**
> a novice here.

I installed ubuntu 9.10. No any problem since the first day.
Just now, the update manager informed me some updates then I did it.
After that, the system is crashed. 
I am wondering if I can restore my system back to the point before the updates?
If yes, how to do it?

Thanks a lot

---

