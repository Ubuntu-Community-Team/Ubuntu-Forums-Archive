---
title: "Fresh install of Ubuntu Server and there are 320 packages manually installed"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by sixcorners on 2011-06-03
I want to some how get a list of the packages I installed. I was hoping that I could just list all of the packages that were not installed automatically as a dependency. It turns out that there are 320 packages that match that description (I think). Is there a way to do what I want to do? Shouldn't all of these dependencies have been installed as a handful of meta-packages instead?

---

### Post by zvacet on 2011-06-07
I think recommended way is 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```

This command will list all installed packages.

---

### Post by sixcorners on 2011-06-19
> **zvacet said:**
> I think recommended way is 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```

This command will list all installed packages.

Although it doesn't answer why a fresh install of ubuntu has 300+ packages installed instead of 5 or so meta-packages, that information is still useful to me. Thanks. :)
I don't know how I will reconcile that information with aptitude search '~i!~E' though which seems to do the same thing. I can't use the man page because the information is so sparse and it references some aptitude reference manual but I don't know how to access that.

---

