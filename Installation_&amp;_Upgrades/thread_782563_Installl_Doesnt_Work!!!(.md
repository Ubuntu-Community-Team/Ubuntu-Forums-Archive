---
title: "Installl Doesnt Work!!!:("
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by chris1890 on 2008-05-05
Hi, have only recently just got the 8.04 version of Ubuntu, first time used, and have been trying to install programmes and bits and pieces however the install now doesnt work.
I installed a driver for my wireless card which didnt work with the network manager, and i started installing Limewire, which then crashed after getting to about 25%, and now any time i run it, it reads: 
"Only one software management tool is allowed to run at the same time.

Please close the other application e.g: 'Update Manager', 'aptitude' or 'Synaptic' first."

however i have none of these applications open or running, and also, going through 'Add/Remove', ubuntu comes up with a box reading:

"E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report."

I have absolutely no knowledge on anything using this kind of system, which is why i need help. please, if theres anything you think will make the .deb install naturally, please say!
Cheers
Chris

---

### Post by corevette on 2008-05-05
go to Applications --> Accessories --> Terminal
and type:
```
sudo dpkg --configure -a
```

---

