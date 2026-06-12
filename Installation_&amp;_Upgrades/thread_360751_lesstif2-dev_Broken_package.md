---
title: "lesstif2-dev Broken package"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by kasnas01 on 2007-02-13
Hello,
I am trying to install the package lesstif2-dev but I kept getting the following error:
The following packages have unmet dependencies:
  lesstif2-dev: Depends: libxft-dev but it is not going to be installed
                Depends: libfontconfig1-dev but it is not going to be installed
                Depends: libfreetype6-dev but it is not going to be installed
E: Broken packages
 
can anyone suggest a solution,
many thanks,

---

### Post by mikewhatever on 2007-02-13
As you can see, the package you're trying to install needs dependencies, namely three additional packages: bxft-dev, libfontconfig1-dev, libfreetype6-dev. Install them first and then see how it goes.

---

### Post by kasnas01 on 2007-02-14
I have got the same error for the last two packages you mentioned,
and could not find the first one,
thanks,

---

