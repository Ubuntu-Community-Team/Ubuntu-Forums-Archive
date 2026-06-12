---
title: "how do i uninstall 3rd party software like maya?"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by raylistic87 on 2008-06-07
Does anyone has any idea how do i uninstall autodesk maya?

---

### Post by wolfen69 on 2008-06-07
did you search for it in synaptic? if it's there, you can uninstall it.

---

### Post by raylistic87 on 2008-06-09
I can't find it in synaptic.

---

### Post by Misilo on 2009-05-11
In case you installed maya with rpm packages, you can uninstall Maya using the rpm utility. I did it with maya 2008-x64, couse it was giving me some problems running on Ubuntu Jaunty.

1) List the installed package names by entering:

```
    rpm -qa | egrep 'AWCommon|Maya'
```

2) Identify each package name you want to uninstall.

3)Uninstall each listed package using the following command:

```
   rpm -e *Package*
```

   where *Package* is the name obtained in the previous step.

---

### Post by barx on 2010-04-25
Thanx A lot :popcorn:. It worked like a charm xD

---

