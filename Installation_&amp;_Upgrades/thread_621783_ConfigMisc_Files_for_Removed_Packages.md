---
title: "Config/Misc Files for Removed Packages"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by Jabbapop on 2007-11-24
I've been installing and uninstalling a lot of packages. I notice that config files get left behind in the etc and home directories when i uninstall packages. is it good/bad/unnecessary to go ahead and delete those config files? are these files ever automatically purged through routine maintenance? the fact that these files are left behind makes me wonder what other files are left behind when programs get removed. i know from experience with windows that certain uninstall programs can be kind of messy and leave upwards of ten megabytes of stray program files behind, not to mention invalid references to non-extant programs, which tend to slow things down. can this be the case with packages removed with synaptic?

---

### Post by banewman on 2007-11-24
Open synaptic package manager and at the bottom left click status - that will help remove any leftovers. :)

---

### Post by Jabbapop on 2007-11-24
I'm guessing you're referring to not installed (residual config). What I would do is right click on the packages in there and select "Mark For Complete Removal?"

---

### Post by zvacet on 2007-11-24
```
sudo apt-get autoremove
```

---

