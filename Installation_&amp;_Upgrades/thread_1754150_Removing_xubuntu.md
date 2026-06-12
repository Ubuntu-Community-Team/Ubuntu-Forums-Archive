---
title: "Removing xubuntu"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by jacqueshappy on 2011-05-09
I use ubuntu and wanted to try xubuntu. Installation worked fine and when I tried it out after a while I wanted to get rid of it and go back to ubuntu. There was no errors or anything, I just wanted to give it a trial run and I just prefer gnome. 
Back on ubuntu, how do I remove the xfce packages?

---

### Post by AlphaLexman on 2011-05-09
```
sudo apt-get remove xfce4
```

---

### Post by jacqueshappy on 2011-05-09
> **AlphaLexman said:**
> ```
sudo apt-get remove xfce4
```

Thanks for replying but that just gives me this

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Toz on 2011-05-09
It could be that something like update manager was running and had it locked. Try again.

---

### Post by jacqueshappy on 2011-05-10
Ok problem solved here. 
For anyone who has same problem, the solving of this problem can be seen [here]("http://http://ubuntuforums.org/showthread.php?t=1754136") , unravelling in my similar thread on kubuntu

---

