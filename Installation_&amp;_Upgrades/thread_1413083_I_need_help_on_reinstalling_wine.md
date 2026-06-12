---
title: "I need help on reinstalling wine"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by thematrixuum on 2010-02-22
I already have uninstall wine using 

```
$sudo apt-get --purge remove wine
```

then i installed it back using terminal.. but i got this error : 

```
sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

```

can anybody help? thanks a mil

---

### Post by zvacet on 2010-02-22
```
sudo apt-get -f install
```

---

