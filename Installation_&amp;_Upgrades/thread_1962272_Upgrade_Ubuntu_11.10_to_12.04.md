---
title: "Upgrade Ubuntu 11.10 to 12.04"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by thodoris1012 on 2012-04-20
I was trying to install via wubi Ubuntu 12.04 beta 2 but the installation was crashing due to an error... errno 5. Finally I installed ubuntu 11.10. If I try to upgrade it to Ubuntu 12.04 beta 2 or to 12.04 - when it released - may I have problem with my files if the installation fail?
Thank you...!
_______________________________________________
Windows Vista Home Premium (x32)
3GB RAM
224GB Hard Disk
AMD Turion x2 64 (2.3 G)

---

### Post by jadtech on 2012-04-20
if you have an amd 64bit processor and  amd ati graphic card there are afew step you should take there is a bug when you try to update from update manager..

I just successfully upgraded  wubi install from 11.10 to 12.04 after 3 times failing and having to uninstall  and re-install wubi..
the key is to install  (apt python-apt) in advance of upgrading , and run the upgrade from term window not the manager ..

---

