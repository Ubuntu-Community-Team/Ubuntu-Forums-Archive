---
title: "Synaptic  Package Mgr Error"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by Sierra_Dave on 2007-12-22
Hi,

I was in the process of upgrading to 7.10 and the screen locked-up.  Since it was late, I just shut down.  I rebooted this morning and it loads 7.10, but when I went into Synaptic Package Mgr.., I got this error message:

"E: dpkg was interrupted, you must manually run ' dpkg--configure -a' to correct the problem.  
E:_cache->open() failed, please report."


I opened "Terminal" and ran the commands but got no such command exists.  Is my syntax off or am I missing something that must be loaded?

I was almost done with the upgrade and I am writing this on the machine that was upgraded.
Thanks for the Help!
Dave:confused:

---

### Post by Pumalite on 2007-12-22
sudo dpkg --configure -a

---

### Post by Sierra_Dave on 2007-12-22
Thanks Pumalite!:)

---

### Post by Pumalite on 2007-12-22
You are welcome. Good luck!

---

