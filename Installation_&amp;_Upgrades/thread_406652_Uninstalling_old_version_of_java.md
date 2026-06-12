---
title: "Uninstalling old version of java"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by Franscisco on 2007-04-11
This is my problem, I just install Frostwire, but before doing this installation, downloaded Java, but I did not know it was an old version which would not let Frostwire work. So I installed Java again, but now Java 5.0 which lets Frostwire run, but when I open Frostwire, the program closes itseft everytime I want to open it. I tried to open Frostwire from the Terminal, it opens, but when it closes, the Terminal says that an old java and an new java versions were causing the error(Frostwire closes).
Any help! 
how to uninstall the older java version?

---

### Post by zvacet on 2007-04-11
Uninstall it with synaptic.

---

### Post by YoG%*@ on 2007-04-11
you can switch between installed java versions:
```

sudo update-alternatives --config java

```

mx

---

### Post by iansane on 2007-12-28
> **mux said:**
> you can switch between installed java versions:
```

sudo update-alternatives --config java

```

mx

Awesome! that was simple. I had the same problem. I Chose the newest version and frostwire works now.

---

### Post by underdog512 on 2007-12-28
> **mux said:**
> you can switch between installed java versions:
```

sudo update-alternatives --config java

```

mx

maybe in the next version of ubuntu we should set the sun java as the default.

---

### Post by underdog512 on 2007-12-28
> **mux said:**
> you can switch between installed java versions:
```

sudo update-alternatives --config java

```

mx

maybe in the next version of ubuntu we should set the sun java as the default.

---

### Post by iansane on 2008-01-02
so can anyone tell me why I have 6 places to get java from? If the other 5 are no good it would be nice for them to not be there. They are not under synaptic. At least not as jre.x.x.x. Are some of them used for other programs? I guess it'll take a while to find and remove them.

---

