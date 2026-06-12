---
title: "Installing .deb packages"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by jose3 on 2005-10-21
Hi guys:
Pardon my ignorance, I am kinda new to Linux. 
¿How can I install a .deb package?

Thanks in advance and sorry for the sillly question.:eek:

---

### Post by aysiu on 2005-10-21
If you're absolutely certain you can't install the program through Synaptic Package Manager, even after [enabling extra repositories](http://www.psychocats.net/sources.html), then type ```
sudo dpkg -i packagename.deb
```

---

### Post by jose3 on 2005-10-21
Thanks lot aysiu.

I am actually fighting with dependencies right now. ;) 

Jose

---

### Post by bored2k on 2005-10-21
```
sudo apt-get -f install
``` is great for that.

---

