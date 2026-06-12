---
title: "Build-Essentials Help"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by nescontroller on 2007-04-01
Okay I need to build ndiswrapper from source, however I need build-essentials to do so. Since I cannot connect to the interent I can't do a simple apt-get to get it. My question is there anyway can I download build-essentials plus all of its dependencies in one neat package? Or do I have to go into the dep repo and download them all manually?

---

### Post by taurus on 2007-04-01
The build-essential package is on the CD.  So, insert the install CD into a drive and run

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v 
```

---

### Post by nescontroller on 2007-04-01
Thank you!

---

