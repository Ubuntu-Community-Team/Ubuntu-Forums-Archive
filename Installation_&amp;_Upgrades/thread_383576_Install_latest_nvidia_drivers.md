---
title: "Install latest nvidia drivers"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by stchman on 2007-03-13
Hello all, I was wanting to know how to install the latest nvidia drivers on Edgy.  I believe the drivers are 97.55 from nvidia website.  I can install drivers as long as they are are in the synaptic package manager.  I think the package manager installed 87.75.  The drivers that are on nvidia's website have .run extension.

Thanks

---

### Post by roon on 2007-03-13
If you want the latest nvidia drivers then you can get them by using the "envy" program created by Alberto Milone.You can get it from [here]("http://www.albertomilone.com/nvidia_scripts1.html").Please read the instructions and the info provided on the site before installing the drivers.

---

### Post by Darkdelusions on 2007-03-13
I normally do it the long way....

[LIST=1]
[*]Download the file from nvidia 
[*]Hit Alt F1 to switch to a differnce console and Login
[*]Type sudo /etc/init.d/gdm stop (This kill the Xserver)
[*]Type sudo sh Nivida_XXX-XXX.sh
[*]When the install finishes type sudo /etc/init.d/gdm restart (restart X)
[/LIST]

---

