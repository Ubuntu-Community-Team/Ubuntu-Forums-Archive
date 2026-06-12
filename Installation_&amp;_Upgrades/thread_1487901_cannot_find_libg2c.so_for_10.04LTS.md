---
title: "cannot find libg2c.so for 10.04LTS"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by janec on 2010-05-19
Hi,  Which package do I need to get libg2c.so install on 10.04LTS  - Thank you.

---

### Post by davidmohammed on 2010-05-19
download and install the deb package from [here]("http://packages.ubuntu.com/jaunty/libg2c0")

even though it was created for jaunty, it should be still compatible with lucid

---

### Post by dinofelis on 2010-06-03
I'm having the same problem (trying to use the garfield-9 executable from CERN), and it's looking for 
```

./garfield-9: error while loading shared libraries: libg2c.so.0: cannot open shared object file: No such file or directory

```

However, with the link given above, the gdebi package manager tells me:
```

Error: Dependency is not satisfiable: gcc-3.4-base (= 3.4.6-8ubuntu2)

```

so I'm hesitating to install this.  Should I install then also its dependencies (gcc3.4) or will this screw up gcc4.4 ?

---

### Post by dino99 on 2010-06-03
this dependency come from an old release, so you have to recompile this app with actual gcc packages, or install jaunty

---

