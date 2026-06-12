---
title: "Ubuntu Update Fails"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by Jerriy on 2011-02-06
The regular/auto update of ubuntu isn't properly working (see image below)

---

### Post by Rubi1200 on 2011-02-06
You could try running the following commands in the terminal:

```
sudo apt-get install -f
sudo dpkg --configure -a
```
Post back if there are errors.

---

### Post by kansasnoob on 2011-02-06
I would certainly try to avoid rebooting until that's resolved!

Depending on what Rubi1200's suggestion renders I'd also consider trying:

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

NOTE: you may or may not need to use the "apt-get -f install" or "dpkg --configure -a" commands more than once, that is after trying any one of the above commands.

Another option is to open Synaptic and look for "broken packages". That will often tell you what needs to be done.

---

