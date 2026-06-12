---
title: "Wine installed but still can't open executables"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by miLl3niUm on 2007-04-30
Wine on Ubuntu Feisty 7.04
I have installed wine as the official site said. I added the APT key list (wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -) and the APT source (sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list). Then I installed wine from synaptic package manager but I can't open executables. Why?

(screenshot attached)

---

### Post by drbob07 on 2007-04-30
Try launching it through terminal

CD to the folder your .exe is in

Then ```
wine blah.exe 
```

(remember that the exe name is case sensitive)

---

### Post by miLl3niUm on 2007-04-30
> **drbob07 said:**
> Try launching it through terminal

CD to the folder your .exe is in

Then ```
wine blah.exe 
```

(remember that the exe name is case sensitive)

Thanks man, and I also found another easier way. For others who have this problem, right-click on any executable file. Go to "Open With" tab and click "Add" button. Click on use custom command and type "wine" in the box. Then add and close.

---

### Post by bsmith1051 on 2007-05-11
Exactly!  Now, why doesn't the package do this automatically?

---

