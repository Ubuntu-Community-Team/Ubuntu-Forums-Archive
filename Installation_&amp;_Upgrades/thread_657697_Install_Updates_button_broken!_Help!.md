---
title: "Install Updates button broken! Help!"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by blueberry17 on 2008-01-03
Now when I try and click the "Install Updates" button in the Update Manager, I get the same effect as clicking the "Check" button next to it: it runs the "Checking for Updates" process. See the attached screen shot to see what I mean! How can I fix this? I already tried reinstalling the update manager and I also tried clicking the "Mark all Upgrades" button in Synaptic, but it shows there is nothing to upgrade. I need to be able to install updates in the future! Help!

---

### Post by taurus on 2008-01-03
Have you tried from a terminal to see if you can update your machine?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

p.s.  Make sure you have closed the update manager window first before you run those two commands.

---

### Post by blueberry17 on 2008-01-03
That worked! However, I still want to know what was the actual problem with the Update Manager program and how to fix it.

---

### Post by adamvert on 2008-02-05
I'm also having this problem - did you find a solution?

---

