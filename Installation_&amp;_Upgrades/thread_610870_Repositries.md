---
title: "Repositries"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by Cloudedbrains on 2007-11-12
Do you need too add repositories under gutsy gibbon ??
If so how do I do it ??

---

### Post by MrFSL on 2007-11-12
You would add repos if you want to install software that is not available in the regular repos. Understand that software in other repos isn't necessarily fully supported or guaranteed in anyway.

To get started you might want to look at the contents of: /etc/apt/sources.list

For more detailed information open a terminal and type:
```
man sources.list
```

---

### Post by taurus on 2007-11-12
What repos do you plan to add?  Just edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and add whatever you want to the end of it.  Just be careful what repos you want to add because it could cause more trouble later.

Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Cloudedbrains on 2007-11-12
Can u add them without the terminal window, eg, via add remove preferences ??
I notice there are 2 already in - are they enough ??

---

### Post by taurus on 2007-11-12
You can with System -> Administration -> Synaptic Package Manager -> Settings -> Repositories -> Third-Party Software -> Add.

---

### Post by MrFSL on 2007-11-12
In Feisty Click On:

System > Administration > Software Sources

---

### Post by Cloudedbrains on 2007-11-12
I've found where to add them but are there any recommended 3rd party ones for Gutsy at all ??

---

### Post by taurus on 2007-11-12
What are you looking for?

---

### Post by Cloudedbrains on 2007-11-12
I've found where to add them but are there any recommended 3rd party ones for Gutsy at all ??

---

### Post by Cloudedbrains on 2007-11-13
Oh I've solved this one lol
Under Gutsy the 3rd party stuff is listed in add/remove anyway if you choose to show it listed :)

No extra repositries needed it seems :)

---

