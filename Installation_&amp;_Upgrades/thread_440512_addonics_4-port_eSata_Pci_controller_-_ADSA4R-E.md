---
title: "addonics 4-port eSata Pci controller - ADSA4R-E"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by huggy77 on 2007-05-11
I cant get passed the screen that prompts you to hit the f4 button to enter the raid utility...  This is a pre-existing install of fiesty that is completely up to date...  The raid card is connected to a addonics 5 disk array with 2 seagate 750 gig drives...  Any thought?

---

### Post by huggy77 on 2007-05-21
anything... hello (echo)

---

### Post by huggy77 on 2007-06-13
Solved...

The issue was that the bios on the card cannot support the size of those drives...  I called addonics and had them kick me up to there second tier support...  Second tier sent me some files and a procedure... i then hooked  the raid up to a windows machine, booted with a dos6 cd, flashed the card and now it works great....  i have seen alot of frustration with the root of the problem, the sil 3114 card bios... All you have to do is update it...

---

